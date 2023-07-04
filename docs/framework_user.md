---
tags:
  - 客户端
---

# 用户

### web指纹

#### 登录

如果账号不存在就自动注册，并返回用户信息。

???+ note "提示"
    该方法通过使用 FingerprintJS2 库生成当前设备的 web 指纹，并通过与 OAuthApp 后台服务器进行匹配来自动完成用户的注册或登录。
    如果用户之前已经在该应用程序中注册过，此方法将自动登录用户并返回用户数据。该方法返回一个 promise 对象，该对象在用户登录成功时解析为用户数据。如果发生错误，则返回拒绝状态。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.signInWithWebIdentity().then(function(appUser){
        // appUser是登录成功后的用户对象
        console.log(appUser);
        // 也可以通过window.oauthapp.appUser获取
        // console.log(oauthapp.appUser);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
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
    [演示](https://web.oauthapp.com/4/examples/apidemo/signInWithWebIdentity.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_signInwithwebidentity/){ .md-button }

### UnionID

UnionID可以是任意平台的用户ID，unionID + platform 必须唯一。

#### 登录

???+ note "提示"
    该方法用于用户已经在第三方平台（例如微信）进行了登录，并且已经获得了该平台的 unionId，此时应用程序需要将该 unionId 提交给 OAuthApp 服务器进行处理。OAuthApp 服务器会检查是否存在与该 unionId 相关联的账户，并返回生成的 access_token，应用程序通过该 access_token 访问 OAuthApp API。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.signIn(unionId,platform).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
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
    [演示](https://web.oauthapp.com/4/examples/apidemo/signin.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_signin/){ .md-button }

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| unionId | 第三方平台的用户ID  | oauthapp.settings.fingerIdentity / 自定义 |
| platform | 第三方平台标识字符串  | web、weibo、wexin、qq / 自定义 |

#### 注册

???+ note "提示"
    该方法将会向 OAuthApp 后台服务器发送注册请求。如果请求成功，服务器将返回一个包含 access_token 的 JSON 对象，可以用于后续的 API 请求。如果注册失败，将会返回相应的错误信息。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.signUp(unionId, platform, password, avatar, nickname, phone, email, username,
        emailIsValid, phoneIsValid).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>signUp</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>unionId</label>
            <input type="text" id="unionId" />
            <label>platform</label>
            <input type="text" id="platform" />
            <label>password</label>
            <input type="text" id="password" />
            <label>avatar</label>
            <input type="text" id="avatar" />
            <button type="button" id="signUpButton">注册</button>
        </div>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signUpButton').onclick = function () {
                    var unionid = $('#unionId').val() || oauthapp.settings.fingerIdentity;
                    var platform = $('#platform').val() || 'web';
                    var password = $('#password').val() || '123456';
                    var avatar = $('#avatar').val() || oauthapp.app.info.logo;
                    oauthapp.signUp(unionid, platform, password, avatar).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/signup.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_accountsignup/){ .md-button }

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| unionId | 第三方平台的用户ID  | oauthapp.settings.fingerIdentity / 自定义 |
| platform | 第三方平台标识字符串  | web、weibo、wexin、qq、dingtalk / 自定义 |
| password | 密码，可空  | 默认为：123456 |
| avatar | 头像，可空  | 注册后可使用文件api上传头像 |
| nickname | 昵称，可空  |  |
| phone | 手机号，可空  |  |
| email | 邮箱，可空  |  |
| username | 登陆账号，可空  |  |
| emailIsValid | 邮箱已验证，可空  | 默认为 false |
| phoneIsValid | 手机已验证，可空  | 默认为 false |


### 账号密码

#### 登录

???+ note "提示"
    使用账号密码登录。它向OAuthApp服务器发送请求，使用传递的用户名和密码进行身份验证，如果验证成功，则返回包含 access_token 和其他用户信息的响应对象，以便后续的 API 调用。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.accountSignIn(userName, password).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>accountsignin</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>account</label>
            <input type="text" id="account" />
            <label>password</label>
            <input type="password" id="password" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <h1>结果</h1>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    oauthapp.accountSignIn(
                        $('#account').val(),
                        $('#password').val()
                    ).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/accountsignin.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_signin/){ .md-button }
    
| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| userName | 登录账号 |  |
| password | 登陆密码 |  |

#### 注册

???+ note "提示"
    该方法会向后台服务器发送请求，在服务器上创建一个新的用户账户，账户创建成功后，会直接返回access_token。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.accountSignUp(userName, password, avatar, nickName, platform).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>accountSignUp</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>userName</label>
            <input type="text" id="userName" />
            <label>password</label>
            <input type="text" id="password" />
            <label>avatar</label>
            <input type="text" id="avatar" />
            <label>nickName</label>
            <input type="text" id="nickName" />
            <label>platform</label>
            <input type="text" id="platform" />
            <button type="button" id="signUpButton">注册</button>
        </div>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signUpButton').onclick = function () {
                    var userName = $('#userName').val() || oauthapp.settings.fingerIdentity;
                    var password = $('#password').val() || '123456';
                    var avatar = $('#avatar').val() || oauthapp.app.info.logo;
                    var nickName = $('#nickName').val() || userName;
                    var platform = $('#platform').val() || 'web';
                    oauthapp.accountSignUp(userName, password, avatar, nickName, platform).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/accountsignup.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_signup/){ .md-button }
    
| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| userName | 登录账号  |  |
| password | 登陆密码  |  |
| avatar | 头像，可空  |  |
| nickName | 昵称，可空  |  |
| platform | 第三方平台标识字符串  | web、weibo、wexin、qq / 自定义 |

### 微信小程序

#### 扫码登录

使用微信小程序扫码登录

???+ note "提示"
    生成一个带有登录授权的二维码，并在HTML页面展示该二维码。
    用户使用微信扫描该二维码后，会跳转到小程序进行授权操作。
    授权成功后，HTML页面通过 **oauthapp.minipSignInResult(signInKey)** 方法查询用户信息和access_token等数据，然后进行相应的处理。
    该方法返回2个参数，signInKey（用于查询登录状态）、qrcode（用img标签展示给用户扫码）。
    **需要先使用发布工具，在应用>>应用配置>>微信小程序 菜单下，配置 微信小程序ClientID、微信小程序ClientSecret。**

=== "API"

    ```JavaScript linenums="1"
    oauthapp.minipSignInQRCode(scopes,remark).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>minipSignInQRCode</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>scopes</label>
            <input type="text" id="scopes" />
            <label>remark</label>
            <input type="text" id="remark" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <p>结果</p>
        <p>
            <b>signInKey：</b>
            <span id="signInKey"></span>
            <img id="signInQRCode" />
        </p>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    var scopes = $('#scopes').val() || 'openid';
                    var remark = $('#remark').val() || navigator.userAgent;

                    oauthapp.minipSignInQRCode(scopes, remark).then(function (res) {
                        $('#signInKey').text(res.signInKey);
                        $('#signInQRCode').attr('src',res.qrcode);
                    });
                }
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/minipSignInQRCode.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_minipsigninqrcode/){ .md-button }
    
| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| scopes | 需要微信小程序用户授权的列表，用英文空格分隔 | openid phone |
| remark | 自定义备注信息 |  |

#### 扫码结果查询

用于获取微信小程序授权登录的结果

???+ note "提示"
    其中signInKey为授权登录时生成的签名密钥。该方法会向服务器发送请求，查询微信小程序授权登录的结果，并返回一个包含登录状态、用户信息和访问令牌的对象。如果授权登录尚未完成，则返回一个空对象。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.minipSignInResult(signInKey).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>minipSignInResult</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>signInKey</label>
            <input type="text" id="signInKey" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    var signInKey = $('#signInKey').val();
                    oauthapp.minipSignInResult(signInKey).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/minipSignInResult.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_minipsigninresult/){ .md-button }
    
| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| signInKey | 小程序登录查询凭证 |  |

### 钉钉

#### 登录

使用钉钉自动注册+登录。

???+ note "提示"
    该方法用于用户已经在钉钉平台进行了登录，并且已经获得了auth code，此时应用程序需要将该 code 提交给 OAuthApp 服务器进行处理。OAuthApp 服务器会检查是否存在与该 code 相关联的账户，并返回生成的 access_token，应用程序通过该 access_token 访问 OAuthApp API。

      钉钉应用需申请如下权限：

     - 成员信息读权限（qyapi_get_member）  
     - 个人手机号信息（Contact.User.mobile）
     - 邮箱等个人信息（fieldEmail）
     - 钉钉应用需配置IP白名单、PC/移动端的网页地址

      发布工具需要，在应用>>应用配置>>顶顶应用 菜单下，配置：
      
      - 应用ClientID
      - 应用ClientSecret
      - 企业ID。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.dingtalkSignIn(code).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
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
    [演示](https://web.oauthapp.com/4/examples/apidemo/dingtalkSignIn.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_dingtalksignin/){ .md-button }


### access_token 登录

直接使用access_token登录并获取用户资料。

???+ note "提示"
    使用传入的 Access Token 直接在后台服务器上进行验证和登录，并返回相应的用户信息。具体功能包括：

    - 使用传入的 Access Token 在后台服务器上进行验证和登录。
    
    - 如果验证成功，则返回相应的用户信息。
    
    - 如果验证失败，则返回相应的错误信息

=== "API"

    ```JavaScript linenums="1"
    oauthapp.accesstokenSignIn(_access_token, _expires_in).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>accesstokenSignIn</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <label>access_token</label>
            <input type="text" id="access_token" />
            <label>expires_in</label>
            <input type="number" id="expires_in" value="7200" />
            <button type="button" id="signInButton">登录</button>
        </div>
        <h1>结果</h1>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                document.getElementById('signInButton').onclick = function () {
                    oauthapp.accesstokenSignIn(
                        $('#access_token').val(),
                       parseInt($('#expires_in').val())
                    ).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/accesstokenSignIn.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_accesstokensignIn/){ .md-button }

    
| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| _access_token | 用户令牌 |  |
| _expires_in | 令牌有效时间，单位：秒 |  |



### 统一登录(单点登录)

使用统一的UI登录，用户登录后会回传accesstoken到回调地址。 可使用[配置工具](https://web.oauthapp.com/4/examples/signin_authorize.html)生成登录链接。

???+ note "提示"
    用户点击单点登录链接，跳转到OAuthApp的授权页面。
    用户在授权页面上输入用户账号和密码，授权页面验证身份后会展示需要授权的权限列表。
    当用户授权成功后，单点登录会将访问令牌（access token）重定向到预设的回调地址（redirect_uri）上，并将其作为参数传递给回调地址。
    在回调地址中，可以通过解析 URL 参数来获取访问令牌，然后调用 **accesstokenSignIn** 方法登录或进行后续操作。

    > OAuthApp单点登录功能是指在OAuthApp应用中，用户只需要在其中一个应用中进行登录，即可将授权的访问令牌（access_token）传入到其他应用中，进行自动登录，无需再次输入账号和密码。


基于token的单点登录的实现步骤如下：



=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>统一登陆</title>
    </head>
    <body>
        <a href="https://www.oauthapp.com/oauth/2?scheme=app&redirect_uri=https://web.oauthapp.com/4/examples/apidemo/sso.html&scopes=openid profile role&nonce=1667553723079">
            登录
        </a>
        <h1>结果</h1>
        <div id="result"></div>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/sso.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_sso/){ .md-button }

    
| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| {{scheme}} | 登录协议(必填) | 固定为 "app" |
| {{appId}} | 应用ID(必填) |  |
| {{scopes}} | 授权列表(必填) | 多个权限用英文空格分隔 |
| {{redirect_uri}} | 回调地址(必填) |  |
| {{redirect_uri_name}} | 自定义授权标题 |  |
| {{nonce}} | 自定义字符串，32位(必填) |  |
| {{expireInDays}} | 令牌有效期(非必填，单位：天，取值：1~99) |  |



### 获取个人信息

登录成功后，调用该api获取到用户信息。

???+ note "提示"
    用于获取当前登录用户的个人信息，包括用户 ID、昵称、头像等。该方法会返回一个 Promise 对象，调用该方法后需要通过 .then() 方法获取返回的用户信息。

    其中，userInfo 包含以下信息：
    
    - appID：授权应用的ID号
    - platform：授权应用的平台
    - unionID：授权应用内的用户唯一标识符
    - phone：用户绑定的电话号码
    - createDate：用户账户创建时间
    - userName：用户账户的用户名
    - phoneIsValid：用户电话号码是否验证
    - data：自定义数据字段
    - email：用户绑定的电子邮件地址
    - emailIsValid：用户电子邮件地址是否验证
    - lastUpdate：用户账户最近一次更新时间
    - nickName：用户昵称
    - id：用户账户ID号
    - avatar：用户头像
    - role：用户角色
    
    注意，调用该方法前需要确保用户已经完成登录并获取到了访问令牌。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.profile().then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>profile</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.profile().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                });
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/profile.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_profile/){ .md-button }
    
