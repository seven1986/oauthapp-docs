# QQ

本文档介绍了在应用中实现QQ开放登录[^1]的配置说明。

## 说明

- [x] QQ 登录

???+ note "提示"
    
    1，跳转登录授权地址：https://www.oauthapp.com/qq/**{{appId}}**/Authorize

    2，回调页面通过URL的 app_qq 参数获取用户数据

    **请将{{appId}}替换为OAuthApp应用的AppID**


## 配置项

### QQClientID

申请QQ登录成功后，分配给网站的appid。

### QQClientSecret

申请QQ登录成功后，分配给网站的appkey。

### QQ回调地址

用户在QQ登录授权后，会被重定向至您预先设定的回调页面。

授权完成将附加**app_qq**参数到回调地址，该参数包含了用户信息、access_token等数据。

## 截图

![](https://docs.oauthapp.com/doc_appsetting_qq/1.png){ loading=lazy }


[^1]:QQ互联网站应用接入流程：[https://wiki.connect.qq.com/%e7%bd%91%e7%ab%99%e5%ba%94%e7%94%a8%e6%8e%a5%e5%85%a5%e6%b5%81%e7%a8%8b](https://wiki.connect.qq.com/%e7%bd%91%e7%ab%99%e5%ba%94%e7%94%a8%e6%8e%a5%e5%85%a5%e6%b5%81%e7%a8%8b)