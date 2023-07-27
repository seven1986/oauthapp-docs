# 微信开放平台

本文档介绍了在PC端使用微信"扫一扫"登录的配置说明。

## 说明

- [x] 微信“扫一扫”，在PC端扫码登录

???+ note "提示"
    
    1，跳转登录授权地址：https://www.oauthapp.com/openwechat/**{{appId}}**/Authorize

    2，回调页面通过URL的 app_wechat 参数获取用户数据

    **请将{{appId}}替换为OAuthApp应用的AppID**
    
## 配置项

### 微信开放平台ClientID

应用唯一标识，在微信开放平台提交应用审核通过后获得

### 微信开放平台ClientSecret

应用密钥AppSecret，在微信开放平台提交应用审核通过后获得

### 微信开放平台用户授权范围 

| 授权域  | 用户侧使用流程 |
| ----------- | ----------- |
| snsapi_login | （1）用户使用微信“扫一扫”，在PC端扫码（2）客户端打开授权页，完成登录授权 |

### 微信开放平台回调地址

用户在微信授权后，回调到您网站的地址，用于处理微信返回的授权信息并完成登录流程。

授权完成将附加**app_wechat**参数到回调地址，该参数包含了用户信息、access_token等数据。

在使用微信网页PC端扫码登录功能之前，您需要先在微信开放平台注册并获取相关的开发者信息。

接入流程

（1）注册微信开放平台（open.weixin.qq.com）帐号，并完成开发者资质认证

（2）申请【网站应用】并审核通过后可以使用，查看[开发文档](https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&id=open1419316505&token=&lang=zh_CN)

## 截图

![](https://docs.oauthapp.com/doc_appsetting_openwechat/1.png){ loading=lazy }