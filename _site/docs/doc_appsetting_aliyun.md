# 阿里云

## 说明

阿里云AccessKey 是通过API方式使用阿里云服务的一个身份令牌。配置成功后，即可使用发送短信、邮件等功能。

1，进入[阿里云RAM访问控制页面](https://ram.console.aliyun.com/users)

2，创建用户

3，在用户列表中，找到上一步创建的用户，点击 **添加权限**，选择如下权限

AliyunDirectMailFullAccess：管理邮件推送(DirectMail)的权限

AliyunDysmsFullAccess：管理短信服务(SMS)的权限

![](https://docs.oauthapp.com/doc_appsetting_aliyun/1.png){ loading=lazy }

4，点击进入 刚创建的用户详情页，点击 “创建AccessKey”，将AccessKey ID与AccessKey Secret同步配置到系统中。

![](https://docs.oauthapp.com/doc_appsetting_aliyun/2.png){ loading=lazy }

## 配置项

### AccessKey ID

阿里云 AccessKey ID

### AccessKey 密钥 

阿里云 AccessKey Secret


## 截图

![](https://docs.oauthapp.com/doc_appsetting_aliyun/3.png){ loading=lazy }
