# OAuthApp 统一登录

## 说明

- [x] 禁用系统账号登录

> 禁用系统账号登录，只保留第三方账号来登录系统。

- [x] 小程序扫码登录（需配置微信小程序[^1]）

> 启用小程序扫码登录后，用户可以通过扫描小程序上的二维码来登录系统

- [x] 钉钉登录（钉钉应用内有效，需配置钉钉应用[^2]）

> 用户可以通过钉钉应用内进行登录。这种登录方式特别适合企业内部使用钉钉作为主要通信和认证工具的场景

- [x] Web ID登录

> 用户可以使用预先分配的Web ID来登录系统，无需密码，提供了一种简单的登录方式。

- [x] 禁止注册账号

通过禁止注册账号，系统将不再允许新用户自行注册账号。

## 配置项

### 禁用系统账号登录 

启用此项后，系统将不再支持系统账号和密码登录。

### 禁止注册账号 

启用此项后，系统将不再允许新用户自行注册账号。

### 启用Web ID登录 

启用此项后，系统将提供Web ID登录的方式，用户可以通过预分配的Web ID来登录。

### 启用钉钉登录

启用此项后，系统将支持通过钉钉登录的方式。

### 启用微信小程序登录

启用此项后，系统将支持通过微信小程序登录的方式。

通过适当地配置上述项，您可以灵活地定制系统的登录方式，提供更加便捷和安全的登录体验，同时符合不同场景的需求。

## 截图

![](https://docs.oauthapp.com/doc_appsetting_oauthapp_sso/1.png){ loading=lazy }

[^1]:微信小程序配置：[https://docs.oauthapp.com/doc_appsetting_wechatminip.html](https://docs.oauthapp.com/doc_appsetting_wechatminip.html)

[^2]:钉钉应用配置：[https://docs.oauthapp.com/doc_appsetting_dingtalk.html](https://docs.oauthapp.com/doc_appsetting_dingtalk.html)