---
tags:
  - 教程 - 微信公众号 - 脚本库与API
---

# JS SDK Config


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
        <button type="button" onclick="getJsConfig()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

该代码段中包含一个 HTML 输入框和一个按钮，它们用于获取某个微信用户的 JS-SDK 配置参数。

在输入框中，用户需要输入一个 _openid，这是一个微信用户的唯一标识符。用户点击提交按钮后，会触发 getJsConfig() 函数。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function getJsConfig() {
        var _url = $('#_url').val() || location.href;
        oauthapp.wechatJSConfig(_url).then(function (res) {
            
        });
    }
    ```

该函数会调用 oauthapp.wechatGetJsConfig() 方法来获取 JS-SDK 配置参数，然后将结果显示在页面上的一个 span 元素中。

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
        <title>wechatJSConfig</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="_openid" placeholder="_openid" />
            <button type="button" onclick="getJsConfig()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function getJsConfig() {
                var _url = $('#_url').val() || location.href;
                oauthapp.wechatJSConfig(_url).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

