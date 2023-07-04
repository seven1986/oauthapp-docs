---
tags:
  - 教程 - 应用 -脚本库与API
---

# 获取应用配置

!!! Tip "提示"
    OAuthApp提供了一个名为__appPropValue()的方法，用于获取OAuthApp应用中特定属性的值。通过调用此方法，您可以轻松地获取OAuthApp应用中的各种属性，例如应用名称、应用图标、应用描述等等。属性代码可以在OAuthApp应用管理页面中找到。这个方法通常与其他OAuthApp SDK方法一起使用，以便根据应用配置来自定义OAuth登录体验，例如更改OAuth登录按钮的文本或样式等。

下面是使用__appPropValue()方法的示例代码：


## 步骤一：引入 OAuthApp 库
=== "HTML"
    ```HTML
    <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    ```

在 HTML 文件的头部，我们首先需要引入 OAuthApp 库。其中 data-appid 属性需要替换为你的 OAuthApp 应用的 ID。


## 步骤二：页面结构

=== "HTML"
    ```HTML
    <label for="propCode">属性代码:</label>
    <input type="text" id="propCode" />
    <p>结果:</p>
    <div id="result"></div>
    ```

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
     oauthapp.allReady().then(function () {
            var propCode = document.getElementById("propCode").value;
            var propValue = oauthapp.__appPropValue(propCode);
    });
    ```

在脚本部分，我们在oauthapp.allReady()方法中使用__appPropValue()方法获取属性值。

## 步骤四：测试结果

将结果显示在页面上。

=== "Javascript"
    ```Javascript
    if (propValue != '') {
         document.getElementById("result").innerHTML = propValue;
     }
     else{
         document.getElementById("result").innerHTML = '属性不存在，获取没有设置接口权限。';
     }
    ```

**需要注意的是，获取应用属性值之前需要确保已经设置了接口权限。如果属性不存在或者获取没有设置接口权限，__appPropValue()方法将返回空字符串。**

## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>__appPropValue</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="{{appid}}"></script>
    </head>
    <body>
        <label for="propCode">属性代码:</label>
        <input type="text" id="propCode" />
        <p>结果:</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
                var propCode = document.getElementById("propCode").value;
                var propValue = oauthapp.__appPropValue(propCode);
                if (propValue != '') {
                    document.getElementById("result").innerHTML = propValue;
                }
                else{
                    document.getElementById("result").innerHTML = '属性不存在，获取没有设置接口权限。';
                }
            });
        </script>
    </body>
    </html>
    ```