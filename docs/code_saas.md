---
tags:
  - 功能应用
---

# 在线部署

## 说明

本文档提供了服务器的创建、支付和使用的详细步骤和说明，以帮助您顺利部署和管理您的服务器。

| 镜像版本  | 更新说明 |
| ----------- | ----------- |
| oauthapp.238.23.1 | 数据导入导出、证书工具 |
| oauthapp.238.7.2 | .net core 6.0 升级 7.0 |
| oauthapp.234.26.4 |  |

## 创建服务器

### 步骤 1: 选择配置

进入服务器创建页面。

- 设置一个二级域名，作为服务器的访问地址。

- 选择服务器的部署区域，可选的区域有：上海、北京和广东。

- 根据您的需求选择适当的云服务器配置，可选的配置有：基础版、高级版和企业版。

- 选择计费方式，可选的方式包括：按小时、按天、按月和按年计费。

- 根据所选计费方式选择购买时长：

    - 小时计费可选择1至23小时，

    - 天计费可选择1至30天，

    - 月计费可选择1至11个月

    - 年计费可选择1至2年。


![1](https://docs.oauthapp.com/code_saas/1.png){ loading=lazy }

### 步骤 2: 在线支付

在服务器创建页面，填写完服务器配置和购买时长后，点击"创建订单"按钮。
在主机列表中会新增一条记录，找到对应的记录，在右侧点击"立即支付"按钮。
使用支付宝扫码支付完成支付流程。支付成功后，服务器将在5至10分钟内完成云端部署。

![2](https://docs.oauthapp.com/code_saas/2.png){ loading=lazy }

![3](https://docs.oauthapp.com/code_saas/3.png){ loading=lazy }

![4](https://docs.oauthapp.com/code_saas/4.png){ loading=lazy }

![5](https://docs.oauthapp.com/code_saas/5.png){ loading=lazy }

![6](https://docs.oauthapp.com/code_saas/6.png){ loading=lazy }

![7](https://docs.oauthapp.com/code_saas/7.png){ loading=lazy }

![8](https://docs.oauthapp.com/code_saas/8.png){ loading=lazy }


### 步骤 3: 使用

在oauthapp发布工具导航栏中，切换到您的私有云服务器。
您可以使用服务器提供的功能和服务，进行开发、部署和管理您的应用程序。

**切换到您的服务器后，请立即注册账号，首个账号为默认管理员**

![9](https://docs.oauthapp.com/code_saas/9.png){ loading=lazy }

![10](https://docs.oauthapp.com/code_saas/10.png){ loading=lazy }

![11](https://docs.oauthapp.com/code_saas/11.png){ loading=lazy }


## 自定义域名

???+ note "提示"
    **部署成功后，默认您还需要用[证书申请工具](https://docs.oauthapp.com/code_ssltool/)，申请1张{你的域名}.oauthapp.com的证书进行绑定替换，否则创建的应用站点将不支持https协议**。

如果是自定义域名，则按照下面的步骤进行操作：

1，进入自定义域名页面，添加解析记录

2，上传域名证书（必须是支持通配符类型的SSL证书。**否则创建的应用站点将不支持https协议**）

3，打开系统配置面板，更新下面的内容：

- 服务器域名：改为自定义域名
- 配置 阿里云 AccessKey ID和密钥（AccessKey必须设置权限：**AliyunDNSFullAccess、AliyunDirectMailFullAccess、AliyunDysmsFullAccess**）

## 远程桌面链接

您可以使用远程桌面客户端软件连接到服务器，以便进行服务器的管理和操作。请确保您已安装合适的远程桌面客户端软件，并按照提供商的指南进行设置和连接。

???+ note "提示"
    **安全起见，请勿随意修改程序数据库或代码，以防止造成不可预知的错误或数据丢失。**
    在进行任何更改之前，请确保您理解相关操作的影响，并备份重要数据和配置文件。

![image](https://docs.oauthapp.com/code_togglesaas/11.png){ loading=lazy }

![image](https://docs.oauthapp.com/code_togglesaas/12.png){ loading=lazy }

**使用远程桌面链接工具，依次输入：IP地址，登录账号、登录密码，进入远程服务器**

![image](https://docs.oauthapp.com/code_saas/13.png){ loading=lazy }

## 续费、服务器回收

服务器的使用有效期为所购买的时长。
超过使用有效期后，服务器将被自动回收，数据记录不会保存。

**请确保在使用有效期内续费服务器或及时备份重要数据，以免数据丢失和服务中断。**
通过按照上述步骤进行服务器的创建、支付和使用，您将能够轻松部署和管理您的云服务器。