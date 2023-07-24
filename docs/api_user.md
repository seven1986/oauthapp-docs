---
tags:
  - API
---

# 用户

## Union ID

### 登录

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/UnionIDSignIn

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | platform | 第三方平台标识字符串 | web、weibo、wexin、qq / 自定义 |
    | unionID | 第三方平台的用户ID |  |


=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignIn' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"platform": "","unionID": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new RestClient("https://www.oauthapp.com/api/AppUsers/:appId[^2]/UnionIDSignIn");
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

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\n  \"platform\": \"web\",\n  \"unionID\":     \"123456\"\n}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/UnionIDSignIn")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer access_token")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        var axios = require('axios');
        var data = JSON.stringify({
          "platform": "web",
          "unionID": "123456"
        });

        var config = {
          method: 'post',
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/UnionIDSignIn',
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

    === "Python"

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
        conn.request("POST", "/api/AppUsers/:appId[^2]/UnionIDSignIn", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

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

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/UnionIDSignIn", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        ```


=== "返回数据"

    [点击查看](#fn:3){ .md-button }


[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserUnionIDSignIn){ .md-button }

### 注册

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/UnionIDSignUp

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | unionId | 第三方平台的用户ID  | oauthapp.settings.fingerIdentity / 自定义 |
    | platform | 第三方平台标识字符串  | web、weibo、wexin、qq、dingtalk / 自定义 |
    | pwd | 密码，可空  | 默认为：123456 |
    | nickname | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |
    | phone | 手机号，可空  | 如果应用配置了验证手机，则必填 |
    | phoneCode | 手机验证码，可空  | 如果应用配置了验证手机，则必填 |
    | email | 邮箱，可空  | 如果应用配置了验证邮箱，则必填 |
    | emailCode | 邮箱已验证，可空  | 如果应用配置了验证邮箱，则必填 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignUp' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"platform": "","pwd": "","unionID": "","nickName": "","avatar": "","data": "","email": "","emailCode": "","phone": "","phoneCode": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignUp");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"platform\": \"\",\"pwd\": \"\",\"unionID\": \"\",\"nickName\":\"\",\"avatar\": \"\",\"data\": \"\",\"email\": \"\",\"emailCode\": \"\",\"phone\": \"\",\"phoneCode\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"platform\": \"\",\"pwd\": \"\",\"unionID\":\"\",\"nickName\": \"\",\"avatar\": \"\",\"data\": \"\",\"email\": \"\",\"emailCode\": \"\",\"phone\": \"\",\"phoneCode\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignUp")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "platform": "",
          "pwd": "",
          "unionID": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/UnionIDSignUp',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "platform": "",
          "pwd": "",
          "unionID": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
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

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "platform": "",
          "pwd": "",
          "unionID": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
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

=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserUnionIDSignUp){ .md-button }

## 账号密码

### 登录

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/SignIn

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | userName | 登录账号 |  |
    | password | 登陆密码 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/SignIn' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"pwd": "","userName": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId/SignIn");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"pwd\": \"\",\"userName\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"pwd\": \"\",\"userName\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/SignIn")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "pwd": "",
          "userName": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/SignIn',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "pwd": "",
          "userName": ""
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

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "pwd": "",
          "userName": ""
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

=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserSignIn){ .md-button }


### 注册

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/SignUp

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | userName | 登录账号  |  |
    | pwd | 登陆密码  |  |
    | nickName | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |
    | phone | 手机号，可空  | 如果应用配置了验证手机，则必填 |
    | phoneCode | 手机验证码，可空  | 如果应用配置了验证手机，则必填 |
    | email | 邮箱，可空  | 如果应用配置了验证邮箱，则必填 |
    | emailCode | 邮箱已验证，可空  | 如果应用配置了验证邮箱，则必填 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/SignUp' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"pwd": "","userName": "","nickName": "","avatar": "","data": "","email": "","emailCode": "","phone": "","phoneCode": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId/SignUp");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"pwd\": \"\",\"userName\": \"\",\"nickName\": \"\",\"avatar\":\"\",\"data\": \"\",\"email\": \"\",\"emailCode\": \"\",\"phone\": \"\",\"phoneCode\": \"\"}", null,"application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"pwd\": \"\",\"userName\": \"\",\"nickName\":         \"\",\"avatar\": \"\",\"data\": \"\",\"email\": \"\",\"emailCode\": \"\",\"phone\": \"\",       \"phoneCode\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/SignUp")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "pwd": "",
          "userName": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/SignUp',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "pwd": "",
          "userName": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
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

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "pwd": "",
          "userName": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
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

=== "返回数据"

    [点击查看](#fn:3){ .md-button }


[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserSignUp){ .md-button }


## 手机号

### 注册

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/PhoneSignUp

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | phone | 手机号，必填 |  |
    | phoneCode | 手机验证码，必填 | 调用发送手机验证码方法获取 |
    | pwd | 密码，可空  | 默认为：123456 |
    | email | 邮箱，可空  | 如果应用配置了验证邮箱，则必填 |
    | emailCode | 邮箱已验证，可空  | 如果应用配置了验证邮箱，则必填 |
    | nickname | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |

=== "示例"

    === "cURL"

        ``` curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignUp' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"phone": "","phoneCode": "","pwd": "","email": "","emailCode": "","nickName": "","avatar": "","data": ""}'
        ```

    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignUp");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"phone\": \"\",\"phoneCode\": \"\",\"pwd\": \"\",\"email\": \"\",\"emailCode\": \"\",\"nickName\": \"\",\"avatar\": \"\",\"data\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder().build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"phone\": \"\",\"phoneCode\": \"\",\"pwd\": \"\",\"email\": \"\",\"emailCode\": \"\",\"nickName\": \"\",\"avatar\": \"\",\"data\": \"\"}");
        Request request = new Request.Builder()
        .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignUp")
        .method("POST", body)
        .addHeader("Content-Type", "application/json")
        .addHeader("Authorization", "Bearer {{bearerToken}}")
        .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "phone": "",
          "phoneCode": "",
          "pwd": "",
          "email": "",
          "emailCode": "",
          "nickName": "",
          "avatar": "",
          "data": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignUp',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "phone": "",
          "phoneCode": "",
          "pwd": "",
          "email": "",
          "emailCode": "",
          "nickName": "",
          "avatar": "",
          "data": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/:appId[^2]/PhoneSignUp", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "phone": "",
          "phoneCode": "",
          "pwd": "",
          "email": "",
          "emailCode": "",
          "nickName": "",
          "avatar": "",
          "data": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignUp", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserPhoneSignUp){ .md-button }


### 登录

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/PhoneSignIn

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | phone | 手机号 |  |
    | verifyCode | 手机验证码 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignIn' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "phone": "",
          "verifyCode": ""
        }'
        ```
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignIn");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"phone\": \"\",\"verifyCode\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder().build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"phone\": \"\",\"verifyCode\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignIn")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "phone": "",
          "verifyCode": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignIn',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "phone": "",
          "verifyCode": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/:appId[^2]/PhoneSignIn", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "phone": "",
          "verifyCode": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/PhoneSignIn", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserPhoneSignIn){ .md-button }


### 发送验证码

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/SendSMSCode

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | phone | 手机号，必填 |  |
    | type | 用途，必填 | 可选值：signup / forgetpwd |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendSMSCode' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"phone": "","type": ""}'
        ```
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendSMSCode");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"phone\": \"\",\"type\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());

        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"phone\": \"\",\"type\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendSMSCode")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "phone": "",
          "type": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendSMSCode',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "phone": "",
          "type": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/:appId[^2]/SendSMSCode", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "phone": "",
          "type": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendSMSCode", requestOptions)
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

    ```json
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```


