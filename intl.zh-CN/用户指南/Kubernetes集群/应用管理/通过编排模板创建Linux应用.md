# 通过编排模板创建Linux应用 {#task_vwv_xwl_vdb .task}

在容器服务 kubernetes 模板编排中，您需要自己定义一个应用运行所需的资源对象，通过标签选择器等机制，将资源对象组合成一个完整的应用。

创建一个 kubernetes 集群，参见[创建Kubernetes集群](intl.zh-CN/用户指南/Kubernetes集群/集群管理/创建Kubernetes集群.md#)。

本例演示如何通过一个编排模板创建 nginx 应用，包含一个 Deployment 和 Service，后端 Deployment会创建Pod 资源对象， Service 会绑定到后端 Pod 上，形成一个完整的 nginx 应用。

1.  登录[容器服务管理控制台](https://cs.console.aliyun.com)。
2.  在 Kubernetes 菜单下，单击左侧导航栏中的**应用** \> **无状态**，进入无状态（Deployment）页面。
3.  单击页面右上角的**使用模板创建**。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16659/155687019711072_zh-CN.png)

4.  对模板进行相关配置，完成配置后单击**创建**。 

    -   **集群**：选择目标集群。资源对象将部署在该集群内。
    -   **命名空间**：选择资源对象所属的命名空间，默认是 default。除了节点、持久化存储卷等底层计算资源以外，大多数资源对象需要作用于命名空间。
    -   **示例模板**：阿里云容器服务提供了多种资源类型的 Kubernetes yaml 示例模板，让您快速部署资源对象。您可以根据 Kubernetes Yaml 编排的格式要求自主编写，来描述您想定义的资源类型。
    -   **添加部署**：您可通过此功能快速定义一个Yaml模板。
    -   **使用已有模板**：您可将已有编排模板导入到模板配置页面。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16659/155687019711074_zh-CN.png)

    下面是一个 nginx 应用的示例编排，基于容器服务内置的编排模板。通过该编排模板，即可快速创建一个属于 nginx 应用的 deployment 。

    **说明：** 容器服务支持Kubernetes Yaml编排，支持通过`---`符号将资源对象分隔，从而通过一个模板创建多个资源对象。

    ```
    apiVersion: apps/v1beta2 # for versions before 1.8.0 use apps/v1beta1
    kind: Deployment
    metadata:
        name: nginx-deployment
        labels:
          app: nginx
    spec:
        replicas: 2
        selector:
          matchLabels:
            app: nginx
        template:
          metadata:
            labels:
              app: nginx
          spec:
            containers:
            - name: nginx
              image: nginx:1.7.9 # replace it with your exactly <image_name:tags>
              ports:
              - containerPort: 80
    		  
    ---
    
    apiVersion: v1     # for versions before 1.8.0 use apps/v1beta1
    kind: Service
    metadata:
       name: my-service1        #TODO: to specify your service name
       labels:
         app: nginx
    spec:
       selector:
         app: nginx             #TODO: change label selector to match your backend pod
       ports:
       - protocol: TCP
         name: http
         port: 30080            #TODO: choose an unique port on each node to avoid port conflict
         targetPort: 80
       type: LoadBalancer        ##本例中将type从Nodeport修改为LoadBalancer
    ```

5.  单击**创建**后。会提示部署状态信息。成功后，单击**Kubernetes 控制台**前往Kubernetes Dashboard 查看部署进度。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16659/155687019711075_zh-CN.png)

6.  在 Kubernetes Dashboard 里，您可以看到 my-service1 服务已成功部署，并暴露了外部入口。单击**外部入口**的访问地址。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16659/155687019711084_zh-CN.png)

7.  您可以在浏览器中访问 nginx 服务欢迎页面。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16659/155687019811086_zh-CN.png)


您也可返回容器服务首页，单击左侧导航栏中的**路由与负载均衡** \> **服务**，查看该nginx的服务。

