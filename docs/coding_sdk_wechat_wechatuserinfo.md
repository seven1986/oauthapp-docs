---
tags:
  - 教程 - 微信公众号 - 脚本库与API
---

# 公众号- 获取用户UnionID


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
        <input type="text" id="_openid" placeholder="_openid" />
        <button type="button" onclick="getUserInfo()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

用户需要在输入框中输入openid，点击提交按钮后，程序会调用getUserInfo函数，并将openid作为参数传递给该函数。

函数中使用_openid获取用户输入的openid，并将该openid作为参数调用oauthapp.wechatUserInfo方法，以获取对应的用户信息。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function getUserInfo() {
        var _openid = $('#_openid').val();
        oauthapp.wechatUserInfo(_openid).then(function (res) {
            
        });
    }
    ```

这段代码中的getUserInfo函数用于获取指定openid的用户信息。用户信息包括昵称、头像等基本信息。

获取到的用户信息会被保存在res对象中，可以在函数中将其进行处理，最终呈现在页面上，如将昵称和头像显示在页面上。


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
        <title>wechatUserInfo</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="_openid" placeholder="_openid" />
            <button type="button" onclick="getUserInfo()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function getUserInfo() {
                var _openid = $('#_openid').val();
                oauthapp.wechatUserInfo(_openid).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