[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserSendSMSCode){ .md-button }


## 邮箱账号

### 注册

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/EmailSignUp

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | email | 邮箱，必填  |  |
    | emailCode | 邮箱已验证，必填  | 调用发送邮箱验证码方法获取 |
    | pwd | 密码，可空  | 默认为：123456 |
    | nickname | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |
    | phone | 手机号，可空  | 如果应用配置了验证手机，则必填 |
    | phoneCode | 手机验证码，可空  | 如果应用配置了验证手机，则必填 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/EmailSignUp' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"email": "","pwd": "","emailCode": "","phone": "","phoneCode": "","nickName": "","avatar":"","data": ""}'
        ```
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId[^2]/EmailSignUp");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"email\": \"\",\"pwd\": \"\",\"emailCode\": \"\",\"phone\": \"\",\"phoneCode\": \"\",\"nickName\": \"\",\"avatar\": \"\",\"data\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"email\": \"\",\"pwd\": \"\",\"emailCode\": \"\",\"phone\": \"\",\"phoneCode\": \"\",\"nickName\": \"\",\"avatar\": \"\",\"data\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/EmailSignUp")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "email": "",
          "pwd": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": "",
          "nickName": "",
          "avatar": "",
          "data": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/EmailSignUp',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "email": "",
          "pwd": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": "",
          "nickName": "",
          "avatar": "",
          "data": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/:appId[^2]/EmailSignUp", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "email": "",
          "pwd": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": "",
          "nickName": "",
          "avatar": "",
          "data": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/EmailSignUp", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserEmailSignUp){ .md-button }


### 登录

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/EmailSignIn

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | email | 邮箱，必填 |  |
    | emailCode | 邮箱验证码，必填 | 调用发送邮箱验证码方法获取 |


=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/：appId/EmailSignIn' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"email": "","verifyCode": ""}'
        ```

    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/：appId/EmailSignIn");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"email\": \"\",\"verifyCode\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"email\": \"\",\"verifyCode\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/：appId/EmailSignIn")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "email": "",
          "verifyCode": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/：appId/EmailSignIn',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "email": "",
          "verifyCode": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/：appId/EmailSignIn", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "email": "",
          "verifyCode": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppUsers/：appId/EmailSignIn", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    [点击查看](#fn:3){ .md-button }


