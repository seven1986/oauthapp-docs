---
tags:
  - 教程 - 订单 - 脚本库与API
---

# 订单列表


## 步骤一：引入 OAuthApp 库
=== "完整代码 - HTML"
    ```HTML
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    ```

在 HTML 文件的头部，我们首先需要引入 OAuthApp 库。其中 data-appid 属性需要替换为你的 OAuthApp 应用的 ID。


## 步骤二：页面结构

=== "HTML"
    ```HTML
    <p>结果</p>
    <div id="result"></div>
    ```


## 步骤三：调用方法

oauthapp.orders() 方法用于获取订单列表数据。以下是该方法的参数说明：

 - 参数	说明	默认值
 - state（可选）：订单状态。可选值包括 "TRADE_CLOSED"、"TRADE_FINISHED"、"TRADE_SUCCESS" 和 "WAIT_BUYER_PAY"。
 - orderNo（可选）：系统订单号。
 - tradeNo（可选）：外部订单号。
 - userId（可选）：用户ID。
 - pctType（可选）：商品类型。
 - pctId（可选）：商品ID。
 - pctName（可选）：商品名称。
 - skip：要跳过的条数。
 - take：要获取的条数。


您可以根据实际需求传入相应的参数值来获取符合条件的订单列表数据。请注意，根据订单数量和数据量的大小，适当调整 skip 和 take 的值以控制返回的数据条数。


=== "Javascript"
    ```Javascript
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
    ```



## 步骤三：测试结果

根据返回的数据结构，您可以按需提取和展示订单的各个字段。订单数据的结构包括订单的ID、用户ID、订单号、订单状态、订单金额、支付类型、产品名称等信息。请根据您的需求进行数据的处理和展示。

=== "Javascript"
    ```Javascript
    $('#result').text(JSON.stringify(res));
    ```



## 完整代码示例

=== "HTML"
    ```HTML
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

