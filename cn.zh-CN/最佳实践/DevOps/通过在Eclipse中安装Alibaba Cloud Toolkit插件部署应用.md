# 通过在Eclipse中安装Alibaba Cloud Toolkit插件部署应用 {#concept_wjz_dkj_yfb .concept}

本文档将向您介绍如何在Eclipse中安装Cloud Toolkit，并使用Cloud Toolkit快速部署一个应用。

## 背景信息 {#section_iwc_kkj_yfb .section}

Alibaba Cloud Toolkit for Eclipse（下文简称 Cloud Toolkit）是一个免费的 IDE 插件，帮助阿里云用户更高效的使用阿里云。

您只需注册或使用一个已有的阿里云账号，即可免费下载Cloud Toolkit。下载完成后，您可以将该插件安装到Eclipse中。

当您在本地完成应用程序的开发、调试及测试后，通过该插件即可轻松将应用程序部署到阿里云。

## 安装Cloud Toolkit {#section_pl1_rkj_yfb .section}

**前提条件**

-   下载并安装[JDK 1.8 或更高版本](https://www.oracle.com/technetwork/java/javase/downloads/index.html)。
-   下载并安装适用于 Java EE 开发人员的[Eclipse IDE、4.5.0（代号：Mars）或更高版本](https://www.eclipse.org/downloads/)。

有两种安装Cloud Toolkit 方式：在Eclipse Marketplace中下载安装和直接通过Cloud Toolkit的官方地址安装。

**在Eclipse Marketplace中下载安装**

1.  启动Eclipse。
2.  在菜单栏中选择**Help** \> **Eclipse Marketplace...**。
3.  在Eclipse Marketplace对话框中**Find**右侧的文本框中输入**Alibaba Cloud Toolkit**，然后回车。
4.  单击搜索结果中**Alibaba Cloud Toolkit**右下角的**installed**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533265_zh-CN.png)

5.  按照Eclipse安装页面的提示，完成后续安装步骤。

**直接通过Cloud Toolkit 的官方地址安装**

**说明：** 如果您无法连接Eclipse Market服务器，请选择这种安装方式。

1.  启动Eclipse。
2.  在菜单栏中选择**Help** \> **Install New Software**。
3.  在Available Software对话框的**Work with**文本框输入Cloud Toolkit for Eclipse的URLhttp://toolkit.aliyun.com/eclipse/。
4.  在下面的列表区域中勾选需要的组件 `Alibaba Cloud Toolkit Core`和`Alibaba Cloud Toolkit Deployment Tools`，并在下方的Details区域中不勾选`Connect all update sites during install to find required software.`

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533267_zh-CN.png)

5.  配置完成后，单击**Next**，Elipse开始安装插件，并显示安装进度。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533268_zh-CN.png)

6.  按照Eclipse安装页面的提示，完成后续安装步骤。

**预期结果**

插件安装成功后，重启Eclipse，您可以在工具栏看到Alibaba Cloud Toolkit的图标。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533269_zh-CN.png)

## 获取Access Key ID和Access Key Secret {#section_lqw_glj_yfb .section}

您本地的应用部署到云端时，都需要使用阿里云上的资源、应用。所以在部署前，需要设置您的阿里云账号信息，以保证拥有使用、管理相关资源、应用的权限。

**使用阿里云主账号获取Access Key ID和Access Key Secret**

1.  登录[容器服务管理控制台](https://cs.console.aliyun.com)。
2.  将光标滑动（非单击）到控制台页面右上角您的头像上，在弹出的下拉菜单中单击**accesskeys**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533270_zh-CN.png)

3.  在安全提示对话框中单击**继续使用AccessKey**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533271_zh-CN.png)

4.  在安全信息管理页面，用户 AccessKey区域右侧单击**创建AccessKey**，在手机验证对话框中单击**点击获取**后输入验证码。
5.  记录该账号的Access Key ID和Access Key Secret。

**使用 RAM 子账号获取Access Key ID和Access Key Secret**

1.  登录[RAM子账号登录页面](https://signin.aliyun.com/login.htm)，输入您的子账号，单击**下一步**，再输入密码，单击**登录**。
2.  将光标滑动（非单击）到控制台页面右上角您的头像上，在弹出的下拉菜单中单击**AccessKey管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533273_zh-CN.png)

