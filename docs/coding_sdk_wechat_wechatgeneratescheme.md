---
tags:
  - 开发教程 - 微信
---

# 生成scheme码

本教程将介绍如何使用 OAuthApp SDK 中的 wechatGenerateScheme() 方法来生成微信小程序的跳转链接。通过这个功能，您可以方便地生成带有特定页面路径和参数的微信小程序跳转链接。

## 步骤一：引入 OAuthApp 库
=== "完整代码 - HTML"
    ```HTML
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    ```

在 HTML 文件的头部，我们首先需要引入 OAuthApp 库。其中 data-appid 属性需要替换为你的 OAuthApp 应用的 ID。


## 步骤二：页面结构


在页面的主体部分，找到 **textarea** 元素，其中的内容为默认的请求参数。您可以根据您的需求修改请求参数，具体的参数说明如下：

- jump_wxa（可选）：跳转到的目标小程序信息。
- path：通过 Scheme 码进入的小程序页面路径。如果为空，则会跳转到小程序的主页。
- query：通过 Scheme 码进入小程序时的 query 参数。
- env_version：要打开的小程序版本，默认为 "release"。
- is_expire（可选）：生成的 Scheme 码类型。设置为 true 表示到期失效，设置为 false 表示30天有效。

=== "HTML"
    ```HTML
    <div>
        <textarea rows="10" placeholder="请求数据" id="postData">
            {
            "jump_wxa":
            {
                "path": "/pages/hot/hot",
                "query": "",
                "env_version": "release"
            },
            "is_expire":false
            }
        </textarea>
        <button type="button" onclick="sendMsg()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```


## 步骤三：调用方法

在页面的 JavaScript 部分，找到 sendMsg() 函数。该函数会在用户点击提交按钮时被调用。

在 sendMsg() 函数内，会获取 **textarea** 元素中的请求数据，并调用 oauthapp.wechatGenerateScheme() 方法来生成微信小程序的跳转链接。生成的结果将会显示在页面中的 **span** 元素内。

=== "Javascript"
    ```Javascript
    function sendMsg() {
        var postData = JSON.parse($('#postData').val());
        oauthapp.wechatGenerateScheme(postData).then(function (res) {
            $('#result').text(JSON.stringify(res));
        });
    }
    ```



## 步骤三：测试结果

=== "Javascript"
    ```Javascript
    $('#result').text(JSON.stringify(res));
    ```

您可以在 **textarea** 元素内修改请求参数，然后点击提交按钮来生成微信小程序的跳转链接。生成的结果将会显示在页面中。

> 请确保在引入 OAuthApp SDK 时，将 data-appid 属性替换为您的实际 OAuthApp 应用的 ID。另外，确保您已正确设置请求参数和调用了正确的方法。


## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatgenerateScheme</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                "jump_wxa":
                {
                    "path": "/pages/hot/hot",
                    "query": "",
                    "env_version": "release"
                },
                "is_expire":false
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatGenerateScheme(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

