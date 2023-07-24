---
tags:
  - 开发教程 - 微信
---

# 小程序 - 登录凭证校验


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
    <div>
        <input type="text" id="code" placeholder="code" />
        <button type="button" onclick="code2session()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

这段代码实现了一个简单的页面，包含一个文本框和一个按钮。用户可以在文本框中输入 code，点击按钮后会触发 code2session() 函数，将 code 作为参数传递给函数。

函数会调用 oauthapp.wechatCode2Session() 方法，返回一个 Promise 对象，当 Promise 被 resolved 时，将结果显示在页面中的 result 元素中。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function code2session() {
        var js_code = JSON.parse($('#code').val());
        oauthapp.wechatJSCode2Session(js_code).then(function (res) {
            
        });
    }
    ```

该代码段定义了一个名为 code2session 的函数，该函数通过oauthapp.wechatJSCode2Session 方法将输入的 code 转换为微信小程序提用户的 session 信息，并将结果存储在 res 变量中。

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
        <title>wechatJSCode2Session</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="code" placeholder="code" />
            <button type="button" onclick="code2session()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function code2session() {
                var js_code = JSON.parse($('#code').val());
                oauthapp.wechatJSCode2Session(js_code).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

