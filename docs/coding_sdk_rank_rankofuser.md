---
tags:
  - 教程 - 排行榜 - 脚本库与API
---

# 用户排名 / 我的排名


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
        <input type="text" id="table" placeholder="table" />
        <input type="text" id="platform" placeholder="platform" />
        <input type="text" id="unionid" placeholder="unionid" />
        <button type="button" id="queryButton">查询</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

这段代码包含一个表单和一个展示结果的区域。表单中有三个输入框用于填写table、platform和unionid，以及一个按钮用于查询相关信息。

点击查询按钮后，会调用oauthapp.rankOfUser()函数，传入表单中的参数进行查询，并将查询结果展示在结果区域中。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('queryButton').onclick = function () {
            var table = $('#table').val();
            var platform = $('#platform').val();
            var unionid = $('#unionid').val();
            oauthapp.rankOfUser(table, platform, unionid).then(function (res) {
                
            })
        }
    });
    ```

这段代码使用了OAuth应用程序的JavaScript SDK，先检查应用程序是否准备好，然后在查询按钮被点击时，获取输入的表名（table）、平台（platform）和UnionID（unionid），并调用 rankOfUser 方法来查询指定用户在指定表格中的排名信息。

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
        <title>rankOfMe</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="table" placeholder="table" />
            <input type="text" id="platform" placeholder="platform" />
            <input type="text" id="unionid" placeholder="unionid" />
            <button type="button" id="queryButton">查询</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var table = $('#table').val();
                    var platform = $('#platform').val();
                    var unionid = $('#unionid').val();
                    oauthapp.rankOfUser(table, platform, unionid).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

