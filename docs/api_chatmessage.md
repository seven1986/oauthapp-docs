---
tags:
  - API
---

# 消息

### 消息表集合

{{serverUrl}}[^1]/api/AppChatMessages/:appId[^2]/Tables


=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppChatMessages/:appId/Tables' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppChatMessages/:appId/Tables", Method.Get);
        request.AddHeader("Authorization", "Bearer token");
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java "

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppChatMessages/:appId/Tables")
          .method("GET", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppChatMessages/:appId/Tables',
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

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {
          'Authorization': 'Bearer token'
        }
        conn.request("GET", "/api/AppChatMessages/:appId/Tables", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer token");

        var requestOptions = {
          method: 'GET',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppChatMessages/:appId/Tables", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 返回一个数组，每个元素代表1个消息表的名称 |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": [
        "class1",
        "class2",
        "class3"
    ],
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppChatMessages/AppChatMessageTables){ .md-button }


### 创建消息表

{{serverUrl}}[^1]/api/AppChatMessages/:appid[^2]/CreateTable?tableName=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |
    | tableName | 表名 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request POST 'https://www.oauthapp.com/api/AppChatMessages/:appId/CreateTable?tableName=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```

    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppChatMessages/:appId/CreateTable?tableName=");
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
          .url("https://www.oauthapp.com/api/AppChatMessages/:appId/CreateTable?tableName=")
          .method("POST", body)
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppChatMessages/:appId/CreateTable?tableName=',
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
        conn.request("POST", "/api/AppChatMessages/:appId/CreateTable?tableName=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppChatMessages/:appId/CreateTable?tableName=", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | true 或 false |

    ```json
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppChatMessages/AppChatMessageCreateTable){ .md-button }


### 消息组

{{serverUrl}}[^1]/api/AppChatMessages/:appId[^2]/:table[^3]/Categories

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table/Categories' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppChatMessages/:appId/:table/Categories", Method.Get);
        request.AddHeader("Authorization", "Bearer token");
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java "

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppChatMessages/:appId/:table/Categories")
          .method("GET", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table/Categories',
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

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {
          'Authorization': 'Bearer token'
        }
        conn.request("GET", "/api/AppChatMessages/:appId/:table/Categories", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer token");

        var requestOptions = {
          method: 'GET',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppChatMessages/:appId/:table/Categories", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 返回一个数组，每个元素代表1个分类 |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": [
        "分类1",
        "分类2"
        "分类3"
    ],
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppChatMessages/AppChatMessageCategories){ .md-button }

### 消息列表

{{serverUrl}}[^1]/api/AppChatMessages/:appId[^2]/:table[^3]?category=&tag=&search=&take=10&skip=0

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |
    | category | 消息组  |  |
    | tag | 消息标签  |  |
    | search | 查询关键词  |  |
    | take | 拉取条数 | 10 |
    | skip | 跳过条数 | 0 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table?category=&tag=&search=&       take=&skip=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppChatMessages/:appId/:table?category=&tag=&search=&take=10&   skip=0", Method.Get);
        request.AddHeader("Authorization", "Bearer token");
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java "

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppChatMessages/:appId/:table?category=&tag=&search=&take=10&    skip=0")
          .method("GET", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table?category=&tag=&search=&take=10&    skip=0',
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

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {
          'Authorization': 'Bearer token'
        }
        conn.request("GET", "/api/AppChatMessages/:appId/:table?category=&tag=&search=&take=10&skip=0",     payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer token");

        var requestOptions = {
          method: 'GET',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppChatMessages/:appId/:table?category=&tag=&search=&take=10&   skip=0", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含total、data 、take 和 skip |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": {
        "total": 2,
        "data": [
            {
                "id": 2,
                "category": "17_20221123.18.7",
                "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
                "nickName": "张三",
                "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
                "platform": "dingtalk",
                "messageType": "TEXT",
                "content": "2121",
                "remark": "",
                "tags": "",
                "showIndex": 0,
                "createDate": "2022-11-24 17:08:41",
                "lastUpdate": "2022-11-24 17:08:41"
            },
            {
                "id": 1,
                "category": "125_20221124.17.39",
                "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
                "nickName": "张三",
                "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
                "platform": "dingtalk",
                "messageType": "TEXT",
                "content": "2121",
                "remark": "",
                "tags": "",
                "showIndex": 0,
                "createDate": "2022-11-24 17:07:11",
                "lastUpdate": "2022-11-24 17:07:11"
            }
        ],
        "take": 10,
        "skip": 0
    },
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppChatMessages/AppChatMessages){ .md-button }

### 发送消息

{{serverUrl}}[^1]/api/AppChatMessages/:appId[^2]/:table[^3]

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "category": "125_20221124.17.39",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com")
        {
          MaxTimeout = -1,
        };
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppChatMessages/:appId/:table", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        request.AddHeader("Authorization", "Bearer token");
        var body = @"{" + "\n" +
        @"    ""category"": ""125_20221124.17.39""," + "\n" +
        @"    ""unionID"": ""a0bfc6e0d3b03383b0ea9f23673d2c58""," + "\n" +
        @"    ""nickName"": ""张三""," + "\n" +
        @"    ""avatar"": ""https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png""," + "\n" +
        @"    ""platform"": ""dingtalk""," + "\n" +
        @"    ""messageType"": ""TEXT""," + "\n" +
        @"    ""content"": ""2121""," + "\n" +
        @"    ""remark"": """"," + "\n" +
        @"    ""tags"": """"," + "\n" +
        @"    ""showIndex"": 0" + "\n" +
        @"}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java "

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n    \"category\": \"125_20221124.17.39\",    \n    \"unionID\": \"a0bfc6e0d3b03383b0ea9f23673d2c58\",\n    \"nickName\": \"张三\",\n       \"avatar\": \"https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png\",\n    \"platform\":   \"dingtalk\",\n    \"messageType\": \"TEXT\",\n    \"content\": \"2121\",\n    \"remark\": \"\",   \n    \"tags\": \"\",\n    \"showIndex\": 0\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppChatMessages/:appId/:table")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "category": "125_20221124.17.39",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        });

        var config = {
          method: 'post',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table',
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

    === "Python"

        ```Python linenums="1"
        import http.client
        import json

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = json.dumps({
          "category": "125_20221124.17.39",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer token'
        }
        conn.request("POST", "/api/AppChatMessages/:appId/:table", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer token");

        var raw = JSON.stringify({
          "category": "125_20221124.17.39",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppChatMessages/:appId/:table", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | true 或 false |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": true,
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppChatMessages/AppChatMessagePost){ .md-button }

### 删除消息

{{serverUrl}}[^1]/api/AppChatMessages/:appId[^2]/:table[^3]/:id[^4]

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | DELETE |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request DELETE 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppChatMessages/:appId/:table/:id", Method.Delete);
        request.AddHeader("Authorization", "Bearer token");
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java "

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("text/plain");
        RequestBody body = RequestBody.create(mediaType, "");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id")
          .method("DELETE", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        var axios = require('axios');

        var config = {
          method: 'delete',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id',
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

    === "Python"

        ```Python linenums="1"
        import http.client

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = ''
        headers = {
          'Authorization': 'Bearer token'
        }
        conn.request("DELETE", "/api/AppChatMessages/:appId/:table/:id", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer token");

        var requestOptions = {
          method: 'DELETE',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | true 或 false |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": true,
    "err": ""
    }
    ```


[在线调试](https://www.oauthapp.com/swagger/index.html#/AppChatMessages/AppChatMessageDelete){ .md-button }

### 修改消息

{{serverUrl}}[^1]/api/AppChatMessages/:appId[^2]/:table[^3]/:id[^4]

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request PUT 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "category": "125_20221124.17.39",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppChatMessages/:appId/:table/:id", Method.Put);
        request.AddHeader("Content-Type", "application/json");
        request.AddHeader("Authorization", "Bearer token");
        var body = @"{" + "\n" +
        @"    ""category"": ""17_20221123.18.7""," + "\n" +
        @"    ""unionID"": ""a0bfc6e0d3b03383b0ea9f23673d2c58""," + "\n" +
        @"    ""nickName"": ""张三""," + "\n" +
        @"    ""avatar"": ""https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png""," + "\n" +
        @"    ""platform"": ""dingtalk""," + "\n" +
        @"    ""messageType"": ""TEXT""," + "\n" +
        @"    ""content"": ""2121""," + "\n" +
        @"    ""remark"": """"," + "\n" +
        @"    ""tags"": """"," + "\n" +
        @"    ""showIndex"": 0" + "\n" +
        @"}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java "

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n    \"category\": \"17_20221123.18.7\",\n        \"unionID\": \"a0bfc6e0d3b03383b0ea9f23673d2c58\",\n    \"nickName\": \"张三\",\n    \"avatar\":    \"https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png\",\n    \"platform\": \"dingtalk\",   \n    \"messageType\": \"TEXT\",\n    \"content\": \"2121\",\n    \"remark\": \"\",\n      \"tags\": \"\",\n    \"showIndex\": 0\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id")
          .method("PUT", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "category": "17_20221123.18.7",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        });

        var config = {
          method: 'put',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id',
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

    === "Python"

        ```Python linenums="1"
        import http.client
        import json

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        payload = json.dumps({
          "category": "17_20221123.18.7",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer token'
        }
        conn.request("PUT", "/api/AppChatMessages/:appId/:table/:id", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer token");

        var raw = JSON.stringify({
          "category": "17_20221123.18.7",
          "unionID": "a0bfc6e0d3b03383b0ea9f23673d2c58",
          "nickName": "张三",
          "avatar": "https://blob.oauthapp.com/4/tenant/4/%E5%BA%94%E7%94%A8.png",
          "platform": "dingtalk",
          "messageType": "TEXT",
          "content": "2121",
          "remark": "",
          "tags": "",
          "showIndex": 0
        });

        var requestOptions = {
          method: 'PUT',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppChatMessages/:appId/:table/:id", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | true 或 false |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
    "code": 200,
    "data": true,
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppChatMessages/AppChatMessagePut){ .md-button }

[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID

[^3]:table：要替换为实际数据表的名称

[^4]:id：需要替换为实际单条数据的id