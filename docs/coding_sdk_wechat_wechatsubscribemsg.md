---
tags:
  - 开发教程 - 微信
---

# 公众号 - 发送一次性订阅消息


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
                "touser": "OPENID",
                "template_id": "TEMPLATE_ID",
                "url": "URL",
                "miniprogram": {
                    "appid": "xiaochengxuappid12345",
                    "pagepath": "index?foo=bar"
                },
                "scene": "SCENE",
                "title": "TITLE",
                "data": {
                    "content": {
                        "value": "VALUE",
                        "color": "COLOR"
                    }
                }
            }
        </textarea>
        <button type="button" onclick="sendMsg()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

该代码段展示了一个包含模板消息请求数据的文本框和一个提交按钮的HTML表单，其中请求数据是一个JSON对象，包含以下字段：

 - touser：接收者的openid

 - template_id：所需下发的模板消息的id

 - url：模板跳转链接（可选）

 - miniprogram：跳小程序所需数据，如果需要跳小程序，则传该字段

 - appid：对应的小程序appid

 - pagepath：对应小程序内页面路径

 - scene：消息进入的场景值（可选）

 - title：模板标题

 - data：模板内容，格式形如 {"key1": {"value": any},"key2": {"value": any}}。

当用户单击提交按钮时，将调用一个名为“sendMsg”的JavaScript函数，它将获取文本框中的JSON对象数据，使用OAuthApp中的wechatTemplateMessageSend方法发送模板消息，并将结果显示在结果部分的span元素中。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function sendMsg() {
        var postData = JSON.parse($('#postData').val());
        oauthapp.wechatSubscribeMSG(postData).then(function (res) {
            
        });
    }
    ```

该函数的作用是通过调用 oauthapp 对象的 wechatSubscribeMSG 方法，发送微信订阅消息。

该方法会发送 HTTP 请求到微信服务器，请求发送订阅消息。在请求成功后，会将结果传递给 Promise 对象，通过 .then() 方法传递一个回调函数来处理请求结果。

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
        <title>wechatSubscribeMSG</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "touser": "OPENID",
                    "template_id": "TEMPLATE_ID",
                    "url": "URL",
                    "miniprogram": {
                        "appid": "xiaochengxuappid12345",
                        "pagepath": "index?foo=bar"
                    },
                    "scene": "SCENE",
                    "title": "TITLE",
                    "data": {
                        "content": {
                            "value": "VALUE",
                            "color": "COLOR"
                        }
                    }
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatSubscribeMSG(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

