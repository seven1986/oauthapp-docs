---
tags:
  - 开发教程 - 用户
---


# UnionID 注册

!!! Tip "提示"
    本文将介绍如何使用 OAuthApp 库实现一个简单的注册功能，并解释代码的每个部分是如何工作的。


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
        <label>unionId</label>
        <input type="text" id="unionId" />
        <label>platform</label>
        <input type="text" id="platform" />
        <label>password</label>
        <input type="text" id="password" />
        <label>avatar</label>
        <input type="text" id="avatar" />
        <button type="button" id="signUpButton">注册</button>
    </div>
    <p>结果</p>
    <div id="result"></div>
    ```

注册表单包括四个输入框，分别为 unionId，platform，password，avatar。点击注册按钮后，结果将会以 JSON 格式显示在页面上。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(function () {
        document.getElementById('signUpButton').onclick = function () {
            var unionid = $('#unionId').val() || oauthapp.settings.fingerIdentity;
            var platform = $('#platform').val() || 'web';
            var password = $('#password').val() || '123456';
            var avatar = $('#avatar').val() || oauthapp.app.info.logo;
            oauthapp.signUp(unionid, platform, password, avatar).then(function (res) {
            });
        }
    });
    ```

当用户点击注册按钮时，我们通过 jQuery 获取表单输入框的值，并在需要时使用默认值进行填充。


## 步骤四：测试结果

=== "Javascript"
    ```Javascript
    $('#result').text(JSON.stringify(res));
    ```

将结果以 JSON 格式显示在页面上。

## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>signUp</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>unionId</label>
            <input type="text" id="unionId" />
            <label>platform</label>
            <input type="text" id="platform" />
            <label>password</label>
            <input type="text" id="password" />
            <label>avatar</label>
            <input type="text" id="avatar" />
            <button type="button" id="signUpButton">注册</button>
        </div>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signUpButton').onclick = function () {
                    var unionid = $('#unionId').val() || oauthapp.settings.fingerIdentity;
                    var platform = $('#platform').val() || 'web';
                    var password = $('#password').val() || '123456';
                    var avatar = $('#avatar').val() || oauthapp.app.info.logo;
                    oauthapp.signUp(unionid, platform, password, avatar).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```
