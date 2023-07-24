---
tags:
  - 文档
---

# 订单

### 订单列表

oauthapp.orders

???+ note "提示"
    获取订单列表数据。返回的数据结构包括订单的ID、用户ID、订单号、订单状态、订单金额、支付类型、产品名称等信息。

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 订单列表
     * @params state 订单状态 | 可选值：TRADE_CLOSED、TRADE_FINISHED、TRADE_SUCCESS、WAIT_BUYER_PAY
     * @params orderNo 系统订单号
     * @params tradeNo 外部订单号
     * @params userId 用户ID
     * @params pctType 商品类型
     * @params pctId 商品ID
     * @params pctName 商品名称
     * @params skip 跳过条数
     * @params take 拉取条数
    */
    oauthapp.orders(state,orderNo,tradeNo,userId,pctType,pctId,pctName,skip.take).then(function(res){
      console.log(res);
      /*
      * 返回数据结构
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
        <title>orders</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <select id="state">
            <option></option>
            <option>WAIT_BUYER_PAY</option>
            <option>TRADE_SUCCESS</option>
            <option>TRADE_CLOSED</option>
            <option>TRADE_FINISHED</option>
        </select>
        <input type="text" id="orderNo" placeholder="orderNo" />
        <input type="text" id="tradeNo" placeholder="orderNo" />
        <input type="number" id="userId" placeholder="userId" />
        <input type="text" id="pctType" placeholder="pctType" />
        <input type="text" id="pctId" placeholder="pctId" />
        <input type="text" id="pctName" placeholder="pctName" />
        <input type="number" id="skip" placeholder="skip" />
        <input type="number" id="take" placeholder="take" />
        <button type="button" id="runButton">查询</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
            
                document.getElementById('runButton').onclick = function () {
                    var state = $('#state').val();
                    var orderNo = $('#orderNo').val();
                    var tradeNo = $('#tradeNo').val();
                    var userId = $('#userId').val()||0;
                    var pctType = $('#pctType').val();
                    var pctId = $('#pctId').val();
                    var pctName = $('#pctName').val();
                    var skip = $('#skip').val() || 0;
                    var take = $('#take').val() || 10;
                    oauthapp.orders(state, orderNo, tradeNo, userId, 
                    pctType, pctId, pctName, skip.take).then(function (res) {
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
    | state |  订单状态，默认为空，返回全部 | 可选值：TRADE_CLOSED、TRADE_FINISHED、TRADE_SUCCESS、WAIT_BUYER_PAY |
    | orderNo | 系统订单号，非必填 |
    | tradeNo | 支付平台单号 ，非必填|
    | userId | 用户ID，非必填，默认为为：0 |
    | pctType | 商品类型，非必填 |
    | pctId | 商品ID，非必填 |
    | pctName | 商品名称，非必填 |
    | skip |  可选，指定要拉取的数据条数。 | 0 |
    | take |  可选，指定要跳过的数据条数。 | 10 |

[演示](https://web.oauthapp.com/4/examples/apidemo/orders.html){ .md-button }   [教程](http://docs.oauthapp.com/coding_sdk_order_orders/){ .md-button }


### 创建订单

oauthapp.orderCreate

???+ note "提示"
    在创建订单成功后，您将获得订单ID和订单号。**可用于后续调用支付宝下单支付功能。**

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 创建订单
     * @params amount 订单金额
     * @params productType 商品类型
     * @params productID 商品ID
     * @params productName 商品名称
    */
    oauthapp.orderCreate({amount:0.01,productType:"point",productID:"1",productName:"测试商品"}).then(function(res){
      console.log(res);
      // 返回数据参考
      /*
      {
      "code": 200,
      "data": {
        "id": 1,
        "orderNo": "638205225950488498"
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
        <title>orderCreate</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <label>订单金额</label>
        <input type="text" id="amount" value="0.01" />

        <label>商品类型</label>
        <input type="text" id="productType" value="point" />

        <label>商品ID</label>
        <input type="text" id="productID" value="1" />

        <label>商品名称</label>
        <input type="text" id="productName" value="测试商品" />

        <button type="button" id="actionButton">提交</button>

        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
            
                document.getElementById('actionButton').onclick = function () {
                
                    var postData = {};
                    postData.amount = $('#amount').val() || 0.01;
                    postData.productType = $('#productType').val();
                    postData.productID = $('#productID').val();
                    postData.productName = $('#productName').val();

                    oauthapp.orderCreate(postData).then(function (res) {
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
    | amount | 商品金额，必填  | 最小值为0.01元 |
    | productType | 商品类型，必填  | **point** 或自定义，如果为**point**，支付成功后将自动充值积分，并产生充值记录。 |
    | productID | 商品ID，必填  | 自定义 |
    | productName | 商品名称，必填  |  |


[演示](https://web.oauthapp.com/4/examples/apidemo/orderCreate.html){ .md-button }  [教程](http://docs.oauthapp.com/coding_sdk_order_ordercreate/){ .md-button }


### 订单详情

oauthapp.order

???+ note "提示"
    订单详情接口用于获取特定订单的详细信息。

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 订单详情
     * @params orderId 订单ID
    */
    oauthapp.order(orderId).then(function(res){
      console.log(res);
      /*
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
        <title>order</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <label>订单ID</label>
        <input type="text" id="orderId" value="1" />
        <button type="button" id="actionButton">提交</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('actionButton').onclick = function () {
                    var orderId = $('#orderId').val();
                    oauthapp.order(orderId).then(function (res) {
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
    | orderId | 订单ID，数值类型  | 1 |

[演示](https://web.oauthapp.com/4/examples/apidemo/order.html){ .md-button }    [教程](http://docs.oauthapp.com/coding_sdk_order_order/){ .md-button }