---
tags:
  - 开发教程 - 排行榜
---

# 榜单集合


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
        oauthapp.ranks().then(function (res) {
            
        })
    });
    ```

该段代码使用OAuth进行身份验证，等待OAuth准备完毕后，使用oauthapp.ranks()方法获取排行榜信息。

在获取到排行榜信息之后，执行一个回调函数来处理返回结果。其中，res参数代表获取到的排行榜信息。

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
        <title>ranks</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.ranks().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                })
            });
        </script>
    </body>
    </html>
    ```

