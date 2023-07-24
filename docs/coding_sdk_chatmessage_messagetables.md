---
tags:
  - 开发教程 - 消息
---

# 消息表集合


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
    <div>结果：<span id="result"></span></div>
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        oauthapp.messageTables().then(function (res) {
           
        })
    });
    ```

这段代码是在使用 OAuthApp 库中的 allReady() 方法确保 OAuthApp 库已经准备就绪后，调用 messageTables() 方法来获取可用的消息表信息。

在该方法的回调函数中，使用了一个参数 res，该参数包含了返回的消息表信息。

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
        <title>messageTables</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.messageTables().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                })
            });
        </script>
    </body>
    </html>
    ```

