# 微博

本文档介绍了在应用中实现微博开放登录[^1]的配置说明。

## 说明

- [x] 微博 登录

???+ note "提示"
    
    1，跳转登录授权地址：https://www.oauthapp.com/weibo/**{{appId}}**/Authorize

    2，回调页面通过URL的 app_weibo 参数获取用户数据

    **请将{{appId}}替换为OAuthApp应用的AppID**



## 配置项

### 微博ClientSecret

在微博开放平台注册的应用所对应的AppSecret。

### 微博ClientID

在微博开放平台注册的APPKEY。

### 微博回调地址

用户在微博登录授权后，会被重定向至您预先设定的回调页面。

授权完成将附加**app_weibo**参数到回调地址，该参数包含了用户信息、access_token等数据。

## 截图

![](https://docs.oauthapp.com/doc_appsetting_weibo/1.png){ loading=lazy }


[^1]:微博账号登录文档：[https://open.weibo.com/wiki/%E6%8E%88%E6%9D%83%E6%9C%BA%E5%88%B6](https://open.weibo.com/wiki/%E6%8E%88%E6%9D%83%E6%9C%BA%E5%88%B6)