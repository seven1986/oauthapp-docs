---
tags:
  - API
---

# 应用

### 应用详情

{{serverUrl}}[^1]/api/Apps/:appId[^2]/Info

该接口有2分钟的缓存。

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | 不需要 |  |
    | propCode | 配置key，可空 | 默认返回全部 |
    | blobPath | 文件目录，可空 | 获取指定文件夹下的文件列表 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Apps/:appId/Info?propCode=&blobPath=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Get, "https://www.oauthapp.com/api/Apps/:appId/Info?propCode=&blobPath=");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());

        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Apps/:appId/Info?propCode=&blobPath=")
          .method("GET", body)
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');

        let config = {
          method: 'get',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Apps/:appId/Info?propCode=&blobPath=',
          headers: { 
            'Authorization': 'Bearer {{bearerToken}}'
          }
        };

        axios.request(config)
        .then((response) => {
          console.log(JSON.stringify(response.data));
        })
        .catch((error) => {
          console.log(error);
        });
        ```

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("GET", "/api/Apps/:appId/Info?propCode=&blobPath=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var requestOptions = {
          method: 'GET',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Apps/:appId/Info?propCode=&blobPath=", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | |
    | data.info | 应用信息 | |
    | data.props | 应用的属性 | 在 应用配置[^3] 菜单下，启用接口权限后即可访问。 |
    
    ```json linenums="1"
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/Apps/AppInfo){ .md-button }


[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID

[^3]:
    应用配置：在 OAuthApp发布工具 >> 应用详情 >> 应用配置 菜单下。