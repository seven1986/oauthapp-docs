# 安全

## 说明

- [x] OAuthApp统一登录、开放认证API，允许接收access_token的returlUrl集合

通过配置这个集合，可以控制哪些URL可以接收来自OAuthApp统一登录的access_token，从而减少潜在的安全风险。

## 配置项

### 令牌有效天数

access_token有效期，未配置的情况下，默认为1天。

### 开放认证网址白名单 

开放认证网址白名单是一个允许接收access_token的URL集合，用","分隔。

您可以在这里添加受信任的URL，只有在白名单中的URL才能成功接收来自OAuthApp统一登录的access_token。

**默认允许所有returlUrl**

**如果returlUrl不为空**，请求的returlUrl不在白名单中，系统将拒绝传递access_token，从而保护用户数据和系统资源。

## 截图

![1](https://docs.oauthapp.com/doc_appsetting_safe/1.png){ loading=lazy }