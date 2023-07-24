---
tags:
  - 开发教程 - 用户
---

# 积分记录

获取用户积分变更历史记录，正数为充值，负数为消耗。


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
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.pointLogs(type, skip, take)
    ```



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

