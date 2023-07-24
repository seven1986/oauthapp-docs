---
tags:
  - 开发教程 - 用户
---

# UnionID 登录

!!! Tip "提示"
    在开始之前，您需要注册一个OAuthApp开发者账户，并创建一个应用程序。如果您还没有注册，请访问OAuthApp官方网站进行注册。

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
      <label>unionId</label>
      <input type="text" id="unionId" />
      <label>platform</label>
      <input type="text" id="platform" />
      <button type="button" id="signInButton">登录</button>
    </div>
    ```

这段代码是一个登录表单，用于实现用户登录功能。表单包含两个输入框，一个是unionId输入框，另一个是platform输入框，以及一个登录按钮。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(function () {
      document.getElementById('signInButton').onclick = function () {
      
        var unionid = $('#unionId').val();
        var platform = $('#platform').val();
        if (!unionid) {
          unionid = oauthapp.settings.fingerIdentity;
        }
        if (!platform) {
          platform = 'web';
        }
        oauthapp.signIn(unionid, platform).then(function (res) {
         
        });

      }
    }); 
    ```

在该方法中，您需要传入unionId和platform参数，以告诉OAuthApp要登录哪个用户和使用哪个第三方平台。如果这些参数为空，则使用默认值。

## 步骤四：测试结果

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
        <title>signIn</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>unionId</label>
            <input type="text" id="unionId" />
            <label>platform</label>
            <input type="text" id="platform" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    var unionid = $('#unionId').val();
                    var platform = $('#platform').val();
                    if (!unionid) {
                        unionid = oauthapp.settings.fingerIdentity;
                    }
                    if (!platform) {
                        platform = 'web';
                    }
                    oauthapp.signIn(unionid, platform).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

如果一切正常，OAuthApp将返回一个access_token，您可以将其用于访问OAuthApp的API。