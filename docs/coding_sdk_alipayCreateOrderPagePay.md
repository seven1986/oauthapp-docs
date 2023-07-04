---
tags:
  - 教程 - 支付宝 - 脚本库与API
---

# 电脑网站支付

需要先开通[电脑网站支付](https://b.alipay.com/page/ar-center/merchant-sign/form?productCode=I1011000100000000005)，将引导用户使用支付宝电脑网页完成付款。


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
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.alipayCreateOrderPagePay()
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

