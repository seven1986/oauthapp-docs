---
tags:
  - 功能应用
---

# SSL证书

## 说明

SSL证书可以保证您的网站的数据传输过程是安全的。

## 申请证书

### 步骤一：申请证书

- 证书域名必须由小写字母、数字、_、-符号组成，长度在4-32位之间。

- 输入电子邮件地址。证书到期前将发送提醒邮件到该邮箱。

**提交后不能修改**

![image](https://docs.oauthapp.com/code_ssltool/1.png)


### 步骤二：域名DNS验证

![image](https://docs.oauthapp.com/code_ssltool/2.png)


#### 自动验证

如果您已经绑定了阿里云accessKey，则可以自动验证。需要在oauthapp发布工具 **修改资料** 页面，配置2个声明 **alibabacloud_accesskeyid** 、**alibabacloud_accesskeysecret**。 并确认你的accesskey已经拥有DNS接口权限。

![image](https://docs.oauthapp.com/code_ssltool/7.png)

![image](https://docs.oauthapp.com/code_ssltool/3.png)

#### 手动验证

您需要前往您的域名控制台，根据提示添加2条TXT解析记录。

![image](https://docs.oauthapp.com/code_ssltool/4.png)

> 每次提交验证都会向证书颁发机构申请验证域名解析记录。您可以进行多次提交来刷新证书申请状态。


### 步骤三：下载证书

当您的证书验证通过后，您可以点击下载并使用该证书。

![image](https://docs.oauthapp.com/code_ssltool/5.png)

![image](https://docs.oauthapp.com/code_ssltool/6.png)

> 请注意，在整个申请过程中，尽量不要刷新页面，以免导致申请失败。

### 注意事项

#### 生效时间有延迟

为防止新证书即时生效有延迟，更换证书后站点HTTPS协议不能立即生效，请至少在到期前7天，重新申请证书。同时在证书距离到期前1个月的时候，您也会收到提醒邮件。

#### 申请速率限制

- 域名 **/** 50张证书 **/** 周

- 账户 **/** 提交300个申请 **/** 3小时

- IP **/** 创建10个账户 **/** 3小时

- 帐户 **/** 最多300个待验证域名 

**重置限制**

如果达到了速率限制，需等待一周，直到这些速率限制过期。

## 使用证书

参考[这篇文章](https://docs.oauthapp.com/code_appdomain/)，为你的应用添加自定义域名并绑定新申请的证书。