---
tags:
  - 服务端
---

# 应用

> baseUrl ：https://www.oauthapp.com

### 应用详情

这个接口有2分钟的缓存。

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/Apps/:appId/Info | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |


=== "C# - RestSharp"

    ```CSharp linenums="1"
    var client = new RestClient("https://www.oauthapp.com/api/Apps/:appId/Info");
    client.Timeout = -1;
    var request = new RestRequest(Method.GET);
    IRestResponse response = client.Execute(request);
    Console.WriteLine(response.Content);
    ```

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder().build();
    MediaType mediaType = MediaType.parse("text/plain");
    RequestBody body = RequestBody.create(mediaType, "");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/Apps/:appId/Info")
      .method("GET", body)
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```NodeJs linenums="1"
    var axios = require('axios');
    var config = {
      method: 'get',
      url: 'https://www.oauthapp.com/api/Apps/:appId/Info',
      headers: { }
    };

    axios(config)
    .then(function (response) {
      console.log(JSON.stringify(response.data));
    })
    .catch(function (error) {
      console.log(error);
    });
    ```

=== "Python - http.client"

    ```Python linenums="1"
    import http.client
    conn = http.client.HTTPSConnection("www.oauthapp.com")
    payload = ''
    headers = {}
    conn.request("GET", "/api/Apps/:appId/Info", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var requestOptions = {
      method: 'GET',
      redirect: 'follow'
    };
    fetch("https://www.oauthapp.com/api/Apps/:appId/Info", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
    ```


返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含应用信息 (info)、应用属性 (props) 和应用文件 |
| err | 错误信息 |  |

!!! Tip ""
    info 字段下的 **props** 代表应用的属性，是在 oauthapp发布工具 >> 应用 >> 应用配置 菜单下，启用配置节点的接口权限后才会返回。

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": {
            "info": {
                "id": 4,
                "userID": 1,
                "projectID": 5,
                "website": "https://web.oauthapp.com/4/examples",
                "serverPath": "examples",
                "name": "示例汇总",
                "logo": "https://blob.oauthapp.com/4/tenant/4/应用.png",
                "description": null,
                "tags": null,
                "appKey": "e87e8958-6667-4c44-aa71-c801a2b9e6e8",
                "share": true,
                "createDate": "2022-01-21 22:28:57",
                "lastUpdate": "2022-01-21 22:28:57",
                "isDelete": false,
                "sort": 0
            },
            "props": [
                {
                    "code": "WechatMiniPSignIn",
                    "value": "true",
                    "desc": null
                },
                {
                    "code": "DingTalkSignIn",
                    "value": "true",
                    "desc": null
                },
                {
                    "code": "DingTalkCorpId",
                    "value": "",
                    "desc": null
                }
            ],
            "blobs": [
                "https://blob.oauthapp.com/4/app/4/API.png"
            ]
        },
        "err": ""
    }
    ```