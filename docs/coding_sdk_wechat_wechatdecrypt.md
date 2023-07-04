---
tags:
  - 教程 - 微信小程序 - 脚本库与API
---

# 小程序 - 解密数据


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
        <input type="text" id="_encryptedData" placeholder="_encryptedData" />
        <input type="text" id="_iv" placeholder="_iv" />
        <input type="text" id="_sessionKey" placeholder="_sessionKey" />
        <button type="button" onclick="decrypt()">提交</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

这段代码创建了一个包含三个文本输入框和一个按钮的 HTML 表单，用于接收小程序端的数据，然后执行解密操作。

当用户在文本框中输入了待解密的数据后，点击“提交”按钮，将触发 decrypt() 函数的执行。



## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function decrypt() {
        var _encryptedData = $('#_encryptedData').val();
        var _iv = $('#_iv').val();
        var _sessionKey = $('#_sessionKey').val();
        oauthapp.wechatDecrypt(_encryptedData, _iv, _sessionKey).then(function (res) {
            
        });
    }
    ```

该函数从文本框中读取加密的数据和相应的密钥，然后调用 oauthapp.wechatDataDecrypt() 方法对数据进行解密。解密后的结果将会显示在结果区域的文本框中。


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
        <title>wechatDecrypt</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="_encryptedData" placeholder="_encryptedData" />
            <input type="text" id="_iv" placeholder="_iv" />
            <input type="text" id="_sessionKey" placeholder="_sessionKey" />
            <button type="button" onclick="decrypt()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function decrypt() {
                var _encryptedData = $('#_encryptedData').val();
                var _iv = $('#_iv').val();
                var _sessionKey = $('#_sessionKey').val();
                oauthapp.wechatDecrypt(_encryptedData, _iv, _sessionKey).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

