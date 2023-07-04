---
tags:
  - 教程 - 微信小程序 - 脚本库与API
---

# 获取小程序码


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
                "path": "page/index/index",
                "env_version": "release",
                "width": 430
            }
        </textarea>
        <button type="button" onclick="sendMsg()">提交</button>
    </div>
    <div>结果：
        <span id="result"></span>
        <img id="result2" />
    </div>
    ```

这段代码包含一个多行文本框，用于输入一个JSON格式的请求数据，以及一个提交按钮，点击按钮后会触发sendMsg函数，并将请求结果显示在页面上。

sendMsg函数会从文本框中读取JSON格式的请求数据，然后调用oauthapp.wechatWXACodeUnlimited函数发起请求。请求成功后，将返回一个Blob类型的文件对象res。

接下来，代码通过URL.createObjectURL函数将Blob对象转换成URL地址，然后将URL地址显示在页面上的结果元素中。此外，代码还将URL地址作为img元素的src属性，从而在页面上显示二维码图片。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function sendMsg() {
        var postData = JSON.parse($('#postData').val());
        oauthapp.wechatWXACodeGet(postData).then(function (res) {

        });
    }
    ```

这段代码是一个JavaScript函数，其名称为 sendMsg()。当点击页面上的提交按钮时，j将获取文本区域中的请求数据并将其解析为JSON对象。

然后作为参数来调用 oauthapp.wechatWXACodeGet() 函数。最后，将返回的小程序二维码（通过 id 为 result2 的 img 元素）显示出来。

## 步骤三：测试结果

=== "Javascript"
    ```Javascript
    var url = URL.createObjectURL(res)
    $('#result').text(url);
    $('#result2').attr('src', url);
    ```


这段代码是在将一个二进制流（res）转化为可访问的URL，并将这个URL分别设置给一个文本和一个图像元素。

具体来说，URL.createObjectURL(res) 创建一个包含二进制流数据的 URL 对象，这个 URL 对象可以作为图片或者其他资源的 URL 引用。

$('#result').text(url) 将这个 URL 对象设置为文本元素 #result 的文本内容，而 $('#result2').attr('src', url) 将这个 URL 对象设置为图像元素 #result2 的 src 属性值，这样就可以在页面上展示这个图像。


## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatWXACodeGet</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "path": "page/index/index",
                    "env_version": "release",
                    "width": 430
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：
            <span id="result"></span>
            <img id="result2" />
        </div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatWXACodeGet(postData).then(function (res) {
                    var url = URL.createObjectURL(res)
                    $('#result').text(url);
                    $('#result2').attr('src', url);
                });
            }
        </script>
    </body>
    </html>
    ```

