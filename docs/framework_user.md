---
tags:
  - 文档
---

# 用户

### web指纹

#### 登录

oauthapp.signInWithWebIdentity

如果账号不存在就自动注册，并返回用户信息。

???+ note "提示"
    该方法通过使用 FingerprintJS2 库生成当前设备的 web 指纹，并通过与 OAuthApp 后台服务器进行匹配来自动完成用户的注册或登录。
    如果用户之前已经在该应用程序中注册过，此方法将自动登录用户并返回用户数据。该方法返回一个 promise 对象，该对象在用户登录成功时解析为用户数据。如果发生错误，则返回拒绝状态。



=== "方法"

    ```JavaScript linenums="1"
    oauthapp.signInWithWebIdentity().then(function(appUser){
        // appUser是登录成功后的用户对象
        console.log(appUser);
        // 也可以通过window.oauthapp.appUser获取
        // console.log(oauthapp.appUser);
    });
    ```

=== "示例"

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

[演示](https://web.oauthapp.com/4/examples/apidemo/signInWithWebIdentity.html){ .md-button }    [教程](https://docs.oauthapp.com/code_sdk_user_signInwithwebidentity.html){ .md-button }

### UnionID

UnionID可以是任意平台的用户ID，unionID + platform 必须唯一。

#### 登录

oauthapp.unionIDSignIn

???+ note "提示"
    该方法用于用户已经在第三方平台（例如微信）进行了登录，并且已经获得了该平台的 unionId，此时应用程序需要将该 unionId 提交给 OAuthApp 服务器进行处理。OAuthApp 服务器会检查是否存在与该 unionId 相关联的账户，并返回生成的 access_token，应用程序通过该 access_token 访问 OAuthApp API。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.unionIDSignIn(unionId,platform).then(function(res){
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
        <title>UnionID登录</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>UnionID登录</h3>
            <p>unionId：<input type="text" id="unionId" /></p>
            <p>platform：<input type="text" id="platform" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var unionid = $('#unionId').val() || oauthapp.settings.fingerIdentity;
                    var platform = $('#platform').val() || 'web';
                    oauthapp.unionIDSignIn(unionid, platform).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | unionId | 第三方平台的用户ID  | oauthapp. settings.fingerIdentity / 自定义 |
    | platform | 第三方平台标识字符串  | web、weibo、wexin、qq / 自定义 |

[演示](https://web.oauthapp.com/4/examples/apidemo/unionIDSignIn.html){ .md-button }   [教程](https://docs.oauthapp.com/code_sdk_user_unionidsignin.html){ .md-button }



#### 注册

oauthapp.unionIDSignUp

???+ note "提示"
    该方法将会向 OAuthApp 后台服务器发送注册请求。如果请求成功，服务器将返回一个包含 access_token 的 JSON 对象，可以用于后续的 API 请求。如果注册失败，将会返回相应的错误信息。

=== "方法"

    ```JavaScript linenums="1"
    /**
     * data 属性：
    {
        "unionID": "string",
        "platform": "string",
        "pwd": "yc6EJ}v~tTzl!J@NQ@9Rl|}JX",
        "nickName": "string",
        "avatar": "string",
        "data": "string",
        "email": "user@example.com",
        "emailCode": "",
        "phone": "",
        "phoneCode": ""
    }
    */
    oauthapp.unionIDSignUp(data).then(function(res){
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
        <title>UnionID注册</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>UnionID注册</h3>
            <p>unionId：<input type="text" id="unionId" /></p>
            <p>platform：<input type="text" id="platform" /></p>
            <p>password：<input type="text" id="password" /></p>
            <p>nickName：<input type="text" id="nickName" /></p>
            <p>avatar：<input type="text" id="avatar" /></p>
            <p>data：<input type="text" id="data" /></p>
            <p>email：<input type="text" id="email" /></p>
            <p>emailCode：<input type="text" id="emailCode" /></p>
            <p>phone：<input type="text" id="phone" /></p>
            <p>phoneCode：<input type="text" id="phoneCode" /></p>
            <button type="button" id="actionButton">提交</button>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {

                    var data = {
                        "unionID":  $('#unionId').val() || oauthapp.settings.fingerIdentity,
                        "platform": $('#platform').val() || 'web',
                        "pwd": $('#password').val() || '123456',
                        "nickName":$('#nickName').val() || '',
                        "avatar": $('#avatar').val() || oauthapp.app.info.logo,
                        "data": $('#data').val() || '',
                        "email": $('#email').val() || '',
                        "emailCode": $('#emailCode').val() || '',
                        "phone": $('#phone').val() || '',
                        "phoneCode": $('#phoneCode').val() || ''
                    };

                    oauthapp.unionIDSignUp(data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                })
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | unionId | 第三方平台的用户ID  | oauthapp.settings.fingerIdentity / 自定义 |
    | platform | 第三方平台标识字符串  | web、weibo、wexin、qq、dingtalk / 自定义 |
    | pwd | 密码，可空  | 默认为：123456 |
    | nickname | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |
    | phone | 手机号，可空  | 如果应用配置了验证手机，则必填 |
    | phoneCode | 手机验证码，可空  | 如果应用配置了验证手机，则必填 |
    | email | 邮箱，可空  | 如果应用配置了验证邮箱，则必填 |
    | emailCode | 邮箱已验证，可空  | 如果应用配置了验证邮箱，则必填 |


[演示](https://web.oauthapp.com/4/examples/apidemo/unionIDSignUp.html){ .md-button }   [教程](https://docs.oauthapp.com/code_sdk_user_inionidsignup.html){ .md-button }


### 账号密码

#### 登录

oauthapp.accountSignIn

???+ note "提示"
    使用账号密码登录。它向OAuthApp服务器发送请求，使用传递的用户名和密码进行身份验证，如果验证成功，则返回包含 access_token 和其他用户信息的响应对象，以便后续的 API 调用。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.accountSignIn(userName, password).then(function(res){
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | userName | 登录账号 |  |
    | password | 登陆密码 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/accountsignin.html){ .md-button }    [教程](https://docs.oauthapp.com/code_sdk_user_signin.html){ .md-button }


#### 注册

oauthapp.accountSignUp

???+ note "提示"
    该方法会向后台服务器发送请求，在服务器上创建一个新的用户账户，账户创建成功后，会直接返回access_token。

=== "方法"

    ```JavaScript linenums="1"
    /**
    * data 属性：
    {
      "userName": "uM@J5",
      "pwd": "6E7U3CESUFTCQF4SfDcN|{CO3Ea~3WG",
      "nickName": "string",
      "avatar": "string",
      "data": "string",
      "email": "user@example.com",
      "emailCode": "",
      "phone": "",
      "phoneCode": ""
    }
    */
    oauthapp.accountSignUp(data).then(function(res){
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | userName | 登录账号  |  |
    | pwd | 登陆密码  |  |
    | nickName | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |
    | phone | 手机号，可空  | 如果应用配置了验证手机，则必填 |
    | phoneCode | 手机验证码，可空  | 如果应用配置了验证手机，则必填 |
    | email | 邮箱，可空  | 如果应用配置了验证邮箱，则必填 |
    | emailCode | 邮箱已验证，可空  | 如果应用配置了验证邮箱，则必填 |

[演示](https://web.oauthapp.com/4/examples/apidemo/accountsignup.html){ .md-button }    [教程](https://docs.oauthapp.com/code_sdk_user_signup.html){ .md-button }


### 手机号

#### 注册

oauthapp.phoneSignUp

=== "方法"

    ```JavaScript linenums="1"
    /**
     * data 参数如下：
    {
        "phone": "",
        "phoneCode": "",
        "pwd": "hXeqUI3$gUKV",
        "email": "user@example.com",
        "emailCode": "",
        "nickName": "string",
        "avatar": "string",
        "data": "string"
    }
    */
    oauthapp.phoneSignUp(data).then(function(res){
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
        <title>手机号注册</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>手机号注册</h3>
            <p>phone：<input type="text" id="phone" /></p>
            <p>phoneCode：<input type="text" id="phoneCode" /></p>
            <p>password：<input type="text" id="password" /></p>
            <p>email：<input type="text" id="email" /></p>
            <p>emailCode：<input type="text" id="emailCode" /></p>
            <p>nickName：<input type="text" id="nickName" /></p>
            <p>avatar：<input type="text" id="avatar" /></p>
            <p>data：<input type="text" id="data" /></p>
            <button type="button" id="actionButton">提交</button>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {

                    var data = {
                        "phone": $('#phone').val() || '',
                        "phoneCode": $('#phoneCode').val() || '',
                        "pwd": $('#password').val() || '123456',
                        "email": $('#email').val() || '',
                        "emailCode": $('#emailCode').val() || '',
                        "nickName": $('#nickName').val() || '',
                        "avatar": $('#avatar').val() || oauthapp.app.info.logo,
                        "data": $('#data').val() || ''
                    };

                    oauthapp.phoneSignUp(data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                })
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | phone | 手机号，必填 |  |
    | phoneCode | 手机验证码，必填 | 调用发送手机验证码方法获取 |
    | pwd | 密码，可空  | 默认为：123456 |
    | email | 邮箱，可空  | 如果应用配置了验证邮箱，则必填 |
    | emailCode | 邮箱已验证，可空  | 如果应用配置了验证邮箱，则必填 |
    | nickname | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/phoneSignUp.html){ .md-button }    
<!-- [教程](){ .md-button } -->


#### 登录

oauthapp.phoneSignIn

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.phoneSignIn(phone,phoneCode).then(function(res){
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
        <title>手机号登录</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>手机号登录</h3>
            <p>phone：<input type="text" id="phone" /></p>
            <p>phoneCode：<input type="text" id="phoneCode" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var phone = $('#phone').val();
                    var phoneCode = $('#phoneCode').val();
                    oauthapp.phoneSignIn(phone, phoneCode).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | phone | 手机号，必填 |  |
    | phoneCode | 手机验证码，必填 | 调用发送手机验证码方法获取 |

[演示](https://web.oauthapp.com/4/examples/apidemo/phoneSignIn.html){ .md-button }    
<!-- [教程](){ .md-button } -->



#### 找回密码

oauthapp.resetPwd

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 参数如下：
    {
        "phone": "string",
        "code": "1344",
        "pwd": "]\\vUbfK6T|1Mp"
    }
    */
    oauthapp.resetPwd(data).then(function(res){
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
        <title>根据手机号找回密码</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>根据手机号找回密码</h3>
            <p>phone：<input type="text" id="phone" /></p>
            <p>phoneCode：<input type="text" id="phoneCode" /></p>
            <p>pwd：<input type="text" id="pwd" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var data = {
                        "phone": $('#phone').val(),
                        "code": $('#phoneCode').val(),
                        "pwd": $('#pwd').val()
                    }
                    oauthapp.resetPwd(data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | phone | 手机号，必填 |  |
    | code | 手机验证码，必填 | 调用发送手机验证码方法获取 |
    | pwd | 新的密码，必填 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/resetPwdByPhone.html){ .md-button }    
<!-- [教程](){ .md-button } -->


#### 发送验证码

oauthapp.sendSMSCode

=== "方法"

    ```JavaScript linenums="1"
    /**
     * data参数如下： 
    {
       "phone": "string",
       "type": "string"
    }
    */
    oauthapp.sendSMSCode(data).then(function(res){
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
        <title>发送手机验证码</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>发送手机验证码</h3>
            <p>phone：<input type="text" id="phone" /></p>
            <p>type：<select id="type">
                    <option value="signup">注册</option>
                    <option value="forgetpwd">找回密码</option>
                </select></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var data = {
                        "phone": $('#phone').val(),
                        "type": $('#type').val()
                    }
                    oauthapp.sendSMSCode(data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | phone | 手机号，必填 |  |
    | type | 用途，必填 | 可选值：signup / forgetpwd |

[演示](https://web.oauthapp.com/4/examples/apidemo/sendSMSCode.html){ .md-button }    
<!-- [教程](){ .md-button } -->


### 邮箱账号

#### 注册

oauthapp.emailSignUp

=== "方法"

    ```JavaScript linenums="1"
    /**
     * data参数如下：
     * {
          "email": "user@example.com",
          "pwd": "897V5rFabJ3&!#",
          "emailCode": "16509",
          "phone": "49735952361",
          "phoneCode": "50840290",
          "nickName": "string",
          "avatar": "string",
          "data": "string"
        }
    */
    oauthapp.emailSignUp(data).then(function(res){
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
        <title>使用邮箱注册</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>使用邮箱注册</h3>
            <p>email：<input type="text" id="email" /></p>
            <p>emailCode：<input type="text" id="emailCode" /></p>
            <p>phone：<input type="text" id="phone" /></p>
            <p>phoneCode：<input type="text" id="phoneCode" /></p>
            <p>password：<input type="text" id="password" /></p>
            <p>nickName：<input type="text" id="nickName" /></p>
            <p>avatar：<input type="text" id="avatar" /></p>
            <p>data：<input type="text" id="data" /></p>
            <button type="button" id="actionButton">提交</button>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var data = {
                        "email": $('#email').val() || '',
                        "emailCode": $('#emailCode').val() || '',
                        "phone": $('#phone').val() || '',
                        "phoneCode": $('#phoneCode').val() || '',
                        "pwd": $('#password').val() || '123456',
                        "nickName": $('#nickName').val() || '',
                        "avatar": $('#avatar').val() || oauthapp.app.info.logo,
                        "data": $('#data').val() || ''
                    };
                    oauthapp.emailSignUp(data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    }).catch(err=>{
                        $('#result').text(err.responseText);
                    });
                })
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | email | 邮箱，必填  |  |
    | emailCode | 邮箱已验证，必填  | 调用发送邮箱验证码方法获取 |
    | pwd | 密码，可空  | 默认为：123456 |
    | nickname | 昵称，可空  |  |
    | avatar | 头像，可空  |  |
    | data | 自定义数据，可空  |  |
    | phone | 手机号，可空  | 如果应用配置了验证手机，则必填 |
    | phoneCode | 手机验证码，可空  | 如果应用配置了验证手机，则必填 |

[演示](https://web.oauthapp.com/4/examples/apidemo/emailSignUp.html){ .md-button }    
<!-- [教程](){ .md-button } -->



#### 登录

oauthapp.emailSignIn

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.emailSignIn(email,emailCode).then(function(res){
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
        <title>使用邮箱登录</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>使用邮箱登录</h3>
            <p>email：<input type="text" id="email" /></p>
            <p>emailCode：<input type="text" id="emailCode" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var email = $('#email').val();
                    var emailCode = $('#emailCode').val();
                    oauthapp.emailSignIn(email, emailCode).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | email | 邮箱，必填 |  |
    | emailCode | 邮箱验证码，必填 | 调用发送邮箱验证码方法获取 |

[演示](https://web.oauthapp.com/4/examples/apidemo/emailSignIn.html){ .md-button }    
<!-- [教程](){ .md-button } -->



#### 找回密码

oauthapp.resetPwd

=== "方法"

    ```JavaScript linenums="1"
    /**
     * 参数如下：
    {
        "email": "user@example.com",
        "code": "1344",
        "pwd": "]\\vUbfK6T|1Mp"
    }
    */
    oauthapp.resetPwd(data).then(function(res){
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
        <title>根据邮箱账号找回密码</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>根据邮箱账号找回密码</h3>
            <p>email：<input type="text" id="email" /></p>
            <p>emailCode：<input type="text" id="emailCode" /></p>
            <p>pwd：<input type="text" id="pwd" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var data = {
                        "email": $('#email').val(),
                        "code": $('#emailCode').val(),
                        "pwd": $('#pwd').val()
                    }
                    oauthapp.resetPwd(data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | email | 邮箱账号，必填 |  |
    | code | 邮箱收到的验证码，必填 | 调用发送邮箱验证码方法获取 |
    | pwd | 新的密码，必填 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/resetPwdByEmail.html){ .md-button }
<!-- [教程](){ .md-button } -->


#### 发送验证码

oauthapp.sendEmailCode

=== "方法"

    ```JavaScript linenums="1"
    /**
     * data参数如下： 
        {
           "email": "string",
           "type": "string"
        }
    */
    oauthapp.sendEmailCode(data).then(function(res){
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
        <title>发送邮箱证码</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>发送邮箱证码</h3>
            <p>email：<input type="text" id="email" /></p>
            <p>type：<select id="type">
                    <option value="signup">注册</option>
                    <option value="forgetpwd">找回密码</option>
                </select></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var data = {
                        "email": $('#email').val(),
                        "type": $('#type').val()
                    }
                    oauthapp.sendEmailCode(data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | email | 邮箱，必填 |  |
    | type | 用途，必填 | 可选值：signup / forgetpwd |

[演示](https://web.oauthapp.com/4/examples/apidemo/sendEmailCode.html){ .md-button }
<!-- [教程](){ .md-button } -->

### 微信小程序

#### 扫码登录

oauthapp.minipSignInQRCode

使用微信小程序扫码登录

???+ note "提示"
    生成一个带有登录授权的二维码，并在HTML页面展示该二维码。
    用户使用微信扫描该二维码后，会跳转到小程序进行授权操作。
    授权成功后，HTML页面通过 **oauthapp.minipSignInResult(signInKey)** 方法查询用户信息和access_token等数据，然后进行相应的处理。
    该方法返回2个参数，signInKey（用于查询登录状态）、qrcode（用img标签展示给用户扫码）。
    **需要先使用发布工具，在应用>>应用配置>>微信小程序 菜单下，配置 微信小程序ClientID、微信小程序ClientSecret。**

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.minipSignInQRCode(scopes,remark).then(function(res){
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | scopes | 需要微信小程序用户授权的列表，用英文空格分隔 | openid phone |
    | remark | 自定义备注信息 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/minipSignInQRCode.html){ .md-button }    [教程](https://docs.oauthapp.com/code_sdk_user_minipsigninqrcode.html){ .md-button }
    

#### 扫码结果查询

oauthapp.minipSignInResult

用于获取微信小程序授权登录的结果

???+ note "提示"
    其中signInKey为授权登录时生成的签名密钥。该方法会向服务器发送请求，查询微信小程序授权登录的结果，并返回一个包含登录状态、用户信息和访问令牌的对象。如果授权登录尚未完成，则返回一个空对象。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.minipSignInResult(signInKey).then(function(res){
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | signInKey | 小程序登录查询凭证 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/minipSignInResult.html){ .md-button }    [教程](https://docs.oauthapp.com/code_sdk_user_minipsigninresult.html){ .md-button }


#### 确认扫码与注册

**以下操作需要在小程序端进行操作**

- 1，当小程序页面解析到了signInKey，需调用[小程序端确认扫码](https://docs.oauthapp.com/api_user.html#_11)，获取请求用户授权的应用信息，并展示出来。

- 2，当用户同意授权后，继续调用[小程序注册](https://docs.oauthapp.com/api_user.html#_12)，完成注册账号。


### 钉钉

#### 登录

oauthapp.dingtalkSignIn

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

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.dingtalkSignIn(code).then(function(res){
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

[演示](https://web.oauthapp.com/4/examples/apidemo/dingtalkSignIn.html){ .md-button }   [教程](https://docs.oauthapp.com/code_sdk_user_dingtalksignin.html){ .md-button }


### access_token 登录

oauthapp.accesstokenSignIn

直接使用access_token登录并获取用户资料。

???+ note "提示"
    使用传入的 Access Token 直接在后台服务器上进行验证和登录，并返回相应的用户信息。具体功能包括：

    - 使用传入的 Access Token 在后台服务器上进行验证和登录。
    
    - 如果验证成功，则返回相应的用户信息。
    
    - 如果验证失败，则返回相应的错误信息

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.accesstokenSignIn(_access_token, _expires_in).then(function(res){
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | _access_token | 用户令牌 |  |
    | _expires_in | 令牌有效时间，单位：秒 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/accesstokenSignIn.html){ .md-button }    [教程](https://docs.oauthapp.com/code_sdk_user_accesstokensignIn.html){ .md-button }


### OAuthApp统一登录

使用统一的UI登录，用户登录后会回传accesstoken到回调地址。 可使用[配置工具](https://web.oauthapp.com/4/examples/signin_authorize.html)生成登录链接。

???+ note "提示"
    用户点击单点登录链接，跳转到OAuthApp的授权页面。
    用户在授权页面上输入用户账号和密码，授权页面验证身份后会展示需要授权的权限列表。
    当用户授权成功后，单点登录会将访问令牌（access token）重定向到预设的回调地址（redirect_uri）上，并将其作为参数传递给回调地址。
    在回调地址中，可以通过解析 URL 参数来获取访问令牌，然后调用 **access_token 登录** 登录或进行后续操作。

=== "示例"

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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | {{scheme}} | 登录协议(必填) | 固定为 "app" |
    | {{appId}} | 应用ID(必填) |  |
    | {{scopes}} | 授权列表(必填) | 多个权限用英文空格分隔 |
    | {{redirect_uri}} | 回调地址(必填) |  |
    | {{redirect_uri_name}} | 自定义授权标题 |  |
    | {{nonce}} | 自定义字符串，32位(必填) |  |
    | {{expireInDays}} | 令牌有效期(非必填，单位：天，取值：1~99) |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/sso.html){ .md-button }  [教程](https://docs.oauthapp.com/code_sdk_user_sso.html){ .md-button }


### 获取用户资料

oauthapp.profile

用于获取当前登录用户的个人信息，包括用户 ID、昵称、头像等信息。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.profile().then(function(res){
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

=== "返回数据"

    | 参数  | 说明 |
    | ----------- | ----------- |
    | appID | 授权应用的ID号 |
    | id | 账户ID |
    | userName | 用户名 |
    | nickName | 用户昵称 |
    | avatar | 用户头像 |
    | role | 用户角色 |
    | unionID | UnionID |
    | platform | UnionID关联的平台 |
    | phone | 电话号码 |
    | phoneIsValid | 电话号是否验证 |
    | email | 电子邮件地址 |
    | emailIsValid | 邮件地址是否验证 |
    | data | 自定义数据 |
    | lastUpdate | 最近一次更新时间 |
    | createDate | 用户账户创建时间 |

[演示](https://web.oauthapp.com/4/examples/apidemo/profile.html){ .md-button }  [教程](https://docs.oauthapp.com/code_sdk_user_profile.html){ .md-button }


### 更新用户资料

oauthapp.profilePut

必须登录以后才能更新用户信息，可更新头像、昵称、自定义json数据3个字段。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.profilePut(avatar,nickName,jsonData).then(function(res){
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | avatar | 头像  |  |
    | nickName | 昵称  |  |
    | jsonData | 自定义json对象  |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/profilePut.html){ .md-button }   [教程](https://docs.oauthapp.com/code_sdk_user_profileput.html){ .md-button }


### 开放认证

#### 申请授权码

oauthapp.oauthGrantCode

=== "方法"

    ```JavaScript linenums="1"
    /**
     * scheme 固定为：app
     * data 参数如下：
     * {
        "redirect_uri": "string",
        "grant_type": "email",
        "scopes": "string",
        "userName": "string",
        "password": "string",
        "unionId": "string",
        "platform": "string",
        "expireInDays": 99
        }
    */
    oauthapp.oauthGrantCode(scheme,data).then(function(res){
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
        <title>申请授权码</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>申请授权码</h3>
            <p>redirect_uri：<input type="text" id="redirect_uri" /></p>
            <p>expireInDays：<input type="number" min="1" max="99" value="1" id="expireInDays" /></p>
            <p>scopes：<input type="text" id="scopes" /></p>
            <p><select id="grant_type" onchange="toggleIdentityDiv(this.value)">
                    <option>email</option>
                    <option>phone</option>
                    <option>unionid</option>
                    <option>account</option>
                </select></p>
            <div id="identity1">
                <p>userName：<input type="text" id="userName" /></p>
                <p>password：<input type="text" id="password" /></p>
            </div>
            <div id="identity2" style="display: none;">
                <p>unionId：<input type="text" id="unionId" /></p>
                <p>platform：<input type="text" id="platform" /></p>
            </div>
            <button type="button" id="actionButton">提交</button>
        </div>
        <div id="result"></div>
        <script>
            function toggleIdentityDiv(val) {
                console.log(val)
                if (val == 'unionid') {
                    $('#identity1').hide();
                    $('#identity2').show();
                }
                else {
                    $('#identity2').hide();
                    $('#identity1').show();
                }
            }
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var data = {
                        "redirect_uri": $('#redirect_uri').val(),
                        "grant_type": $('#grant_type').val(),
                        "scopes": $('#scopes').val(),
                        "userName": $('#userName').val(),
                        "password": $('#password').val(),
                        "unionId": $('#unionId').val(),
                        "platform": $('#platform').val(),
                        "expireInDays": $('#expireInDays').val()
                    };
                    oauthapp.oauthGrantCode('app', data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    }).catch(err => {
                        $('#result').text(err.responseText);
                    });
                })
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | scheme | 身份验证协议 | 固定填：app |
    | data参数如下 |  |  |
    | redirect_uri | 返回地址，必填 | 默认无限制，也可在【安全-开放认证网址白名单】配置 |
    | grant_type | 授权类型，必填 | 可选：email、phone、unionid、account |
    | scopes | 自定义授权范围，必填 | 用英文空格分隔 |
    | userName |  用户名 | 授权类型为：email/phone/account必填 |
    | password | 登录密码 | 授权类型为：email/phone/account必填 |
    | unionId | unionId | 授权类型为：unionid必填 |
    | platform | 平台 | 授权类型为：unionid必填 |
    | expireInDays | 授权有效期（天） | 默认为1，取值范围：1~99 |

[演示](https://web.oauthapp.com/4/examples/apidemo/oauthGrantCode.html){ .md-button }    
<!-- [教程](){ .md-button } -->

#### 获取access_token

oauthapp.oauthAuthorize

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.oauthAuthorize(scheme,code).then(function(res){
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
        <title>使用授权码获取access_token</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>使用授权码获取access_token</h3>
            <p>code:<input type="text" id="code" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var code = $('#code').val();
                    oauthapp.oauthAuthorize('app', code).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    }).catch(err => {
                        $('#result').text(err.responseText);
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | scheme | 身份验证协议 | 固定填：app |
    | code | 授权码 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/oauthAuthorize.html){ .md-button }    
<!-- [教程](){ .md-button } -->

#### 授权记录

oauthapp.oauthConsents

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.oauthConsents().then(function(res){
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
        <title>获取授权记录</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>获取授权记录</h3>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                $('#actionButton').click(function () {
                    oauthapp.oauthConsents().then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    }).catch(err => {
                        $('#result').text(err.responseText);
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/oauthConsents.html){ .md-button }    
<!-- [教程](){ .md-button } -->


#### 删除授权记录

oauthapp.oauthDeleteConsent

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.oauthDeleteConsent(id).then(function(res){
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
        <title>删除授权记录</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>删除授权记录</h3>
            <p>id:<input type="text" id="id" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var id = $('#id').val();
                    oauthapp.oauthDeleteConsent(id).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    }).catch(err => {
                        $('#result').text(err.responseText);
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | id | 记录id，必填 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/oauthDeleteConsent.html){ .md-button }    
<!-- [教程](){ .md-button } -->


### 积分记录

oauthapp.pointLogs

???+ note "提示"
    获取当前登录用户的积分变更记录。

=== "方法"

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

=== "示例"

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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | type | 分类 | 0：全部，1：充值，2：消耗 |
    | skip |  可选，指定要拉取的数据条数。 | 0 |
    | take |  可选，指定要跳过的数据条数。 | 10 |

[演示](https://web.oauthapp.com/4/examples/apidemo/pointlogs.html){ .md-button }    [教程](http://docs.oauthapp.com/coding_sdk_pointlogs.html){ .md-button }