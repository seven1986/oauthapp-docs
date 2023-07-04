---
tags:
  - 教程 - 存储 - 脚本库与API
---

# 上传文件


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
    <div>选择文件：<input id="fileUploader" type="file"></div>
    <div>结果：<span id="result"></span></div>
    ```

这段代码实现了一个文件上传功能，通过input标签的type属性设置为file，可以实现文件上传的功能，并且将文件上传的结果显示在span标签的id为result的位置上。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
          document.getElementById('fileUploader').onchange = function (event) {
            var file = event.target.files[0];
            oauthapp.upload(file).then(function (res) {
              
            })
          }
    });
    ```

该代码段用于将文件上传到 OAuth 应用程序。首先，调用 oauthapp.allReady() 方法确保应用程序已准备就绪，然后为文件上传器添加一个 onchange 事件处理程序，以便在文件发生变化时触发处理程序。在处理程序中，从事件对象中获取文件，然后调用 oauthapp.upload() 方法将文件上传到 OAuth 应用程序，最后，在 Promise 对象的回调函数中处理响应结果。


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
      <title>upload</title>
      <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
      <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
      <div>选择文件：<input id="fileUploader" type="file"></div>
      <div>结果：<span id="result"></span></div>
      <script>
        oauthapp.allReady().then(function () {
          document.getElementById('fileUploader').onchange = function (event) {
            var file = event.target.files[0];
            oauthapp.upload(file).then(function (res) {
              $('#result').text(JSON.stringify(res));
            })
          }
        });
      </script>
    </body>
    </html>      
    ```