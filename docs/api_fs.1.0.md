---
tags:
  - API
---

# 存储

!!! warning "该文档已废弃"

### 上传文件

{{serverUrl}}[^1]/api/TenantBlobs/app/:appId[^2]?path=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  
    | path | 上传路径，默认为根目录 |  

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=&service=' \
        --header 'Content-Type: multipart/form-data' \
        --header 'Authorization: Bearer {{access_token}}' \
        --form 'file=""'
        ```
    
    === "C# "

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Post, "https://www.oauthapp.com/api/TenantBlobs/app/        :appId?path=&service=");
        request.Headers.Add("Authorization", "Bearer {{access_token}}");
        var content = new MultipartFormDataContent();
        content.Add(new StringContent(""), "file");
        request.Content = content;
        var response = await client.SendAsync(request);
        response.EnsureSuccessStatusCode();
        Console.WriteLine(await response.Content.ReadAsStringAsync());

        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("multipart/form-data");
        RequestBody body = new MultipartBody.Builder().setType(MultipartBody.FORM)
          .addFormDataPart("file","")
          .build();
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=&service=")
          .method("POST", body)
          .addHeader("Content-Type", "multipart/form-data")
          .addHeader("Authorization", "Bearer {{access_token}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        const axios = require('axios');
        const FormData = require('form-data');
        let data = new FormData();
        data.append('file', '');

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=&service=',
          headers: { 
            'Content-Type': 'multipart/form-data', 
            'Authorization': 'Bearer {{access_token}}', 
            ...data.getHeaders()
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
        import mimetypes
        from codecs import encode

        conn = http.client.HTTPSConnection("www.oauthapp.com")
        dataList = []
        boundary = 'wL36Yn8afVp8Ag7AmP8qZ0SA4n1v9T'
        dataList.append(encode('--' + boundary))
        dataList.append(encode('Content-Disposition: form-data; name=file;'))

        dataList.append(encode('Content-Type: {}'.format('text/plain')))
        dataList.append(encode(''))

        dataList.append(encode(""))
        dataList.append(encode('--'+boundary+'--'))
        dataList.append(encode(''))
        body = b'\r\n'.join(dataList)
        payload = body
        headers = {
          'Content-Type': 'multipart/form-data',
          'Authorization': 'Bearer {{access_token}}',
          'Content-type': 'multipart/form-data; boundary={}'.format(boundary)
        }
        conn.request("POST", "/api/TenantBlobs/app/:appId?path=&service=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "multipart/form-data");
        myHeaders.append("Authorization", "Bearer {{access_token}}");

        var formdata = new FormData();
        formdata.append("file", "");

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

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | 上传成功后的文件地址 |

    ```json linenums="1"
    {
        "code": 200,
        "data": "https://2.fs.oauthapp.com/知识.png",
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/TenantBlobs/TenantBlobUpload){ .md-button }

### 删除文件

{{serverUrl}}[^1]/api/TenantBlobs/app/:appId[^2]?path=

???+ note "提示"
    系统保留文件夹及文件：

    - /database

    - /appversion

    - /releasetemp

    - /__chatmessages

    - /__ranks

    - /web.config
    
    - /__loghistory.txt


=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | DELETE |  |
    | 登陆凭证 | Bearer Token |  |
    | path | 文件或文件夹的路径 |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request DELETE 'https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=' \
        --header 'Authorization: Bearer {{access_token}}'
        ```
    
    === "C# "

        ```CSharp linenums="1"
        var client = new HttpClient();
        var request = new HttpRequestMessage(HttpMethod.Delete, "https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=");
        request.Headers.Add("Authorization", "Bearer {{access_token}}");
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
          .url("https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=")
          .method("DELETE", body)
          .addHeader("Authorization", "Bearer {{access_token}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```Nodejs linenums="1"
        const axios = require('axios');

        let config = {
          method: 'delete',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=',
          headers: { 
            'Authorization': 'Bearer {{access_token}}'
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
          'Authorization': 'Bearer {{access_token}}'
        }
        conn.request("DELETE", "/api/TenantBlobs/app/:appId?path=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer {{access_token}}");

        var requestOptions = {
          method: 'DELETE',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/TenantBlobs/app/:appId?path=", requestOptions)
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

[在线调试](https://www.oauthapp.com/swagger/index.html#/TenantBlobs/TenantBlobDelete){ .md-button }

[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID