---
tags:
  - 教程 - 微信小程序 - 脚本库与API
---

# 小程序 - 发送订阅消息


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
                "page": "index",
                "miniprogram_state": "developer",
                "lang": "zh_CN",
                "data": {
                    "number01": {
                        "value": "339208499"
                    },
                    "date01": {
                        "value": "2015年01月05日"
                    },
                    "site01": {
                        "value": "TIT创意园"
                    },
                    "site02": {
                        "value": "广州市新港中路397号"
                    }
                }
            }
        </textarea>
        <button type="button" onclick="sendMsg()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

这段代码是一个包含一个文本框和一个按钮的 HTML 页面，可以用来发送微信模板消息。其中文本框中包含一个 JSON 格式的请求数据，按钮可以触发一个 JavaScript 函数 sendMsg()，该函数会将文本框中的数据发送给微信服务器，并将服务器的响应显示在页面上。

具体来说，这段代码的功能如下：

在页面上显示一个文本框和一个按钮。

在文本框中预填入一段 JSON 格式的请求数据，用于向微信服务器发送模板消息。

当用户点击按钮时，触发 sendMsg() 函数，该函数会读取文本框中的数据，将其作为请求发送到微信服务器，并将服务器的响应显示在页面上。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function sendMsg() {
        var postData = JSON.parse($('#postData').val());
        oauthapp.wechatSubscribeSend(postData).then(function (res) {
            
        });
    }
    ```

这段代码定义了一个名为 sendMsg 的函数，该函数会从页面中获取一个名为 postData 的 textarea 中的 JSON 格式数据，并将其解析为一个 JavaScript 对象。

然后使用 oauthapp 对象调用 wechatSubscribeSend 方法来发送微信订阅消息，并在发送成功后执行一个回调函数。

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
        <title>wechatSubscribeSend</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "touser": "OPENID",
                    "template_id": "TEMPLATE_ID",
                    "page": "index",
                    "miniprogram_state": "developer",
                    "lang": "zh_CN",
                    "data": {
                        "number01": {
                            "value": "339208499"
                        },
                        "date01": {
                            "value": "2015年01月05日"
                        },
                        "site01": {
                            "value": "TIT创意园"
                        },
                        "site02": {
                            "value": "广州市新港中路397号"
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
                oauthapp.wechatSubscribeSend(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

