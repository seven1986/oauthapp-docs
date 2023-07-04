---
tags:
  - 教程 - 用户 - 脚本库与API
---

# 钉钉 登录

## 步骤一：引入 OAuthApp 库

!!! Tip ""
    **您还需要引入dingtalk.open.js 脚本库**

=== "HTML"
    ```HTML
    <script src="https://g.alicdn.com/dingding/dingtalk-jsapi/2.13.42/dingtalk.open.js"></script>
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    ```

在 HTML 文件的头部，我们首先需要引入 OAuthApp 库。其中 data-appid 属性需要替换为你的 OAuthApp 应用的 ID。


## 步骤二：页面结构
=== "HTML"
    ```HTML
    <button type="button" id="signInButton">登录</button>
    <div id="result"></div>
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.ready().then(function () {
        document.getElementById('signInButton').onclick = function () {
            signIn();
        }
    });

    function signIn() {

        if (dd.env.platform == "notInDingTalk") {
            document.getElementById('result').innerHTML =
                `<b>请用钉钉打开当前网页</b>` +
                `<p>PC地址：<input type="text" value="dingtalk://dingtalkclient/page/link?url=${encodeURIComponent(location.href)}&pc_slide=true" /></p>` +
                `<p>移动端地址：<input type="text" value="${location.href}" /></p>`;
            return;
        }

        var corpId = oauthapp.__appPropValue("DingTalkCorpId");
        if (corpId == '') {
            document.getElementById('result').innerHTML = '请先配置应用的钉钉企业ID';
            return;
        }

        dd.runtime.permission.requestAuthCode({
            corpId: corpId,
            onSuccess: function (result) {
                oauthapp.dingtalkSignIn(result.code).then(function (userinfoRes) {
                    // success
                })
            },
            onFail: function (err) {
                document.getElementById('result').innerHTML = JSON.stringify(err);
            }
        });
    }
    ```

这段代码实现了一个使用钉钉登录的功能。页面上有一个按钮，当用户点击这个按钮时，会触发 signIn() 函数。

在 signIn() 函数中，首先判断当前环境是否是钉钉客户端：

 - 如果不是，则提示用户用钉钉打开当前网页。

 - 如果是钉钉客户端，则通过 dd.runtime.permission.requestAuthCode() 方法获取钉钉用户授权码，然后通过 oauthapp.dingtalkSignIn() 方法将授权码发送到后端服务器进行验证。

如果验证成功，则可以进行相应的业务逻辑处理。如果授权码验证失败，则会将错误信息输出到页面上。

## 步骤四：测试结果

=== "Javascript"
    ```Javascript
    document.getElementById('result').innerHTML = JSON.stringify(userinfoRes);
    ```


## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>dingtalkSignIn</title>
        <script src="https://g.alicdn.com/dingding/dingtalk-jsapi/2.13.42/dingtalk.open.js"></script>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <button type="button" id="signInButton">登录</button>
        <div id="result"></div>
        <script type="text/javascript">
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    signIn();
                }
            });

            function signIn() {

                if (dd.env.platform == "notInDingTalk") {
                    document.getElementById('result').innerHTML =
                        `<b>请用钉钉打开当前网页</b>` +
                        `<p>PC地址：<input type="text" value="dingtalk://dingtalkclient/page/link?url=${encodeURIComponent(location.href)}&pc_slide=true" /></p>` +
                        `<p>移动端地址：<input type="text" value="${location.href}" /></p>`;
                    return;
                }

                var corpId = oauthapp.__appPropValue("DingTalkCorpId");
                if (corpId == '') {
                    document.getElementById('result').innerHTML = '请先配置应用的钉钉企业ID';
                    return;
                }

                dd.runtime.permission.requestAuthCode({
                    corpId: corpId,
                    onSuccess: function (result) {
                        oauthapp.dingtalkSignIn(result.code).then(function (userinfoRes) {
                            document.getElementById('result').innerHTML = JSON.stringify(userinfoRes);
                        })
                    },
                    onFail: function (err) {
                        document.getElementById('result').innerHTML = JSON.stringify(err);
                    }
                });
            }
        </script>
    </body>
    </html>
    ```

