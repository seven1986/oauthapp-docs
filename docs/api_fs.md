---
tags:
  - 服务端
---

# 存储

> baseUrl ：https://www.oauthapp.com

### 上传文件

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | POST |  |
| 请求地址 | {{baseUrl}}/api/TenantBlobs/app/:appId?path= | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | Bearer Token |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/TenantBlobs/app/:appId?path=&service=", Method.Post);
    request.AddHeader("Content-Type", "multipart/form-data");
    request.AddHeader("Authorization", "Bearer token");
    request.AlwaysMultipartFormData = true;
    request.AddFile("file", "/C:/知识.png");
    RestResponse response = await client.ExecuteAsync(request);
    Console.WriteLine(response.Content);
    ```

=== "Java - OkHttp"

    ```Java linenums="1"
    OkHttpClient client = new OkHttpClient().newBuilder()
      .build();
    MediaType mediaType = MediaType.parse("multipart/form-data");
    RequestBody body = new MultipartBody.Builder().setType(MultipartBody.FORM)
      .addFormDataPart("file","/C:/Users/jxsh08.DESKTOP-361U268/Downloads/知识.png",
        RequestBody.create(MediaType.parse("application/octet-stream"),
        new File("/C:/知识.png")))
      .build();
    Request request = new Request.Builder()
      .url("https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=&service=")
      .method("POST", body)
      .addHeader("Content-Type", "multipart/form-data")
      .addHeader("Authorization", "Bearer token")
      .build();
    Response response = client.newCall(request).execute();
    ```

=== "NodeJs - Axios"

    ```Nodejs linenums="1"
    var axios = require('axios');
    var FormData = require('form-data');
    var fs = require('fs');
    var data = new FormData();
    data.append('file', fs.createReadStream('/C:/知识.png'));

    var config = {
      method: 'post',
    maxBodyLength: Infinity,
      url: 'https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=&service=',
      headers: { 
        'Content-Type': 'multipart/form-data', 
        'Authorization': 'Bearer token', 
        ...data.getHeaders()
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
    import mimetypes
    from codecs import encode

    conn = http.client.HTTPSConnection("www.oauthapp.com")
    dataList = []
    boundary = 'wL36Yn8afVp8Ag7AmP8qZ0SA4n1v9T'
    dataList.append(encode('--' + boundary))
    dataList.append(encode('Content-Disposition: form-data; name=file; filename={0}'.format('/C:/知识.png')))

    fileType = mimetypes.guess_type('/C:/知识.png')[0] or 'application/octet-stream'
    dataList.append(encode('Content-Type: {}'.format(fileType)))
    dataList.append(encode(''))

    with open('/C:/知识.png', 'rb') as f:
      dataList.append(f.read())
    dataList.append(encode('--'+boundary+'--'))
    dataList.append(encode(''))
    body = b'\r\n'.join(dataList)
    payload = body
    headers = {
      'Content-Type': 'multipart/form-data',
      'Authorization': 'Bearer token',
      'Content-type': 'multipart/form-data; boundary={}'.format(boundary)
    }
    conn.request("POST", "/api/TenantBlobs/app/:appId?path=&service=", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))
    ```

=== "JavaScript - Fetch"

    ```JavaScript linenums="1"
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "multipart/form-data");
    myHeaders.append("Authorization", "Bearer token");

    var formdata = new FormData();
    formdata.append("file", fileInput.files[0], "/C:/知识.png");

    var requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: formdata,
      redirect: 'follow'
    };

    fetch("https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=&service=", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
    ```

返回示例


| 描述 |  |  |
| --- | --- | --- |
| code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
| data | 表示返回的数据 | 上传成功后的文件地址 |
| err | 错误信息 |  |

=== "返回结果"
    ```json
    {
        "code": 200,
        "data": "https://2.fs.oauthapp.com/知识.png",
        "err": ""
    }
    ```

### 删除文件

???+ note "提示"
    系统保留文件夹及文件：

    - /database

    - /appversion

    - /releasetemp

    - /__chatmessages

    - /__ranks

    - /web.config
    
    - /__loghistory.txt

| 描述 |  |  |
| --- | --- | --- |
| 请求方式 | DELETE |  |
| 请求地址 | {{baseUrl}}/api/TenantBlobs/app/:appId?path= | :appId 部分需要替换为实际应用的 ID |
| 登陆凭证 | Bearer Token |  |

=== "C# - RestSharp"

    ```CSharp linenums="1"
    var options = new RestClientOptions("https://www.oauthapp.com")
    {
      MaxTimeout = -1,
    };
    var client = new RestClient(options);
    var request = new RestRequest("/api/TenantBlobs/app/:appId?path=/知识.png", Method.Delete);
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
      .url("https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=/知识.png")
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
      url: 'https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=/知识.png',
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
    conn.request("DELETE", "/api/TenantBlobs/app/:appId?path=/%E7%9F%A5%E8%AF%86.png", payload, headers)
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

    fetch("https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=/知识.png", requestOptions)
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