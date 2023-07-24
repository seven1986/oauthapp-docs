---
tags:
  - 开发教程 - 订单
---

# 订单详情


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

订单详情接口用于获取特定订单的详细信息。


=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        oauthapp.order(1).then(function(res){
            $('#result').text(JSON.stringify(res));
        });
    });
    ```

参数

- orderId（必填）：订单ID，数值类型。

在上述示例中，通过调用 oauthapp.order() 方法并传入订单ID作为参数，即可获取订单的详细信息。根据返回的数据结构，您可以判断订单的支付状态以及相关的订单状态信息。


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

