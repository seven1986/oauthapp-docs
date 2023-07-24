---
tags:
  - 文档
---

# 微信

## 小程序

{++在开始前，请确认已成功配置 微信小程序 ++}

### 发送订阅消息

oauthapp.wechatSubscribeSend

用于在微信小程序中向用户发送根据特定模板的消息。

???+ note "提示"
    该方法返回的是一个 Promise 对象，可以使用 .then() 和 .catch() 方法来处理异步操作的结果和错误。[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/subscribe-message/subscribeMessage.send.html)

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatSubscribeSend({
        // 接收者的openid。
      "touser": "OPENID",  
      // 所需下发的模板消息的id。
      "template_id": "TEMPLATE_ID", 
      // 小程序卡片所跳转的页面。
      "page": "index", 
      // 跳转小程序的类型：developer为开发版；trial为体验版；formal为正式版；默认为正式版。
      "miniprogram_state":"developer", 
      "lang":"zh_CN", 
      // 模板数据
      "data": {
          "number01": {
              "value": "339208499"
          },
          "date01": {
              "value": "2015年01月05日"
          },
          "site01": {
              "value": "TIT创意园"
          } ,
          "site02": {
              "value": "广州市新港中路397号"
          }
      }
    }).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatSubscribeSend</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "touser": "OPENID",
                    "template_id": "TEMPLATE_ID",
                    "page": "index",
                    "miniprogram_state": "developer",
                    "lang": "zh_CN",
                    "data": {
                        "number01": {
                            "value": "339208499"
                        },
                        "date01": {
                            "value": "2015年01月05日"
                        },
                        "site01": {
                            "value": "TIT创意园"
                        },
                        "site02": {
                            "value": "广州市新港中路397号"
                        }
                    }
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatSubscribeSend(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatSubscribeSend.html){ .md-button }  [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatsubscribesend.html){ .md-button }
    

### 生成网页跳转地址

oauthapp.wechatUrlLinkGenerate

用于生成微信小程序网页跳转地址，适用于短信、邮件、网页、微信内等拉起小程序的业务场景。

???+ note "提示"
    该方法返回一个包含生成的跳转地址的 Promise 对象。在调用该方法后，你可以通过 .then() 方法获取跳转地址。[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/url-link/urllink.generate.html)


=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatUrlLinkGenerate({
        // 小程序中的页面路径，必填。
        "path": "/pages/publishHomework/publishHomework",
        // 小程序的查询字符串参数，必填。
        "query": "",
        // 二维码有效时间类型，必填。
        "expire_type": 1,
        // 二维码有效时间，单位为秒，必填。
        "expire_interval": 3600,
        // 跳转小程序的类型：developer为开发版；trial为体验版；formal为正式版；默认为正式版。
        "env_version": "release"
    }).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatUrlLinkGenerate</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "path": "/pages/publishHomework/publishHomework",
                    "query": "",
                    "expire_type": 1,
                    "expire_interval": 1,
                    "env_version": "release"
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatUrlLinkGenerate(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatUrlLinkGenerate.html){ .md-button }    [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechaturllinkgenerate.html){ .md-button }

### 生成scheme码

oauthapp.wechatGenerateScheme

用于短信、邮件、外部网页、微信内等拉起小程序的业务场景。

