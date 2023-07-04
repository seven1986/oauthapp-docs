---
tags:
  - 服务端
---

# 用户

> baseUrl ：https://www.oauthapp.com

## Union ID

### 登录

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/UnionIDSignIn | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |


=== "C# - RestSharp"

    ```CSharp linenums="1"
    var client = new RestClient("https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignIn");
    client.Timeout = -1;
    var request = new RestRequest(Method.POST);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer access_token");
    var body = @"{" + "\n" +
    @"  ""platform"": ""web""," + "\n" +
    @"  ""unionID"": ""123456""" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"platform\": \"web\",\n  \"unionID\": \"123456\"\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignIn")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer access_token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "platform": "web",
      "unionID": "123456"
    });

    var config = {
      method: 'post',
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignIn',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer access_token'
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
      "platform": "web",
      "unionID": "123456"
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer access_token'
    }
    conn.request("POST", "/api/AppUsers/:appId/UnionIDSignIn", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer access_token");

    var raw = JSON.stringify({"platform":"web","unionID":"123456"});

    var requestOptions = {
    method: 'POST',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignIn", requestOptions)
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
        "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI2MzgxMjY3NDkxOTg4MzA0MTMiLCJ0ZW5hbnRfaWQiOiI0IiwidGVuYW50X25hbWUiOiJ3d3cub2F1dGhhcHAuY29tIiwiYXBwaWQiOiIyIiwibmFtZWlkIjoiMzYiLCJ1bmlxdWVfbmFtZSI6IjZhZDE4YmFlMzQwOGQ0ZDFiNjU1YjVjMTU5MjJmZmFkIiwicm9sZSI6IiIsInBpY3R1cmUiOiIiLCJlbWFpbCI6IiIsIm1vYmlsZSI6IiIsInVuaW9uaWQiOiI2YWQxOGJhZTM0MDhkNGQxYjY1NWI1YzE1OTIyZmZhZCIsInBsYXRmb3JtIjoid2ViIiwiZ3JhbnRfdHlwZSI6InVuaW9uaWQiLCJnaXZlbl9uYW1lIjoiIiwiZ3JvdXBzaWQiOiJhcHAiLCJwZXJtaXNzaW9uIjoiIiwibmJmIjoxNjc3MDQ5MzE5LCJleHAiOjE2NzcxMzU3MTksImlhdCI6MTY3NzA0OTMxOSwiaXNzIjoiaHR0cHM6Ly93d3cub2F1dGhhcHAuY29tLyIsImF1ZCI6Imh0dHBzOi8vd3d3Lm9hdXRoYXBwLmNvbS8ifQ.680xn17uYLJUMP2-aalsICxouVasVB-9DsUlLtCKMF8",
        "token_type": "Bearer",
        "expires_in": 86400
    },
    "err": ""
    }
    ```

