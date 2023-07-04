---
tags:
  - 服务端
---

# 微信

> baseUrl ：https://www.oauthapp.com

!!! Tip ""
    需要先使用oauthapp发布工具，应用>> 应用配置 >> 微信小程序 菜单下，配置 微信小程序ClientID、微信小程序ClientSecret。。

## 小程序

### 发送订阅消息

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/SubscribeSend | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |


=== "C# - RestSharp"

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

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder()
      .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "{\n  \"touser\": \"OPENID\",\n  \"template_id\": \"TEMPLATE_ID\",\n  \"page\": \"index\",\n     \"miniprogram_state\":\"developer\",\n  \"lang\":\"zh_CN\",\n  \"data\": {\n      \"number01\": {\n          \"value\": \"339208499\"\n      },\n      \"date01\":    {\n          \"value\": \"2015年01月05日\"\n      },\n      \"site01\": {\n          \"value\": \"TIT创意园\"\n      } ,\n      \"site02\": {\n          \"value\": \"广州市   新港中路397号\"\n      }\n  }\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/Wechat/:appId/SubscribeSend")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");

    var raw = JSON.stringify({"touser":"OPENID","template_id":"TEMPLATE_ID","page":"index","miniprogram_state":"developer","lang":"zh_CN","data":{"number01":   {"value":"339208499"},"date01":{"value":"2015年01月05日"},"site01":{"value":"TIT创意园"},"site02":{"value":"广州市新港中路397号"}}});

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

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
    "code": 200,
    "data": "{\"errcode\":0,\"errmsg\":\"ok\",\"msgid\":2812129620514029569}",
    "err": ""
    }
    ```

### 生成网页跳转地址

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/UrlLinkGenerate | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

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

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder()
      .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "{\n    \"path\": \"/pages/index/index\",\n    \"query\": \"\",\n    \"expire_type\":1,\n    \"expire_interval\":30,   \n    \"env_version\": \"trial\"\n} ");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/Wechat/:appId/UrlLinkGenerate")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

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

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
    "code": 200,
    "data": "{\"errcode\":0,\"errmsg\":\"ok\",\"url_link\":\"https:\/\/wxaurl.cn\/nZZOknTF4En\"}",
    "err": ""
    }
    ```