???+ note "提示"
    该方法返回一个包含生成的跳转地址的 Promise 对象。在调用该方法后，你可以通过 .then() 方法获取跳转地址。[官方文档](https://developers.weixin.qq.com/miniprogram/dev/OpenApiDoc/qrcode-link/url-scheme/generateScheme.html)


=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatGenerateScheme({
        "jump_wxa":
        {
            // 小程序中的页面路径，必填。
            "path": "/pages/hot/hot",
            // 小程序的查询字符串参数。
            "query": "",
            // 跳转小程序的类型：developer为开发版；trial为体验版；formal为正式版；默认为正式版。
            "env_version": "release"
        },
        // 默认值false。生成的 scheme 码类型，到期失效：true，30天有效：false。
        "is_expire":false
    }).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatgenerateScheme</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                "jump_wxa":
                {
                    "path": "/pages/hot/hot",
                    "query": "",
                    "env_version": "release"
                },
                "is_expire":false
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatGenerateScheme(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatgenerateScheme.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatgeneratescheme.html){ .md-button }

### 获取小程序码

oauthapp.wechatWXACodeGet

用于获取微信小程序码，即适用于需要的码数量较少的业务场景，通过该接口生成的小程序码，永久有效，有数量限制。

???+ note "提示"
    该方法返回一个 Promise 对象，调用该方法后，如果执行成功，Promise 对象的返回值将是一个 Blob 对象，Blob 对象可以通过 URL.createObjectURL(res) 方法转换成一个 URL 地址，然后可以使用该地址来加载图片。如果执行失败，Promise 对象的返回值将是一个错误对象，需要通过 catch 方法来捕捉错误并进行处理。[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/qr-code/wxacode.get.html)

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatWXACodeGet({
        // 字符串，必填项，小程序页面路径，例如：page/index/index；
        "path": "page/index/index",
        // 字符串，必填项，小程序版本号，可选值为 develop、trial 和 release，默认为 release；
        "env_version": "release",
        // 数字，非必填项，小程序码的宽度，单位 px，取值范围为 280 - 1280，默认为 430。
        "width": 430
    }).then(function(res){
        console.log(URL.createObjectURL(res));
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatWXACodeGet</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "path": "page/index/index",
                    "env_version": "release",
                    "width": 430
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：
            <span id="result"></span>
            <img id="result2" />
        </div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatWXACodeGet(postData).then(function (res) {
                    var url = URL.createObjectURL(res)
                    $('#result').text(url);
                    $('#result2').attr('src', url);
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatWXACodeGet.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatwxacodeget.html){ .md-button }


### 获取小程序码（无限数量）

oauthapp.wechatWXACodeGetUnlimited

用于获取无限制数量的微信小程序码，通过该接口生成的小程序码，永久有效。

???+ note "提示"
    该方法会返回一个 Promise 对象，你可以通过 then() 方法获取小程序码内容的 Blob URL。[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/qr-code/wxacode.getUnlimited.html)

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatWXACodeGetUnlimited({
        // 必填场景值，字符串类型，最大32个字符。
        "scene":"1",
        // 必填小程序中页面的路径。
        "path": "page/index/index",
        // 必填，小程序版本号，可选值为 develop、trial 和 release，默认为 release；
        "env_version": "release",
        // 二维码的宽度，单位 px。默认值为 430。
        "width": 430
    }).then(function(res){
        console.log(URL.createObjectURL(res));
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatWXACodeGet</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "scene":1,
                    "path": "page/index/index",
                    "env_version": "release",
                    "width": 430
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：
            <span id="result"></span>
            <img id="result2" />
        </div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatWXACodeGetUnlimited(postData).then(function (res) {
                    var url = URL.createObjectURL(res)
                    $('#result').text(url);
                    $('#result2').attr('src', url);
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatWXACodeGetUnlimited.html){ .md-button }    [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatwxacodegetunlimited.html){ .md-button }



### 登录凭证校验

oauthapp.wechatJSCode2Session

可以校验用户登录凭证（code）是否正确，并返回用户的唯一标识（openid）和会话密钥（session_key）。

???+ note "提示"
    在微信小程序中，只要有了openid和session_key，就可以获取该用户的所有数据。具体来说，当小程序需要登录时，前端会将用户登录凭证（code）为参数调用oauthapp.wechatJSCode2Session()方法。oauthapp会使用该凭证去请求微信提供的接口，微信会校验该凭证是否正确，并返回用户的openid和session_key。[官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/login/auth.code2Session.html#%E8%AF%B7%E6%B1%82%E5%9C%B0%E5%9D%80)

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatJSCode2Session(js_code).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatJSCode2Session</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="code" placeholder="code" />
            <button type="button" onclick="code2session()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function code2session() {
                var js_code = JSON.parse($('#code').val());
                oauthapp.wechatJSCode2Session(js_code).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatJSCode2Session.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatjscode2session.html){ .md-button }
    

### 解密数据

oauthapp.wechatDecrypt

当开发者在微信小程序中使用了开放数据，如用户信息等，用户数据会经过加密传输到开发者后台。开发者需要对这些数据进行解密才能读取其中的内容。oauthapp.wechatDecrypt 提供了一种简便的方式来进行解密。

???+ note "提示"
    具体来说，oauthapp.wechatDecrypt 方法接收三个参数：加密的数据、加密使用的向量以及 session_key。其中，加密使用的向量和 session_key 都可以在 oauthapp.wechatJSCode2Session 方法中获得。oauthapp.wechatDecrypt 方法返回一个解密后的字符串。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatDecrypt(_encryptedData, _iv, _sessionKey).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
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

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatDecrypt.html){ .md-button }    [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatdecrypt.html){ .md-button }
    

## 公众号H5

!!! Tip ""
    需要先使用oauthapp发布工具，应用>> 应用配置 >> 微信公众平台 菜单下，配置 微信公众号ClientID、微信公众号ClientSecret。

### 获取用户UnionID

oauthapp.wechatUserInfo

用于获取微信公众号用户UnionID的方法。

???+ note "提示"
    该方法需要传入用户的openid，返回该用户在当前微信公众号中的UnionID。获取UnionID需要用户将当前微信公众号绑定到开放平台账号下，并且该用户已经关注公众号。该方法返回一个Promise对象，可以通过then()方法注册回调函数来获取请求结果。[官方文档](https://developers.weixin.qq.com/doc/offiaccount/User_Management/Get_users_basic_information_UnionID.html#UinonId)

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatUserInfo(_openid).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatUserInfo</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="_openid" placeholder="_openid" />
            <button type="button" onclick="getUserInfo()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function getUserInfo() {
                var _openid = $('#_openid').val();
                oauthapp.wechatUserInfo(_openid).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatUserInfo.html){ .md-button }   [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatuserinfo.html){ .md-button }
    

### 发送一次性订阅消息

oauthapp.wechatSubscribeMSG

用于发送微信公众号的一次性订阅消息。

???+ note "提示"
    一次性订阅消息是指，在用户没有关注公众号的前提下，用户通过扫描公众号的带参数二维码或者公众号提供的链接来订阅某一个特定的消息，而这个订阅只会发送一次。一次性订阅消息的内容必须先在微信公众平台上审核通过，才能进行发送。发送一次性订阅消息时，用户必须先同意授权，授权完成后才能发送消息。[官方文档](https://developers.weixin.qq.com/doc/offiaccount/Message_Management/One-time_subscription_info.html)

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatSubscribeMSG({
        // 必填，接收者openid
        "touser": "OPENID",
        // 必填，模板ID
        "template_id": "TEMPLATE_ID",
        // 选填，点击模板消息后跳转的链接
        "url": "URL",
        // 选填，跳转小程序的数据，包括appid和路径
        "miniprogram": {
            "appid": "xiaochengxuappid12345",
            "pagepath": "index?foo=bar"
        },
        //  必填，订阅场景值
        "scene": "SCENE",
        // 选填，消息标题
        "title": "TITLE",
        // 必填，模板消息数据
        "data": {
            "content": {
                "value": "VALUE",
                "color": "COLOR"
            }
        }
    }).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatSubscribeMSG</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <textarea rows="10" placeholder="请求数据" id="postData">
                {
                    "touser": "OPENID",
                    "template_id": "TEMPLATE_ID",
                    "url": "URL",
                    "miniprogram": {
                        "appid": "xiaochengxuappid12345",
                        "pagepath": "index?foo=bar"
                    },
                    "scene": "SCENE",
                    "title": "TITLE",
                    "data": {
                        "content": {
                            "value": "VALUE",
                            "color": "COLOR"
                        }
                    }
                }
            </textarea>
            <button type="button" onclick="sendMsg()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function sendMsg() {
                var postData = JSON.parse($('#postData').val());
                oauthapp.wechatSubscribeMSG(postData).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatSubscribeMSG.html){ .md-button }   [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatsubscribemsg.html){ .md-button }
    

### JS SDK Config

oauthapp.wechatJSConfig

 用于生成微信公众号 JS SDK 的配置参数。

???+ note "提示"
    该方法的参数 _url 是当前页面的 URL 地址，用于微信 JS SDK 鉴权。该方法返回一个 Promise 对象，成功时返回一个包含微信 JS SDK 配置参数的对象，失败时返回一个包含错误信息的对象。通过调用该方法生成的 JS SDK 配置参数，可以在公众号的网页中使用 JS SDK 功能，如获取用户基本信息、分享、支付等。[官方文档](https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#63)

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.wechatJSConfig(_url).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>wechatJSConfig</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="_openid" placeholder="_openid" />
            <button type="button" onclick="getJsConfig()">提交</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            function getJsConfig() {
                var _url = $('#_url').val() || location.href;
                oauthapp.wechatJSConfig(_url).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/wechatJSConfig.html){ .md-button }   [教程](https://docs.oauthapp.com/coding_sdk_wechat_wechatjsconfig.html){ .md-button }