---
tags:
  - 开发教程 - 支付宝
---

# 发起退款

当交易发生之后一段时间内，由于买家或者卖家的原因需要退款时，卖家可以通过退款接口将支付款退还给买家，支付宝将在收到退款请求并且验证成功之后，按照退款规则将支付款按原路退到买家帐号上。

交易超过约定时间（签约时设置的可退款时间）的订单无法进行退款。

支付宝退款支持单笔交易分多次退款，多次退款需要提交原支付订单的订单号和设置不同的退款请求号。

一笔退款失败后重新提交，要保证重试时退款请求号不能变更，防止该笔交易重复退款。

同一笔交易累计提交的退款金额不能超过原始交易总金额。

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
    <label>订单ID</label>
    <input type="number" id="amount" value="0.01" />
    <input type="text" id="orderNo" value="638227710323944845" />
    <button type="button" id="actionButton">提交</button>
    <p>结果</p>
    <div id="result"></div>
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.alipayOrderRefund(amount,orderNo)
    ```



## 步骤三：测试结果

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

