# 注册、找回密码

???+ note "提示"

    1，需先购买阿里云短信[^1] 和邮件推送[^2] 服务。
    > 为验证配置正确，请确认你已经可以在阿里云平台发短信、推送邮件。

    2，配置 阿里云AccessKey[^3]

    

## 说明

- [x] 验证新用户手机号、邮箱账号

启用此功能后，所有经由OAuthApp统一登录或用户注册相关的API都将强制验证用户的手机号或邮箱账号。这样可以确保新用户的信息有效和可信。

- [x] 用户注册成功发送欢迎邮件

启用此功能后，不论是通过OAuthApp统一登录还是调用用户API进行注册，新用户都会自动收到一封欢迎邮件


## 配置项

### 注册账号 - 赠送积分

新用户注册后，赠送的积分。

### 注册账号 - 默认角色

新用户注册后，默认的角色名称，必须与已存在的角色名称保持一致。

### 找回密码 - 邮件模板 

配置找回密码功能中发送邮件的模板，以便用户可以通过注册的邮箱来重置密码。

自定义内容，必须添加变量{code}，系统会自动替换为验证码

### 找回密码 - 短信模板 

配置找回密码功能中发送短信的模板，以便用户可以通过注册的手机号来重置密码。也可以和 **注册账号 - 短信模板** 使用同一模板。 如：SMS_123456

### 邮箱发信账号

配置用于发送邮件的邮箱账号信息。

### 注册账号 - 欢迎邮件模板 

配置注册账号功能中发送欢迎邮件的模板，以便新用户收到注册成功的欢迎邮件。

自定义文字内容

### 注册账号 - 发送欢迎邮件

启用此项后，当用户成功注册账号时，系统会自动发送欢迎邮件。

### 注册账号 - 邮件模板 

配置注册账号功能中发送邮件的模板，以便用户可以验证其邮箱账号。

自定义内容，必须添加变量{code}，系统会自动替换为验证码

### 注册账号 - 需验证邮箱 

启用此项后，新用户在注册时将需要验证其邮箱账号。

### 注册账号 - 需验证手机号 

启用此项后，新用户在注册时将需要验证其手机号。

### 注册账号 - 短信模板 

配置注册账号功能中发送短信的模板，以便用户可以验证其手机号。

自定义内容，必须添加变量{code}，系统会自动替换为验证码

将阿里云审核通过的 模板CODE[^4] 填写到这里

### 短信签名

配置用于发送短信的签名信息，将会显示在发送的短信内容中。

将阿里云审核通过的签名名称[^5]填写到这里

## 截图

![1](https://docs.oauthapp.com/doc_appsetting_signup_resetpwd/1.png){ loading=lazy }


通过适当地配置上述项，您可以实现强化注册安全性和用户体验的目标。用户将能够更加可靠地注册和找回密码，并在注册成功时收到欢迎邮件表示诚挚的问候。


[^1]:阿里云短信：[https://www.aliyun.com/product/sms](https://www.aliyun.com/product/sms)

[^2]:阿里云邮件推送：[https://www.aliyun.com/product/directmail](https://www.aliyun.com/product/directmail)、[配置发信域名](https://help.aliyun.com/document_detail/29426.html)、[设置发信地址](https://help.aliyun.com/document_detail/29427.html)

[^3]:阿里云AccessKey配置：[https://docs.oauthapp.com/doc_appsetting_aliyun.html](https://docs.oauthapp.com/doc_appsetting_aliyun.html)

[^4]:短信模板规范：短信服务的模板需要审核通过后才可以使用。[https://help.aliyun.com/document_detail/463161.html](https://help.aliyun.com/document_detail/463161.html)

[^5]:短信签名规范：短信服务的签名都需要经过审核，审核通过后才可以使用该签名。[https://help.aliyun.com/document_detail/108076.html](https://help.aliyun.com/document_detail/108076.html)