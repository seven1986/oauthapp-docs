---
tags:
  - 教程 - 用户 - 脚本库与API
---


# 微信小程序 扫码结果查询

这段代码展示了如何通过 oauthapp.minipSignInResult 方法使用 signInKey 进行轮询登录。用户使用微信小程序完成登录后，获取用户信息。
其中 signInKey 是 通过调用 **oauthapp.minipSignInQRCode** 方法获取。

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
         <label>signInKey</label>
         <input type="text" id="signInKey" />
         <button type="button" id="signInButton">登录</button>
     </div>
     <p>结果</p>
     <div id="result"></div>
    ```

在 HTML 中定义相应的输入框、按钮和结果区域


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(function () {
        document.getElementById('signInButton').onclick = function () {
            var signInKey = $('#signInKey').val();
            oauthapp.minipSignInResult(signInKey).then(function (res) {
            });
        }
    });
    ```

这段代码实现了在网页中使用 OAuthApp 的 minipSignInResult 方法查询小程序登录结果并处理结果。

需要注意的是，使用 minipSignInResult 方法查询小程序登录结果需要传入 signInKey，该密钥是在调用 minipSignInQRCode 方法时返回的。

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
        <title>minipSignInResult</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>signInKey</label>
            <input type="text" id="signInKey" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    var signInKey = $('#signInKey').val();
                    oauthapp.minipSignInResult(signInKey).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

