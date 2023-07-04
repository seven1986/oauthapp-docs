---
tags:
  - 教程 - 支付宝 - 脚本库与API
---

# 订单查询

查询支付宝支付订单，并同步支付状态、支付宝订单号、付款时间到系统订单。

需要调用查询接口的情况： 当后台、网络、服务器等出现异常，系统最终未接收到支付通知；

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
    <input type="text" id="orderNo" value="638227710323944845" />
    <button type="button" id="actionButton">提交</button>
    <p>结果</p>
    <div id="result"></div>
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.alipayOrder(orderNo)
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

