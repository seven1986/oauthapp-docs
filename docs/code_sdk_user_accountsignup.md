---
tags:
  - 开发教程 - 用户
---

# 账号 注册

!!! Tip "提示"
    本代码演示了如何使用 OAuthApp 的 JavaScript SDK 进行用户注册，包括输入用户名、密码、头像、昵称和平台信息，然后调用 accountSignUp() 方法向 OAuthApp 服务器发送注册请求。


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
        <label>userName</label>
        <input type="text" id="userName" />
        <label>password</label>
        <input type="text" id="password" />
        <label>avatar</label>
        <input type="text" id="avatar" />
        <label>nickName</label>
        <input type="text" id="nickName" />
        <label>platform</label>
        <input type="text" id="platform" />
        <button type="button" id="signUpButton">注册</button>
    </div>
    ```

这段代码展示了一个简单的用户注册表单，包括输入用户名、密码、头像、昵称和平台信息的输入框，以及一个注册按钮。用户可以输入个人信息，然后点击按钮进行注册

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(function () {
            document.getElementById('signUpButton').onclick = function () {
                var userName = $('#userName').val() || oauthapp.settings.fingerIdentity;
                var password = $('#password').val() || '123456';
                var avatar = $('#avatar').val() || oauthapp.app.info.logo;
                var nickName = $('#nickName').val() || userName;
                var platform = $('#platform').val() || 'web';
                oauthapp.accountSignUp(userName, password, avatar, nickName, platform).then(function (res) {
                   
                });
            }
        });
    ```

在 accountSignUp() 方法中，我们需要传递五个参数：

- userName：用户的用户名，可以为空，默认值为 SDK 配置中的 fingerIdentity。
- password：用户的密码，可以为空，默认值为 "123456"。
- avatar：用户的头像 URL，可以为空，默认值为应用的 logo URL。
- nickName：用户的昵称，可以为空，默认值为 userName。
- platform：用户的平台信息，可以为空，默认值为 "web"。


## 步骤四：测试结果

=== "Javascript"
    ```Javascript
     $('#result').text(JSON.stringify(res));
    ```

当注册请求成功返回时，我们可以在回调函数中将返回值显示在 HTML 页面上，


## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>accountSignUp</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>userName</label>
            <input type="text" id="userName" />
            <label>password</label>
            <input type="text" id="password" />
            <label>avatar</label>
            <input type="text" id="avatar" />
            <label>nickName</label>
            <input type="text" id="nickName" />
            <label>platform</label>
            <input type="text" id="platform" />
            <button type="button" id="signUpButton">注册</button>
        </div>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signUpButton').onclick = function () {
                    var userName = $('#userName').val() || oauthapp.settings.fingerIdentity;
                    var password = $('#password').val() || '123456';
                    var avatar = $('#avatar').val() || oauthapp.app.info.logo;
                    var nickName = $('#nickName').val() || userName;
                    var platform = $('#platform').val() || 'web';
                    oauthapp.accountSignUp(userName, password, avatar, nickName, platform).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```