[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserEmailSignIn){ .md-button }


### 发送验证码

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/SendEmailCode

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | email | 邮箱，必填 |  |
    | type | 用途，必填 | 可选值：signup / forgetpwd |


=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendEmailCode' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"email": "","type": ""}'
        ```
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendEmailCode");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"email\": \"\",\"type\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());

        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"email\": \"\",\"type\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendEmailCode")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "email": "",
          "type": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendEmailCode',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "email": "",
          "type": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/:appId[^2]/SendEmailCode", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "email": "",
          "type": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/SendEmailCode", requestOptions)
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

    ```json
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```


[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserSendEmailCode){ .md-button }


## 重置密码

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/ResetPwd

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | phone | 手机号 | 手机号、邮箱账号必选一种 |
    | email | 邮箱账号 | 手机号、邮箱账号必选一种 |
    | code | 验证码，必填 | 手机号或邮箱账号收到的验证码 |
    | pwd | 新的密码，必填 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/ResetPwd' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"code": "","pwd": "","phone": "","email": ""}'
        ```
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId[^2]/ResetPwd");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"code\": \"\",\"pwd\": \"\",\"phone\": \"\",\"email\": \"\"}",         null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"code\": \"\",\"pwd\": \"\",\"phone\": \"\",\"email\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/ResetPwd")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "code": "",
          "pwd": "",
          "phone": "",
          "email": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/ResetPwd',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "code": "",
          "pwd": "",
          "phone": "",
          "email": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/:appId[^2]/ResetPwd", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "code": "",
          "pwd": "",
          "phone": "",
          "email": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/ResetPwd", requestOptions)
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

    ```json
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserResetPwd){ .md-button }


## 微信小程序

### 网页端

#### 获取预登录SignKey

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/QRCodePreSignIn

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | scheme | 身份验证协议	 | 固定填：app |
    | scopes | 需要微信小程序用户授权的列表，用英文空格分隔 | openid phone |
    | remark | 自定义备注信息 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodePreSignIn' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"scopes": "","remark": "","scheme": "app"}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId/QRCodePreSignIn");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"scopes\": \"\",\"remark\": \"\",\"scheme\": \"app\"}", null,"application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());

        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"scopes\": \"\",\"remark\": \"\",\"scheme\":\"app\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodePreSignIn")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "scopes": "",
          "remark": "",
          "scheme": "app"
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodePreSignIn',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "scopes": "",
          "remark": "",
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

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "scopes": "",
          "remark": "",
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

=== "返回数据"

    | 说明 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | signInKey |

    ```json linenums="1"
    {
        "code": 200,
        "data": 19,
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserQRCodePreSignIn){ .md-button }


