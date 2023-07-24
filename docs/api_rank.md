---
tags:
  - API
---

# 排行榜


### 榜单集合

{{serverUrl}}[^1]/api/AppRank/:appId[^2]/Tables

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppRank/:appId/Tables' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppRank/:appId/Tables", Method.Get);
        request.AddHeader("Authorization", "Bearer token");
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
          .url("https://www.oauthapp.com/api/AppRank/:appId/Tables")
          .method("GET", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppRank/:appId/Tables',
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
        conn.request("GET", "/api/AppRank/:appId/Tables", payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppRank/:appId/Tables", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 数据表集合的数组，每个数组元素代表1个榜单名称 |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
        "code": 200,
        "data": [
            "game1",
            "game2",
            "game3"
        ],
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppRank/AppRankTables){ .md-button }


### 创建榜单

{{serverUrl}}[^1]/api/AppRank/:appid[^2]/CreateTable?tableName=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |
    | tableName | 表名 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request POST 'https://www.oauthapp.com/api/AppRank/:appId/CreateTable?tableName=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppRank/:appId/CreateTable?tableName=");
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
          .url("https://www.oauthapp.com/api/AppRank/:appId/CreateTable?tableName=")
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
          url: 'https://www.oauthapp.com/api/AppRank/:appId/CreateTable?tableName=',
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
        conn.request("POST", "/api/AppRank/:appId/CreateTable?tableName=", payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppRank/:appId/CreateTable?tableName=", requestOptions)
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppRank/AppRankCreateTable){ .md-button }


### 榜单统计

{{serverUrl}}[^1]/api/AppRank/:appId[^2]/:table[^3]/Report

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppRank/:appId/:table/Report' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppRank/:appId/:table/Report", Method.Get);
        request.AddHeader("Authorization", "Bearer token");
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
          .url("https://www.oauthapp.com/api/AppRank/:appId/:table/Report")
          .method("GET", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppRank/:appId/:table/Report',
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
        conn.request("GET", "/api/AppRank/:appId/:table/Report", payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppRank/:appId/:table/Report", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"


    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含count、totalScore、maxScore、minScore 和 avgScore |
    | err | 错误信息 |  |

  ```json linenums="1"
  {
      "code": 200,
      "data": {
          // 总数据条数
          "count": 4,
          // 总分数
          "totalScore": 48,
          // 最高分
          "maxScore": 22,
          // 最低分
          "minScore": 3,
          // 平均分
          "avgScore": 12
      },
      "err": ""
  }
  ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppRank/AppRankReport){ .md-button }

### 榜单数据

{{serverUrl}}[^1]/api/AppRank/:appId[^2]/:table[^3]?pltform=&unionId&nickName&tag&skip=0&take=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |
    | platform | 字符串类型，可选，第三方平台标识字符串，  | 如"web"、"weibo"、"wexin"、"qq"等。如果不传递该参数，则默认为"web"，表示当前应用的网站平台。 |
    | unionId | 字符串类型，可选，第三方平台的用户ID。 | 如果不传递该参数，则默认为当前登录用户的ID。 |
    | nickName | 字符串类型，可选，用户昵称。 |  |
    | tag | 字符串类型，可选，自定义标签。 |  |
    | skip | 数字类型，可选，表示要跳过的记录数 | 默认为0 |
    | take | 数字类型，可选，表示要获取的记录数 | 默认为10 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppRank/:appId/:table?pltform=&unionId=&nickName=&tag=&       take=&skip=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com")
        {
          MaxTimeout = -1,
        };
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppRank/:appId/:table?pltform=&unionId=&nickName=&tag=&   take=30&skip=0", Method.Get);
        request.AddHeader("Authorization", "Bearer token");
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
          .url("https://www.oauthapp.com/api/AppRank/:appId/:table?pltform=&unionId=&nickName=&tag=&    take=30&skip=0")
          .method("GET", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppRank/:appId/:table?pltform=&unionId=&nickName=&tag=&    take=30&skip=0',
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
        conn.request("GET", "/api/AppRank/:appId/:table?pltform=&unionId=&nickName=&tag=&take=30&skip=0",     payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppRank/:appId/:table?pltform=&unionId=&nickName=&tag=&   take=30&skip=0", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含 total 、data、take和skip |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
        "code": 200,
        "data": {
            "total": 4,
            "data": [
                {
                    "id": 2,
                    "userID": 1,
                    "tags": "",
                    "data": "",
                    "remark": "",
                    "unionID": "15f51ff96acb3f85cdcf4383e879d8d6",
                    "platform": "web",
                    "avatar": "https://2.fs.oauthapp.com/__ranks/user.png",
                    "nickName": "",
                    "score": 22,
                    "maximumScore": 22,
                    "showIndex": 0,
                    "createDate": "2022-11-25 14:00:56",
                    "lastUpdate": "2022-12-09 15:35:23"
                },
                {
                    "id": 4,
                    "userID": 2,
                    "tags": "",
                    "data": "",
                    "remark": "",
                    "unionID": "15f51ff96acb3f85cdcf4383e879d8d6",
                    "platform": "web",
                    "avatar": "https://2.fs.oauthapp.com/__ranks/user.png",
                    "nickName": "",
                    "score": 22,
                    "maximumScore": 22,
                    "showIndex": 0,
                    "createDate": "2022-11-25 14:00:56",
                    "lastUpdate": "2022-12-09 15:35:23"
                }
            ],
            "take": 30,
            "skip": 0
        },
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppRank/AppRankList){ .md-button }

### 提交分数

{{serverUrl}}[^1]/api/AppRank/:appId[^2]/:table[^3]

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | PUT |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request PUT 'https://www.oauthapp.com/api/AppRank/:appId/:table' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "userID": "",
          "tags": "",
          "data": "",
          "remark": "",
          "unionID": "",
          "platform": "",
          "avatar": "",
          "nickName": "",
          "score": "",
          "maximumScore": ""
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppRank/:appId/:table", Method.Put);
        request.AddHeader("Content-Type", "application/json");
        request.AddHeader("Authorization", "Bearer token");
        var body = @"{" + "\n" +
        @"    ""userID"": 2," + "\n" +
        @"    ""tags"": """"," + "\n" +
        @"    ""data"": """"," + "\n" +
        @"    ""remark"": """"," + "\n" +
        @"    ""unionID"": ""15f51ff96acb3f85cdcf4383e879d8d6""," + "\n" +
        @"    ""platform"": ""web""," + "\n" +
        @"    ""avatar"": ""https://2.fs.oauthapp.com/__ranks/user.png""," + "\n" +
        @"    ""nickName"": """"," + "\n" +
        @"    ""score"": 22," + "\n" +
        @"    ""maximumScore"": 22," + "\n" +
        @"    ""showIndex"": 0," + "\n" +
        @"    ""createDate"": ""2022-11-25 14:00:56""," + "\n" +
        @"    ""lastUpdate"": ""2022-12-09 15:35:23""" + "\n" +
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
        RequestBody body = RequestBody.create(mediaType, "{\n    \"userID\": 2,\n    \"tags\": \"\",\n        \"data\": \"\",\n    \"remark\": \"\",\n    \"unionID\":    \"15f51ff96acb3f85cdcf4383e879d8d6\",   \n    \"platform\": \"web\",\n    \"avatar\": \"https://2.fs.oauthapp.com/__ranks/user.png\",   \n    \"nickName\": \"\",\n       \"score\": 22,\n    \"maximumScore\": 22,\n    \"showIndex\": 0,   \n    \"createDate\": \"2022-11-25 14:00:56\",\n    \"lastUpdate\": \"2022-12-09 15:35:23\"\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppRank/:appId/:table")
          .method("PUT", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "userID": 2,
          "tags": "",
          "data": "",
          "remark": "",
          "unionID": "15f51ff96acb3f85cdcf4383e879d8d6",
          "platform": "web",
          "avatar": "https://2.fs.oauthapp.com/__ranks/user.png",
          "nickName": "",
          "score": 22,
          "maximumScore": 22,
          "showIndex": 0,
          "createDate": "2022-11-25 14:00:56",
          "lastUpdate": "2022-12-09 15:35:23"
        });

        var config = {
          method: 'put',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppRank/:appId/:table',
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
          "userID": 2,
          "tags": "",
          "data": "",
          "remark": "",
          "unionID": "15f51ff96acb3f85cdcf4383e879d8d6",
          "platform": "web",
          "avatar": "https://2.fs.oauthapp.com/__ranks/user.png",
          "nickName": "",
          "score": 22,
          "maximumScore": 22,
          "showIndex": 0,
          "createDate": "2022-11-25 14:00:56",
          "lastUpdate": "2022-12-09 15:35:23"
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer token'
        }
        conn.request("PUT", "/api/AppRank/:appId/:table", payload, headers)
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
          "userID": 2,
          "tags": "",
          "data": "",
          "remark": "",
          "unionID": "15f51ff96acb3f85cdcf4383e879d8d6",
          "platform": "web",
          "avatar": "https://2.fs.oauthapp.com/__ranks/user.png",
          "nickName": "",
          "score": 22,
          "maximumScore": 22,
          "showIndex": 0,
          "createDate": "2022-11-25 14:00:56",
          "lastUpdate": "2022-12-09 15:35:23"
        });

        var requestOptions = {
          method: 'PUT',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppRank/:appId/:table", requestOptions)
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppRank/AppRankPut){ .md-button }

### 用户排名

{{serverUrl}}[^1]/api/AppRank/:appId[^2]/:table[^3]/UserRank?platform=&unionID=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppRank/:appId/:table/UserRanking?platform=&unionID=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppRank/:appId/:table/UserRanking?platform=&unionID=", Method.    Get);
        request.AddHeader("Authorization", "Bearer token");
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
          .url("https://www.oauthapp.com/api/AppRank/:appId/:table/UserRanking?platform=&unionID=")
          .method("GET", body)
          .addHeader("Authorization", "Bearer token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');

        var config = {
          method: 'get',
        maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppRank/:appId/:table/UserRanking?platform=&unionID=',
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
        conn.request("GET", "/api/AppRank/:appId/:table/UserRanking?platform=&unionID=", payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppRank/:appId/:table/UserRanking?platform=&unionID=",    requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含unionID、avatar、nickName、data、score、maximumScore、betterRankIndex、rankIndex、rankTotalCount 和 beyoundPercent |
    | err | 错误信息 |  |

    ```json linenums="1"
    {
        "code": 200,
        "data": {
            "unionID": "15f51ff96acb3f85cdcf4383e879d8d6",
            "avatar": "https://2.fs.oauthapp.com/__ranks/user.png",
            "nickName": "",
            "data": "",
            "score": 22,
            "maximumScore": 22,
            "betterRankIndex": 1,
            "rankIndex": 1,
            "rankTotalCount": 4,
            "beyoundPercent": 100.0
        },
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppRank/AppRankUserRanking){ .md-button }

[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID

[^3]:table：要替换为实际数据表的名称