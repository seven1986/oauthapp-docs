# 数据库

数据库是一种用于存储和管理数据的工具，支持对数据进行查看、编辑、删除、导入和导出等操作。它可以帮助我们存储和管理各种数据，包括用户信息、应用配置、订单记录等等

!!! quote "AuthApp使用SQLite[^1]作为数据库引擎，它是一种轻量级的数据库，非常适合嵌入式应用和移动应用。"

## 查看数据

在OAuthApp中，您可以轻松地查看已经存储在数据库中的数据，并支持对单个数据记录进行详细查看和编辑。此外，您还可以执行删除操作，从而对数据进行管理和维护。

操作步骤

1，单击“数据库”

2，单击“ID编号”，可以查看详情或更新数据

=== "图例 1-1"
    ![](https://docs.oauthapp.com/doc_app_database/1-1.png){ loading=lazy }
=== "图例 1-2"
    ![](https://docs.oauthapp.com/doc_app_database/1-2.png){ loading=lazy }


## 创建数据表

数据表是数据库中的基本单元，您可以创建多个数据表来存储不同类型的数据。在创建数据表时，您还可以设置约束条件来保证数据的唯一性。数据表的创建过程非常简单，只需要几步操作即可完成。

操作步骤

1，单击下拉菜单中的“创建数据表”

2，输入“数据库名称”

3，点击“确认创建”

=== "图例 2-1"
    ![](https://docs.oauthapp.com/doc_app_database/2-1.png){ loading=lazy }
=== "图例 2-2"
    ![](https://docs.oauthapp.com/doc_app_database/2-2.png){ loading=lazy }


## 导入导出数据

数据的导入和导出功能允许您将数据从外部文件导入到数据库中，或者将数据库中的数据导出到外部文件进行备份或分享。这样，您可以方便地在不同的环境之间迁移数据，或者在不同的应用之间共享数据。

操作步骤

1，单击下拉菜单中的“导入”，进行数据导入

2，单击下拉菜单中的“导出”，进行数据导出

=== "图例 3-1"
    ![](https://docs.oauthapp.com/doc_app_database/3-1.png){ loading=lazy }
=== "图例 3-2"
    ![](https://docs.oauthapp.com/doc_app_database/3-2.png){ loading=lazy }
=== "图例 3-3"
    ![](https://docs.oauthapp.com/doc_app_database/3-3.png){ loading=lazy }
=== "图例 3-4"
    ![](https://docs.oauthapp.com/doc_app_database/3-4.png){ loading=lazy }

## 数据表权限管理

为了确保数据的安全性和隐私保护，OAuthApp提供了基于用户角色的权限管理功能。您可以设置不同用户在不同数据表上的操作权限，从而控制数据的访问和修改权限。这样，只有具有相应权限的用户才能对数据进行操作，确保数据的安全和完整性。

操作步骤

1，单击下拉菜单中的“权限设置”

=== "图例 4-1"
    ![](https://docs.oauthapp.com/doc_app_database/4-1.png){ loading=lazy }
=== "图例 4-2"
    ![](https://docs.oauthapp.com/doc_app_database/4-2.png){ loading=lazy }

## 清空和删除数据表

有时候，我们需要对数据进行清空或删除操作。OAuthApp提供了清空数据表和删除数据表的选项，您可以根据实际需求选择执行相应的操作。

!!! quote "需要注意的是，数据的清空和删除操作是不可逆的，请谨慎操作以免造成数据的丢失。"

操作步骤

1，单击下拉菜单中的“清空表”，可清空当前数据表

2，单击下拉菜单中的“删除表”，可删除当前数据表

=== "图例 5-1"
    ![](https://docs.oauthapp.com/doc_app_database/5-1.png){ loading=lazy }


## 开发文档和API

为了方便开发者使用数据库功能，我们提供了详细的开发文档和API参考。开发文档中包含了数据库功能的具体用法和示例代码，供开发者参考和学习。API参考则列出了所有与数据库相关的接口和方法，开发者可以根据需要调用相应的API来实现数据管理功能。

- 文档：[https://docs.oauthapp.com/framework_storage.html](https://docs.oauthapp.com/framework_storage.html)

- 接口：[https://docs.oauthapp.com/api_storage.html](https://docs.oauthapp.com/api_storage.html)

[^1]:SQLite:https://sqlite.org/index.html