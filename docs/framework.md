---
tags:
  - 文档
---

# 应用

### 提示

!!! quote "在开始前，请确认用OAuthApp发布工具创建应用并获取了 **appid**。"

### 安装

#### 下载到本地

[点击下载](https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.zip){ .md-button }

#### 在线引用

=== "OAuthApp服务器"
    ```html linenums="1"
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="{{appid}}"></script>
    ```

=== "jsDelivr CDN"
    ```html linenums="1"
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script src="https://cdn.jsdelivr.net/npm/oauthapp@1.9.891/oauthapp.min.js" data-appid="{{appid}}"></script>
    ```

=== "unpkg CDN"
    ```html linenums="1"
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script src="https://unpkg.com/oauthapp@1.9.891/oauthapp.min.js" data-appid="{{appid}}"></script>
    ```

#### 软件包管理器

[npm](https://www.npmjs.com/package/oauthapp)

```shell linenums="1"
npm install oauthapp@latest
```

### 初始化

oauthapp.ready

获取应用的基本信息、配置项、文件列表。
???+ note "提示"
    在 OAuthApp SDK 加载完成之前，调用 SDK 的其他方法将会报错。因此在使用 SDK 的其他方法之前，应该先调用 oauthapp.ready() 方法来确保 SDK 已经准备好使用。
=== "方法"

    ```JavaScript linenums="1"
    oauthapp.ready() 
    .then(() => {
     // SDK 已经准备好使用，可以调用其他方法
    })
    .catch(err => {
     console.error('OAuthApp SDK 加载失败', err);
    });

    // 在上面的示例代码中，当 oauthapp.ready() 方法返回 Promise 对象成功后，我们就可以安全地调用 oauthapp sdk方法了。
    // 如果 oauthapp.ready() 方法返回 Promise 对象失败，则说明 SDK 加载失败，我们需要检查错误并进行处理。
    ```
=== "示例" 

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>ready</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
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

=== "返回数据"

    ```JavaScript linenums="1"
    {
    "code": 200,
    "data": {
      "info": {
        "id": 2,
        "userID": 1,
        "projectID": 1,
        "website": "https://docs.oauthapp.com",
        "serverPath": "docs",
        "name": "开发文档",
        "logo": "https://blob.oauthapp.com/4/tenant/2/API.png",
        "description": "oauthapp 开发文档",
        "tags": null,
        "appKey": "613f1d05-6fc0-42ac-9b3a-c3259d5dc8f4",
        "share": false,
        "createDate": "2022-01-21 14:34:24",
        "lastUpdate": "2022-01-21 14:34:24",
        "isDelete": false,
        "sort": 0
      },
      "props": [
        {
          "code": "DingTalkCorpId",
          "value": "*ding5c589fe4688de*****",
          "desc": null
        },
        {
          "code": "WechatMiniPSignIn",
          "value": "true",
          "desc": null
        },
        {
          "code": "DingTalkSignIn",
          "value": "true",
          "desc": null
        },
        {
          "code": "WebIDSignIn",
          "value": "true",
          "desc": null
        }
      ],
      "blobs": []
    },
    "err": ""
    }
    ```
[演示](https://web.oauthapp.com/4/examples/apidemo/ready.html){ .md-button }    [教程](https://docs.oauthapp.com/coding_sdk_app_ready.html){ .md-button }


### 初始化 + 自动注册账号

oauthapp.allReady

获取应用的基本信息、配置项、文件列表 + web指纹登录，可直接调用所有api。

???+ note "提示"
    oauthapp.allReady()方法用于在oauthapp SDK中注册/登录用户并确保所有必要的依赖项都已加载并准备好使用。
    此方法还将使用web指纹（fingerprintjs2）自动注册，如果账号不存在就自动注册；如果存在就自动登录，然后将用户信息赋值到window.oauthapp.appUser对象中。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.allReady().then(function(){
        console.log(oauthapp.app);
        console.log(oauthapp.appUser);
        console.log(oauthapp.settings.access_token);
    });
    
    // 当调用此方法时，它将执行以下操作：
    // 检查oauthapp SDK是否已经准备好使用。如果尚未准备好，则将等待所有必要的依赖项加载完成。
    // 检查当前用户是否已经注册/登录。如果尚未注册/登录，则将使用web指纹（fingerprintjs2）自动注册用户。
    // 如果用户已经注册/登录，则将用户信息赋值到window.oauthapp.appUser对象中。
    // 如果在注册/登录过程中遇到任何错误，则将抛出一个错误并拒绝promise。
    ```
=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>allReady</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
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

=== "返回数据"

    ```Javascript linenums="1"
    {
      "code": 200,
      "data": {
        "appID": 2,
        "platform": "web",
        "unionID": "2192a3d9aab0517b9590b6fc67381c23",
        "phone": null,
        "createDate": "2023-07-18 16:27:26",
        "userName": "2192a3d9aab0517b9590b6fc67381c23",
        "phoneIsValid": false,
        "data": null,
        "email": null,
        "emailIsValid": false,
        "lastUpdate": "2023-07-18 16:27:26",
        "nickName": null,
        "id": 132,
        "avatar": null,
        "point": 0,
        "role": "user"
      },
      "err": ""
    }
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/allready.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_app_allready.html){ .md-button }

???+ note "提示"
    oauthapp.ready() 和 oauthapp.allReady() 都会初始化应用信息，但是 oauthapp.allReady() 会自动注册或登录用户信息，并将用户信息赋值到 window.oauthapp.appUser 对象中，以便在后续的操作中使用。这两个方法并没有先后顺序之分，可以根据具体的业务需求选择使用哪一个方法。
    
    - 如果需要获取用户信息并进行后续操作，可以使用 oauthapp.allReady() 方法。
    
    - 如果只需要初始化应用信息，可以使用 oauthapp.ready() 方法。


### 获取应用配置

oauthapp.__appPropValue

使用发布工具配置，在 应用详情>>应用配置菜单下，配置后还需开启接口权限才能访问。

???+ note "提示"
    用于获取 OAuthApp 应用中特定属性的值。这个方法接受一个参数 **propertyCode**，代表要获取的属性的代码。
    通过调用此方法，您可以轻松地获取 OAuthApp 应用中的各种属性，例如应用名称、应用图标、应用描述等等。属性代码可以在 OAuthApp 应用管理页面中找到。
    这个方法通常与其他 OAuthApp SDK 方法一起使用，以便根据应用配置来自定义 OAuth 登录体验，例如更改 OAuth 登录按钮的文本或样式等。

=== "方法"

    ```JavaScript linenums="1"
    // 获取应用名称
    var appName = oauthapp.__appPropValue('app_name');
    console.log('应用名称：', appName);
    ```

=== "示例"
    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>__appPropValue</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <label>属性code</label>
        <input type="text" id="propCode" />
        <button type="button" id="actionBtn">提交</button>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
              $('#actionBtn').click(function () {
                 var propCode = $('#propCode').val();
                  var propValue = oauthapp.__appPropValue(propCode);
                if (propValue != '') {
                    $('#result').text(propValue);
                }
                else{
                    $('#result').text('属性不存在，或没有设置接口权限。');
                }
              })
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明" 

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | propertyCode | 配置项的code  |  |



[演示](https://web.oauthapp.com/4/examples/apidemo/__appPropValue.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_app___apppropvalue.html){ .md-button }



### 重置meat标签

oauthapp.__resetHeaderTags

会自动重置页面的title、icon、描述信息，具体可在后台配置。

???+ note "提示"
    用于重置 HTML 页面中的所有 OAuthApp 相关标记（meta 标签、title 标签、facicon 标签等），以便重新初始化 OAuthApp 应用程序信息，而无需手动更改 HTML 页面。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.__resetHeaderTags();
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>__resetHeaderTags</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.__resetHeaderTags();
            });
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/__resetHeaderTags.html){ .md-button }


## 属性

| 名称  | 说明 | 参数 |
| ----------- | ----------- | ----------- |
| oauthapp.app  | 应用数据 | 需在“oauthapp.ready”或“oauthapp.allReady”方法后使用 |
| oauthapp.app.info | 应用信息 | 使用发布工具配置：应用>>基本信息 菜单下 |
| oauthapp.app.blobs | 应用文件 | 使用发布工具配置：应用>>存储 菜单下 |
| oauthapp.app.props | 应用配置 | 使用发布工具配置：应用>>应用配置——client配置节 菜单下 |
| oauthapp.appUser | 用户数据 | 需在“oauthapp.allReady”方法后使用 |
| oauthapp.settings.access_token | 用户令牌 |  |
| oauthapp.settings.appid | 应用id |  |
| oauthapp.settings.fingerIdentity | Web指纹 |  |
| oauthapp.settings.server | 服务器地址 |  |