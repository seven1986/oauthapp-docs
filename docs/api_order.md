---
tags:
  - API
---

# 订单

### 订单列表

{{serverUrl}}[^1]/api/AppOrder/:appId[^2]?state=&orderNo=&tradeNo=&userId=&pctType=&pctId=&pctName=&skip=&take=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |
    | state |  订单状态，默认为空，返回全部 | 可选值：TRADE_CLOSED、TRADE_FINISHED、TRADE_SUCCESS、WAIT_BUYER_PAY |
    | orderNo | 系统订单号，非必填 |
    | tradeNo | 支付平台单号 ，非必填|
    | userId | 用户ID，非必填，默认为为：0 |
    | pctType | 商品类型，非必填 |
    | pctId | 商品ID，非必填 |
    | pctName | 商品名称，非必填 |
    | take | 可选，指定要拉取的数据条数。 | 10 |
    | skip | 可选，指定要跳过的数据条数。 | 0 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppOrder/:appId?state=&orderNo=&tradeNo=&userId=&       pctType=&pctId=&pctName=&skip=&take=' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppOrder/:appId?state=&orderNo=&tradeNo=&userId=&pctType=&    pctId=&pctName=&skip=&take=", Method.Get);
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
          .url("https://www.oauthapp.com/api/AppOrder/:appId?state=&orderNo=&tradeNo=&userId=&pctType=&   pctId=&pctName=&skip=&take=")
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
          url: 'https://www.oauthapp.com/api/AppOrder/:appId?state=&orderNo=&tradeNo=&userId=&pctType=&   pctId=&pctName=&skip=&take=',
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
        conn.request("GET", "/api/AppOrder/:appId?state=&orderNo=&tradeNo=&userId=&pctType=&pctId=&   pctName=&skip=&take=", payload, headers)
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
        fetch("https://www.oauthapp.com/api/AppOrder/:appId?state=&orderNo=&tradeNo=&userId=&pctType=&    pctId=&pctName=&skip=&take=", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```


=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | 订单列表集合。包括订单的ID、用户ID、订单号、订单状态、订单金额、支付类型、产品名称等信息 |

    ```json
    {
      "code": 200,
      "data": {
        "total": 1,
        "data": [
          {
            "id": 1,
            "userID": 5,
            "orderNo": "638205225950488498",
            "state": "WAIT_BUYER_PAY",
            "amount": 0.01,
            "payType": "alipay",
            "productName": "test",
            "productType": null,
            "productID": null,
            "tag": null,
            "remark": null,
            "tradeNo": null,
            "orderPayTime": "0001-01-01 00:00:00",
            "expireTime": "2024-05-24 10:56:35",
            "createDate": "2023-05-24 10:56:35",
            "lastUpdate": "2023-05-24 10:56:35"
          }
        ]
      },
      "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppOrder/AppOrders){ .md-button }

### 创建订单

{{serverUrl}}[^1]/api/AppOrder/:appId[^2]/Create

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |
    | `参数说明`  |  |  |
    | amount | 商品金额，必填  | 最小值为0.01元 |
    | productType | 商品类型，必填  | **point** 或自定义，如果为**point**，支付成功后将自动充值积分，并产生充值记录。 |
    | productID | 商品ID，必填  | 自定义 |
    | productName | 商品名称，必填  |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppOrder/:appId/Create' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{bearerToken}}' \
        --data '{
          "amount": "0.01",
          "productID": "point",
          "productName": "1",
          "productType": "测试商品"
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppOrder/:appId/Create", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        request.AddHeader("Authorization", "Bearer {{bearerToken}}");
        var body = @"{""amount"": ""0.01"", ""productID"": ""point"",""productName"": ""1"",      ""productType"": ""测试商品""}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"amount\": \"0.01\", \"productID\": \"point\",    \"productName\": \"1\",  \"productType\":     \"测试商品\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/AppOrder/:appId/Create")
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
          "amount": "0.01",
          "productID": "point",
          "productName": "1",
          "productType": "测试商品"
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/AppOrder/:appId/Create',
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
          "amount": "0.01",
          "productID": "point",
          "productName": "1",
          "productType": "测试商品"
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{bearerToken}}'
        }
        conn.request("POST", "/api/AppOrder/:appId/Create", payload, headers)
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
          "amount": "0.01",
          "productID": "point",
          "productName": "1",
          "productType": "测试商品"
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/AppOrder/:appId/Create", requestOptions)
          .then(response => response.text())
          .then(result => console.log(result))
          .catch(error => console.log('error', error));
        ```

=== "返回数据"

    | 描述 |  |  |
    | --- | --- | --- |
    | code | 表示返回结果的状态码 | 200 表示成功，非 200 表示失败 |
    | err | 错误信息 |  |
    | data | 表示返回的数据 | 订单ID、订单号 |

        ```json
        {
          "code": 200,
          "data": {
            "id": 1,
            "orderNo": "638205225950488498"
          },
          "err": ""
        }
        ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppOrder/AppOrderCreate){ .md-button }

### 订单详情

{{serverUrl}}[^1]/api/AppOrder/:appId[^2]/:orderId[^3]

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/AppOrder/:appId/:id' \
        --header 'Authorization: Bearer {{bearerToken}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/AppOrder/:appId/:id", Method.Get);
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
          .url("https://www.oauthapp.com/api/AppOrder/:appId/:id")
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
          url: 'https://www.oauthapp.com/api/AppOrder/:appId/:id',
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
        conn.request("GET", "/api/AppOrder/:appId/:id", payload, headers)
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

        fetch("https://www.oauthapp.com/api/AppOrder/:appId/:id", requestOptions)
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

    ```json linenums="1"
    {
      "code": 200,
      "data": {
        "id": 1,
        "userID": 5,
        "orderNo": "638205225950488498",
        "state": "WAIT_BUYER_PAY",
        "amount": 0.01,
        "payType": "alipay",
        "productName": "test",
        "productType": null,
        "productID": null,
        "tag": null,
        "remark": null,
        "tradeNo": null,
        "orderPayTime": "0001-01-01 00:00:00",
        "expireTime": "2024-05-24 10:56:35",
        "createDate": "2023-05-24 10:56:35",
        "lastUpdate": "2023-05-24 10:56:35"
      },
      "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/AppOrder/AppOrder){ .md-button }

[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID

[^3]:orderId：订单ID