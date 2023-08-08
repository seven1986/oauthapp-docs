---
tags:
  - API
---

# 微信

!!! quote "在开始前，请确认已成功配置 微信小程序。"

## 小程序

### 发送订阅消息

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/SubscribeSend

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 无 |  |
    | touser	| 接收者（用户）的 openid |	OPENID |
    | template_id	| 订阅模板id |	TEMPLATE_ID |
    | page	| 跳转页面，支持带参数 |	index |
    | miniprogram_state	| 跳转小程序类型[^4] |	developer |
    | lang	| 语言 |	zh_CN |
    | data	| 模板数据 | 查看示例[^3] |


=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/SubscribeSend' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "touser": "OPENID",
          "template_id": "TEMPLATE_ID",
          "page": "index",
          "miniprogram_state": "developer",
          "lang": "zh_CN",
          "data": {
            "number01": {
              "value": "339208499"
            },
            "date01": {
              "value": "2015年01月05日"
            },
            "site01": {
              "value": "TIT创意园"
            },
            "site02": {
              "value": "广州市新港中路397号"
            }
          }
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new RestClient("https://www.oauthapp.com/api/Wechat/:appId/SubscribeSend");
        client.Timeout = -1;
        var request = new RestRequest(Method.POST);
        request.AddHeader("Content-Type", "application/json");
        var body = @"{" + "\n" +
        @"  ""touser"": ""OPENID""," + "\n" +
        @"  ""template_id"": ""TEMPLATE_ID""," + "\n" +
        @"  ""page"": ""index""," + "\n" +
        @"  ""miniprogram_state"":""developer""," + "\n" +
        @"  ""lang"":""zh_CN""," + "\n" +
        @"  ""data"": {" + "\n" +
        @"      ""number01"": {" + "\n" +
        @"          ""value"": ""339208499""" + "\n" +
        @"      }," + "\n" +
        @"      ""date01"": {" + "\n" +
        @"          ""value"": ""2015年01月05日""" + "\n" +
        @"      }," + "\n" +
        @"      ""site01"": {" + "\n" +
        @"          ""value"": ""TIT创意园""" + "\n" +
        @"      } ," + "\n" +
        @"      ""site02"": {" + "\n" +
        @"          ""value"": ""广州市新港中路397号""" + "\n" +
        @"      }" + "\n" +
        @"  }" + "\n" +
        @"}";
        request.AddParameter("application/json", body,  ParameterType.RequestBody);
        IRestResponse response = client.Execute(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n  \"touser\": \"OPENID\",\n      \"template_id\": \"TEMPLATE_ID\",\n  \"page\": \"index\",\n         \"miniprogram_state\":\"developer\",\n  \"lang\":\"zh_CN\",\n  \"data\": {\n      \"number01\":     {\n          \"value\": \"339208499\"\n      },\n      \"date01\":    {\n          \"value\":     \"2015年01月05日\"\n      },\n      \"site01\": {\n          \"value\": \"TIT创意园\"\n      } ,    \n      \"site02\": {\n          \"value\": \"广州市   新港中路397号\"\n      }\n  }\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/SubscribeSend")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "touser": "OPENID",
          "template_id": "TEMPLATE_ID",
          "page": "index",
          "miniprogram_state": "developer",
          "lang": "zh_CN",
          "data": {
            "number01": {
              "value": "339208499"
            },
            "date01": {
              "value": "2015年01月05日"
            },
            "site01": {
              "value": "TIT创意园"
            },
            "site02": {
              "value": "广州市新港中路397号"
            }
          }
        });

        var config = {
          method: 'post',
          url: 'https://www.oauthapp.com/api/Wechat/:appId/SubscribeSend',
          headers: { 
            'Content-Type': 'application/json'
          },
          data : data
        };

        axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });
        ```

    === "Python"

        ```Python linenums="1"
        import http.client
        import json

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = json.dumps({
          "touser": "OPENID",
          "template_id": "TEMPLATE_ID",
          "page": "index",
          "miniprogram_state": "developer",
          "lang": "zh_CN",
          "data": {
            "number01": {
              "value": "339208499"
            },
            "date01": {
              "value": "2015年01月05日"
            },
            "site01": {
              "value": "TIT创意园"
            },
            "site02": {
              "value": "广州市新港中路397号"
            }
          }
        })
        headers = {
          'Content-Type': 'application/json'
        }
        conn.request("POST", "/api/Wechat/:appId/SubscribeSend", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");

        var raw = JSON.stringify({"touser":"OPENID","template_id":"TEMPLATE_ID","page":"index",   "miniprogram_state":"developer","lang":"zh_CN","data":{"number01":   {"value":"339208499"},   "date01":{"value":"2015年01月05日"},"site01":{"value":"TIT创意园"},"site02":{"value":"广州市新港中   路397号"}}});

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/SubscribeSend", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": "{\"errcode\":0,\"errmsg\":\"ok\",\"msgid\":2812129620514029569}",
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatSubscribeSend){ .md-button }

