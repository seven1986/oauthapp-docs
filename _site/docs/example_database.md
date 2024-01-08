# 数据库

说明：存储的数据为json对象。

## 启用功能

启用数据库成功后，才能存储数据。

![](https://blob.oauthapp.com/4/app/2/example_database/1.png)

## 创建一个表

![](https://blob.oauthapp.com/4/app/2/example_database/2.png)

## 新增数据

数据必须为json格式，值统一为字符串类型。

| 开发参考  | 说明 |
| ----------- | ----------- |
| 框架 | oauthapp.tablePost |
| API | 数据库.创建数据 |


![](https://blob.oauthapp.com/4/app/2/example_database/3.png)



## 查询数据

根据每张表的首条记录，自动枚举字段，筛选数据。 

| 开发参考  | 说明 |
| ----------- | ----------- |
| 框架 | oauthapp.table |
| API | 数据库.查询数据 |
 
![](https://blob.oauthapp.com/4/app/2/example_database/6.png)

## 修改数据 

 | 开发参考  | 说明 |
| ----------- | ----------- |
| 框架 | oauthapp.tablePut |
| API | 数据库.修改数据 |

![](https://blob.oauthapp.com/4/app/2/example_database/4.png)

## 删除数据

 | 开发参考  | 说明 |
| ----------- | ----------- |
| 框架 | oauthapp.tableDelete |
| API | 数据库.删除数据 |

![](https://blob.oauthapp.com/4/app/2/example_database/5.png)

## 所有数据表

| 开发参考  | 说明 |
| ----------- | ----------- |
| 框架 | oauthapp.tables |
| API | 数据库.数据表集合 |

![](https://blob.oauthapp.com/4/app/2/example_database/7.png)

## 示例

- 数据库 示例 1：https://web.oauthapp.com/4/examples/storage_tool.html

- 新闻中心 示例： https://web.oauthapp.com/4/examples/h5wiki.html