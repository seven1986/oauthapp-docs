# 微信公众平台

本文档介绍了在微信公众号[^1]相关配置说明。

## 说明

- [x] 微信公众号 H5网页开发

- [x] 微信应用内 H5登录

???+ note "提示"
    
    1，跳转登录授权地址：https://www.oauthapp.com/wechat/**{{appId}}**/Authorize

    2，回调页面通过URL的 app_wechat 参数获取用户数据

    **请将{{appId}}替换为OAuthApp应用的AppID**

## 配置项

### 微信H5 JS默认配置

页面默认需要申请授权的JS接口集合[^2]，用于处理前端的相关逻辑和请求。

多个接口用"**,**"分隔。

### 微信公众号ClientSecret

公众号的appsecret

### 微信公众号ClientID

公众号的唯一标识


### 微信用户授权范围 

在进行微信网页登录时，需要指定用户授权的范围，例如基本信息、头像、昵称等。

可选值：

| 授权域  | 用户侧使用流程 |
| ----------- | ----------- |
| snsapi_base | 静默授权 |
| snsapi_userinfo | （1）用户在H5内点击登录，唤起授权弹窗（2）用户侧完成登录授权 |


### 微信回调地址

用户在微信授权后，回调到您网站的地址，用于处理微信返回的授权信息并完成登录流程。

授权完成将附加**app_wechat**参数到回调地址，该参数包含了用户信息、access_token等数据。


## 截图

![](https://docs.oauthapp.com/doc_appsetting_wechat/1.png){ loading=lazy }

[^1]:微信公众号接入流程：

    （1）注册微信公众号，选择“服务号”类型，并完成微信认证

    （2）在公众号管理后台设置回调域名
    
    （3）接入微信登录能力，查看[开发文档](https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421140842)

[^2]:JS接口列表：[https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#63](https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#63)