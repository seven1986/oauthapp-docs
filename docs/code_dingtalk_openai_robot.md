---
tags:
  - 功能应用
---

# 钉钉智能机器人

## 说明

这个教程展示了在钉钉内使用 Azure OpenAI作为对话机器人，实现群聊、一对一聊天的问答效果。

 使用钉钉扫码，查看示例
 
![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/12.jpg){ loading=lazy }


## 步骤一：创建钉钉企业内部应用

### 创建应用

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/1.png){ loading=lazy }

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/2.png){ loading=lazy }
 
> 一个企业内部应用可以在企业范围内实现各种功能，如发送消息、管理日程等等。

 <!-- - 在创建企业内部应用时，需要添加服务器 IP 白名单。

> 这是为了确保钉钉应用能够正常连接到服务器。如果服务器的 IP 不在白名单中，则钉钉应用将无法连接到服务器。 -->

### 申请权限

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/3.png){ loading=lazy }

> 机器人是钉钉应用中发送消息的重要组成部分。在申请机器人权限时，需要选择“自定义机器人”，并填写机器人名称和描述。

### 配置机器人

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/4.png){ loading=lazy }

> 在创建机器人时，需要为其设置一个消息接收地址，用于接收机器人发送的消息，appId 需要替换为 oauthpp的 appid。

### 发布应用

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/10.png){ loading=lazy }

> 发布后，钉钉应用就可以在企业内部使用了。

## 步骤二：配置Azure OpenAI

具体参考：[https://docs.oauthapp.com/doc_appsetting_azure.html](https://docs.oauthapp.com/doc_appsetting_azure.html)

<!-- 
![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/5.png){ loading=lazy }

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/6.png){ loading=lazy } -->

<!-- > 在将 OpenAI 与钉钉应用集成时，需要将 App Key 嵌入到钉钉应用的代码中。这样钉钉应用才能使用 OpenAI 的 API 服务进行对话。 -->

<!-- - 配置钉钉应用的 ID 和密钥。

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/8.png)

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/7.png)

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/9.png)

> 在将钉钉应用与 OpenAI 集成时，需要将钉钉应用的 ID 和密钥填入 OpenAI 应用的配置文件中。这样 OpenAI 才能通过 Webhook 地址向钉钉应用发送消息。
 -->

## 步骤三：测试使用

### 添加钉钉机器人

### 测试对话，查看结果是否符合预期。

![image](https://docs.oauthapp.com/code_dingtalk_openai_robot/11.png){ loading=lazy }

> 在测试对话时，您可以向钉钉机器人发送消息，并查看 OpenAI 返回的结果。