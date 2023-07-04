---
tags:
  - 教程 - 用户 - 脚本库与API
---


# 统一登录(单点登录)


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
    <h1>结果</h1>
    <div id="result"></div>
    ```


## 步骤三：调用方法

=== "HTML"
    ```HTML
    <a href="https://www.oauthapp.com/oauth/2?scheme=app&redirect_uri=https://web.oauthapp.com/4/examples/apidemo/sso.html&scopes=openid profile role&  nonce=1667553723079">
        登录
    </a>
    ```

直接点击 a 标签，将跳转到oauthapp 单点登录。跳转参数说明：

 - scheme：登录协议(必填)	固定为 "app"
 - appId：应用ID(必填)	
 - scopes：授权列表(必填)	多个权限用英文空格分隔
 - redirect_uri：回调地址(必填)	
 - redirect_uri_name：自定义授权标题	
 - nonce：自定义字符串，32位(必填)	


## 步骤四：测试结果

=== "Javascript"
    ```Javascript
    document.getElementById('result').innerHTML = location.search;
    ```

登陆成功后，将access_token展示到页面



## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>统一登陆</title>
    </head>
    <body>
        <a
            href="https://www.oauthapp.com/oauth/2?scheme=app&redirect_uri=https://web.oauthapp.com/4/examples/apidemo/sso.html&scopes=openid profile role& nonce=1667553723079">
            登录
        </a>
        <h1>结果</h1>
        <div id="result"></div>
        <script>
            document.getElementById('result').innerHTML = location.search;
        </script>
    </body>
    </html>
    ```