### 注册

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/UnionIDSignUp | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/UnionIDSignUp", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer {{bearerToken}}");
    var body = @"{" + "\n" +
    @"  ""platform"": ""web""," + "\n" +
    @"  ""pwd"": ""123456""," + "\n" +
    @"  ""unionID"": ""laborumUt""," + "\n" +
    @"  ""avatar"": """"," + "\n" +
    @"  ""nickName"": ""utreprehenderit""," + "\n" +
    @"  ""email"": ""laborumUt@test.com""," + "\n" +
    @"  ""phone"": ""111111111""," + "\n" +
    @"  ""userName"": ""Duis""," + "\n" +
    @"  ""data"": """"," + "\n" +
    @"  ""emailIsValid"": false," + "\n" +
    @"  ""phoneIsValid"": false" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"platform\": \"web\",\n  \"pwd\": \"123456\",\n  \"unionID\": \"laborumUt\",\n  \"avatar\": \"\",\n     \"nickName\": \"utreprehenderit\",\n  \"email\": \"laborumUt@test.com\",\n  \"phone\": \"111111111\",\n  \"userName\": \"Duis\",\n  \"data\": \"\",\n     \"emailIsValid\": false,\n  \"phoneIsValid\": false\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignUp")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer {{bearerToken}}")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "platform": "web",
      "pwd": "123456",
      "unionID": "laborumUt",
      "avatar": "",
      "nickName": "utreprehenderit",
      "email": "laborumUt@test.com",
      "phone": "111111111",
      "userName": "Duis",
      "data": "",
      "emailIsValid": false,
      "phoneIsValid": false
    });

    var config = {
      method: 'post',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignUp',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer {{bearerToken}}'
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
      "platform": "web",
      "pwd": "123456",
      "unionID": "laborumUt",
      "avatar": "",
      "nickName": "utreprehenderit",
      "email": "laborumUt@test.com",
      "phone": "111111111",
      "userName": "Duis",
      "data": "",
      "emailIsValid": False,
      "phoneIsValid": False
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer {{bearerToken}}'
    }
    conn.request("POST", "/api/AppUsers/:appId/UnionIDSignUp", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer {{bearerToken}}");

    var raw = JSON.stringify({
      "platform": "web",
      "pwd": "123456",
      "unionID": "laborumUt",
      "avatar": "",
      "nickName": "utreprehenderit",
      "email": "laborumUt@test.com",
      "phone": "111111111",
      "userName": "Duis",
      "data": "",
      "emailIsValid": false,
      "phoneIsValid": false
    });

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignUp", requestOptions)
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
        "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI2MzgxMjY3NTA0NjkxMzIzODUiLCJ0ZW5hbnRfaWQiOiI0IiwidGVuYW50X25hbWUiOiJ3d3cub2F1dGhhcHAuY29tIiwiYXBwaWQiOiIyIiwibmFtZWlkIjoiMzciLCJ1bmlxdWVfbmFtZSI6IkR1aXMiLCJyb2xlIjoiIiwicGljdHVyZSI6IiIsImVtYWlsIjoibGFib3J1bVV0QHRlc3QuY29tIiwibW9iaWxlIjoiMTExMTExMTExIiwidW5pb25pZCI6ImxhYm9ydW1VdCIsInBsYXRmb3JtIjoid2ViIiwiZ3JhbnRfdHlwZSI6InVuaW9uaWQiLCJnaXZlbl9uYW1lIjoidXRyZXByZWhlbmRlcml0IiwiZ3JvdXBzaWQiOiJhcHAiLCJwZXJtaXNzaW9uIjoiIiwibmJmIjoxNjc3MDQ5NDQ2LCJleHAiOjE2NzcxMzU4NDYsImlhdCI6MTY3NzA0OTQ0NiwiaXNzIjoiaHR0cHM6Ly93d3cub2F1dGhhcHAuY29tLyIsImF1ZCI6Imh0dHBzOi8vd3d3Lm9hdXRoYXBwLmNvbS8ifQ.K2lcuryliPfCv-9U_LurNWjYq4zsKhINtn6-NELGmKY",
        "token_type": "Bearer",
        "expires_in": 86400
    },
    "err": ""
    }
    ```

## 账号密码

### 登录

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/SignIn | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/SignIn", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer {{bearerToken}}");
    var body = @"{" + "\n" +
    @"  ""pwd"": ""123456""," + "\n" +
    @"  ""userName"": ""wwww""" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"pwd\": \"123456\",\n  \"userName\": \"wwww\"\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/SignIn")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer {{bearerToken}}")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "pwd": "123456",
      "userName": "wwww"
    });

    var config = {
      method: 'post',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/SignIn',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer {{bearerToken}}'
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
      "pwd": "123456",
      "userName": "wwww"
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer {{bearerToken}}'
    }
    conn.request("POST", "/api/AppUsers/:appId/SignIn", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer {{bearerToken}}");

    var raw = JSON.stringify({
      "pwd": "123456",
      "userName": "wwww"
    });

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/SignIn", requestOptions)
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
        "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI2MzgxMjY3NjA0NzQ4MDI5NzIiLCJ0ZW5hbnRfaWQiOiI0IiwidGVuYW50X25hbWUiOiJ3d3cub2F1dGhhcHAuY29tIiwiYXBwaWQiOiIyIiwibmFtZWlkIjoiMzgiLCJ1bmlxdWVfbmFtZSI6Ind3d3ciLCJyb2xlIjoiIiwicGljdHVyZSI6IiIsImVtYWlsIjoid3d3d0B0ZXN0LmNvbSIsIm1vYmlsZSI6IjExMTExMTExMSIsInVuaW9uaWQiOiIiLCJwbGF0Zm9ybSI6IndlYiIsImdyYW50X3R5cGUiOiJhY2NvdW50IiwiZ2l2ZW5fbmFtZSI6Ind3d3ciLCJncm91cHNpZCI6ImFwcCIsInBlcm1pc3Npb24iOiIiLCJuYmYiOjE2NzcwNTA0NDcsImV4cCI6MTY3NzEzNjg0NywiaWF0IjoxNjc3MDUwNDQ3LCJpc3MiOiJodHRwczovL3d3dy5vYXV0aGFwcC5jb20vIiwiYXVkIjoiaHR0cHM6Ly93d3cub2F1dGhhcHAuY29tLyJ9.ZSzCyc4r_gy-rm4IObRC1woCnefcZH-44r3r0_4IpHM",
        "token_type": "Bearer",
        "expires_in": 86400
    },
    "err": ""
    }
    ```

