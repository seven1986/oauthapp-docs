# 微信小程序

此文档介绍了微信小程序的相关功能和配置项。

## 说明

- [x] 发送订阅消息：允许小程序向用户发送订阅消息。

- [x] 生成网页跳转地址：用于在小程序中生成用于网页跳转的地址。

- [x] 获取scheme码、小程序码：用于在其他场景中推广小程序。

- [x] 获取用户UnionID：用于获取用户在微信开放平台下的唯一标识UnionID。

## 配置项

### 微信小程序ClientSecret

小程序唯一凭证密钥，即 AppSecret，获取方式同 appid

### 微信小程序ClientID

小程序唯一凭证，即 AppID，可在「微信公众平台 - 设置 - 开发设置」页中获得。（需要已经成为开发者，且账号没有异常状态）

## 截图

![](https://docs.oauthapp.com/doc_appsetting_wechatminip/1.png){ loading=lazy }

## 其他

微信登录

| 授权域  | 用户侧使用流程 |
| ----------- | ----------- |
| wx.login | 静默授权，开发者可获取openid |
| wx.getUserInfo | （1）用户在小程序内点击组件，唤起登录窗口（2）用户侧完成登录授权 |

小程序登录[开发文档](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/login.html)，查看[登录流程设计指引](https://developers.weixin.qq.com/community/develop/doc/0006026b3c83c0e244573a0025bc08)