---
tags:
  - 教程 - 应用 -脚本库与API
---


# 初始化 + 自动注册账号

!!! Tip "提示"
    oauthapp.allReady()方法是在oauthapp SDK中注册/登录用户并确保所有必要的依赖项都已加载并准备好使用的方法。此方法还将使用web指纹（fingerprintjs2）自动注册，如果账号不存在就自动注册；如果存在就自动登录，然后将用户信息赋值到window.oauthapp.appUser对象中。这使得在应用程序中可以使用所有API而无需手动注册或登录。

以下是使用oauthapp.allReady()方法的步骤：


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
    <h1>用户资料</h1><div id="appUser"></div>
    ```

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function(){
      
    });
    ```

在此示例中，当调用oauthapp.allReady()方法时，它将执行以下操作：

- 检查oauthapp SDK是否已经准备好使用。如果尚未准备好，则将等待所有必要的依赖项加载完成。

- 检查当前用户是否已经注册/登录。如果尚未注册/登录，则将使用web指纹（fingerprintjs2）自动注册用户。

如果用户已经注册/登录，则将用户信息赋值到window.oauthapp.appUser对象中。
如果在注册/登录过程中遇到任何错误，则将抛出一个错误并拒绝promise。可以在应用程序中使用oauthapp.app和oauthapp.appUser对象访问应用程序和用户的信息，

## 步骤四：测试结果

如果SDK已经准备好使用，页面则会展示应用、用户的相关信息。

=== "Javascript"
    ```Javascript
      $('#appInfo').text(JSON.stringify(oauthapp.app.info));
      $('#appProps').text(JSON.stringify(oauthapp.app.props));
      $('#appFiles').text(JSON.stringify(oauthapp.app.blobs));
      $('#appUser').text(JSON.stringify(oauthapp.appUser));
    ```

通过使用oauthapp.allReady()方法，可以轻松地注册/登录用户并准备使用所有API，而无需手动注册或登录。
这使得开发人员可以专注于开发应用程序的功能，而不是处理注册和登录的细节。

`oauthapp.app`：包含应用程序的基本信息、配置项和文件列表等。

`oauthapp.appUser`：包含当前登录用户的信息，例如用户ID、昵称和头像等。

`oauthapp.settings.access_token`：包含当前登录用户的访问令牌。


## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>allReady</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="{{appid}}"></script>
    </head>
    <body>
    <h1>应用详情</h1><div id="appInfo"></div>
    <h1>应用配置</h1><div id="appProps"></div>
    <h1>应用文件</h1><div id="appFiles"></div>
    <h1>用户资料</h1><div id="appUser"></div>
    <script>
        oauthapp.allReady().then(function () {
          $('#appInfo').text(JSON.stringify(oauthapp.app.info));
          $('#appProps').text(JSON.stringify(oauthapp.app.props));
          $('#appFiles').text(JSON.stringify(oauthapp.app.blobs));
          $('#appUser').text(JSON.stringify(oauthapp.appUser));
        });
    </script>
    </body>
    </html>
    ```