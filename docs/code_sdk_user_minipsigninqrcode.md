---
tags:
  - 开发教程 - 用户
---


# 微信小程序 扫码登录


## 步骤一：引入 OAuthApp 库
=== "完整代码 - HTML"
    ```HTML
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    ```

在 HTML 文件的头部，我们首先需要引入 OAuthApp 库。其中 data-appid 属性需要替换为你的 OAuthApp 应用的 ID。


## 步骤二：页面结构
=== "HTML"
    ```HTML linenums="1"
    <div>
        <label>scopes</label>
        <input type="text" id="scopes" />
        <label>remark</label>
        <input type="text" id="remark" />
        <button type="button" id="signInButton">登录</button>
    </div>
    <p>结果</p>
    <p>
        <b>signInKey：</b>
        <span id="signInKey"></span>
        <img id="signInQRCode" />
    </p>
    ```

这是一个包含输入框和按钮的div，输入框用于填写scopes和remark信息，按钮用于触发登录事件。登录成功后，会在页面上展示signInKey和QRCode。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(function () {
        document.getElementById('signInButton').onclick = function () {
            var scopes = $('#scopes').val() || 'openid';
            var remark = $('#remark').val() || navigator.userAgent;
            oauthapp.minipSignInQRCode(scopes, remark).then(function (res) {
            
            });
        }
    });
    ```

这段代码实现了一个使用 OAuthApp 的小程序登录功能，并生成登录二维码的功能。


## 步骤四：测试结果

=== "Javascript"
    ```Javascript
    $('#signInKey').text(res.signInKey);
    $('#signInQRCode').attr('src',res.qrcode);
    ```

其中 res.signInKey 表示登录密钥，res.qrcode 表示二维码图片的 URL。通过 jQuery 将这些信息显示在页面上，用于用户扫描登录。

## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>minipSignInQRCode</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>scopes</label>
            <input type="text" id="scopes" />
            <label>remark</label>
            <input type="text" id="remark" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <p>结果</p>
        <p>
            <b>signInKey：</b>
            <span id="signInKey"></span>
            <img id="signInQRCode" />
        </p>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    var scopes = $('#scopes').val() || 'openid';
                    var remark = $('#remark').val() || navigator.userAgent;

                    oauthapp.minipSignInQRCode(scopes, remark).then(function (res) {
                        $('#signInKey').text(res.signInKey);
                        $('#signInQRCode').attr('src',res.qrcode);
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

