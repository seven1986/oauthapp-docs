---
tags:
  - 功能应用
---

# 访问令牌

## 说明

访问令牌是一种授权机制，通过为应用程序分配令牌，可以让应用程序获得访问资源的权限。例如数据库、排行榜和消息模块。
您还可以指定令牌的有效期和权限，还可以通过禁用或启用访问令牌来管理令牌的状态。

## 步骤一：创建令牌

- 登录OAuthApp发布工具，并进入应用详情页面。
- 点击 用户管理
- 选择要创建或编辑的用户，并点击下拉菜单中的“令牌管理”。

![image](https://docs.oauthapp.com/code_useraccesskey/1.png){ loading=lazy }

 - 点击“创建令牌”以创建新的访问令牌。在创建令牌时，您可以指定令牌的名称、有效期和权限。

 - 点击“保存”以保存访问令牌。

![image](https://docs.oauthapp.com/code_useraccesskey/2.png){ loading=lazy }

## 步骤二：令牌管理

您可以在“令牌管理”页面中查看和管理所有访问令牌。在此页面上，您可以编辑令牌的名称、有效期和权限，也可以禁用或启用令牌。

![image](https://docs.oauthapp.com/code_useraccesskey/3.png){ loading=lazy }

![image](https://docs.oauthapp.com/code_useraccesskey/4.png){ loading=lazy }

## 步骤三：使用令牌

访问令牌与用户登录接口返回的access_token功能一样，免去了用户登录的步骤，通过访问令牌可直接调用API。