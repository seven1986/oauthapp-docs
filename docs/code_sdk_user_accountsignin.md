---
tags:
  - 教程 - 用户 - 脚本库与API
---

# 账号 登录


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
        <label>account</label>
        <input type="text" id="account" />
        <label>password</label>
        <input type="password" id="password" />
        <button type="button" id="signInButton">登录</button>
        <h1>结果</h1>
        <div id="result"></div>
    </div>
    ```

这段HTML代码展示了一个登录表单，其中包含账号、密码和登录按钮。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    document.getElementById('signInButton').onclick = function () {
        oauthapp.accountSignIn(
            $('#account').val(),
            $('#password').val()
        ).then(function (res) {
        });
    }
    ```

当用户点击 "登录" 按钮时，会调用 oauthapp.accountSignIn 函数，并将文本输入框中输入的用户名和密码作为参数传递给该函数。该函数返回一个 Promise 对象，其中包含服务器响应的信息

## 步骤四：测试结果

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
        <title>accountsignin</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>account</label>
            <input type="text" id="account" />
            <label>password</label>
            <input type="password" id="password" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <h1>结果</h1>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    oauthapp.accountSignIn(
                        $('#account').val(),
                        $('#password').val()
                    ).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```