### 注册

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/SignUp | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/SignUp", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer {{bearerToken}}");
    var body = @"{" + "\n" +
    @"  ""nickName"": ""wwww""," + "\n" +
    @"  ""platform"": ""web""," + "\n" +
    @"  ""pwd"": ""123456""," + "\n" +
    @"  ""userName"": ""wwww""," + "\n" +
    @"  ""email"": ""wwww@test.com""," + "\n" +
    @"  ""phone"": ""111111111""," + "\n" +
    @"  ""avatar"": """"," + "\n" +
    @"  ""data"": """"" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"nickName\": \"wwww\",\n  \"platform\": \"web\",\n  \"pwd\": \"123456\",\n  \"userName\": \"wwww\",\n     \"email\": \"wwww@test.com\",\n  \"phone\": \"111111111\",\n  \"avatar\": \"\",\n  \"data\": \"\"\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/SignUp")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer {{bearerToken}}")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "nickName": "wwww",
      "platform": "web",
      "pwd": "123456",
      "userName": "wwww",
      "email": "wwww@test.com",
      "phone": "111111111",
      "avatar": "",
      "data": ""
    });

    var config = {
      method: 'post',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/SignUp',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer {{bearerToken}}'
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
      "nickName": "wwww",
      "platform": "web",
      "pwd": "123456",
      "userName": "wwww",
      "email": "wwww@test.com",
      "phone": "111111111",
      "avatar": "",
      "data": ""
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer {{bearerToken}}'
    }
    conn.request("POST", "/api/AppUsers/:appId/SignUp", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer {{bearerToken}}");

    var raw = JSON.stringify({
      "nickName": "wwww",
      "platform": "web",
      "pwd": "123456",
      "userName": "wwww",
      "email": "wwww@test.com",
      "phone": "111111111",
      "avatar": "",
      "data": ""
    });

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/SignUp", requestOptions)
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
        "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI2MzgxMjY3NTczNzY3OTUxNzYiLCJ0ZW5hbnRfaWQiOiI0IiwidGVuYW50X25hbWUiOiJ3d3cub2F1dGhhcHAuY29tIiwiYXBwaWQiOiIyIiwibmFtZWlkIjoiMzgiLCJ1bmlxdWVfbmFtZSI6Ind3d3ciLCJyb2xlIjoiIiwicGljdHVyZSI6IiIsImVtYWlsIjoid3d3d0B0ZXN0LmNvbSIsIm1vYmlsZSI6IjExMTExMTExMSIsInVuaW9uaWQiOiIiLCJwbGF0Zm9ybSI6IndlYiIsImdyYW50X3R5cGUiOiJhY2NvdW50IiwiZ2l2ZW5fbmFtZSI6Ind3d3ciLCJncm91cHNpZCI6ImFwcCIsInBlcm1pc3Npb24iOiIiLCJuYmYiOjE2NzcwNTAxMzcsImV4cCI6MTY3NzEzNjUzNywiaWF0IjoxNjc3MDUwMTM3LCJpc3MiOiJodHRwczovL3d3dy5vYXV0aGFwcC5jb20vIiwiYXVkIjoiaHR0cHM6Ly93d3cub2F1dGhhcHAuY29tLyJ9.OPWa8n2vc6bZb8yYau411I6N3tKDRW1yDyxvJhl0WtM",
        "token_type": "Bearer",
        "expires_in": 86400
    },
    "err": ""
    }
    ```

## 微信小程序

### 网页端

#### 获取预登录SignKey

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/QRCodePreSignIn | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/QRCodePreSignIn", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer {{bearerToken}}");
    var body = @"{" + "\n" +
    @"  ""scopes"": ""laboris""," + "\n" +
    @"  ""remark"": ""ad amet laboris""," + "\n" +
    @"  ""scheme"": ""app""" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"scopes\": \"laboris\",\n  \"remark\": \"ad amet laboris\",\n  \"scheme\": \"app\"\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodePreSignIn")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer {{bearerToken}}")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "scopes": "laboris",
      "remark": "ad amet laboris",
      "scheme": "app"
    });

    var config = {
      method: 'post',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodePreSignIn',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer {{bearerToken}}'
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
      "scopes": "laboris",
      "remark": "ad amet laboris",
      "scheme": "app"
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer {{bearerToken}}'
    }
    conn.request("POST", "/api/AppUsers/:appId/QRCodePreSignIn", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer {{bearerToken}}");

    var raw = JSON.stringify({
      "scopes": "laboris",
      "remark": "ad amet laboris",
      "scheme": "app"
    });

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/QRCodePreSignIn", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | signInKey |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": 19,
        "err": ""
    }
    ```