### 生成scheme码

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/generateScheme | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/Wechat/:appId/GenerateScheme", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    var body = @"{""jump_wxa"": {""path"": ""/pages/hot/hot"",""query"": """",""env_version"": ""release""},""is_expire"": false}";
    request.AddStringBody(body, DataFormat.Json);
    RestResponse response = await client.ExecuteAsync(request);
    Console.WriteLine(response.Content);
    ```

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder()
      .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "{\r\n    \"jump_wxa\": {\r\n        \"path\": \"/pages/hot/hot\",\r\n        \"query\":     \"\",\r\n        \"env_version\": \"release\"\r\n    },\r\n    \"is_expire\": false\r\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/Wechat/:appId/GenerateScheme")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

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

返回示例


| 描述 |  |  |
| --- | --- | --- |
| errcode | 表示返回结果的状态码 | 0 表示成功，非 0 表示失败 |
| openlink | 表示返回的数据 |  |
| errmsg | 错误信息 |  |

=== "返回结果"
    ```json
    {
    "errcode": 0,
    "errmsg": "ok",
    "openlink": "weixin://dl/business/?t=xxxxxxxxxxx"
    }
    ```


### 获取小程序码

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/WXACodeGet | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

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

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder()
      .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "{\n    \"env_version\": \"trial\",\n    \"path\": \"/pages/index/index?id=1&instanceid=2\",\n    \"width\": 128\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/Wechat/:appId/WXACodeGet")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

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

返回示例


=== "返回结果"
    ```json
     小程序码图片
    ```

### 获取小程序码(无限制)

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/WXACodeGetUnlimited | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

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

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder()
      .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "{\n    \"env_version\": \"trial\",\n    \"path\": \"/pages/index/index\",\n    \"scene\": \"1\",\n    \"width\": 128\n}   ");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/Wechat/:appId/WXACodeGetUnlimited")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

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

返回示例


=== "返回结果"
    ```json
    小程序码图片
    ```

### 登录凭证校验

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/JSCode2Session?js_code= | :appId 部分需要替换为实际应用的 ID；js_code 需要替换为小程序中用户的授权码 |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com");
    var client = new RestClient(options);
    var request = new RestRequest("/api/Wechat/:appId/JSCode2Session?js_code=", Method.Get);
    request.AddHeader("Authorization", "Bearer {{bearerToken}}");
    RestResponse response = await client.ExecuteAsync(request);
    Console.WriteLine(response.Content);
    ```

=== "Java - OkHttp"

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

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

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

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
    "code": 200,
    "data": "{\"session_key\":\"\/GNPi8WgWRzLAL\/g+mgzGg==\",\"openid\":\"oKOsq40U1rMJ0CruOArCbEf8aJA8\"}",
    "err": ""
    }
    ```

### 解密数据

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey= | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var client = new RestClient("https://www.oauthapp.com/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=");
    client.Timeout = -1;
    var request = new RestRequest(Method.GET);
    IRestResponse response = client.Execute(request);
    Console.WriteLine(response.Content);
    ```

=== "Java - OkHttp"

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

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

    ```Python linenums="1"
    import http.client

    conn = http.client.HTTPSConnection("www.oauthapp.com")
    payload = ''
    headers = {}
    conn.request("GET", "/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=", payload, headers)
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

    fetch("https://www.oauthapp.com/api/Wechat/:appId/Decrypt?encryptedData=&iv=&sessionKey=", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    
    ```

## 公众号H5

!!! Tip ""
    需要先使用oauthapp发布工具，应用>> 应用配置 >> 微信公众平台 菜单下，配置 微信公众号ClientID、微信公众号ClientSecret。
    
    在微信公众平台：安全中心 >> IP白名单 菜单下，添加IP：101.133.132.64


### 获取用户UnionID

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/Wechat/UserInfo?openid= | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var client = new RestClient("https://www.oauthapp.com/api/Wechat/UserInfo?openid=");
    client.Timeout = -1;
    var request = new RestRequest(Method.GET);
    IRestResponse response = client.Execute(request);
    Console.WriteLine(response.Content);
    ```

=== "Java - OkHttp"

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

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

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

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
    "code": 200,
    "data": "{\"subscribe\":1,\"openid\":\"o-cq80Tic2OL5xAX5Lc_quoy16Cs\",\"nickname\":\"\",\"sex\":0,\"language\":\"zh_CN\",\"city\":\"\",\"province\":\"\",\"country\":\"\",\"headimgurl\":\"\",\"subscribe_time\":1526532566,\"unionid\":\"o0t3Fw2jOc0GEVh_NI8TZDXiOEvY\",\"remark\":\"\",\"groupid\":0,\"tagid_list\":[],\"subscribe_scene\":\"ADD_SCENE_QR_CODE\",\"qr_scene\":0,\"qr_scene_str\":\"\"}",
    "err": ""
    }
    ```

### 发送一次性订阅消息

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/SubscribeMSG | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

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

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder()
      .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "{\n    \"touser\": \"OPENID\",\n    \"template_id\": \"TEMPLATE_ID\",\n    \"url\": \"URL\",\n    \"miniprogram\": {\n        \"appid\": \"xiaochengxuappid12345\",   \n        \"pagepath\": \"index?foo=bar\"\n    },\n    \"scene\": \"SCENE\",\n    \"title\": \"TITLE\",\n    \"data\": {\n        \"content\": {\n            \"value\": \"VALUE\",\n            \"color\":    \"COLOR\"\n        }\n    }\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/Wechat/:appId/SubscribeMSG")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");

    var raw = JSON.stringify({"touser":"OPENID","template_id":"TEMPLATE_ID","url":"URL","miniprogram":{"appid":"xiaochengxuappid12345","pagepath":"index?foo=bar"},"scene":"SCENE","title":"TITLE","data":{"content":   {"value":"VALUE","color":"COLOR"}}});

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

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
    "code": 200,
    "data": "{\"errcode\":0,\"errmsg\":\"ok\"}",
    "err": ""
    }
    ```

### JS SDK Config

???+ note "提示"
    需要在微信公众平台：公众号设置 >> 功能设置 >> JS接口安全域名 配置：**{{你的应用域名，如：www.oauthapp.com}}**


| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/Wechat/:appId/JSConfig?url= | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 无 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var client = new RestClient("https://www.oauthapp.com/api/Wechat/:appId/JSConfig?url=");
    client.Timeout = -1;
    var request = new RestRequest(Method.GET);
    IRestResponse response = client.Execute(request);
    Console.WriteLine(response.Content);
    ```

=== "Java - OkHttp"

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

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
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

=== "Python - http.client"

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

=== "JavaScript - Fetch"

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

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    
    ```