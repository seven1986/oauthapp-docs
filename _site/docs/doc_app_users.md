# 用户管理

用户管理是OAuthApp平台的核心功能之一，它提供了一套完整的用户管理解决方案[^1]，包括查看用户信息、角色管理、权限管理等功能。用户管理功能旨在帮助开发者高效、安全地管理应用中的用户，并为用户分配不同的角色和权限，实现灵活的用户权限控制。

## 用户列表

在用户管理页面，您可以查看已注册的所有用户信息。通过数据列表视图，您可以方便地浏览和搜索用户信息，包括用户名、邮箱、手机号等。此外，您还可以查看单个用户的详细信息，了解用户的角色和权限分配情况。

操作步骤

1，单击“用户”

=== "图例 1-1"
    ![](https://docs.oauthapp.com/doc_app_users/1-1.png){ loading=lazy }

## 角色管理

角色是用户管理中的重要概念，它定义了不同用户的身份和权限级别。在OAuthApp中，您可以创建多个角色，并为不同的用户分配相应的角色。角色管理功能允许您灵活地定义用户的权限，从而实现对用户进行精细化的权限控制。

操作步骤

1，单击角色右侧的下拉菜单中的”创建角色“

2，输入角色名称，点击”确认“完成创建


=== "图例 2-1"
    ![](https://docs.oauthapp.com/doc_app_users/2-1.png){ loading=lazy }

=== "图例 2-2"
    ![](https://docs.oauthapp.com/doc_app_users/2-2.png){ loading=lazy }


## 导入导出数据

用户管理功能还支持数据的导入和导出。您可以将用户数据从外部文件导入到用户管理系统中，或者将用户数据导出到外部文件进行备份或分享。这样，您可以方便地在不同的环境之间迁移用户数据，或者在不同的应用之间共享用户信息。

操作步骤

1，导入：单击下拉菜单中的”导入“，然后点击”上传文件“

2，导出：单击下拉菜单中的”导出“

=== "图例 3-1"
    ![](https://docs.oauthapp.com/doc_app_users/3-1.png){ loading=lazy }
=== "图例 3-2"
    ![](https://docs.oauthapp.com/doc_app_users/3-2.png){ loading=lazy }
=== "图例 3-3"
    ![](https://docs.oauthapp.com/doc_app_users/3-3.png){ loading=lazy }
=== "图例 3-4"
    ![](https://docs.oauthapp.com/doc_app_users/3-4.png){ loading=lazy }

## 权限管理

权限管理是用户管理功能的重要组成部分，它用于控制用户在应用中的操作权限。您可以为不同的角色分配不同的操作权限，从而确保用户只能执行其具备权限的操作。

操作步骤

1，单击角色右侧下拉菜单的”权限设置“

2，勾选要开通的权限，单击“确认”

=== "图例 4-1"
    ![](https://docs.oauthapp.com/doc_app_users/4-1.png){ loading=lazy }
=== "图例 4-2"
    ![](https://docs.oauthapp.com/doc_app_users/4-2.png){ loading=lazy }

## 清空和删除数据

有时候，我们需要对用户数据进行清空或删除操作。OAuthApp提供了清空用户数据和删除用户的选项，您可以根据实际需求选择执行相应的操作。

!!! quote "需要注意的是，用户数据的清空和删除操作是不可逆的，请谨慎操作以免造成数据的丢失。"

操作步骤

1，单击下拉菜单的”删除“，将删除你选中的用户

2，单击下拉菜单的”清空表“，将清空当前用于所有的用户数据

=== "图例 5-1"
    ![](https://docs.oauthapp.com/doc_app_users/5-1.png){ loading=lazy }
=== "图例 5-2"
    ![](https://docs.oauthapp.com/doc_app_users/5-2.png){ loading=lazy }

## 令牌管理

访问令牌是一种授权机制，通过为应用程序分配令牌，可以让应用程序获得访问资源的权限。例如数据库、排行榜和消息模块。
您还可以指定令牌的有效期和权限，还可以通过禁用或启用访问令牌来管理令牌的状态。


### 创建令牌

操作步骤

1，点击下拉菜单中的“令牌管理”

2，点击创建令牌

3，输入令牌名称、有效期、标签、备注，然后点击“确认“

=== "图例 6-1"
    ![](https://docs.oauthapp.com/doc_app_users/6-1.png){ loading=lazy }
=== "图例 6-2"
    ![](https://docs.oauthapp.com/doc_app_users/6-2.png){ loading=lazy }
=== "图例 6-3"
    ![](https://docs.oauthapp.com/doc_app_users/6-3.png){ loading=lazy }
=== "图例 6-4"
    ![](https://docs.oauthapp.com/doc_app_users/6-4.png){ loading=lazy }

### 令牌管理

您可以在“令牌管理”页面中查看和管理所有访问令牌。您可以编辑令牌的名称、有效期、权限和状态。

操作步骤

1，点击”复制密钥”，可以直接将带有当前用户信息的“access_token”复制到剪切板

2，点击“权限设置”，可编辑当前令牌的权限

=== "图例 7-1"
    ![](https://docs.oauthapp.com/doc_app_users/7-1.png){ loading=lazy }
=== "图例 7-2"
    ![](https://docs.oauthapp.com/doc_app_users/7-2.png){ loading=lazy }
=== "图例 7-3"
    ![](https://docs.oauthapp.com/doc_app_users/7-3.png){ loading=lazy }

### 使用令牌

访问令牌与用户登录接口返回的access_token功能一样，免去了用户登录的步骤，通过访问令牌可直接调用API。

## 订单记录

可查看用户订单信息、在线支付、退款等操作，

=== "图例 8-1"
    ![](https://docs.oauthapp.com/doc_app_users/8-1.png){ loading=lazy }
=== "图例 8-2"
    ![](https://docs.oauthapp.com/doc_app_users/8-2.png){ loading=lazy }

## 开发文档和API

为了方便开发者使用用户管理功能，我们提供了详细的开发文档和API参考。开发文档中包含了用户管理功能的具体用法和示例代码，供开发者参考和学习。

- 文档：[https://docs.oauthapp.com/framework_user.html](https://docs.oauthapp.com/framework_user.html)

- 接口：[https://docs.oauthapp.com/api_user.html](https://docs.oauthapp.com/api_user.html)

[^1]:用户系统：[https://docs.oauthapp.com/code_usersystem.html](https://docs.oauthapp.com/code_usersystem.html)