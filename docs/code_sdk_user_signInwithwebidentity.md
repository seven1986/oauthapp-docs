---
tags:
  - 开发教程 - 用户
---

# Web ID 注册


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
        <p>结果</p>
        <div id="result"></div>
    ```

该部分代码定义了一个段落 p 元素和一个 div 元素，用于在页面上显示认证结果。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        oauthapp.signInWithWebIdentity().then(function (res) {
        });
    });
    ```

该部分代码首先调用了 OAuthApp SDK 的 allReady 方法，确保 OAuthApp SDK 已经加载并准备就绪，之后使用 signInWithWebIdentity 方法进行身份认证。



## 步骤四：测试结果

=== "Javascript"
    ```Javascript
    $('#result').text(JSON.stringify(res));
    ```

认证成功后，signInWithWebIdentity 方法会返回一个包含用户身份信息的对象 res，该代码使用 JSON.stringify 方法将其转换为字符串，并将其显示在页面上。


## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>signInWithWebIdentity</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.signInWithWebIdentity().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            });
        </script>
    </body>
    </html>
    ```

