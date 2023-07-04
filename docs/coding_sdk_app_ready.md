---
tags:
  - 教程 - 应用 -脚本库与API
---

# 初始化

!!! Tip "提示"
    在使用SDK的其他方法之前，必须调用oauthapp.ready()方法确保SDK已经准备就绪。


## 步骤一：引入 OAuthApp 库
=== "HTML"
    ```HTML
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    ```

在 HTML 文件的头部，我们首先需要引入 OAuthApp 库。其中 data-appid 属性需要替换为你的 OAuthApp 应用的 ID。

## 步骤二：页面结构

=== "HTML"
    ```HTML
    <h1>应用详情</h1><div id="appInfo"></div>
    <h1>应用配置</h1><div id="appProps"></div>
    <h1>应用文件</h1><div id="appFiles"></div>
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(() => {
      // SDK 已经准备好使用，可以调用其他方法
    }).catch(err => {
      console.error('OAuthApp SDK 加载失败', err);
    });
    ```

在上面的代码中，首先调用了oauthapp.ready()方法，该方法返回一个Promise对象。在Promise对象的then()方法中编写SDK准备好后执行的回调函数。如果SDK加载失败，则在catch()方法中输出错误信息。

## 步骤四：测试结果

SDK加载成功后，通过访问 **window.oauthapp** 对象可获取应用相关信息，在实际开发中，我们可以根据需要在oauthapp.ready()方法的回调函数中编写其他业务逻辑。

=== "Javascript"
    ```Javascript
      $('#appInfo').text(JSON.stringify(oauthapp.app.info));
      $('#appProps').text(JSON.stringify(oauthapp.app.props));
      $('#appFiles').text(JSON.stringify(oauthapp.app.blobs));
    ```

上面的代码演示了将应用信息、应用属性、应用文件列表展示在html元素中。

## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>ready</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="{{appid}}"></script>
    </head>
    <body>
    <h1>应用详情</h1><div id="appInfo"></div>
    <h1>应用配置</h1><div id="appProps"></div>
    <h1>应用文件</h1><div id="appFiles"></div>
    <script>
        oauthapp.ready().then(function () {
          $('#appInfo').text(JSON.stringify(oauthapp.app.info));
          $('#appProps').text(JSON.stringify(oauthapp.app.props));
          $('#appFiles').text(JSON.stringify(oauthapp.app.blobs));
        });
    </script>
    </body>
    </html>
    ```