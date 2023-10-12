---
tags:
  - API
---

# 支付宝

### 电脑网站支付

{{serverUrl}}[^1]/api/Alipay/:appId[^2]/CreateOrderPagePay

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |
    | orderNo | 系统订单号，必填 |
    | amount | 商品金额，必填  | 最小值为0.01元 |
    | subject | 商品名称，必填 |
    | returnUrl |  支付同步通知地址，非必填 | 为空将从**应用配置**——**支付宝**——**支付成功返回页**中读取 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Alipay/:appId/CreateOrderPagePay' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{access_token}}' \
        --data '{
          "amount": "0.01",
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Alipay/:appId/CreateOrderPagePay", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        request.AddHeader("Authorization", "Bearer {{access_token}}");
        var body = @"{""amount"": ""0.01"",""orderNo"": ""1"",""subject"": ""测试商品"",""returnUrl"":    ""http://127.0.0.1""}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"amount\": \"0.01\",\"orderNo\": \"1\",   \"subject\": \"测试商品\",\"returnUrl\": \"http://   127.0.0.1\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Alipay/:appId/CreateOrderPagePay")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{access_token}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "amount": "0.01",
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Alipay/:appId/CreateOrderPagePay',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{access_token}}'
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
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{access_token}}'
        }
        conn.request("POST", "/api/Alipay/:appId/CreateOrderPagePay", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{access_token}}");

        var raw = JSON.stringify({
          "amount": "0.01",
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Alipay/:appId/CreateOrderPagePay", requestOptions)
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
      "data": "<form id='alipaysubmit' name='alipaysubmit' action='https://openapi.alipay.com/gateway.do?charset=UTF-8' method='POST' style='display:none;'><input  name='alipay_sdk' value='alipay-sdk-net-4.7.261.ALL'/><input  name='app_id' value='2021003192659285'/><input  name='biz_content' value='{\"out_trade_no\":\"string\",       \"product_code\":\"FAST_INSTANT_TRADE_PAY\",\"qrcode_width\":0,\"subject\":\"string\",\"total_amount\":\"0.01\"}'/  ><input  name='charset' value='UTF-8'/><input  name='format' value='json'/><input  name='method' value='alipay.trade.        page.pay'/><input  name='notify_url' value='https://localhost:44377/api/Alipay/2/Notify'/><input  name='return_url' value='string'/><input  name='sign_type' value='RSA2'/><input  name='timestamp' value='2023-06-19 15:03:43'/><input name='version' value='1.0'/><input  name='sign' value='NZpcHPHMsZSQhiy7y2CYl2lM+T16R9cPXumfm2Dqne/  X8pwFddmkRl2BJkA5I1GJWBJn7gelCXPeSv/qzzyw6DpESFTAzSI1IszeAgLXFhZA+WU1Rgt6zWFmtE2lWPKH7yDogL1VDL/     BPfX0HBCV4uzmo0NDbFNwxqWgvLF/6atQZv/RhrIrhT8OWKa9ZTOTBOJg/7IW7Gi5ll+gw93BgQObHedUeDjK/      P04go42FMtUNFpSYBk9CNKvYNXgPVJzoh9qxXg/baIl/Ip9w5PUtNWGisNakOZPCs9jUNO3OrR3qLv7qE1PkpvzztrJoQA5rhHzdthFSMUFXoWnzd/     8iQ=='/><input type='submit' value='POST' style='display:none;'></form><script>document.forms['alipaysubmit'].submit();     </script>",
      "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Alipay/AlipayCreateOrderPagePay){ .md-button }

### 手机网站支付

{{serverUrl}}[^1]/api/Alipay/:appId[^2]/CreateOrderWapPay

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |
    | orderNo | 系统订单号，必填 |
    | amount | 商品金额，必填  | 最小值为0.01元 |
    | subject | 商品名称，必填 |
    | returnUrl |  支付同步通知地址，非必填 | 为空将从**应用配置**——**支付宝**——**支付成功返回页**中读取 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Alipay/:appId/CreateOrderWapPay' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{access_token}}' \
        --data '{
          "amount": "0.01",
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Alipay/:appId/CreateOrderWapPay", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        request.AddHeader("Authorization", "Bearer {{access_token}}");
        var body = @"{""amount"": ""0.01"",""orderNo"": ""1"",""subject"": ""测试商品"",""returnUrl"":    ""http://127.0.0.1""}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"amount\": \"0.01\",\"orderNo\": \"1\",   \"subject\": \"测试商品\",\"returnUrl\": \"http://   127.0.0.1\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Alipay/:appId/CreateOrderWapPay")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{access_token}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "amount": "0.01",
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Alipay/:appId/CreateOrderWapPay',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{access_token}}'
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
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{access_token}}'
        }
        conn.request("POST", "/api/Alipay/:appId/CreateOrderWapPay", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{access_token}}");

        var raw = JSON.stringify({
          "amount": "0.01",
          "orderNo": "1",
          "subject": "测试商品",
          "returnUrl": "http://127.0.0.1"
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Alipay/:appId/CreateOrderWapPay", requestOptions)
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
        "data": "<form id='alipaysubmit' name='alipaysubmit' action='https://openapi.alipay.com/gateway.do?charset=UTF-8' method='POST' style='display:none;'><input  name='alipay_sdk' value='alipay-sdk-net-4.7.261.ALL'/><input  name='app_id' value='2021003192659285'/><input  name='biz_content' value='{\"out_trade_no\":\"string\",\"product_code\":\"QUICK_WAP_WAY\",\"subject\":\"string\",\"total_amount\":\"0.01\"}'/><input  name='charset' value='UTF-8'/><input  name='format' value='json'/><input  name='method' value='alipay.trade.wap.pay'/><input  name='notify_url' value='https://localhost:44377/api/Alipay/2/Notify'/><input  name='return_url' value='string'/><input  name='sign_type' value='RSA2'/><input  name='timestamp' value='2023-06-19 15:09:32'/><input  name='version' value='1.0'/><input  name='sign' value='qlBm5ZgLOwE5r/7UDs6yYzQujcRbxZhBrxxMT8y07S7gDhyRhz68PT1elGABcRKLb8939kykLvlWgKjjXHMDcSAkLvNyp7pBWbXb3IeYa0MRYtm1CsgYXGgJuOuLgL0nxtoR877AVeeRo7uLykEdeGzzT+c0+DHngHqaCcmledHo07VrpM2STzrqt0zccBb7ZAeyqYgiHf9P7kP/7Ybgqkr1WxiP/GhSavBZfrsIguSfd//628qNafBx0O3yPHDws9bu5yjJlYfsiZ6DFkEHB/bkX8hr/8qlRjICTx2rUk97XTyx2Fa9B9/ZCchsUiYqP3+EPYKIbVS052SVHnwYcQ=='/><input type='submit' value='POST' style='display:none;'></form><script>document.forms['alipaysubmit'].submit();</script>",
        "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Alipay/AlipayCreateOrderWapPay){ .md-button }

### 订单查询

{{serverUrl}}[^1]/api/Alipay/:appId[^2]/OrderDetail?orderNo=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | GET |  |
    | 登陆凭证 | Bearer Token |  |
    | orderNo | 系统订单号，必填 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Alipay/:appId/OrderDetail?orderNo=' \
        --header 'Authorization: Bearer {{access_token}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Alipay/:appId/OrderDetail?orderNo=", Method.Get);
        request.AddHeader("Authorization", "Bearer {{access_token}}");
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
          .url("https://www.oauthapp.com/api/Alipay/:appId/OrderDetail?orderNo=")
          .method("GET", body)
          .addHeader("Authorization", "Bearer {{access_token}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');

        let config = {
          method: 'get',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Alipay/:appId/OrderDetail?orderNo=',
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
        conn.request("GET", "/api/Alipay/:appId/OrderDetail?orderNo=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer {{access_token}}");

        var requestOptions = {
          method: 'GET',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Alipay/:appId/OrderDetail?orderNo=", requestOptions)
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
        "alipayStoreId": null,
        "alipaySubMerchantId": null,
        "authTradePayMode": null,
        "bkagentRespInfo": null,
        "body": null,
        "buyerLogonId": "v1v***@qq.com",
        "buyerOpenId": null,
        "buyerPayAmount": "0.00",
        "buyerUserId": "2088632335506388",
        "buyerUserName": null,
        "buyerUserType": null,
        "chargeAmount": null,
        "chargeFlags": null,
        "chargeInfoList": null,
        "creditBizOrderId": null,
        "creditPayMode": null,
        "discountAmount": null,
        "discountGoodsDetail": null,
        "enterprisePayInfo": null,
        "extInfos": null,
        "fundBillList": null,
        "hbFqPayInfo": null,
        "hybAmount": null,
        "industrySepcDetail": null,
        "industrySepcDetailAcc": null,
        "industrySepcDetailGov": null,
        "invoiceAmount": "0.00",
        "mdiscountAmount": null,
        "openId": null,
        "outTradeNo": "638227710323944845",
        "passbackParams": null,
        "payAmount": null,
        "payCurrency": null,
        "pointAmount": "0.00",
        "receiptAmount": "0.00",
        "receiptCurrencyType": null,
        "sendPayDate": "2023-06-19 11:30:44",
        "settleAmount": null,
        "settleCurrency": null,
        "settleTransRate": null,
        "settlementId": null,
        "storeId": null,
        "storeName": null,
        "subject": null,
        "terminalId": null,
        "totalAmount": "0.30",
        "tradeNo": "2023061922001406381431771492",
        "tradeSettleInfo": null,
        "tradeStatus": "TRADE_SUCCESS",
        "transCurrency": null,
        "transPayRate": null,
        "voucherDetailList": null,
        "code": "10000",
        "msg": "Success",
        "subCode": null,
        "subMsg": null,
        "isError": false
      },
      "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Alipay/AlipayOrderDetail){ .md-button }

### 发起退款

{{serverUrl}}[^1]/api/Alipay/:appId[^2]/OrderRefund?amount=&orderNo=

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |
    | orderNo | 系统订单号，必填 |
    | amount | 退款金额，必填 |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location --request POST 'https://www.oauthapp.com/api/Alipay/:appId/OrderRefund?amount=&       orderNo=' \
        --header 'Authorization: Bearer {{access_token}}'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Alipay/:appId/OrderRefund?amount=&orderNo=", Method.Post);
        request.AddHeader("Authorization", "Bearer {{access_token}}");
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
          .url("https://www.oauthapp.com/api/Alipay/:appId/OrderRefund?amount=&orderNo=")
          .method("POST", body)
          .addHeader("Authorization", "Bearer {{access_token}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Alipay/:appId/OrderRefund?amount=&orderNo=',
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
        conn.request("POST", "/api/Alipay/:appId/OrderRefund?amount=&orderNo=", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Authorization", "Bearer {{access_token}}");

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Alipay/:appId/OrderRefund?amount=&orderNo=", requestOptions)
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
        "buyerLogonId": "v1v***@qq.com",
        "buyerOpenId": null,
        "buyerUserId": "2088632335506388",
        "fundChange": "Y",
        "gmtRefundPay": "2023-06-19 15:17:34",
        "hasDepositBack": null,
        "openId": null,
        "outTradeNo": "638227710323944845",
        "presentRefundBuyerAmount": null,
        "presentRefundDiscountAmount": null,
        "presentRefundMdiscountAmount": null,
        "refundChargeAmount": null,
        "refundChargeInfoList": null,
        "refundCurrency": null,
        "refundDetailItemList": null,
        "refundFee": "0.30",
        "refundHybAmount": null,
        "refundPresetPaytoolList": null,
        "refundSettlementId": null,
        "sendBackFee": "0.00",
        "storeName": null,
        "tradeNo": "2023061922001406381431771492",
        "code": "10000",
        "msg": "Success",
        "subCode": null,
        "subMsg": null,
        "body": "{\"alipay_trade_refund_response\":{\"code\":\"10000\",\"msg\":\"Success\",\"buyer_logon_id\":\"v1v***@qq.  com\",  \"buyer_user_id\":\"2088632335506388\",\"fund_change\":\"Y\",\"gmt_refund_pay\":\"2023-06-19 15:17:34\",      \"out_trade_no\":\"638227710323944845\",\"refund_fee\":\"0.30\",\"send_back_fee\":\"0.00\",   \"trade_no\":\"2023061922001406381431771492\"},\"sign\":\"A  +8rbBL47iYVB9b7CrWf6on2slySye2zJ76ZQ61TyVDAvKxZ5jLfqFbs4TrPpkKfqZ    +1wtrszXThdKpCWCpqJ8gA5Ni3OQ+qS6mVvf/    ZW79ntCTMDtjxo8KTMYCPcSmBRDRM3Oz7IqPtvD3mlf/FhdajZLIM0pZ5sqTZGEO3Jbz24zEOa/    3cvTmPt5ySQdX73iJsfG054GgDDys1F8dMTeeaAwDM/  JailQXNNMi/vYOg+8ylOlfozMLgJXXV89voNbKfBlTlWfTwJHCYQiZWXIeBFujaTqQzszAml7QdtlujQiQypRguIB/ gP  +u8Wq9fvbYyNVRPIRITm3S4GHzaJQ==\"}",
        "isError": false
      },
      "err": ""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Alipay/AlipayOrderRefund){ .md-button }

### 支付同步通知

{{serverUrl}}[^1]/api/Alipay/:appId[^2]/ReturnPageNotify

=== "请求参数"

    | 描述 |  |  |
    | --- | --- | --- |
    | 请求方式 | POST |  |
    | 登陆凭证 | Bearer Token |  |
    |   | **以下参数来自支付宝同步回传** |  |
    | charset |  |  |
    | out_trade_no |  |  |
    | method |  |  |
    | total_amount |  |  |
    | sign |  |  |
    | trade_no |  |  |
    | auth_app_id |  |  |
    | version |  |  |
    | app_id |  |  |
    | sign_type |  |  |
    | seller_id |  |  |
    | timestamp |  |  |

=== "示例"

    === "cURL"

        ```curl linenums="1"
        curl --location 'https://www.oauthapp.com/api/Alipay/:appId/ReturnPageNotify' \
        --header 'Content-Type: application/json' \
        --header 'Authorization: Bearer {{access_token}}' \
        --data '{
          "app_id": "",
          "auth_app_id": "",
          "charset": "",
          "method": "",
          "out_trade_no": "",
          "seller_id": "",
          "sign": "",
          "sign_type": "",
          "timestamp": "",
          "total_amount": "",
          "trade_no": "",
          "version": ""
        }'
        ```
    
    === "C#"

        ```CSharp linenums="1"
        var options = new RestClientOptions("https://www.oauthapp.com");
        var client = new RestClient(options);
        var request = new RestRequest("/api/Alipay/:appId/ReturnPageNotify", Method.Post);
        request.AddHeader("Content-Type", "application/json");
        request.AddHeader("Authorization", "Bearer {{access_token}}");
        var body = @"{""app_id"":"""",""auth_app_id"":""""," + "\n" +
        @"""charset"":"""",""method"":"""",""out_trade_no"":""""," + "\n" +
        @"""seller_id"":"""",""sign"":""""," + "\n" +
        @"""sign_type"":"""",""timestamp"":"""",""total_amount"":""""," + "\n" +
        @"""trade_no"":"""",""version"":""""}";
        request.AddStringBody(body, DataFormat.Json);
        RestResponse response = await client.ExecuteAsync(request);
        Console.WriteLine(response.Content);
        ```

    === "Java"

        ```Java linenums="1"
        OkHttpClient client = new OkHttpClient().newBuilder()
          .build();
        MediaType mediaType = MediaType.parse("application/json");
        RequestBody body = RequestBody.create(mediaType, "{\"app_id\":\"\",\"auth_app_id\":\"\",    \n\"charset\":\"\",\"method\":\"\", \"out_trade_no\":\"\",\n\"seller_id\":\"\",\"sign\":\"\",   \n\"sign_type\":\"\",\"timestamp\":\"\",\"total_amount\":\"\",\n\"trade_no\":\"\",    \"version\":\"\"}");
        Request request = new Request.Builder()
          .url("https://www.oauthapp.com/api/Alipay/:appId/ReturnPageNotify")
          .method("POST", body)
          .addHeader("Content-Type", "application/json")
          .addHeader("Authorization", "Bearer {{access_token}}")
          .build();
        Response response = client.newCall(request).execute();
        ```

    === "NodeJs"

        ```TypeScript linenums="1"
        const axios = require('axios');
        let data = JSON.stringify({
          "app_id": "",
          "auth_app_id": "",
          "charset": "",
          "method": "",
          "out_trade_no": "",
          "seller_id": "",
          "sign": "",
          "sign_type": "",
          "timestamp": "",
          "total_amount": "",
          "trade_no": "",
          "version": ""
        });

        let config = {
          method: 'post',
          maxBodyLength: Infinity,
          url: 'https://www.oauthapp.com/api/Alipay/:appId/ReturnPageNotify',
          headers: { 
            'Content-Type': 'application/json', 
            'Authorization': 'Bearer {{access_token}}'
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
          "app_id": "",
          "auth_app_id": "",
          "charset": "",
          "method": "",
          "out_trade_no": "",
          "seller_id": "",
          "sign": "",
          "sign_type": "",
          "timestamp": "",
          "total_amount": "",
          "trade_no": "",
          "version": ""
        })
        headers = {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer {{access_token}}'
        }
        conn.request("POST", "/api/Alipay/:appId/ReturnPageNotify", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```

    === "JavaScript"

        ```JavaScript linenums="1"
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Authorization", "Bearer {{access_token}}");

        var raw = JSON.stringify({
          "app_id": "",
          "auth_app_id": "",
          "charset": "",
          "method": "",
          "out_trade_no": "",
          "seller_id": "",
          "sign": "",
          "sign_type": "",
          "timestamp": "",
          "total_amount": "",
          "trade_no": "",
          "version": ""
        });

        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

        fetch("https://www.oauthapp.com/api/Alipay/:appId/ReturnPageNotify", requestOptions)
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
        "code":200,
        "data":true,
        "err":""
    }
    ```

[在线调试](https://www.oauthapp.com/swagger/index.html#/Alipay/AlipayReturnPageNotify){ .md-button }

[^1]:serverUrl：https://www.oauthapp.com

[^2]:appId：需要替换为实际应用的 ID
