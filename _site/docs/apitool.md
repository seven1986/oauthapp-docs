# 在线调试

???+ note "提示"
    API支持HTTPS网络请求协议，允许GET、POST、PUT、DELETE方法。您可以通过以下任一方式调用API。
    关于API功能说明、是否需要鉴权，可参考[API说明文档](https://docs.oauthapp.com/api/)。

## Swagger

使用Swagger在线接口调试工具。[点击访问](https://www.oauthapp.com/swagger){.md-button}

## Postman

Postman 接口文档 [点击访问](https://documenter.getpostman.com/view/19619739/2s9Xy3qqZH){.md-button}

!!! quote "建议使用Postman导入openapi文件 [https://www.oauthapp.com/swagger/1.0/swagger.json](https://www.oauthapp.com/swagger/1.0/swagger.json)"


## 接口日志

接口在调用后会产生日志，可通过接口日志[^1]查看具体信息，具体包含如下信息

=== "返回数据"

    ```Json linenums="1"
    {
    "id": 7659,
    "userID": "",
    "userGroup": "app",
    "reqPath": "/api/apps/2/Info",
    "reqStart": "2023-08-07 15:10:03",
    "reqEnd": "2023-08-07 15:10:03",
    "reqData": "{...略}",
    "resData": "{...略}",
    "userAgent": "Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Googlebot/2.1; +http://www.google.com/bot.html) Chrome/114.0.5735.179 Safari/537.36",
    "operationId": "AppInfo"
    }
    ```


=== "字段说明"

    | 字段 | 描述 |  |
    | --- | --- | --- |
    | id | 日志唯一标识 |
    | userID | 用户ID |
    | userGroup | 用户来源 |
    | reqPath | 请求API的地址 |
    | reqStart | 请求时间 |
    | reqEnd | 响应时间 |
    | reqData | 请求携带数据 |
    | resData | 接口响应数据 |
    | userAgent | 客户端详情 |
    | operationId | API标识 |


## 统计分析

可通过统计分析[^2]查看每天接口访问量。

![接口访问量](https://docs.oauthapp.com/apitool/1.png)

[^1]:接口日志：[https://docs.oauthapp.com/doc_app_log.html#_3](https://docs.oauthapp.com/doc_app_log.html#_3)
[^2]:接口统计：[https://docs.oauthapp.com/doc_app_analysis.html#_9](https://docs.oauthapp.com/doc_app_analysis.html#_9)