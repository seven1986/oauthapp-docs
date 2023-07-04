---
tags:
  - 服务端
---

# 数据库

> baseUrl ：https://www.oauthapp.com

!!! Tip ""
    数据表需要使用oauthapp发布工具创建。数据存储统一为 **json** 格式。

### 表集合

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/AppStorage/:appId/Tables | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | Bearer Token |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppStorage/:appId/Tables", Method.Get);
    request.AddHeader("Authorization", "Bearer token");
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
      .url("https://www.oauthapp.com/api/AppStorage/:appId/Tables")
      .method("GET", body)
      .addHeader("Authorization", "Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');

    var config = {
      method: 'get',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppStorage/:appId/Tables',
      headers: { 
        'Authorization': 'Bearer token'
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
      'Authorization': 'Bearer token'
    }
    conn.request("GET", "/api/AppStorage/:appId/Tables", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Authorization", "Bearer token");

    var requestOptions = {
      method: 'GET',
      headers: myHeaders,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppStorage/:appId/Tables", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```


返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 数据表集合的数组，每个数组元素代表1个表名 |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": [
            "categories",
            "news",
            "departments",
            "settings"
        ],
        "err": ""
    }
    ```

### 查询

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/AppStorage/:appId/:table?tag=&filter=&sort=&take=10&skip=0 | :appId 部分需要替换为实际应用的 ID；:table 需要替换为实际数据表的名称 |
| 登陆凭证 | Bearer Token |  |
| `参数说明`  |  |  |
| tag | 可选，指定要查询的标签。 | 可空 |
| filter | 可选，指定要筛选的条件。它应该是一个对象，对象的属性名是要筛选的字段名，属性值是对应的值。 | {"name":"123"} |
| sort | 可选，指定数据的排序方式。它应该是一个对象，对象的属性名是要排序的字段名，属性值是 true 或 false，true 表示升序排列，false 表示降序排列。 | {"id":true} |
| take | 可选，指定要拉取的数据条数。 | 10 |
| skip | 可选，指定要跳过的数据条数。 | 0 |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppStorage/:appId/:table?tag=&filter=&sort=&take=15&skip=0", Method.Get);
    request.AddHeader("Authorization", "Bearer token");
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
      .url("https://www.oauthapp.com/api/AppStorage/:appId/:table?tag=&filter=&sort=&take=15&skip=0")
      .method("GET", body)
      .addHeader("Authorization", "Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');

    var config = {
      method: 'get',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppStorage/:appId/:table?tag=&filter=&sort=&take=15&skip=0',
      headers: { 
        'Authorization': 'Bearer token'
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
      'Authorization': 'Bearer token'
    }
    conn.request("GET", "/api/AppStorage/:appId/:table?tag=&filter=&sort=&take=15&skip=0", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Authorization", "Bearer token");

    var requestOptions = {
      method: 'GET',
      headers: myHeaders,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppStorage/:appId/:table?tag=&filter=&sort=&take=15&skip=0", requestOptions)
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
        "data": {
            "total": 3,
            "data": [
                {
                    "id": 3,
                    "showIndex": 0,
                    "tags": "",
                    "content": {
                        "avatar": "https://blob.oauthapp.com/4/app/4/azure.png",
                        "title": "2112",
                        "description": "21212121",
                        "timestamp": 1665393391395
                    },
                    "lastChange": "2022-10-10 17:16:27"
                },
                {
                    "id": 2,
                    "showIndex": 0,
                    "tags": "",
                    "content": {
                        "title": "dsadsa",
                        "description": "sadsadasds",
                        "timestamp": 1665392525435
                    },
                    "lastChange": "2022-10-10 17:02:01"
                },
                {
                    "id": 1,
                    "showIndex": 0,
                    "tags": "",
                    "content": {
                        "avatar": "https://blob.oauthapp.com/4/user/1644397917743/assets_api_default.png",
                        "title": "dsadsa",
                        "description": "dasdas",
                        "timestamp": 1644397925591
                    },
                    "lastChange": "2022-10-10 17:01:53"
                }
            ],
            "take": 15,
            "skip": 0
        },
        "err": ""
    }
    ```

### 添加

???+ note "提示"
    添加的数据为自定义的JSON对象。

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppStorage/:appId/:table | :appId 部分需要替换为实际应用的 ID；:table 需要替换为实际数据表的名称 |
| 登陆凭证 | Bearer Token |  |
| body | 请求实体 | showIndex 排序 ;tags 自定义标签 ;content 自定义JSON字符串，必须为JSON格式|

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppStorage/:appId/:table", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer Bearer token");
    var body = @"{" + "\n" +
    @"    ""showIndex"": 0," + "\n" +
    @"    ""tags"": """"," + "\n" +
    @"    ""content"": ""{\""a\"": 1,\""b\"": 2}""" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n    \"showIndex\": 0,\n    \"tags\": \"\",\n    \"content\": \"    {\\\"a\\\": 1,\\\"b\\\": 2}\"\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppStorage/:appId/:table")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    const axios = require('axios');
    let data = JSON.stringify({
      "showIndex": 0,
      "tags": "",
      "content": "{\"a\": 1,\"b\": 2}"
    });

    let config = {
      method: 'post',
      maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppStorage/:appId/:table',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer Bearer token'
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
      "showIndex": 0,
      "tags": "",
      "content": "{\"a\": 1,\"b\": 2}"
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer Bearer token'
    }
    conn.request("POST", "/api/AppStorage/:appId/:table", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer Bearer token");

    var raw = JSON.stringify({
      "showIndex": 0,
      "tags": "",
      "content": "{\"a\": 1,\"b\": 2}"
    });

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppStorage/:appId/:table", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | true 或 false |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```


### 详情


| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/AppStorage/:appId/:table/:id | :appId 部分需要替换为实际应用的 ID；:table 需要替换为实际数据表的名称；:id 需要替换为实际单条数据的id |
| 登陆凭证 | Bearer Token |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com");
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppStorage/:appId/:table/:id", Method.Get);
    request.AddHeader("Authorization", "Bearer token");
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
      .url("https://www.oauthapp.com/api/AppStorage/:appId/:table/:id")
      .method("GET", body)
      .addHeader("Authorization", "Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');

    var config = {
      method: 'get',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppStorage/:appId/:table/:id',
      headers: { 
        'Authorization': 'Bearer token'
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
      'Authorization': 'Bearer token'
    }
    conn.request("GET", "/api/AppStorage/:appId/:table/:id", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Authorization", "Bearer token");

    var requestOptions = {
      method: 'GET',
      headers: myHeaders,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppStorage/:appId/:table/:id", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | JSON格式的单条数据详情 |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": {
            "id": 1,
            "showIndex": 0,
            "tags": null,
            "content": "{\r\n  \"avatar\": \"https://blob.oauthapp.com/4/user/1644397917743/assets_api_default.png\",\r\n  \"title\": \"dsadsa\",\r\n  \"description\":     \"dasdas\",\r\n  \"timestamp\": 1644397925591\r\n}",
            "lastChange": "2022-10-10 17:01:53"
        },
        "err": ""
    }
    ```


### 删除

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | DELETE |  |
| 请求地址 | {{baseUrl}}/api/AppStorage/:appId/:table/:id | :appId 部分需要替换为实际应用的 ID；:tableName 需要替换为实际数据表的名称；:id 需要替换为实际单条数据的id |
| 登陆凭证 | Bearer Token |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com");
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppStorage/:appId/:table/:id", Method.Delete);
    request.AddHeader("Authorization", "Bearer token");
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
      .url("https://www.oauthapp.com/api/AppStorage/:appId/:table/:id")
      .method("DELETE", body)
      .addHeader("Authorization", "Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');

    var config = {
      method: 'delete',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppStorage/:appId/:table/:id',
      headers: { 
        'Authorization': 'Bearer token'
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
      'Authorization': 'Bearer token'
    }
    conn.request("DELETE", "/api/AppStorage/:appId/:table/:id", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Authorization", "Bearer token");

    var requestOptions = {
      method: 'DELETE',
      headers: myHeaders,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppStorage/:appId/:table/:id", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | true 或 false |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```

### 更新

???+ note "提示"
    将数据库中指定数据替换为当前提交的JSON数据。

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | PUT |  |
| 请求地址 | {{baseUrl}}/api/AppStorage/:appId/:table/:id | :appId 部分需要替换为实际应用的 ID；:tableName 需要替换为实际数据表的名称；:id 需要替换为实际单条数据的id |
| 登陆凭证 | Bearer Token |  |
| body | 请求实体 | showIndex 排序 ;tags 自定义标签 ;content 自定义JSON字符串，必须为JSON格式|

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com");
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppStorage/:appId/:table/:id", Method.Put);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer token");
    var body = @"{" + "\n" +
    @"    ""showIndex"": 0," + "\n" +
    @"    ""tags"": """"," + "\n" +
    @"    ""content"": ""{\""a\"": 1,\""b\"": 2}""" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n    \"showIndex\": 0,\n    \"tags\": \"\",\n    \"content\": \"    {\\\"a\\\": 1,\\\"b\\\": 2}\"\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppStorage/:appId/:table/:id")
      .method("PUT", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    let data = JSON.stringify({
      "showIndex": 0,
      "tags": "",
      "content": "{\"a\": 1,\"b\": 2}"
    });

    var config = {
      method: 'put',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppStorage/:appId/:table/:id',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer token'
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
      "showIndex": 0,
      "tags": "",
      "content": "{\"a\": 1,\"b\": 2}"
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer token'
    }
    conn.request("PUT", "/api/AppStorage/:appId/:table/:id", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer token");

    var raw = JSON.stringify({
      "showIndex": 0,
      "tags": "",
      "content": "{\"a\": 1,\"b\": 2}"
    });

    var requestOptions = {
      method: 'PUT',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppStorage/:appId/:table/:id", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | true 或 false |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```