---
tags:
  - 教程 - 微信小程序 - 脚本库与API
---

# 小程序 - 生成网页跳转地址


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
        <textarea rows="10" placeholder="请求数据" id="postData">
            {
                "path": "/pages/publishHomework/publishHomework",
                "query": "",
                "expire_type": 1,
                "expire_interval": 1,
                "env_version": "release"
            }
        </textarea>
        <button type="button" onclick="sendMsg()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

这段代码展示了一个包含请求数据文本框和提交按钮的HTML页面。文本框中的请求数据格式为JSON，包含了小程序跳转的路径、查询参数、过期时间类型和过期时间间隔、以及环境版本等信息。

点击提交按钮后，会调用名为sendMsg()的函数，将请求数据发送到服务器进行处理。最终处理结果将在页面中展示出来，放置在结果标签下的result元素中。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function sendMsg() {
        var postData = JSON.parse($('#postData').val());
        oauthapp.wechatUrlLinkGenerate(postData).then(function (res) {
           
        });
    }
    ```

当用户点击“提交”按钮时会调用这个函数。该函数首先获取文本框中输入的JSON数据并将其解析为JavaScript对象，然后使用oauthapp.wechatUrlLinkGenerate方法发送一个请求。

这个方法生成一个微信小程序的URL链接，用于在微信中分享小程序页面。

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
        <title>wechatUrlLinkGenerate</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "path": "/pages/publishHomework/publishHomework",
                    "query": "",
                    "expire_type": 1,
                    "expire_interval": 1,
                    "env_version": "release"
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatUrlLinkGenerate(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

