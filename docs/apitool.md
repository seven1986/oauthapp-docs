# 在线调试

???+ note "提示"
    API支持HTTPS网络请求协议，允许GET、POST、PUT、DELETE方法。您可以通过以下任一方式调用API。
    关于API功能说明、是否需要鉴权，可参考[API说明文档](https://docs.oauthapp.com/api/)。

## Swagger

使用Swagger在线接口调试工具。[点击访问](https://www.oauthapp.com/swagger){.md-button}

## Postman

使用Postman或其他接口调试工具，您需要先导入openapi文件：[https://www.oauthapp.com/swagger/1.0/swagger.json](https://www.oauthapp.com/swagger/1.0/swagger.json)


## 接口日志

接口在调用后会产生日志，可在OAuthApp发布工具的：**应用管理**——**接口日志**查看具体信息，日志包含如下信息：

- 访问时间
> 示例
```
2023-06-20 14:31:05
```
- 响应时间
> 示例
```
2023-06-20 14:31:05
```
- 客户端设备
> 示例
``` linenums="1"
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/113.0.0.0 Safari/537.36
```
- 请求内容
> 示例
```Javascript linenums="1"
{
 "propCode": null,
 "blobPath": null
}
```
- 响应内容
> 示例
```Javascript linenums="1"
{
 "code": 200,
 "data": {
  "info": {
   "ID": 4,
   "UserID": 1,
   "ProjectID": 5,
   "Website": "https://web.oauthapp.com/4/examples",
   "ServerPath": "examples",
   "Name": "示例汇总",
   "Logo": "https://blob.oauthapp.com/4/tenant/4/应用.png",
   "Description": null,
   "Tags": null,
   "AppKey": "e87e8958-6667-4c44-aa71-c801a2b9e6e8",
   "Share": true,
   "CreateDate": "2022-01-21T22:28:57",
   "LastUpdate": "2022-01-21T22:28:57",
   "IsDelete": false,
   "Sort": 0
  },
  "props": [
   {
    "code": "WechatMiniPSignIn",
    "value": "true",
    "Desc": null
   },
   {
    "code": "DingTalkSignIn",
    "value": "true",
    "Desc": null
   },
   {
    "code": "DingTalkCorpId",
    "value": "ding5c589fe4688de29dee0f45d8e4f7c288",
    "Desc": null
   }
  ],
  "blobs": []
 },
 "err": ""
}
```
- 用户ID
> 示例
```
1
```

## 统计分析

可在OAuthApp发布工具的：**应用管理**——**统计分析**——**接口**页面中，查看每天接口访问量。

![接口访问量](https://docs.oauthapp.com/apitool/1.png)