#### 登录结果查询

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/QRCodeSignIn | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/QRCodeSignIn", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer {{bearerToken}}");
    var body = @"{" + "\n" +
    @"  ""signInKey"": 19" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"signInKey\": 19\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignIn")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer {{bearerToken}}")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "signInKey": 19
    });

    var config = {
      method: 'post',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignIn',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer {{bearerToken}}'
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
      "signInKey": 19
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer {{bearerToken}}'
    }
    conn.request("POST", "/api/AppUsers/:appId/QRCodeSignIn", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer {{bearerToken}}");

    var raw = JSON.stringify({
      "signInKey": 19
    });

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignIn", requestOptions)
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
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI2MzgxMjY3OTEzMjYwMTIzNTEiLCJ0ZW5hbnRfaWQiOiI0IiwidGVuYW50X25hbWUiOiJ3d3cub2F1dGhhcHAuY29tIiwiYXBwaWQiOiIyIiwibmFtZWlkIjoiMiIsInVuaXF1ZV9uYW1lIjoib0tPc3E0MFUxck1KMENydU9BckNiRWY4YUpBOCIsInJvbGUiOiIiLCJwaWN0dXJlIjoiaHR0cHM6Ly90aGlyZHd4LnFsb2dvLmNuL21tb3Blbi92aV8zMi9QT2dFd2g0bUlITzRuaWJIMEtsTUVDTmpqR3hRVXEyNFpFYUdUNHBvQzZpY1JpY2NWR0tTeVh3aWJjUHE0QldtaWFJR3VHMWljd3hhUVg2Z3JDOVZlbVpvSjhyZy8xMzIiLCJlbWFpbCI6IiIsIm1vYmlsZSI6IiIsInVuaW9uaWQiOiJvS09zcTQwVTFyTUowQ3J1T0FyQ2JFZjhhSkE4IiwicGxhdGZvcm0iOiJ3eG1pbmlwIiwiZ3JhbnRfdHlwZSI6InVuaW9uaWQiLCJnaXZlbl9uYW1lIjoi5b6u5L-h55So5oi3IiwiZ3JvdXBzaWQiOiJhcHAiLCJwZXJtaXNzaW9uIjoiIiwibmJmIjoxNjc3MDUzNTMyLCJleHAiOjE2NzcxMzk5MzIsImlhdCI6MTY3NzA1MzUzMiwiaXNzIjoiaHR0cHM6Ly93d3cub2F1dGhhcHAuY29tLyIsImF1ZCI6Imh0dHBzOi8vd3d3Lm9hdXRoYXBwLmNvbS8ifQ.GaWqX4GgkKW8jDnNefdVCUAonNOnL3YT9MWQq2fcomM",
    "token_type": "Bearer",
    "expires_in": 86400
    },
    "err": ""
    }     
    ```

### 小程序端

#### 确认扫码成功

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/QRCodeScan | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/QRCodeScan", Method.Post);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer {{bearerToken}}");
    var body = @"{" + "\n" +
    @"  ""signInKey"": 20" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"signInKey\": 20\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeScan")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer {{bearerToken}}")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "signInKey": 20
    });

    var config = {
      method: 'post',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeScan',
      headers: { 
        'Content-Type': 'application/json', 
        'Authorization': 'Bearer {{bearerToken}}'
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
      "signInKey": 20
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer {{bearerToken}}'
    }
    conn.request("POST", "/api/AppUsers/:appId/QRCodeScan", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    myHeaders.append("Authorization", "Bearer {{bearerToken}}");

    var raw = JSON.stringify({
      "signInKey": 20
    });

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeScan", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含appID、name、logo、website、description、tags、scopes、remark 和 scheme |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": {
            "appID": 2,
            "name": "开发文档",
            "logo": "https://blob.oauthapp.com/4/tenant/2/API.png",
            "website": "https://web.oauthapp.com/4/docs",
            "description": null,
            "tags": null,
            "scopes": "openid profile role promission",
            "remark": "test",
            "scheme": "app"
        },
        "err": ""
    }
    ```

