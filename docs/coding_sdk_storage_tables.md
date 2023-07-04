---
tags:
  - 教程 - 数据库 - 脚本库与API
---

# 数据表集合


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

这段代码创建了一个 div 元素，其中包含一个 span 元素，它的 id 为 "result"。在后续代码中，可以使用 JavaScript 来修改这个元素的内容，以显示一些结果或消息。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
       oauthapp.tables().then(function (res) {
          
       })
    });
    ```

这段代码使用了OAuth客户端SDK中的allReady()和tables()方法。当SDK全部加载完毕后，tables()方法用于获取应用程序中定义的所有数据表格的元数据信息。
这个方法返回一个包含所有表格信息的对象数组，可以进一步操作这些表格。在then()方法中，开发人员可以定义数据的操作逻辑，例如创建、修改或查询数据等。


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
        <title>tables</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.tables().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                })
            });
        </script>
    </body>
    </html>
    ```

