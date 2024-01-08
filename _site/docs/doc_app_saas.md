# 私有云部署

私有云部署功能允许您将OAuthApp平台部署在您自己的服务器上，从而实现更高的安全性和更大的自由度。本文档将介绍如何进行私有云部署，切换至私有云环境，以及其他相关操作。

## 在线部署

OAuthApp平台提供了在线部署功能，您可以在OAuthApp官方网站上开始私有云部署。在在线部署过程中，您需要选择服务器配置、地区、计费方式等选项，并遵循相应的指引完成部署过程。在部署过程中，请确保您的服务器满足系统要求，并保留相关证书和账户信息。

操作步骤

1，在左侧导航栏中依次点击“设置”、“私有云部署”。

2，点击“在线部署”，然后选择部署区域、服务器配置等参数。

3，点击“创建订单”，确认订单细节后点击“立即支付”。

4，跳转到支付宝页面，使用支付宝APP扫码支付，支付成功后自动返回订单详情。

5，点击“返回列表”，查看您购买的云服务器。

6，点击“访问”，页面显示Index，代表私有云部署成功。

=== "图例 1-1"
    ![](https://docs.oauthapp.com/doc_app_saas/1-1.png){ loading=lazy }
=== "图例 1-2"
    ![](https://docs.oauthapp.com/doc_app_saas/1-2.png){ loading=lazy }
=== "图例 1-3"
    ![](https://docs.oauthapp.com/doc_app_saas/1-3.png){ loading=lazy }
=== "图例 1-4"
    ![](https://docs.oauthapp.com/doc_app_saas/1-4.png){ loading=lazy }
=== "图例 1-5"
    ![](https://docs.oauthapp.com/doc_app_saas/1-5.png){ loading=lazy }
=== "图例 1-6"
    ![](https://docs.oauthapp.com/doc_app_saas/1-6.png){ loading=lazy }
=== "图例 1-7"
    ![](https://docs.oauthapp.com/doc_app_saas/1-7.png){ loading=lazy }
=== "图例 1-8"
    ![](https://docs.oauthapp.com/doc_app_saas/1-8.png){ loading=lazy }
=== "图例 1-9"
    ![](https://docs.oauthapp.com/doc_app_saas/1-9.png){ loading=lazy }


## 切换私有云

在成功部署私有云后，您可以在登录界面或个人设置页面切换至私有云环境。切换至私有云环境后，您将可以享受私有云部署所带来的安全性和自由度。请确保您已经登录OAuthApp平台的私有云环境，并妥善保管相关登录信息。

操作步骤

1，点击“https://www.oauthapp.com”按钮进行切换

=== "图例 2-1"
    ![](https://docs.oauthapp.com/doc_app_saas/2-1.png){ loading=lazy }
=== "图例 2-2"
    ![](https://docs.oauthapp.com/doc_app_saas/2-2.png){ loading=lazy }

## 注册事项

!!! quote "在私有云部署成功后，首次注册的账号将默认为管理员账号，拥有最高权限。请确保您妥善保管管理员账号的登录信息，避免泄露和丢失。"

## 系统配置

若您的应用需要自动添加域名解析，以实现自定义域名的功能，您需要为AccessKey授予AliyunDNSFullAccess权限。该权限允许系统自动为应用站点添加域名解析，确保自定义域名能够正确指向您的应用。

操作步骤

1，点击下拉菜单中的“系统配置”

2，输入阿里云AccessKey ID，AccessKey Secret。

=== "图例 3-1"
    ![](https://docs.oauthapp.com/doc_app_saas/3-1.png){ loading=lazy }
=== "图例 3-2"
    ![](https://docs.oauthapp.com/doc_app_saas/3-2.png){ loading=lazy }

!!! tip "创建阿里云AccessKey参考"

1，打开阿里云Accesskey管理首页，https://ram.console.aliyun.com/manage/ak

2，点击“创建用户”

3，勾选“OpenAPI 调用访问”，点击“确定”，完成创建

4，点击”用户名称“进入详情页

5，依次点击“权限管理”、“新增授权”，添加“AliyunDNSFullAccess”权限，然后点击“确认”

6，返回用户详情页，依次点击“认证管理”、“创建AccessKey”，完成创建。

=== "图例 4-1"
    ![](https://docs.oauthapp.com/doc_app_saas/4-1.png){ loading=lazy }
=== "图例 4-2"
    ![](https://docs.oauthapp.com/doc_app_saas/4-2.png){ loading=lazy }
=== "图例 4-3"
    ![](https://docs.oauthapp.com/doc_app_saas/4-3.png){ loading=lazy }
=== "图例 4-4"
    ![](https://docs.oauthapp.com/doc_app_saas/4-4.png){ loading=lazy }
=== "图例 4-5"
    ![](https://docs.oauthapp.com/doc_app_saas/4-5.png){ loading=lazy }
=== "图例 4-6"
    ![](https://docs.oauthapp.com/doc_app_saas/4-6.png){ loading=lazy }
=== "图例 4-7"
    ![](https://docs.oauthapp.com/doc_app_saas/4-7.png){ loading=lazy }

## 自定义域

私有云环境支持自定义域名的绑定，您可以在自定义域页面中添加和管理您的自定义域名。通过自定义域名，您的应用可以在私有云环境中使用自定义的URL访问，增强品牌形象和用户体验。

操作步骤

1，点击“自定义域名”

2，点击“添加域名”，

3，填写“自定义域名”，按照要求添加CNAME解析，然后点击“提交绑定”

4，点击“上传证书”，将自定义域名对应的SSL证书上传到服务器

5，点击域名右侧下拉菜单的“更改绑定”，选择刚刚上传的证书，点击“绑定证书”完成绑定

=== "图例 5-1"
    ![](https://docs.oauthapp.com/doc_app_saas/5-1.png){ loading=lazy }
=== "图例 5-2"
    ![](https://docs.oauthapp.com/doc_app_saas/5-2.png){ loading=lazy }
=== "图例 5-3"
    ![](https://docs.oauthapp.com/doc_app_saas/5-3.png){ loading=lazy }
=== "图例 5-4"
    ![](https://docs.oauthapp.com/doc_app_saas/5-4.png){ loading=lazy }
=== "图例 5-5"
    ![](https://docs.oauthapp.com/doc_app_saas/5-5.png){ loading=lazy }
=== "图例 5-6"
    ![](https://docs.oauthapp.com/doc_app_saas/5-6.png){ loading=lazy }
=== "图例 5-7"
    ![](https://docs.oauthapp.com/doc_app_saas/5-7.png){ loading=lazy }
=== "图例 5-8"
    ![](https://docs.oauthapp.com/doc_app_saas/5-8.png){ loading=lazy }


## 远程桌面链接

私有云环境支持远程桌面链接，您可以通过远程桌面链接方式远程连接到您的云服务器，进行系统配置和管理。请确保您使用安全的远程桌面连接方式，并妥善保管远程连接的登录信息。

操作步骤

1，点击下拉菜单中的“远程桌面连接”

2，牢记IP地址、登录账号、登录密码

3，使用windows远程桌面链接工具，依次输入IP地址、登录账号、登录密码

4，点击“连接”，登录远程云服务器

=== "图例 6-1"
    ![](https://docs.oauthapp.com/doc_app_saas/6-1.png){ loading=lazy }
=== "图例 6-2"
    ![](https://docs.oauthapp.com/doc_app_saas/6-2.png){ loading=lazy }
=== "图例 6-3"
    ![](https://docs.oauthapp.com/doc_app_saas/6-3.png){ loading=lazy }
=== "图例 6-4"
    ![](https://docs.oauthapp.com/doc_app_saas/6-4.png){ loading=lazy }
=== "图例 6-5"
    ![](https://docs.oauthapp.com/doc_app_saas/6-5.png){ loading=lazy }
=== "图例 6-6"
    ![](https://docs.oauthapp.com/doc_app_saas/6-6.png){ loading=lazy }
=== "图例 6-7"
    ![](https://docs.oauthapp.com/doc_app_saas/6-7.png){ loading=lazy }

## 续费、订单记录

在私有云环境中，您可以查看云服务器的续费情况和订单记录。请及时续费云服务器，以确保您的私有云环境持续稳定运行。

=== "图例 7-1"
    ![](https://docs.oauthapp.com/doc_app_saas/7-1.png){ loading=lazy }
=== "图例 7-2"
    ![](https://docs.oauthapp.com/doc_app_saas/7-2.png){ loading=lazy }
=== "图例 7-3"
    ![](https://docs.oauthapp.com/doc_app_saas/7-3.png){ loading=lazy }
=== "图例 7-4"
    ![](https://docs.oauthapp.com/doc_app_saas/7-4.png){ loading=lazy }

<!-- ## 其他
除了上述功能，私有云部署页面还提供了其他相关操作，例如查看服务器信息、管理应用和用户、备份数据等。您可以根据实际需要进行相应的操作。 -->

[^1]:创建阿里云AccessKey教程：[https://docs.oauthapp.com/doc_appsetting_aliyun.html](https://docs.oauthapp.com/doc_appsetting_aliyun.html)


## 其他

### 服务器回收机制

如果您的云服务器长时间未续费，可能会被OAuthApp平台回收。在回收前，我们会提前通过邮件通知您，请及时处理以避免数据丢失。

### 私有云如何配置oauthapp.js的API服务器地址？

=== "HTML"

    ```HTML linenums="1"
     <!-- data-server 属性替换为你的 私有云服务器地址，例如：https://example.xxxx.com -->
     <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" 
        data-appid="{{appId}}" data-server="{{server}}"></script>
    ```