#### 登录结果查询

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/QRCodeSignIn

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | signInKey | 小程序登录查询凭证 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignIn' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"signInKey": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignIn");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"signInKey\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"signInKey\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignIn")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "signInKey": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignIn',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "signInKey": ""
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

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "signInKey": ""
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

=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserQRCodeSignIn){ .md-button }


### 小程序端

#### 确认扫码成功

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/QRCodeScan

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | signInKey | 小程序登录查询凭证 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeScan' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"signInKey": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId/QRCodeScan");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"signInKey\": \"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());

        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"signInKey\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeScan")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "signInKey": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeScan',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "signInKey": ""
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

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "signInKey": ""
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

=== "返回数据"

    | 说明 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 | 具体包含appID、name、logo、website、description、tags、scopes、remark 和 scheme |
    | err | 错误信息 |  |

    ```json linenums="1"
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserQRCodeScan){ .md-button }


#### 注册

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/QRCodeSignUp

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | unionId | 微信小程序用户的unionId/openid  |  |
    | pwd | 密码，可空  | 默认为：123456 |
    | nickname | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |
    | phone | 手机号，可空  | 如果应用配置了验证手机，则必填 |
    | phoneCode | 手机验证码，可空  | 如果应用配置了验证手机，则必填 |
    | email | 邮箱，可空  | 如果应用配置了验证邮箱，则必填 |
    | emailCode | 邮箱已验证，可空  | 如果应用配置了验证邮箱，则必填 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"unionID": "","signInKey": "","nickName": "","avatar": "","data": "","email": "",        "emailCode": "","phone": "","phoneCode": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"unionID\": \"\",\"signInKey\": \"\",\"nickName\": \"\",\"avatar\": \"\",\"data\": \"\",\"email\": \"\",\"emailCode\": \"\",\"phone\": \"\",\"phoneCode\":\"\"}", null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"unionID\": \"\",\"signInKey\": \"\",\"nickName\": \"\",\"avatar\": \"\",\"data\": \"\",\"email\": \"\",\"emailCode\": \"\",\"phone\":\"\",\"phoneCode\": \"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "unionID": "",
          "signInKey": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/QRCodeSignUp',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "unionID": "",
          "signInKey": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppUsers/:appId/QRCodeSignUp", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "unionID": "",
          "signInKey": "",
          "nickName": "",
          "avatar": "",
          "data": "",
          "email": "",
          "emailCode": "",
          "phone": "",
          "phoneCode": ""
        });

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

=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserQRCodeSignUp){ .md-button }


## 开放认证

### 申请授权码

{{serverUrl}}[^1]/api/OAuth/:appId[^2]/GrantCode?scheme=

=== "请求参数"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | scheme | 身份验证协议 | 固定填：app |
    | redirect_uri | 返回地址，必填 | 默认无限制，也可在【安全-开放认证网址白名单】配置 |
    | grant_type | 授权类型，必填 | 可选：email、phone、unionid、account |
    | scopes | 自定义授权范围，必填 | 用英文空格分隔 |
    | userName |  用户名 | 授权类型为：email/phone/account必填 |
    | password | 登录密码 | 授权类型为：email/phone/account必填 |
    | unionId | unionId | 授权类型为：unionid必填 |
    | platform | 平台 | 授权类型为：unionid必填 |
    | expireInDays | 授权有效期（天） | 默认为1，取值范围：1~99 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/OAuth/:appId[^2]/GrantCode?scheme=app' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"grant_type": "","scopes": "","redirect_uri": "","userName": "","password": "","unionId":"","platform": "","expireInDays": 1}'
        ```
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/OAuth/:appId[^2]/GrantCode?scheme=app");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"grant_type\": \"\",\"scopes\": \"\",\"redirect_uri\": \"\",\"userName\": \"\",\"password\": \"\",\"unionId\": \"\",\"platform\": \"\",\"expireInDays\": 1}",null, "application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"grant_type\": \"\",\"scopes\": \"\",\"redirect_uri\": \"\",\"userName\": \"\",\"password\": \"\",\"unionId\": \"\",\"platform\": \"\",\"expireInDays\": 1}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/OAuth/:appId[^2]/GrantCode?scheme=app")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "grant_type": "",
          "scopes": "",
          "redirect_uri": "",
          "userName": "",
          "password": "",
          "unionId": "",
          "platform": "",
          "expireInDays": 1
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/OAuth/:appId[^2]/GrantCode?scheme=app',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "grant_type": "",
          "scopes": "",
          "redirect_uri": "",
          "userName": "",
          "password": "",
          "unionId": "",
          "platform": "",
          "expireInDays": 1
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/OAuth/:appId[^2]/GrantCode?scheme=app", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "grant_type": "",
          "scopes": "",
          "redirect_uri": "",
          "userName": "",
          "password": "",
          "unionId": "",
          "platform": "",
          "expireInDays": 1
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/OAuth/:appId[^2]/GrantCode?scheme=app", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"


    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | code：授权码、expires_in：有效时间（秒） |

    ```json
    {
        "code": 200,
        "data": {
            "code": "e663f9e958ab40d39ad08cfe175b6800",
            "expires_in": 120
        },
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/OAuth/OAuthGrantCode){ .md-button }


### 获取access_token

{{serverUrl}}[^1]/api/OAuth/:appId[^2]/Authorize?scheme=&code=

=== "请求参数"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | 请求方式 | POST |  |
    | 登陆凭证 | 不需要 |  |
    | scheme | 身份验证协议 | 固定填：app |
    | code | 授权码 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request POST 'https://www.oauthapp.com/api/OAuth/:appId[^2]/Authorize?scheme=&code=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```

    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/OAuth/:appId[^2]/Authorize?scheme=&code=");
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
          .url("https://www.oauthapp.com/api/OAuth/:appId[^2]/Authorize?scheme=&code=")
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
          url: 'https://www.oauthapp.com/api/OAuth/:appId[^2]/Authorize?scheme=&code=',
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
        conn.request("POST", "/api/OAuth/:appId[^2]/Authorize?scheme=&code=", payload, headers)
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

        fetch("https://www.oauthapp.com/api/OAuth/:appId[^2]/Authorize?scheme=&code=", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    [点击查看](#fn:3){ .md-button }

[在线调试](https://www.oauthapp.com/swagger/index.html#/OAuth/OAuthAuthorize){ .md-button }

### 授权记录

{{serverUrl}}[^1]/api/OAuth/:appId[^2]/Consents

=== "请求参数"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | 请求方式 | GET |  |
    | 登陆凭证 | 不需要 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/OAuth/2/Consents' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```

    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Get, "https://www.oauthapp.com/api/OAuth/2/Consents");
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
          .url("https://www.oauthapp.com/api/OAuth/2/Consents")
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
          url: 'https://www.oauthapp.com/api/OAuth/2/Consents',
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
        conn.request("GET", "/api/OAuth/2/Consents", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var requestOptions = {
          method: 'GET',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/OAuth/2/Consents", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 |  |

    ``` json linenums="1"
    {
    "code": 200,
    "data": [
        {
            "id": 9,
            "createDate": "2023-07-24 13:33:26",
            "lastUpdate": "2023-07-24 13:33:26",
            "grantType": "unionid",
            "redirectUri": "",
            "remark": null,
            "scopes": "openid"
        }
    ],
    "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/OAuth/OAuthConsents){ .md-button }

### 删除授权记录

{{serverUrl}}[^1]/api/OAuth/:appId[^2]/Consents/:id

=== "请求参数"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | 请求方式 | DELETE |  |
    | 登陆凭证 | 不需要 |  |
    | id | 授权记录的ID |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request DELETE 'https://www.oauthapp.com/api/OAuth/:appId[^2]/Consents/:id' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```

    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Delete, "https://www.oauthapp.com/api/OAuth/:appId[^2]/Consents/:id");
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
          .url("https://www.oauthapp.com/api/OAuth/:appId[^2]/Consents/:id")
          .method("DELETE", body)
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');

        let config = {
          method: 'delete',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/OAuth/:appId[^2]/Consents/:id',
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
        conn.request("DELETE", "/api/OAuth/:appId[^2]/Consents/:id", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "Javascript"

        ```Javascript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var requestOptions = {
          method: 'DELETE',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/OAuth/:appId[^2]/Consents/:id", requestOptions)
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/OAuth/OAuthDeleteConsent){ .md-button }

## 获取用户资料

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/Profile

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/Profile' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Get, "https://www.oauthapp.com/api/AppUsers/:appId/Profile");
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
          .url("https://www.oauthapp.com/api/AppUsers/:appId/Profile")
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
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/Profile',
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
        conn.request("GET", "/api/AppUsers/:appId/Profile", payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppUsers/:appId/Profile", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 说明 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | 具体包含appID、platform、unionID、phone、createDate、userName、phoneIsValid、data、email、emailIsValid、lastUpdate、nickName、id、avatr 和 role |

    ```json linenums="1"
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserProfile){ .md-button }

## 更新用户资料

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/Profile

=== "请求参数"

    | 说明 |  |  |
    | --- | --- | --- |
    | 请求方式 | PUT |  |
    | 登陆凭证 | Bearer Token |  |
    | avatar | 头像 |  |
    | nickName | 昵称 |  |
    | data | 自定义数据 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request PUT 'https://www.oauthapp.com/api/AppUsers/:appId/Profile' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{"avatar": "","data": "","nickName": ""}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Put, "https://www.oauthapp.com/api/AppUsers/:appId/Profile");
        request.Headers.Add("Authorization", "Bearer {{bearerToken}}");
        var content = new StringContent("{\"avatar\": \"\",\"data\": \"\",\"nickName\": \"\"}", null,"application/json");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());

        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"avatar\": \"\",\"data\": \"\",\"nickName\":\"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppUsers/:appId/Profile")
          .method("PUT", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{bearerToken}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "avatar": "",
          "data": "",
          "nickName": ""
        });

        let config = {
          method: 'put',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppUsers/:appId/Profile',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{bearerToken}}'
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
          "avatar": "",
          "data": "",
          "nickName": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("PUT", "/api/AppUsers/:appId/Profile", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{bearerToken}}");

        var raw = JSON.stringify({
          "avatar": "",
          "data": "",
          "nickName": ""
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

=== "返回数据"

    | 说明 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | true 或 false |

    ```json linenums="1"
    {
        "code": 200,
        "data": true,
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserUpdateProfile){ .md-button }


## 积分记录

{{serverUrl}}[^1]/api/AppUsers/:appId[^2]/PointLog?type=&skip=&take=

=== "请求参数"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |
    | type | 分类 | 0：全部，1：充值，2：消耗 |
    | skip |  可选，指定要拉取的数据条数。 | 0 |
    | take |  可选，指定要跳过的数据条数。 | 10 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppUsers/:appId/PointLog?type=&skip=&take=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppUsers/:appId[^2]/PointLog?type=&skip=&take=", Method.Get);
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
          .url("https://www.oauthapp.com/api/AppUsers/:appId[^2]/PointLog?type=&skip=&take=")
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
          url: 'https://www.oauthapp.com/api/AppUsers/:appId[^2]/PointLog?type=&skip=&take=',
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
        conn.request("GET", "/api/AppUsers/:appId[^2]/PointLog?type=&skip=&take=", payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppUsers/:appId[^2]/PointLog?type=&skip=&take=", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 说明 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | data | 表示返回的数据 |  |
    | err | 错误信息 |  |

    ```json linenums="1"
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppUsers/AppUserPointLog){ .md-button }


[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID

[^3]:
    登录、注册 返回数据说明

    ```json linenums="1"
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

    | 说明 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | 具体包含access_token、token_type 和 expires_in |