3.  在安全信息管理页面，用户 AccessKey区域右侧单击**创建AccessKey**。

    **说明：** 

    -   如果您当前子账号的**创建AccessKey**置灰不可用，请使用主账号对该子账号授权，可参考[使用子账号](../../../../cn.zh-CN/用户指南/Kubernetes 集群/授权管理/使用子账号.md#)。
    -   在新建用户AccessKey对话框中，单击AccessKey详情右侧下拉箭头，记录当前子账号的**AccessKeyID**和**AccessKeySecret**。
    -   这是用户AccessKey可供下载的唯一机会，请及时保存！

## 设置Access Key ID和Access Key Secret {#section_zkr_hlj_yfb .section}

1.  启动Eclipse。
2.  在工具栏单击**Alibaba Cloud Toolkit**图标，在下拉菜单中单击**Alibaba Cloud Preference...**。
3.  在Preference \(Filtered\)对话框的左侧导航栏中单击**Accounts**。
4.  在Accounts区域设置**Access Key ID**和**Access Key Secret**，然后单击**OK**。

    **说明：** 

    -   如果您已有阿里云账号，单击**Get existing AK/SK**， 参考文档获取**Access Key ID**和**Access Key Secret**。
    -   如果您没有阿里云账号，单击**Sign up**，进入阿里云账号注册页面，注册账号。注册完成后按照上述方式获取**Access Key ID**和**Access Key Secret**。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533310_zh-CN.png)


## 部署应用 {#section_v12_llj_yfb .section}

**前提条件**

-   您已使用设置**Access Key ID** 和 **Access Key Secret**的阿里云账号进入[容器镜像服务控制台](https://cr.console.aliyun.com/cn-hangzhou/new)，创建容器镜像仓库，可参考[仓库构建](https://help.aliyun.com/document_detail/60997.html)。
-   您已使用设置**Access Key ID** 和 **Access Key Secret**的阿里云账号进入[容器服务管理控制台](https://cs.console.aliyun.com)，并使用镜像创建应用，可参考[使用镜像创建无状态Deployment应用](../../../../cn.zh-CN/用户指南/Kubernetes 集群/应用管理/使用镜像创建无状态Deployment应用.md#)或[使用镜像创建有状态StatefulSet应用](../../../../cn.zh-CN/用户指南/Kubernetes 集群/应用管理/使用镜像创建有状态StatefulSet应用.md#)。

1.  设置用于打包本地镜像的Docker环境。
    1.  在 Eclipse 工具栏单击**Alibaba Cloud Toolkit**， 在下拉菜单中单击**Alibaba Cloud Preference...**。
    2.  在Preference \(Filtered\)对话框的左侧导航栏中单击**Docker**。
    3.  在Docker界面中设置可连接的 Docker 环境，包括本地和远程两种方式，然后单击**OK**。

        **本地Docker环境**

        -   如果您本地为Mac或Linux操作系统，勾选**Unix Socket**后单击**Browse...**，选择本地的Docker安装目录。
        -   如果您本地为Windows操作系统，勾选**Tcp Connection**后在 URI 右侧文档框输入本地 Docker 的 URI，如`http://127.0.0.1:2375`。
        **远程Docker环境**

        勾选**Tcp Connection**后在 URI 右侧文档框输入远端Docker环境的URI（包括 IP 地址和端口），如`http://127.0.0.1:2375`，并确保远程主机的 HTTP 服务开启。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533347_zh-CN.png)

2.  在 Eclipse 界面左侧的Package Explorer中右键单击您的 Docker 应用工程名，在弹出的下拉菜单中选择**Alibaba Cloud** \> **Deploy to CS Kubernetes...** 。
3.  在Select a package method对话框选择本地应用程序的**Context Directory**和**Dockerfile**（通常会根据您本地的应用工程自动识别并设置 ），然后单击**Next**。

    **说明：** 您可以根据您的需要决定是否勾选**Use maven build**使用Maven构建应用工程。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533348_zh-CN.png)

4.  在Select a Repository对话框选择容器镜像服务的地域，命令空间和镜像仓库，然后单击**Next**。

    **说明：** 如果您还没有镜像仓库，在对话框右上角单击**Create a new repository**跳转到容器镜像仓库创建镜像仓库。创建步骤可参考[容器镜像服务](https://help.aliyun.com/product/60716.html)文档。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280533349_zh-CN.png)

5.  在Deploy Project to CS Kubernetes对话框选择容器服务Kubernetes的**Cluster**、**Namespace**和**Deployment**，然后单击**Finish**。

    **说明：** 

    -   如果您还没有创建容器服务Kubernetes的Deployment，在对话框右上角单击**Create a new Kubernetes deployment**，跳转到[容器服务管理控制台](https://cs.console.aliyun.com)创建Deployment。创建步骤可参考[容器服务 Kubernetes 版](https://help.aliyun.com/product/85222.html)文档。
    -   Alibaba Cloud Toolkit目前只支持以更新方式部署您的应用，需要您预先在控制台手动创建一个部署（Deployment），然后基于该部署将镜像替换为您的镜像。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280633350_zh-CN.png)


**预期结果**

部署开始后，Eclipse的Console区域会打印部署日志。您可以根据日志信息检查部署结果。

**说明：** 如果您在使用Cloud Toolkit过程中有任何疑问，欢迎您扫描下面的二维码加入钉钉群进行反馈。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65297/154380280633352_zh-CN.png)

