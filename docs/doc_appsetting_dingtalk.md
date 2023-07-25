# 钉钉应用

你需要先创建 钉钉企业内部应用[^1]。

## 说明

- [x] 钉钉登录、消息推送

## 配置项

### 企业ID

配置您的企业在钉钉平台上的唯一标识符，用于与您的钉钉企业相关联。

### 应用ClientID

配置您的钉钉应用的唯一标识符，用于标识和识别您的应用。

### 应用ClientSecret

配置您的钉钉应用的私钥，用于生成签名并对请求数据进行加密。这个私钥必须与钉钉进行通信的接口进行匹配。

### 机器人令牌

配置您的钉钉机器人的令牌，用于验证钉钉推送过来的消息的真实性。

### 钉钉机器人 允许私人对话

配置是否允许钉钉机器人与用户进行私人对话。

请确保配置项的准确性和安全性，避免敏感信息泄露。

## 截图

![](https://docs.oauthapp.com/doc_appsetting_dingtalk/1.png){ loading=lazy }

## 创建钉钉应用参考

### 步骤1：创建企业内部应用

在钉钉开发者后台[^1]，创建一个企业内部应用，获取应用的AppKey和AppSecret。

![](https://docs.oauthapp.com/doc_appsetting_dingtalk/2.png){ loading=lazy }

### 步骤2：申请权限

申请下面的权限，其中{++成员信息读权限、个人手机号信息、邮箱等个人信息++}用于钉钉登录；
{++企业内机器人发送消息权限、单聊机器人使用管理权限++}用于钉钉机器人对话

| 权限信息  | 权限点code |  |
| ----------- | ----------- | ----------- |
| 成员信息读权限 | qyapi_get_member  |  |
| 个人手机号信息 | Contact.User.mobile  |  |
| 邮箱等个人信息 | fieldEmail  |  |
| 企业内机器人发送消息权限 | qyapi_robot_sendmsg  |  |
| 单聊机器人使用管理权限 | Robot.SingleChat.ReadWrite  |  |

![](https://docs.oauthapp.com/doc_appsetting_dingtalk/3.png){ loading=lazy }

### 步骤3：配置应用地址

配置您的钉钉应用的地址信息，{++应用首页地址、PC端首页地址、管理后台地址++}

![](https://docs.oauthapp.com/doc_appsetting_dingtalk/4.png){ loading=lazy }

### 步骤3：配置机器人

如果配置了Azure OpenAI[^2]，可以进行如下配置，实现AI对话[^3]。

=== "消息接收地址"

    ```curl linenums="1"
    # appId 需要替换成你的应用ID
    https://www.oauthapp.com/api/DingTalk/{{appId}}/PostMessage
    ```

![](https://docs.oauthapp.com/doc_appsetting_dingtalk/5.png){ loading=lazy }


### 步骤4：发布应用

在完成配置和权限申请后，发布您的钉钉应用，让用户可以使用该应用的功能。

![](https://docs.oauthapp.com/doc_appsetting_dingtalk/6.png){ loading=lazy }

[^1]:钉钉开发者后台：[https://open-dev.dingtalk.com/](https://open-dev.dingtalk.com/)

[^2]:Azure OpenAI：[http://docs.oauthapp.com/doc_appsetting_azure.html](http://docs.oauthapp.com/doc_appsetting_azure.html)

[^3]:钉钉智能机器人：[https://docs.oauthapp.com/code_dingtalk_openai_robot.html](https://docs.oauthapp.com/code_dingtalk_openai_robot.html)