---
tags:
  - 功能应用
---

# 用户系统

## 说明

本文档旨在为开发人员提供关于用户系统的开发说明。

## OAuthApp统一登录

OAuthApp提供了统一登录功能，开发人员只需要通过简单的配置就可以把登录、注册、找回密码等功能集成到自己的应用系
统中。 可使用[登录链接生成工具](https://web.oauthapp.com/4/examples/signin_authorize.html)预览效果，统一登录的参数说明可查看[这个文档](https://docs.oauthapp.com/framework_user.html#_13)。

``` mermaid
graph LR
  A[应用登录页] --> B{OAuthApp统一登录};
  B --> C[用户名+密码];
  B --> D[手机号+验证码];
  B --> E[第三方平台];
  E --> EE[微信小程序扫码]
  E --> EEE[钉钉]
  E --> EEEE[Web ID]
  C --> F;
  D --> F;
  EE --> F;
  EEE --> F;
  EEEE --> F{登录};
  F -->|成功| G[跳转应用redirect_uri];
  F -->|失败| H[提示错误信息,重试 / 返回应用];
  B ----> I[注册账号];
  B ----> J[找回密码];
```

### 手机号登录 

1，配置 阿里云AccessKey[^1]

2，开通 [阿里云短信服务](https://www.aliyun.com/product/sms)，并申请短信服务的签名[^3]和创建短信模板[^4]

3，打开 应用配置[^2] - {++注册、找回密码++}

- 将阿里云审核通过的 签名名称[^3] 填写到 **短信签名**

- 将阿里云审核通过的 模板CODE[^4] 填写到 **注册账号 - 短信模板、找回密码 - 短信模板**

- 勾选**注册账号 - 需验证手机号**、**接口权限**

### 微信小程序扫码登录

1，打开 应用配置[^2] - {++OAuthApp统一登录++}

- 勾选**启用微信小程序登录**、**接口权限**

2，**默认使用OAuthApp的小程序做授权登录，可忽略下面的3、4步骤**

3，如需使用自己的小程序做授权登录，打开 应用配置[^2] - {++微信小程序++}

- 将微信小程序官方的AppID填写到 **微信小程序ClientID**

- 将微信小程序官方的AppSecret填写到 **微信小程序ClientSecret**

4，小程序端参考代码


=== "交互流程"

    ``` mermaid
    graph LR
        A[用户扫码进入小程序] --> B{获取appId和signKey};
        B -->|成功| C[请求用户授权];
        C --> D[确认授权];
        D --> E[注册应用账号];
        B -->|失败| H[提示错误信息];
    ```

=== "pages/index/index.js"

    ```JavaScript linenums="1"
    import {
      QRCodeScan,
      QRCodeSignUp,
      JSCode2Session
    } from '../services/api'
    
    Page({
    
      data: {
        onloading: false,
        appID: 0,
        appInfo: {},
        signinKey: '',
        userInfo: {},
        canSignin: false
      },
    
      /** 
       * 从options解析参数
       */
      __DecodeParamsFromOptions(_options) {
        this.setData({
          appId: _options.appId,
          signinKey: _options.signinKey
        })
        this.getData()
      },
    
      /**
       * 从scene解析参数
       */
      __DecodeParamsFromScene(_scene) {
        try {
          var result = {};
          decodeURIComponent(_scene).split('&').forEach(function (item) {
            var kv = item.split('=');
            result[kv[0]] = kv[1];
          });
    
          this.setData({
            appId: result.appId,
            signinKey: result.signinKey
          });
          this.getData();
        } catch (err) {
          wx.showToast({
            icon: 'none',
            title: '参数格式错误'
          });
        }
      },
    
      onLoad(options) {
        if (options.appId && options.signinKey) {
          this.__DecodeParamsFromOptions(options);
        } else if (options.scene) {
          this.__DecodeParamsFromScene(options.scene);
        } else {
          wx.showToast({
            icon: 'none',
            title: '非扫码打开'
          });
        }
      },
    
      getData() {
        wx.showLoading();
        QRCodeScan(this.data.appId, this.data.signinKey).then(res => {
          wx.hideLoading();
          if (res.data.data.scopes) {
            res.data.data.scopes = res.data.data.scopes.split(' ');
          }
    
          this.setData({
            appInfo: res.data.data,
            canSignin: true
          })
        }).catch(err=>{
          wx.hideLoading();
        });
    
      },
    
      getUserProfile(e) {
    
        if (this.data.onloading) {
          return;
        }
    
        let that = this;
    
        this.setData({
          onloading: true
        });
    
        wx.getUserProfile({
          desc: '展示用户信息',
          complete: (proflieRes) => {
        
            this.setData({
              onloading: false
            });
    
            if (!proflieRes.userInfo) {
              wx.showModal({
                showCancel: false,
                title: '提示',
                content: proflieRes.errMsg
              })
    
              return;
            }
    
            this.setData({
              'userInfo.avatar': proflieRes.userInfo.avatarUrl,
              'userInfo.nickName': proflieRes.userInfo.nickName,
            })
    
            that.minipSignIn();
          }
        })
      },
    
      minipSignIn() {
        let that = this;
    
        this.setData({
          onloading: true
        });
    
        wx.login({
          success(loginRes) {
        
            if (loginRes.code) {
              //console.log(loginRes.code)
              JSCode2Session(that.data.appId, loginRes.code).then(res => {
                var resJson = JSON.parse(res.data.data)
                that.setData({
                  'userInfo.unionID': resJson.unionid || resJson.openid
                });
                that.oauthappSignup();
              });
            } else {
              console.log('登录失败！' + res.errMsg)
            }
          },
          complete: res => {
            this.setData({
              onloading: false
            });
          }
        })
      },
    
      oauthappSignup() {
    
        this.setData({
          onloading: true
        });
    
        var requestData = {
          appID: this.data.appId,
          signInKey: this.data.signinKey,
          unionID: this.data.userInfo.unionID,
          avatar: this.data.userInfo.avatar,
          platform: "wxminip",
          nickName: this.data.userInfo.nickName,
          userName: "",
          phone: "",
          phoneIsValid: true,
          email: "",
          emailIsValid: true
        }
    
        QRCodeSignUp(this.data.appId, requestData).then(res => {
        
          //console.log(res);
    
          this.setData({
            onloading: false
          });
    
          wx.showModal({
            showCancel: false,
            content: '授权成功',
            success: res => {
              this.setData({
                canSignin: false
              })
              wx.exitMiniProgram();
            }
          })
    
        }).catch(err => {
          this.setData({
            onloading: false
          });
        })
      }
    })
    ```

=== "pages/index/index.wxml"

    ```xml linenums="1"
    <view class="container" wx:if="{{canSignin}}">
      <view>
        <image class="app-logo" src="{{appInfo.logo}}" mode="cover"></image>
      </view>

      <view class="app-name">
        <text>{{appInfo.name}}</text>
      </view>

      <view class="app-website">
        <text>来自 - {{appInfo.website}}</text>
      </view>

      <view>
        <view class="txt-sm">
          {{appInfo.name}} 请求访问您的
        </view>
        <view wx:key="key" wx:for="{{appInfo.scopes}}" class="scopeitem">
          {{item}}
        </view>
      </view>


      <view class="signupBtn" wx:if="{{canSignin}}">
        <button size="mini" type="primary" loading="{{onloading}}" bindtap="getUserProfile">确认授权</  button>
      </view>

      <view class="tip">
       授权成功后，小程序将自动关闭
      </view>
    </view>
    ```

=== "pages/services/api.js"

    ```JavaScript linenums="1"
    const app = getApp();

    const QRCodeScan = function (_appId, _signinKey) {

      var promise = new Promise((resolve, reject) => {
        wx.request({
          url: `${app.globalData.appServer}/AppUsers/${_appId}/QRCodeScan`,
          method: 'POST',
          data: {
            signInKey: parseInt(_signinKey),
          },

          complete: res => {
            if (res.errMsg == 'request:ok') {
              if (res.data.code != 200) {
                wx.showToast({
                  title: res.data.err,
                  icon: 'none',
                  mask: true
                });
              } else {
                resolve(res);
              }
            } else {
              wx.showToast({
                title: res.errMsg,
                icon: 'none',
                mask: true
              });
            }
          }
        });
      })

      return promise;
    }

    const JSCode2Session = function (_appId, _authCode) {
      var promise = new Promise((resolve, reject) => {
        wx.request({
          url: `${app.globalData.appServer}/Wechat/${_appId}/JSCode2Session?js_code=${_authCode}`,
          complete: res => {
            if (res.errMsg == 'request:ok') {
              if (res.data.code != 200) {
                wx.showToast({
                  title: res.data.err,
                  icon: 'none',
                  mask: true
                });
              } else {

                var __result = JSON.parse(res.data.data);
                if (__result.errmsg) {
                  wx.showToast({
                    title: __result.errmsg,
                    icon: 'none',
                    mask: true
                  });
                } else {
                  resolve(res);
                }

              }
            } else {
              wx.showToast({
                title: res.errMsg,
                icon: 'none',
                mask: true
              });
            }
          }
        });
      })

      return promise;
    }

    const QRCodeSignUp = function (_appId, _data) {
      var promise = new Promise((resolve, reject) => {
        wx.request({
          url: `${app.globalData.appServer}/AppUsers/${_appId}/QRCodeSignUp`,
          method: 'POST',
          data: _data,
          complete: res => {
            if (res.errMsg == 'request:ok') {
              if (res.data.code != 200) {
                wx.showToast({
                  title: res.data.err,
                  icon: 'none',
                  mask: true
                });
              } else {
                resolve(res);
              }
            } else {
              wx.showToast({
                title: res.errMsg,
                icon: 'none',
                mask: true
              });
            }
          }
        });
      });

      return promise;
    }

    export {
      QRCodeScan,
      QRCodeSignUp,
      JSCode2Session,
    }
    ```


### 钉钉登录

1，打开 应用配置[^2] - {++钉钉++}

- 将 [钉钉开发者首页](https://open-dev.dingtalk.com/) 的CropId填写到 **企业ID**，勾选**接口权限**
- 将你创建的 钉钉应用[^5] AppKey填写到 **应用ClientID**
- 将你创建的 钉钉应用[^5] AppSecret填写到 **应用ClientSecret**

2，打开 应用配置[^2] - {++OAuthApp统一登录++}

- 勾选 **启用钉钉登录**、**接口权限**

### WebID登录

1，打开 应用配置[^2] - {++OAuthApp统一登录++}

- 勾选 **启用Web ID登录**、**接口权限**

### 禁止注册

在某些情况下，可能需要禁止用户进行注册。

1，打开 应用配置[^2] - {++OAuthApp统一登录++}

- 勾选 **禁止注册账号**、**接口权限**

### 只允许第三方账号登录

在某些场景下，可能只允许使用第三方平台的账号进行登录，而不提供账号密码登录，邮箱或手机号登录功能。

1，打开 应用配置[^2] - {++OAuthApp统一登录++}

- 勾选 **禁用系统账号登录**、**接口权限**

## 发送欢迎邮件

在用户注册成功后，系统自动发送欢迎邮件给用户。

1，开通 [阿里云邮件推送服务](https://www.aliyun.com/product/directmail)，并[配置发信域名](https://help.aliyun.com/document_detail/29426.html)，[设置发信地址](https://help.aliyun.com/document_detail/29427.html)。

2，打开 应用配置[^2] -  - {++注册、找回密码++}

- 配置 阿里云AccessKey[^1]
- 将阿里云创建的 发信地址 填写到：**邮箱的发信账号**
- 勾选 **注册账号 - 发送欢迎邮件**
- 填写 **注册账号 - 欢迎邮件模板**


## 自定义开发

???+ note "提示"
    如需要加灵活的自定义开发，可参考下面的文档


## 注册账号

### 用户名
使用账号和密码进行登录。
开发人员需传入用户的账号和密码，服务器验证成功后，返回用户access_token给前端。

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](http://docs.oauthapp.com/framework_user.html#_7) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_6) |


### 手机号

用户可以使用手机号码进行登录。
开发人员需传入用户的手机号码和验证码，服务器验证成功后，返回用户access_token给前端。

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_9) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_8) |

### 邮箱账号

用户可以使用账邮箱账号进行登录。
开发人员需传入用户的邮箱账号和密码，服务器验证成功后，返回用户access_token给前端。

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_14) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_12) |

