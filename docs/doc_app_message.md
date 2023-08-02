# 消息

消息功能是OAuthApp平台提供的一项重要功能，旨在帮助开发者实现应用内的消息通知和管理。通过消息功能，您可以轻松地向用户发送消息通知，提醒用户关键信息和活动等。同时，您还可以对消息进行管理，包括查看、编辑、删除等操作，以便更好地维护和优化用户体验。

## 创建消息表

消息表是消息中的基本单元，您可以创建多个消息表来存储不同的消息数据。

操作步骤

1，单击下拉菜单中的“创建数据表”

2，输入“消息表名称”

3，点击“确认创建”

=== "图例 1-1"
    ![](https://docs.oauthapp.com/doc_app_message/1-1.png){ loading=lazy }


## 查看消息表

在消息管理界面，您可以查看所有已发送的消息。列表视图展示了消息的标题、内容、发送时间等重要信息，方便您浏览和查找相关消息。您还可以点击单个消息，查看消息的详细内容和接收用户。

操作步骤

1，单击“消息”

2，单击“编辑”，可以查看单个消息详情

3，单击“删除”，可以删除指定消息

=== "图例 2-1"
    ![](https://docs.oauthapp.com/doc_app_message/2-1.png){ loading=lazy }
=== "图例 2-2"
    ![](https://docs.oauthapp.com/doc_app_message/2-2.png){ loading=lazy }

## 导入导出数据

消息功能支持数据的导入和导出，方便您备份消息数据或迁移至其他系统。您可以从外部文件导入消息数据到消息系统，也可以将消息数据导出到外部文件，以便后续处理或共享给其他用户。

操作步骤

1，单击下拉菜单中的“导入”，可导入数据

2，单击下拉菜单中的“导出”，可导出数据

=== "图例 3-1"
    ![](https://docs.oauthapp.com/doc_app_message/3-1.png){ loading=lazy }
=== "图例 3-2"
    ![](https://docs.oauthapp.com/doc_app_message/3-2.png){ loading=lazy }
=== "图例 3-3"
    ![](https://docs.oauthapp.com/doc_app_message/3-3.png){ loading=lazy }
=== "图例 3-4"
    ![](https://docs.oauthapp.com/doc_app_message/3-4.png){ loading=lazy }


## 权限管理

为了确保消息的安全性和准确性，消息功能提供了灵活的权限管理机制。您可以为每个消息表设置不同的角色权限，从而控制用户对消息的访问和操作权限。这样，只有具有相应权限的用户才能查看、发送和管理消息，保障消息的保密性和正确性。

操作步骤

1，单击下拉菜单中的“权限设置”

=== "图例 4-1"
    ![](https://docs.oauthapp.com/doc_app_message/4-1.png){ loading=lazy }
=== "图例 4-2"
    ![](https://docs.oauthapp.com/doc_app_message/4-2.png){ loading=lazy }

## 清空和删除数据

当需要清空消息数据或不再需要某些消息时，您可以选择清空或删除相应的数据。

!!! quote "需要注意的是，数据的清空和删除操作是不可逆的，请谨慎操作以免造成数据的丢失。"

操作步骤

1，单击下拉菜单中的“清空表”，可清空当前消息表

2，单击下拉菜单中的“删除表”，可删除当前消息表

=== "图例 5-1"
    ![](https://docs.oauthapp.com/doc_app_message/5-1.png){ loading=lazy }

## 开发文档和API

为了帮助开发者更好地使用消息功能，我们提供了详细的开发文档和API参考。开发文档包含了使用消息功能的详细指南和示例代码，供开发者学习和参考。API参考列出了所有与消息功能相关的接口和方法，方便开发者根据实际需求调用相应的API来实现功能。

- 文档：[https://docs.oauthapp.com/framework_chatmessage.html](https://docs.oauthapp.com/framework_chatmessage.html)

- 接口：[https://docs.oauthapp.com/api_chatmessage.html](https://docs.oauthapp.com/api_chatmessage.html)