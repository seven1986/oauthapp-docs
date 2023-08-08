
# 常见问题

## 用户如何登录我的应用？

### 自定义UI

通过写代码的方式，调用API 注册/登录，获取用户信息。

- [账号+密码](https://web.oauthapp.com/4/docs/framework_user/#_6)
- [Web ID](https://web.oauthapp.com/4/docs/framework_user/#_2)
- [Union ID +平台标识](https://web.oauthapp.com/4/docs/framework_user/#_3)
- [access_token](https://web.oauthapp.com/4/docs/framework_user/#access_token)
- [微信小程序](https://web.oauthapp.com/4/docs/framework_user/#_9)
- [钉钉](https://web.oauthapp.com/4/docs/framework_user/#_12)

### 统一登录

无需编写登录/注册代码，使用oauthapp单点登录，即可获取用户信息。
[查看文档](https://web.oauthapp.com/4/docs/framework_user/#_13)

> 支持以下登录方式

- 账号+密码
- Web ID （可选）
- 微信小程序 （可选）
- 钉钉 （可选）
<!-- - 邮箱+密码 -->
<!-- - 手机号+密码 -->
<!-- - Union ID +平台标识 -->

## 如何开放我的应用给第三方？

把用户数据开放给外部网址，与外部平台互联互通。

> 例如第三方应用的网址为https://127.0.0.2，使用[oauthapp单点登录](https://web.oauthapp.com/4/docs/framework_user/#_13)，将**redirect_url**参数设置为接收用户access_token的地址即可

=== "示例代码"

    ```HTML linenums="1"
    <a href="https://www.oauthapp.com/oauth/2?scheme=app&redirect_uri=https://127.0.0.2&scopes=openid&nonce=1667553723079">
       登录
    </a>
    <!-- 
        {{scheme}}	登录协议(必填)	固定为 "app"
        {{appId}}	应用ID(必填)	
        {{scopes}}	授权列表(必填)	多个权限用英文空格分隔
        {{redirect_uri}}	回调地址(必填)	
        {{redirect_uri_name}}	自定义授权标题	
        {{nonce}}	自定义字符串，32位(必填)	 
    -->
    ```

## 独立部署后，如何配置oauthapp SDK的服务器地址？

=== "示例代码"

    ```HTML linenums="1"
     <!-- data-server 属性替换为你的 服务器地址，例如：https://example.xxx.com -->
     <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" 
        data-appid="{{appId}}" data-server="{{server}}"></script>
    ```

<!-- 
## 如何实现排行榜功能？

1，用户登录注册

2，提交用户的分数

3，自动计算排名，查看排行榜数据

4，按天/周/月/年计算榜单

## 如何实现打卡签到功能？

1，用户登录注册

2，提交用户打卡记录

3，查看我的打卡记录

## 如何实现问卷调查功能？

1，用户登录注册

2，提交问卷

3，查看数据


## 如何制作一个聊天室？

1，用户登录注册

2，读取聊天消息

3，发送消息

4，删除/更新消息

## 如何制作一个新闻系统？

1，用户登录注册

2，发布新闻

3，读取新闻列表

4，更新/删除新闻 -->