### 第三方UnionID

用户可以通过第三方平台（如微信、H5网页、QQ、微博、Facebook、GMail、Github等其他第三方平台）的账号进行登录。
开发人员需传入用户在第三方平台的认证信息，服务器验证成功后，返回用户access_token给前端。

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_4) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_3) |


## 登录

### 用户名

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_6) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_5) |

### 手机号

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_10) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_9) |


### 邮箱账号

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_15) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_13) |


### 第三方UnionID

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_3) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_2) |


## 找回密码

提供用户找回忘记密码的功能。

1，开发人员需传入用户提交的手机号或邮箱接收验证码，

2，输入新的密码和接收到的验证码，验证通过后，则密码重置成功。

### 通过手机找回密码

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_11) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_15) |


### 通过邮箱找回密码

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_16) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_15) |


## 开放你的用户数据

如需对外开放用户数据，可参考如下两种方式：

### 使用OAuthApp统一登录

外部应用将页面重定向到OAuthApp统一登录，当用户登录成功并确认授权后，系统会将用户的access_token返回到外部应用。

1，打开 应用配置[^2] - {++安全++}

2，填入允许接收access_token的网址到 **开放认证网址白名单**（默认或留空，代表不限制）

### 使用开放认证接口

| 开发参考  | 链接 |
| ----------- | ----------- |
| 文档 | [查看](https://docs.oauthapp.com/framework_user.html#_26) |
| API | [查看](https://docs.oauthapp.com/api_user.html#_22) |


## 用户数据管理

使用OAuthApp发布工具，依次打开 应用详情、 用户，页面提供了如下功能

 - 查询、编辑用户信息
 - 设置用户角色
 - 查看用户订单
 - 管理用户[访问令牌](https://docs.oauthapp.com/code_useraccesskey.html)
 - 导入、导出用户数据
 - 清空用户数据

[^1]:
    阿里云AccessKey：是通过API方式使用阿里云服务的一个身份令牌，只有配置该节点后，才能使用对应的短信、邮件等服务。
    请确认在[阿里云RAM](https://ram.console.aliyun.com/users)访问控制页面中，创建一个用户，并授权如下权限：

    - AliyunDirectMailFullAccess：管理邮件推送(DirectMail)的权限
    - AliyunDysmsFullAccess：管理短信服务(SMS)的权限

[^2]:
    应用配置：使用OAuthApp发布工具，依次打开 应用详情、应用配置 面板。
[^3]:
    短信签名规范：短信服务的签名都需要经过审核，审核通过后才可以使用该签名。[查看文档](https://help.aliyun.com/document_detail/108076.html)

[^4]:
    短信模板规范：短信服务的模板需要审核通过后才可以使用。[查看文档](https://help.aliyun.com/document_detail/463161.html)

[^5]:
    钉钉应用：企业内部应用，钉钉应用下创建的**H5微应用**，创建后还需要申请如下权限
    
    - 成员信息读权限（qyapi_get_member）
    - 个人手机号信息（Contact.User.mobile）
    - 邮箱等个人信息（fieldEmail）
    - 钉钉应用需配置IP白名单、PC/移动端的网页地址