### 更新个人信息

必须登录以后才能更新用户信息，可更新头像、昵称、自定义json数据3个字段。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.profilePut(avatar,nickName,jsonData).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>profilePut</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <div id="userProfile"></div>
            <p>
                昵称
                <input type="text" id="nickName" />
            </p>
            <p>
                头像
                <img id="userAvatar" width="64px" />
                <button type="button" class="btn btn-link" onclick="uploadImage()">上传头像</button>
            </p>
            <div>

                <textarea id="data" rows="10" placeholder=" 自定义数据"></textarea>
            </div>
            <div>
                <button type="button" onclick="updateProfile()">更新用户资料</button>
            </div>
        </div>
        <script type="text/javascript">
            oauthapp.allReady().then(function () {
                $('#userProfile').html(`
                <p>ID： ${oauthapp.appUser.id}<br />
                账号：${oauthapp.appUser.userName}<br />
                邮箱：${oauthapp.appUser.email}, ${oauthapp.appUser.emailIsValid ? '已验证' : ''}<br />
                手机：${oauthapp.appUser.phone}, ${oauthapp.appUser.phoneIsValid ? '已验证' : ''}<br />
                来源：${oauthapp.appUser.platform}<br />
                unionID：${oauthapp.appUser.unionID}<br />
                角色：${oauthapp.appUser.role}<br />
                加入时间：${oauthapp.appUser.createDate}<br />
                最后更新：${oauthapp.appUser.lastUpdate}</p>`);
                $('#data').val(oauthapp.appUser.data);
                $('#nickName').val(oauthapp.appUser.nickName);
                $('#userAvatar').attr('src', oauthapp.appUser.avatar);
            })

            function uploadImage() {
                var ele = document.createElement('input');
                ele.type = 'file';
                ele.onchange = function (_event) {
                    oauthapp.upload(event.target.files[0]).then(function (res) {
                        oauthapp.appUser.avatar = JSON.parse(res).data;
                        $('#userAvatar').attr('src', oauthapp.appUser.avatar);
                    });
                };
                ele.click();
            }

            function updateProfile() {
                var nickName = document.getElementById('nickName').value;
                var data = document.getElementById('data').value;
                oauthapp.profilePut(oauthapp.appUser.avatar, nickName, data).then(function (res) {
                    alert(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/profilePut.html){ .md-button }
    [教程](https://docs.oauthapp.com/code_sdk_user_profileput/){ .md-button }
    

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| avatar | 头像  |  |
| nickName | 昵称  |  |
| jsonData | 自定义json对象  |  |



### 积分记录

???+ note "提示"
    获取当前登录用户的积分变更记录。

=== "API"

    ```JavaScript linenums="1"
    /**
     * 积分记录
     * @params type 分类 | 0：全部，1：充值，2：消耗
     * @params skip 跳过条数
     * @params take 拉取条数
    */
    oauthapp.pointLogs(type,skip,take).then(function(res){
      console.log(res);
      /**
        {
          "code": 200,
          "data": {
            "total": 2,
            "data": [
              {
                "id": 2,
                "userID": 84,
                "used": 10000,
                "remark": "",
                "createDate": "2023-06-16 15:35:06"
              },
              {
                "id": 1,
                "userID": 84,
                "used": 10000,
                "remark": "",
                "createDate": "2023-06-16 15:23:50"
              }
            ]
          },
          "err": ""
        }
       * 
      */
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>order</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    
    <body>
        <select id="type">
            <option value="0">全部</option>
            <option value="1">充值</option>
            <option value="2">消耗</option>
        </select>
        <input type="text" id="skip" value="0" />
        <input type="text" id="take" value="10" />
    
        <button type="button" id="actionButton">查询</button>
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('actionButton').onclick = function () {
                    var type = $('#type').val() || 0;
                    var skip = $('#skip').val() || 0;
                    var take = $('#take').val() || 10;
    
                    oauthapp.pointLogs(type, skip, take).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                };
            });
        </script>
    </body>
    </html>
    ```

    [演示](https://web.oauthapp.com/4/examples/apidemo/pointlogs.html){ .md-button }
    [教程](http://docs.oauthapp.com/coding_sdk_pointlogs/){ .md-button }

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| type | 分类 | 0：全部，1：充值，2：消耗 |
| skip |  可选，指定要拉取的数据条数。 | 0 |
| take |  可选，指定要跳过的数据条数。 | 10 |
