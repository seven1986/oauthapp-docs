# 用户

示例使用的appId是57，实际需要替换成自己的appId。

## web指纹 模式（默认）
使用Fingerprint2,会根据访问设备生成唯一的web指纹。  该模式最简单，框架已内置注册登录，可以直接获取accessToken。

### 自动注册、登录

复制下面的代码，替换appId，然后发布到服务器。

=== "HTML"
``` HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello world</title>
    <script id="appcore" 
    src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" 
    data-appid="57"></script>

</head>
<body>
    <h1>hello world!</h1>
    <script type="text/javascript">
        oauthapp.allReady().then(function () {
            console.log(oauthapp.appUser);
        })
</script>
</body>
</html>
```

发布成功后，从控制台可以看到打印的用户信息。

![](https://blob.oauthapp.com/4/app/2/example_appuser/1.png)


### 用户管理

![](https://blob.oauthapp.com/4/app/2/example_appuser/2.png)


### 获取用户资料
=== "HTML"
``` HTML
<script type="text/javascript">
     oauthapp.profile().then(function(res){
        console.log(res)
    });
</script>
```

### 更新用户资料
=== "HTML"
``` HTML
<script type="text/javascript">
     oauthapp.profilePut({a:1,b:2,c:3}).then(function(res){
        console.log(res)
    });
</script>
```

相关示例：https://web.oauthapp.com/4/examples/updateprofile.html


## 账号密码 模式

自定义登录账号、登录密码，可参考下面的代码示例实现。


- 账号密码登录 示例：https://web.oauthapp.com/4/examples/signin.html

- 账号密码注册 示例：https://web.oauthapp.com/4/examples/signup.html

## 小程序扫码 模式

需要使用微信小程序扫码登录功能的，可参考下面的代码实现。 需分别调用：创建登录码、登录状态查询2个接口。

- 小程序扫码登录 示例 1：https://web.oauthapp.com/4/seedtemplates/signin.html

- 小程序扫码登录 示例 2：https://web.oauthapp.com/4/seedtemplates/index.html

- 小程序扫码登录 示例 3：https://web.oauthapp.com/4/examples/minip_signup.html

## 系统账户 模式

该模式最简单，但用户是来自系统后台的。

单点登录模式，统一跳转到系统登录界面，用户登录并授权后，跳转回应用的站点，并附带accesstoken。

示例：https://web.oauthapp.com/4/examples/signin_authorize.html

### 参考代码

=== "HTML"
    ```html
    <a href="https://www.oauthapp.com/OAuth/SignIn?scheme=OpenAuth&client_id={{client_id}}&redirect_uri={{redirect_uri}}&scope={{scope}}&nonce={{nonce}}&state=">登陆</a>
    ```

### 参数说明

| 名称 | 是否必须 | 说明 |
| ----------- | ----------- | ----------- |
| `scheme` | 是 | 固定为OpenAuth |
| `client_id` | 是 | 应用的appKey |
| `redirect_uri` | 是 | **你的应用地址** |
| `scope` | 是 | 授权集合，可自定义如：`openid profile role permission` |
| `state` | 是 | 自定义回传参数 |
| `nonce` | 是 | 随机字符串，值固定为`123456789` |