#### 注册

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/QRCodeSignUp | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | 不需要 |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var client = new RestClient("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp");
    client.Timeout = -1;
    var request = new RestRequest(Method.POST);
    request.AddHeader("Content-Type", "application/json");
    var body = @"{" + "\n" +
    @"  ""signInKey"": """"," + "\n" +
    @"  ""unionID"": """"," + "\n" +
    @"  ""avatar"": """"," + "\n" +
    @"  ""platform"": ""wxminip""," + "\n" +
    @"  ""nickName"": """"," + "\n" +
    @"  ""userName"": """"," + "\n" +
    @"  ""phone"": """"," + "\n" +
    @"  ""phoneIsValid"": false," + "\n" +
    @"  ""email"": """"," + "\n" +
    @"  ""emailIsValid"": false" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"signInKey\": \"\",\n  \"unionID\": \"\",   \n  \"avatar\": \"\",\n  \"platform\": \"wxminip\",\n  \"nickName\": \"\",\n  \"userName\": \"\",  \n  \"phone\": \"\",\n  \"phoneIsValid\": false,\n  \"email\": \"\",\n  \"emailIsValid\": false\n}    ");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp")
      .method("POST", body)
      .addHeader("Content-Type", "application/json")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "signInKey": "",
      "unionID": "",
      "avatar": "",
      "platform": "wxminip",
      "nickName": "",
      "userName": "",
      "phone": "",
      "phoneIsValid": false,
      "email": "",
      "emailIsValid": false
    });

    var config = {
      method: 'post',
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp',
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
      "signInKey": "",
      "unionID": "",
      "avatar": "",
      "platform": "wxminip",
      "nickName": "",
      "userName": "",
      "phone": "",
      "phoneIsValid": False,
      "email": "",
      "emailIsValid": False
    })
    headers = {
      'Content-Type': 'application/json'
    }
    conn.request("POST", "/api/AppUsers/:appId/QRCodeSignUp", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");

    var raw = JSON.stringify({"signInKey":"","unionID":"","avatar":"","platform":"wxminip", "nickName":"","userName":"","phone":"","phoneIsValid":false,"email":"","emailIsValid":false});

    var requestOptions = {
    method: 'POST',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp", requestOptions)
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
        "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI2MzgxMjY3OTY0MzE3MzgyMTEiLCJ0ZW5hbnRfaWQiOiI0IiwidGVuYW50X25hbWUiOiJ3d3cub2F1dGhhcHAuY29tIiwiYXBwaWQiOiIyIiwibmFtZWlkIjoiMzkiLCJ1bmlxdWVfbmFtZSI6ImV1YWRpcGkiLCJyb2xlIjoiIiwicGljdHVyZSI6ImF2YXRhci5qcGciLCJlbWFpbCI6ImV1YWRpcGlAd3htaW5pcC5jb20iLCJtb2JpbGUiOiIxMTExMTExMTExIiwidW5pb25pZCI6ImV1YWRpcGkiLCJwbGF0Zm9ybSI6Ind4bWluaXAiLCJncmFudF90eXBlIjoidW5pb25pZCIsImdpdmVuX25hbWUiOiJ3d3d3IiwiZ3JvdXBzaWQiOiJhcHAiLCJwZXJtaXNzaW9uIjoiIiwibmJmIjoxNjc3MDU0MDQzLCJleHAiOjE2NzcxNDA0NDMsImlhdCI6MTY3NzA1NDA0MywiaXNzIjoiaHR0cHM6Ly93d3cub2F1dGhhcHAuY29tLyIsImF1ZCI6Imh0dHBzOi8vd3d3Lm9hdXRoYXBwLmNvbS8ifQ.o-MCgxM-_bR7UuHNX2Ul4cK0Cg7MQP524JF4z44camc",
        "token_type": "Bearer",
        "expires_in": 86400
    },
    "err": ""
    }
    ```

## 获取用户资料

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/Profile | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | Bearer Token |  |


=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/Profile", Method.Get);
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
      .url("https://www.oauthapp.com/api/AppUsers/:appId/Profile")
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
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/Profile',
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
    conn.request("GET", "/api/AppUsers/:appId/Profile", payload, headers)
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

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/Profile", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 具体包含appID、platform、unionID、phone、createDate、userName、phoneIsValid、data、email、emailIsValid、lastUpdate、nickName、id、avatr 和 role |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": {
            "appID": 2,
            "platform": "wxminip",
            "unionID": "euadipi",
            "phone": "1111111111",
            "createDate": "2023-02-22 16:20:43",
            "userName": "euadipi",
            "phoneIsValid": true,
            "data": null,
            "email": "euadipi@wxminip.com",
            "emailIsValid": false,
            "lastUpdate": "2023-02-22 16:20:43",
            "nickName": "wwww",
            "id": 39,
            "avatar": "avatar.jpg",
            "role": "user"
        },
        "err": ""
    }
    ```

## 更新用户资料

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | PUT |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/Profile | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | Bearer Token |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/Profile", Method.Put);
    request.AddHeader("Content-Type", "application/json");
    request.AddHeader("Authorization", "Bearer token");
    var body = @"{" + "\n" +
    @"  ""avatar"": ""avatar.png""," + "\n" +
    @"  ""data"": ""自定义数据""," + "\n" +
    @"  ""nickName"": ""wwww""" + "\n" +
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
    RequestBody body = RequestBody.create(mediaType, "{\n  \"avatar\": \"avatar.png\",\n  \"data\": \"自定义数据\",\n  \"nickName\": \"wwww\"\n}");
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/AppUsers/:appId/Profile")
      .method("PUT", body)
      .addHeader("Content-Type", "application/json")
      .addHeader("Authorization", "Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var data = JSON.stringify({
      "avatar": "avatar.png",
      "data": "自定义数据",
      "nickName": "wwww"
    });

    var config = {
      method: 'put',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/Profile',
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
      "avatar": "avatar.png",
      "data": "自定义数据",
      "nickName": "wwww"
    })
    headers = {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer token'
    }
    conn.request("PUT", "/api/AppUsers/:appId/Profile", payload, headers)
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
      "avatar": "avatar.png",
      "data": "自定义数据",
      "nickName": "wwww"
    });

    var requestOptions = {
      method: 'PUT',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/AppUsers/:appId/Profile", requestOptions)
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



## 积分记录

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| 请求方式 | GET |  |
| 请求地址 | {{baseUrl}}/api/AppUsers/:appId/PointLog?type=&skip=&take= | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | Bearer Token |  |
| `参数说明`  |  |  |
| type | 分类 | 0：全部，1：充值，2：消耗 |
| skip |  可选，指定要拉取的数据条数。 | 0 |
| take |  可选，指定要跳过的数据条数。 | 10 |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com");
    var client = new RestClient(options);
    var request = new RestRequest("/api/AppUsers/:appId/PointLog?type=&skip=&take=", Method.Get);
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
      .url("https://www.oauthapp.com/api/AppUsers/:appId/PointLog?type=&skip=&take=")
      .method("GET", body)
      .addHeader("Authorization", "Bearer {{bearerToken}}")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    const axios = require('axios');

    let config = {
      method: 'get',
      maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/AppUsers/:appId/PointLog?type=&skip=&take=',
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

=== "Python - http.client"

    ```Python linenums="1"
    import http.client

    conn = http.client.HTTPSConnection("www.oauthapp.com")
    payload = ''
    headers = {
      'Authorization': 'Bearer {{bearerToken}}'
    }
    conn.request("GET", "/api/AppUsers/:appId/PointLog?type=&skip=&take=", payload, headers)
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
    
    fetch("https://www.oauthapp.com/api/AppUsers/:appId/PointLog?type=&skip=&take=", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 |  |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
       "code": 200,
       "data": {
         "total": 2,
         "data": [
           {
             "id": 2,
             "userID": 84,
             "used": 10000,
             "remark": "",
             "createDate": "2023-06-16 15:35:06"
           },
           {
             "id": 1,
             "userID": 84,
             "used": 10000,
             "remark": "",
             "createDate": "2023-06-16 15:23:50"
           }
         ]
       },
       "err": ""
    }
    ```
