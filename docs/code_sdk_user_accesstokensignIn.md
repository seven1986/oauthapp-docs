---
tags:
  - 教程 - 用户 - 脚本库与API
---


# access_token 登录


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
        <label>access_token</label>
        <input type="text" id="access_token" />
        <label>expires_in</label>
        <input type="number" id="expires_in" value="7200" />
        <button type="button" id="signInButton">登录</button>
    </div>
    <h1>结果</h1>
    <div id="result"></div>
    ```

代码片段显示了一个包含两个输入框和一个登录按钮的HTML表单。其中输入框用于输入访问令牌(access_token)和过期时间(expires_in)，登录按钮用于提交表单。在点击登录按钮后，应该会发起一个请求来验证输入的访问令牌。验证成功后，相关结果将显示在页面上方的"H1"标签下的"结果"标签内的div元素中。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(function () {
        document.getElementById('signInButton').onclick = function () {
            oauthapp.accesstokenSignIn(
                $('#access_token').val(),
               parseInt($('#expires_in').val())
            ).then(function (res) {
            });
        }
    });
    ```
    
当用户点击登录按钮时，会调用accesstokenSignIn方法，该方法将使用传递的参数进行身份验证。如果验证成功，则返回相应的用户信息。

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
        <title>accesstokenSignIn</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>access_token</label>
            <input type="text" id="access_token" />
            <label>expires_in</label>
            <input type="number" id="expires_in" value="7200" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <h1>结果</h1>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    oauthapp.accesstokenSignIn(
                        $('#access_token').val(),
                       parseInt($('#expires_in').val())
                    ).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```