### 生成网页跳转地址

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/UrlLinkGenerate

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 无 |  |
    | path	| 页面路径，不可携带 query  |	/pages/index/index |
    | query	| 通过 URL Link 进入小程序时的query，最大1024个字符，只支持数字，大小写英文以及部分特殊字符：!#$&'()*+,/:;=?@-._~% |	 |
    | expire_type	| 默认值0.小程序 URL Link 失效类型，失效时间：0，失效间隔天数：1 |	0 |
    | expire_interval	| 到期失效的URL Link的失效间隔天数。生成的到期失效URL Link在该间隔时间到达前有效。最长间隔天数为30天。expire_type 为 1 必填 |	30 |
    | env_version	| 跳转小程序类型[^4] | trial |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/UrlLinkGenerate' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "path": "/pages/index/index",
          "query": "",
          "expire_type": 1,
          "expire_interval": 30,
          "env_version": "trial"
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Wechat/:appId/UrlLinkGenerate", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        var body = @"{" + "\n" +
        @"    ""path"": ""/pages/index/index""," + "\n" +
        @"    ""query"": """"," + "\n" +
        @"    ""expire_type"":1," + "\n" +
        @"    ""expire_interval"":30," + "\n" +
        @"    ""env_version"": ""trial""" + "\n" +
        @"} ";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n    \"path\": \"/pages/index/index\",\n        \"query\": \"\",\n    \"expire_type\":1,\n    \"expire_interval\":30,   \n    \"env_version\":    \"trial\"\n} ");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/UrlLinkGenerate")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "path": "/pages/index/index",
          "query": "",
          "expire_type": 1,
          "expire_interval": 30,
          "env_version": "trial"
        });

        var config = {
          method: 'post',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Wechat/:appId/UrlLinkGenerate',
          headers: { 
            'Content-Type': 'application/json'
          },
          data : data
        };

        axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });
        ```

    === "Python"

        ```Python linenums="1"
        import http.client
        import json

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = json.dumps({
          "path": "/pages/index/index",
          "query": "",
          "expire_type": 1,
          "expire_interval": 30,
          "env_version": "trial"
        })
        headers = {
          'Content-Type': 'application/json'
        }
        conn.request("POST", "/api/Wechat/:appId/UrlLinkGenerate", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");

        var raw = JSON.stringify({
          "path": "/pages/index/index",
          "query": "",
          "expire_type": 1,
          "expire_interval": 30,
          "env_version": "trial"
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/UrlLinkGenerate", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": "{\"errcode\":0,\"errmsg\":\"ok\",\"url_link\":\"https:\/\/wxaurl.cn\/nZZOknTF4En\"}",
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatUrlLinkGenerate){ .md-button }

### 生成scheme码

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/generateScheme

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 无 |  |
    | jump_wxa | 跳转到的目标小程序信息 |  |
    | jump_wxa.path | 通过 scheme 码进入的小程序页面路径，必须是已经发布的小程序存在的页面，不可携带 query。path 为空时会跳转小程序主页。 |  |
    | jump_wxa.query | 通过 scheme 码进入小程序时的 query，最大1024个字符，只支持数字，大小写英文以及部分特殊字符：`!#$&'()*+,/:;=?@-._~%`` |  |
    | jump_wxa.env_version | 跳转小程序类型[^4] |  |
    | expire_time	| 到期失效的 scheme 码的失效时间，为 Unix 时间戳。生成的到期失效 scheme 码在该时间前有效。最长有效期为30天。is_expire 为 true 且 expire_type 为 0 时必填 |	 |
    | expire_type	| 默认值0.小程序 URL Link 失效类型，失效时间：0，失效间隔天数：1 |	0 |
    | expire_interval	| 到期失效的URL Link的失效间隔天数。生成的到期失效URL Link在该间隔时间到达前有效。最长间隔天数为30天。expire_type 为 1 必填 |	30 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/GenerateScheme' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "jump_wxa": {
            "path": "/pages/hot/hot",
            "query": "",
            "env_version": "release"
          },
          "is_expire": false
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com")
        {
          MaxTimeout = -1,
        };
        var client = new RestClient(options);
        var request = new RestRequest("/api/Wechat/:appId/GenerateScheme", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        var body = @"{""jump_wxa"": {""path"": ""/pages/hot/hot"",""query"": """",""env_version"":    ""release""},""is_expire"": false}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\r\n    \"jump_wxa\": {\r\n        \"path\":     \"/pages/hot/hot\",\r\n        \"query\":     \"\",\r\n        \"env_version\":     \"release\"\r\n    },\r\n    \"is_expire\": false\r\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/GenerateScheme")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "jump_wxa": {
            "path": "/pages/hot/hot",
            "query": "",
            "env_version": "release"
          },
          "is_expire": false
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Wechat/:appId/GenerateScheme',
          headers: { 
            'Content-Type': 'application/json'
          },
          data : data
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
        import json

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = json.dumps({
          "jump_wxa": {
            "path": "/pages/hot/hot",
            "query": "",
            "env_version": "release"
          },
          "is_expire": False
        })
        headers = {
          'Content-Type': 'application/json'
        }
        conn.request("POST", "/api/Wechat/:appId/GenerateScheme", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");

        var raw = JSON.stringify({
          "jump_wxa": {
            "path": "/pages/hot/hot",
            "query": "",
            "env_version": "release"
          },
          "is_expire": false
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/GenerateScheme", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | errcode | 表示返回结果的状态码 | 0 表示成功，非 0 表示失败 |
    | openlink | 表示返回的数据 |  |
    | errmsg | 错误信息 |  |

    ```json linenums="1"
    {
    "errcode": 0,
    "errmsg": "ok",
    "openlink": "weixin://dl/business/?t=xxxxxxxxxxx"
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatGenerateScheme){ .md-button }

### 获取小程序码

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/WXACodeGet

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 无 |  |
    | path | 扫码进入的小程序页面路径，最大长度 1024 字节，不能为空，scancode_time为系统保留参数，不允许配置；对于小游戏，可以只传入 query 部分，来实现传参效果，如：传入 "?foo=bar"，即可在 wx.getLaunchOptionsSync 接口中的 query 参数获取到 {foo:"bar"}。 |  |
    | width | 二维码的宽度，单位 px。默认值为430，最小 280px，最大 1280px |  |
    | auto_color | 默认值false；自动配置线条颜色，如果颜色依然是黑色，则说明不建议配置主色调 |  |
    | is_hyaline | 默认值false；是否需要透明底色，为 true 时，生成透明底色的小程序码 |  |
    | env_version | 跳转小程序类型[^4] |  |
    | line_color | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |
    | line_color.r | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |
    | line_color.g | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |
    | line_color.b | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/WXACodeGet' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "env_version": "trial",
          "path": "/pages/index/index?id=1&instanceid=2",
          "width": 128
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Wechat/:appId/WXACodeGet", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        var body = @"{" + "\n" +
        @"    ""env_version"": ""trial""," + "\n" +
        @"    ""path"": ""/pages/index/index?id=1&instanceid=2""," + "\n" +
        @"    ""width"": 128" + "\n" +
        @"}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n    \"env_version\": \"trial\",\n        \"path\": \"/pages/index/index?id=1&instanceid=2\",\n    \"width\": 128\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/WXACodeGet")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "env_version": "trial",
          "path": "/pages/index/index?id=1&instanceid=2",
          "width": 128
        });

        var config = {
          method: 'post',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Wechat/:appId/WXACodeGet',
          headers: { 
            'Content-Type': 'application/json'
          },
          data : data
        };

        axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });
        ```

    === "Python"

        ```Python linenums="1"
        import requests
        import json

        url = "https://www.oauthapp.com/api/Wechat/:appId/WXACodeGet"

        payload = json.dumps({
          "env_version": "trial",
          "path": "/pages/index/index?id=1&instanceid=2",
          "width": 128
        })
        headers = {
          'Content-Type': 'application/json'
        }

        response = requests.request("POST", url, headers=headers, data=payload)

        print(response.text)
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");

        var raw = JSON.stringify({
          "env_version": "trial",
          "path": "/pages/index/index?id=1&instanceid=2",
          "width": 128
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/WXACodeGet", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    ```json linenums="1"
     小程序码图片
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatWXACodeGet){ .md-button }

### 获取小程序码(无限制)

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/WXACodeGetUnlimited

=== "请求参数"


    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 无 |  |
    | scene | 最大32个可见字符，只支持数字，大小写英文以及部分特殊字符：!#$&'()*+,/:;=?@-._~，其它字符请自行编码为合法字符（因不支持%，中文无法使用 urlencode 处理，请使用其他编码方式） |  |
    | page | 默认是主页，页面 page，例如 pages/index/index，根路径前不要填加 /，不能携带参数（参数请放在scene字段里），如果不填写这个字段，默认跳主页面。scancode_time为系统保留参数，不允许配置 |  |
    | check_path | 默认是true，检查page 是否存在，为 true 时 page 必须是已经发布的小程序存在的页面（否则报错）；为 false 时允许小程序未发布或者 page 不存在， 但page 有数量上限（60000个）请勿滥用。 |  |
    | env_version | 跳转小程序类型[^4] |  |
    | width | 二维码的宽度，单位 px。默认值为430，最小 280px，最大 1280px |  |
    | auto_color | 默认值false；自动配置线条颜色，如果颜色依然是黑色，则说明不建议配置主色调 |  |
    | is_hyaline | 默认值false；是否需要透明底色，为 true 时，生成透明底色的小程序码 |  |
    | line_color | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |
    | line_color.r | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |
    | line_color.g | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |
    | line_color.b | 默认值{"r":0,"g":0,"b":0} ；auto_color 为 false 时生效，使用 rgb 设置颜色 例如 {"r":"xxx","g":"xxx","b":"xxx"} 十进制表示 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/WXACodeGetUnlimited' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '({
          "env_version": "trial",
          "path": "/pages/index/index",
          "scene": "1",
          "width": 128
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com")
        {
          MaxTimeout = -1,
        };
        var client = new RestClient(options);
        var request = new RestRequest("/api/Wechat/:appId/WXACodeGetUnlimited", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        var body = @"{" + "\n" +
        @"    ""env_version"": ""trial""," + "\n" +
        @"    ""path"": ""/pages/index/index""," + "\n" +
        @"    ""scene"": ""1""," + "\n" +
        @"    ""width"": 128" + "\n" +
        @"}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n    \"env_version\": \"trial\",\n        \"path\": \"/pages/index/index\",\n    \"scene\": \"1\",\n    \"width\": 128\n}   ");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/WXACodeGetUnlimited")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "env_version": "trial",
          "path": "/pages/index/index",
          "scene": "1",
          "width": 128
        });

        var config = {
          method: 'post',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Wechat/:appId/WXACodeGetUnlimited',
          headers: { 
            'Content-Type': 'application/json'
          },
          data : data
        };

        axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });
        ```

    === "Python"

        ```Python linenums="1"
        import http.client
        import json

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = json.dumps({
          "env_version": "trial",
          "path": "/pages/index/index",
          "scene": "1",
          "width": 128
        })
        headers = {
          'Content-Type': 'application/json'
        }
        conn.request("POST", "/api/Wechat/:appId/WXACodeGetUnlimited", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");

        var raw = JSON.stringify({
          "env_version": "trial",
          "path": "/pages/index/index",
          "scene": "1",
          "width": 128
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/WXACodeGetUnlimited", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    ```json linenums="1"
    小程序码图片
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatWXACodeGetUnlimited){ .md-button }

### 登录凭证校验

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/JSCode2Session?js_code=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | 无 |  |
    | js_code | 需要替换为小程序中用户的授权码 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/JSCode2Session?js_code=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Wechat/:appId/JSCode2Session?js_code=", Method.Get);
        request.AddHeader("Authorization", "Bearer {{bearerToken}}");
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/JSCode2Session?js_code=")
          .method("GET", body)
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Wechat/:appId/JSCode2Session?js_code=',
          headers: { 
            'Authorization': 'Bearer {{bearerToken}}'
          }
        };

        axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
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
        conn.request("GET", "/api/Wechat/:appId/JSCode2Session?js_code=", payload, headers)
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

        fetch("https://www.oauthapp.com/api/Wechat/:appId/JSCode2Session?js_code=", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": "{\"session_key\":\"\/GNPi8WgWRzLAL\/g+mgzGg==\",\"openid\":\"oKOsq40U1rMJ0CruOArCbEf8aJA8\"}",
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatJSCode2Session){ .md-button }


### 解密数据

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/Decrypt?encryptedData=&iv=&sessionKey=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | 无 |  |
    | encryptedData | 包括敏感数据在内的完整用户信息的加密数据 |  |
    | iv | 加密算法的初始向量 |  |
    | sessionKey | 无 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new RestClient("https://www.oauthapp.com/api/Wechat/:appId/Decrypt?encryptedData=&   iv=&sessionKey=");
        client.Timeout = -1;
        var request = new RestRequest(Method.GET);
        IRestResponse response = client.Execute(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=")
          .method("GET", body)
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
          url: 'https://www.oauthapp.com/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=',
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

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {}
        conn.request("GET", "/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=", payload,     headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var requestOptions = {
        method: 'GET',
        redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=",    requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
    | err | 错误信息 |  |

    ```json linenums="1"
    
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatDecrypt){ .md-button }

## 公众号H5

???+ note "提示"
    需要先使用oauthapp发布工具，应用>> 应用配置 >> 微信公众平台 菜单下，配置 微信公众号ClientID、微信公众号ClientSecret。
    
    在微信公众平台：安全中心 >> IP白名单 菜单下，添加IP：101.133.132.64


### 获取用户UnionID

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/UserInfo?openid=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | 无 |  |
    | openid | 用户的openid |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/UserInfo?openid=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new RestClient("https://www.oauthapp.com/api/Wechat/UserInfo?openid=");
        client.Timeout = -1;
        var request = new RestRequest(Method.GET);
        IRestResponse response = client.Execute(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/UserInfo?openid=")
          .method("GET", body)
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
          url: 'https://www.oauthapp.com/api/Wechat/UserInfo?openid=',
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

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {}
        conn.request("GET", "/api/Wechat/UserInfo?openid=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var requestOptions = {
        method: 'GET',
        redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/UserInfo?openid=", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": "{\"subscribe\":1,\"openid\":\"o-cq80Tic2OL5xAX5Lc_quoy16Cs\",\"nickname\":\"\",\"sex\":0,\"language\":\"zh_CN\",\"city\":\"\",\"province\":\"\",\"country\":\"\",\"headimgurl\":\"\",\"subscribe_time\":1526532566,\"unionid\":\"o0t3Fw2jOc0GEVh_NI8TZDXiOEvY\",\"remark\":\"\",\"groupid\":0,\"tagid_list\":[],\"subscribe_scene\":\"ADD_SCENE_QR_CODE\",\"qr_scene\":0,\"qr_scene_str\":\"\"}",
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatUserInfo){ .md-button }

### 发送一次性订阅消息

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/SubscribeMSG

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 无 |  |
    | touser | 填接收消息的用户openid |  |
    | template_id	 | 订阅消息模板ID |  |
    | url | 点击消息跳转的链接，需要有ICP备案 |  |
    | miniprogram | 跳小程序所需数据，不需跳小程序可不用传该数据 |  |
    | miniprogram.appid | 所需跳转到的小程序appid（该小程序appid必须与发模板消息的公众号是绑定关联关系，并且小程序要求是已发布的） |  |
    | miniprogram.pagepath | 所需跳转到小程序的具体页面路径，支持带参数,（示例index?foo=bar） |  |
    | scene | 订阅场景值 |  |
    | title | 消息标题，15字以内 |  |
    | data | 消息正文，value为消息内容文本（200字以内），没有固定格式，可用\n换行，color为整段消息内容的字体颜色（目前仅支持整段消息为一种颜色） |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/SubscribeMSG' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "touser": "OPENID",
          "template_id": "TEMPLATE_ID",
          "url": "URL",
          "miniprogram": {
            "appid": "xiaochengxuappid12345",
            "pagepath": "index?foo=bar"
          },
          "scene": "SCENE",
          "title": "TITLE",
          "data": {
            "content": {
              "value": "VALUE",
              "color": "COLOR"
            }
          }
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new RestClient("https://www.oauthapp.com/api/Wechat/:appId/SubscribeMSG");
        client.Timeout = -1;
        var request = new RestRequest(Method.POST);
        request.AddHeader("Content-Type", "application/json");
        var body = @"{" + "\n" +
        @"    ""touser"": ""OPENID""," + "\n" +
        @"    ""template_id"": ""TEMPLATE_ID""," + "\n" +
        @"    ""url"": ""URL""," + "\n" +
        @"    ""miniprogram"": {" + "\n" +
        @"        ""appid"": ""xiaochengxuappid12345""," + "\n" +
        @"        ""pagepath"": ""index?foo=bar""" + "\n" +
        @"    }," + "\n" +
        @"    ""scene"": ""SCENE""," + "\n" +
        @"    ""title"": ""TITLE""," + "\n" +
        @"    ""data"": {" + "\n" +
        @"        ""content"": {" + "\n" +
        @"            ""value"": ""VALUE""," + "\n" +
        @"            ""color"": ""COLOR""" + "\n" +
        @"        }" + "\n" +
        @"    }" + "\n" +
        @"}";
        request.AddParameter("application/json", body,  ParameterType.RequestBody);
        IRestResponse response = client.Execute(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n    \"touser\": \"OPENID\",\n        \"template_id\": \"TEMPLATE_ID\",\n    \"url\": \"URL\",\n    \"miniprogram\": {\n            \"appid\": \"xiaochengxuappid12345\",   \n        \"pagepath\": \"index?foo=bar\"\n    },\n       \"scene\": \"SCENE\",\n    \"title\": \"TITLE\",\n    \"data\": {\n        \"content\":   {\n            \"value\": \"VALUE\",\n            \"color\":    \"COLOR\"\n        }\n    }\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/SubscribeMSG")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "touser": "OPENID",
          "template_id": "TEMPLATE_ID",
          "url": "URL",
          "miniprogram": {
            "appid": "xiaochengxuappid12345",
            "pagepath": "index?foo=bar"
          },
          "scene": "SCENE",
          "title": "TITLE",
          "data": {
            "content": {
              "value": "VALUE",
              "color": "COLOR"
            }
          }
        });

        var config = {
          method: 'post',
          url: 'https://www.oauthapp.com/api/Wechat/:appId/SubscribeMSG',
          headers: { 
            'Content-Type': 'application/json'
          },
          data : data
        };

        axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });

        ```

    === "Python"

        ```Python linenums="1"
        import http.client
        import json

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = json.dumps({
          "touser": "OPENID",
          "template_id": "TEMPLATE_ID",
          "url": "URL",
          "miniprogram": {
            "appid": "xiaochengxuappid12345",
            "pagepath": "index?foo=bar"
          },
          "scene": "SCENE",
          "title": "TITLE",
          "data": {
            "content": {
              "value": "VALUE",
              "color": "COLOR"
            }
          }
        })
        headers = {
          'Content-Type': 'application/json'
        }
        conn.request("POST", "/api/Wechat/:appId/SubscribeMSG", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");

        var raw = JSON.stringify({"touser":"OPENID","template_id":"TEMPLATE_ID","url":"URL",    "miniprogram":{"appid":"xiaochengxuappid12345","pagepath":"index?foo=bar"},"scene":"SCENE",  "title":"TITLE","data":{"content":{"value":"VALUE","color":"COLOR"}}});

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/SubscribeMSG", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": "{\"errcode\":0,\"errmsg\":\"ok\"}",
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatSubscribeMSG){ .md-button }

### JS SDK Config

{{serverUrl}}[^1]/api/Wechat/:appId[^2]/JSConfig?url=

???+ note "提示"
    你可能还需要在微信公众平台：公众号设置 >> 功能设置 >> JS接口安全域名 配置应用页面URL


=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | 无 |  |
    | url | 当前页面的url |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Wechat/:appId/JSConfig?url=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new RestClient("https://www.oauthapp.com/api/Wechat/:appId/JSConfig?url=");
        client.Timeout = -1;
        var request = new RestRequest(Method.GET);
        IRestResponse response = client.Execute(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Wechat/:appId/JSConfig?url=")
          .method("GET", body)
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
          url: 'https://www.oauthapp.com/api/Wechat/:appId/JSConfig?url=',
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

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {}
        conn.request("GET", "/api/Wechat/:appId/JSConfig?url=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var requestOptions = {
        method: 'GET',
        redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Wechat/:appId/JSConfig?url=", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
    | err | 错误信息 |  |

    ```json linenums="1"
    略
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Wechat/WechatJSConfig){ .md-button }

[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID

[^3]:
    模板内容：
    ```Json linenums="1"
    {
        "number01": {
          "value": "339208499"
        },
        "date01": {
          "value": "2015年01月05日"
        },
        "site01": {
          "value": "TIT创意园"
        },
        "site02": {
          "value": "广州市新港中路397号"
        }
      }
    ```
    [^4]:跳转小程序类型：developer为开发版；trial为体验版；formal为正式版；默认为正式版