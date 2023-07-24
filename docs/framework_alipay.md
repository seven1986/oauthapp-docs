---
tags:
  - 文档
---

# 支付宝

???+ note "提示"
    请确认您已开通了支付宝[电脑网站支付](https://open.alipay.com/api/detail?code=I1080300001000041203)和[手机网站支付](https://open.alipay.com/api/detail?code=I1080300001000041949)产品，并在**应用配置**——**支付宝**，配置了相关密钥。


### 电脑网站支付

oauthapp.alipayCreateOrderPagePay

接口调用成功后，将res.data字段内容插入到当前html中，将自动跳转到支付宝支付页面。

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 电脑网站支付
     * @params orderNo 系统单号
     * @params amount 订单金额
     * @params subject 商品名称
     * @params returnUrl 支付同步通知地址
    */
    oauthapp.alipayCreateOrderPagePay({orderNo:"",amount:0.01,subject:"",returnUrl:""}).then(function(res){
      console.log(res);
      /*
        {
          "code": 200,
          "data": "<form id='alipaysubmit' name='alipaysubmit' action='https://openapi.alipay.com/gateway.do?charset=UTF-8' method='POST' style='display:none;'><input  name='alipay_sdk' value='alipay-sdk-net-4.7.261.ALL'/><input  name='app_id' value='2021003192659285'/><input  name='biz_content' value='{\"out_trade_no\":\"string\",       \"product_code\":\"FAST_INSTANT_TRADE_PAY\",\"qrcode_width\":0,\"subject\":\"string\",\"total_amount\":\"0.01\"}'/  ><input  name='charset' value='UTF-8'/><input  name='format' value='json'/><input  name='method' value='alipay.trade.        page.pay'/><input  name='notify_url' value='https://localhost:44377/api/Alipay/2/Notify'/><input  name='return_url' value='string'/><input  name='sign_type' value='RSA2'/><input  name='timestamp' value='2023-06-19 15:03:43'/><input name='version' value='1.0'/><input  name='sign' value='NZpcHPHMsZSQhiy7y2CYl2lM+T16R9cPXumfm2Dqne/  X8pwFddmkRl2BJkA5I1GJWBJn7gelCXPeSv/qzzyw6DpESFTAzSI1IszeAgLXFhZA+WU1Rgt6zWFmtE2lWPKH7yDogL1VDL/     BPfX0HBCV4uzmo0NDbFNwxqWgvLF/6atQZv/RhrIrhT8OWKa9ZTOTBOJg/7IW7Gi5ll+gw93BgQObHedUeDjK/      P04go42FMtUNFpSYBk9CNKvYNXgPVJzoh9qxXg/baIl/Ip9w5PUtNWGisNakOZPCs9jUNO3OrR3qLv7qE1PkpvzztrJoQA5rhHzdthFSMUFXoWnzd/     8iQ=='/><input type='submit' value='POST' style='display:none;'></form><script>document.forms['alipaysubmit'].submit();     </script>",
          "err": ""
        }
      */
    });
    ```
=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>alipayCreateOrderPagePay</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <label>订单号</label>
        <input type="text" id="orderNo" placeholder="orderNo" value="1" />
        <label>订单金额</label>
        <input type="text" id="amount" placeholder="amount" value="0.01" />
        <label>商品名称</label>
        <input type="text" id="subject" placeholder="subject" value="测试商品" />
        <label>同步通知地址</label>
        <input type="text" id="returnUrl" placeholder="returnUrl" />
        <button type="button" id="runButton">查询</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
            $('#returnUrl').val(location.protocol + "//" + location.host + location.pathname);
            oauthapp.allReady().then(function () {    
                document.getElementById('runButton').onclick = function () {
                    var postData = {};
                    postData.orderNo = $('#orderNo').val();
                    postData.amount = $('#amount').val() || 0.01;
                    postData.productID = $('#productID').val();
                    postData.subject = $('#subject').val();
                    oauthapp.alipayCreateOrderPagePay(postData).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | orderNo | 系统订单号，必填 |
    | amount | 商品金额，必填  | 最小值为0.01元 |
    | subject | 商品名称，必填 |
    | returnUrl |  支付同步通知地址，非必填 | 为空将从**应用配置**——**支付宝**——**支付成功返回页**中读取 |


[演示](https://web.oauthapp.com/4/examples/apidemo/alipayCreateOrderPagePay.html){ .md-button } [教程](http://docs.oauthapp.com/coding_sdk_alipayCreateOrderPagePay.html){ .md-button }


### 手机网站支付

oauthapp.alipayCreateOrderWapPay

接口调用成功后，将res.data字段内容插入到当前html中，将自动跳转到支付宝支付页面。

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 手机网站支付
     * @params orderNo 系统单号
     * @params amount 订单金额
     * @params subject 商品名称
     * @params returnUrl 支付同步通知地址
    */
    oauthapp.alipayCreateOrderWapPay({orderNo:"",amount:0.01,subject:"",returnUrl:""}).then(function(res){
      console.log(res);
      /*
        {
            "code": 200,
            "data": "<form id='alipaysubmit' name='alipaysubmit' action='https://openapi.alipay.com/gateway.do?charset=UTF-8' method='POST' style='display:none;'><input  name='alipay_sdk' value='alipay-sdk-net-4.7.261.ALL'/><input  name='app_id' value='2021003192659285'/><input  name='biz_content' value='{\"out_trade_no\":\"string\",\"product_code\":\"QUICK_WAP_WAY\",\"subject\":\"string\",\"total_amount\":\"0.01\"}'/><input  name='charset' value='UTF-8'/><input  name='format' value='json'/><input  name='method' value='alipay.trade.wap.pay'/><input  name='notify_url' value='https://localhost:44377/api/Alipay/2/Notify'/><input  name='return_url' value='string'/><input  name='sign_type' value='RSA2'/><input  name='timestamp' value='2023-06-19 15:09:32'/><input  name='version' value='1.0'/><input  name='sign' value='qlBm5ZgLOwE5r/7UDs6yYzQujcRbxZhBrxxMT8y07S7gDhyRhz68PT1elGABcRKLb8939kykLvlWgKjjXHMDcSAkLvNyp7pBWbXb3IeYa0MRYtm1CsgYXGgJuOuLgL0nxtoR877AVeeRo7uLykEdeGzzT+c0+DHngHqaCcmledHo07VrpM2STzrqt0zccBb7ZAeyqYgiHf9P7kP/7Ybgqkr1WxiP/GhSavBZfrsIguSfd//628qNafBx0O3yPHDws9bu5yjJlYfsiZ6DFkEHB/bkX8hr/8qlRjICTx2rUk97XTyx2Fa9B9/ZCchsUiYqP3+EPYKIbVS052SVHnwYcQ=='/><input type='submit' value='POST' style='display:none;'></form><script>document.forms['alipaysubmit'].submit();</script>",
            "err": ""
        }
      */
    });
    ```
=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>alipayCreateOrderWapPay</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <label>订单号</label>
        <input type="text" id="orderNo" placeholder="orderNo" value="1" />
        <label>订单金额</label>
        <input type="text" id="amount" placeholder="amount" value="0.01" />
        <label>商品名称</label>
        <input type="text" id="subject" placeholder="subject" value="测试商品" />
        <label>同步通知地址</label>
        <input type="text" id="returnUrl" placeholder="returnUrl" />
        <button type="button" id="runButton">查询</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
            $('#returnUrl').val(location.protocol + "//" + location.host + location.pathname);
            oauthapp.allReady().then(function () {
            
                document.getElementById('runButton').onclick = function () {
                    var postData = {};
                    postData.orderNo = $('#orderNo').val();
                    postData.amount = $('#amount').val() || 0.01;
                    postData.productID = $('#productID').val();
                    postData.subject = $('#subject').val();
                    oauthapp.alipayCreateOrderWapPay(postData).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | orderNo | 系统订单号，必填 |
    | amount | 商品金额，必填  | 最小值为0.01元 |
    | subject | 商品名称，必填 |
    | returnUrl |  支付同步通知地址，非必填 | 为空将从**应用配置**——**支付宝**——**支付成功返回页**中读取 |


[演示](https://web.oauthapp.com/4/examples/apidemo/alipayCreateOrderWapPay.html){ .md-button }  [教程](http://docs.oauthapp.com/coding_sdk_alipayCreateOrderWapPay.html){ .md-button }


### 订单查询

oauthapp.alipayOrder

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 订单详情
     * @params orderNo 系统订单号
    */
    oauthapp.alipayOrder(orderNo).then(function(res){
    console.log(res);
    /*
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
    */
    })
    ```
=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>alipayOrder</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <label>订单ID</label>
        <input type="text" id="orderNo" value="638227710323944845" />
        <button type="button" id="actionButton">提交</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('actionButton').onclick = function () {
                    var orderNo = $('#orderNo').val();
                    oauthapp.alipayOrder(orderNo).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                };
            });
        </script>
    </body>
    </html>
    ```
=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | orderNo | 系统订单号，必填 |

[演示](https://web.oauthapp.com/4/examples/apidemo/alipayOrder.html){ .md-button }  [教程](http://docs.oauthapp.com/coding_sdk_alipayOrder.html){ .md-button }

### 发起退款

oauthapp.alipayOrderRefund

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 发起退款
     * @params amount 退款金额
     * @params orderNo 系统订单号
    */
    oauthapp.alipayOrderRefund(amount,orderNo).then(function(res){
    console.log(res);
    /*
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
        "body": "{\"alipay_trade_refund_response\":{\"code\":\"10000\",\"msg\":\"Success\",\"buyer_logon_id\":\"v1v***@qq.  com\",\"buyer_user_id\":\"2088632335506388\",\"fund_change\":\"Y\",\"gmt_refund_pay\":\"2023-06-19 15:17:34\",    \"out_trade_no\":\"638227710323944845\",\"refund_fee\":\"0.30\",\"send_back_fee\":\"0.00\", \"trade_no\":\"2023061922001406381431771492\"},\"sign\":\"A  +8rbBL47iYVB9b7CrWf6on2slySye2zJ76ZQ61TyVDAvKxZ5jLfqFbs4TrPpkKfqZ+1wtrszXThdKpCWCpqJ8gA5Ni3OQ+qS6mVvf/    ZW79ntCTMDtjxo8KTMYCPcSmBRDRM3Oz7IqPtvD3mlf/FhdajZLIM0pZ5sqTZGEO3Jbz24zEOa/3cvTmPt5ySQdX73iJsfG054GgDDys1F8dMTeeaAwDM/  JailQXNNMi/vYOg+8ylOlfozMLgJXXV89voNbKfBlTlWfTwJHCYQiZWXIeBFujaTqQzszAml7QdtlujQiQypRguIB/gP  +u8Wq9fvbYyNVRPIRITm3S4GHzaJQ==\"}",
        "isError": false
      },
      "err": ""
    }
    */
    })
    ```
=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>alipayOrderRefund</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <label>订单ID</label>
        <input type="number" id="amount" value="0.01" />
        <input type="text" id="orderNo" value="638227710323944845" />
        <button type="button" id="actionButton">提交</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('actionButton').onclick = function () {
                    var amount = $('#amount').val();
                    var orderNo = $('#orderNo').val();
                    oauthapp.alipayOrderRefund(amount,orderNo).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                };
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | amount | 退款金额，必填 |
    | orderNo | 系统订单号，必填 |


[演示](https://web.oauthapp.com/4/examples/apidemo/alipayOrderRefund.html){ .md-button }    [教程](http://docs.oauthapp.com/coding_sdk_alipayOrderRefund.html){ .md-button }


### 支付同步通知

oauthapp.alipayReturnPageNotify

???+ note "提示"
    用于实现整个支付流程的同步流程，非必须调用。因为支付异步通知可自动同步订单数据。

所需参数均来自支付宝同步回传，页面只要获取、调用即可。 用于同步支付宝订单号和支付时间。

=== "方法"

    ```JavaScript linenums="1"
    // 支付成功后，支付宝会跳转到下单时传入的 returnUrl，并带上相关参数，参考如下
    // {{returnUrl}}?charset=UTF-8&out_trade_no=1687167960218&method=alipay.trade.page.pay.return&total_amount=0.01&sign=UCXw1EQGluYUXrJF%2B891QFeM0VdZslt%2Bejxz88MiBHKlFg1nH1hgsWam3hmAyaKvWF4GIfsB%2BGwZRBvOpEoyO8bjefLZswOJ9hLSyxQe4ZON8PaJe4R6k1WEZ6nEkU3qIqxZj5ubN13kUvEOeJMkOA1oNvjszLgs13Uso3AmZ1GFC%2B1nTt%2BhOemwrPH0D2OsYkuBKqooQtgKIJyXfGuAFBDm3KW6xx716tbwnXgU840N89LkkX97YjX0yinHy9yh0BnNkIQpj%2FdKFTWIifq0prH7WR%2F2kBIVuXnAUsE7UX7%2Fy9vuyEdThnkcT3cR5Fn6Gg3Iiin5wg1BUHo3A2jFZg%3D%3D&trade_no=2023061922001406381432294248&auth_app_id=2021003192659285&version=1.0&app_id=2021003192659285&sign_type=RSA2&seller_id=2088502858687065&timestamp=2023-06-19+17%3A47%3A02
    // 页面可获取上述参数，同步支付宝订单号和支付时间。
    /**
     * 支付同步通知
     * @params app_id
     * @params auth_app_id
     * @params charset
     * @params method
     * @params out_trade_no
     * @params seller_id
     * @params sign
     * @params sign_type
     * @params timestamp
     * @params total_amount
     * @params trade_no
     * @params version
    */
    oauthapp.alipayReturnPageNotify({app_id:'', auth_app_id:'',
        charset:'', method:'', out_trade_no:'', seller_id:'',
        sign:'', sign_type:'', timestamp:'', total_amount:'',
        trade_no:'', version:''}).then(function(res){
    console.log(res);

    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>alipayReturnPageNotify</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <textarea rows="10" id="postData">
            {
                "charset": "UTF-8",
                "out_trade_no": "1687167960218",
                "method": "alipay.trade.page.pay.return",
                "total_amount": "0.01",
                "sign": "UCXw1EQGluYUXrJF+891QFeM0VdZslt+ejxz88MiBHKlFg1nH1hgsWam3hmAyaKvWF4GIfsB   +GwZRBvOpEoyO8bjefLZswOJ9hLSyxQe4ZON8PaJe4R6k1WEZ6nEkU3qIqxZj5ubN13kUvEOeJMkOA1oNvjszLgs13Uso3AmZ1GFC+1nTt  +hOemwrPH0D2OsYkuBKqooQtgKIJyXfGuAFBDm3KW6xx716tbwnXgU840N89LkkX97YjX0yinHy9yh0BnNkIQpj/dKFTWIifq0prH7WR/    2kBIVuXnAUsE7UX7/y9vuyEdThnkcT3cR5Fn6Gg3Iiin5wg1BUHo3A2jFZg==",
                "trade_no": "2023061922001406381432294248",
                "auth_app_id": "2021003192659285",
                "version": "1.0",
                "app_id": "2021003192659285",
                "sign_type": "RSA2",
                "seller_id": "2088502858687065",
                "timestamp": "2023-06-19 17:47:02"
            }
        </textarea>
        <button type="button" id="actionButton">提交</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
        
            oauthapp.allReady().then(function () {
            
                document.getElementById('actionButton').onclick = function () {
                
                    var data = JSON.parse(document.getElementById('postData').value);

                    oauthapp.alipayReturnPageNotify(data).then((res) => {
                    
                        console.log(res);

                        $('#result').html(JSON.stringify(res));

                        // 查询支付宝订单详情，下发支付成功消息
                        // oauthapp.alipayOrder(data.out_trade_no).then((res2) => {
                        //     console.log(res2);
                        //     $('#result').html(JSON.stringify(res2));
                        //     //替换 url
                        //     history.replaceState(null, null, '?completed=true');
                        // })
                    })
                };
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | 略 | 所需参数均来自支付宝，页面只需获取回传参数、调用**alipayReturnPageNotify**即可 |

[演示](https://web.oauthapp.com/4/examples/apidemo/alipayReturnPageNotify.html){ .md-button }   [教程](http://docs.oauthapp.com/coding_sdk_alipayReturnPageNotify.html){ .md-button }

### 支付异步通知

**由系统自动设置**，交易成功后，自动校验支付宝回传数据并同步到系统订单。