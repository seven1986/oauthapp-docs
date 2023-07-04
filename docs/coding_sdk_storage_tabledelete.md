---
tags:
  - 教程 - 数据库 - 脚本库与API
---

# 删除数据


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
    <p>
        <input type="text" id="table" placeholder="数据表名称" />
        <input type="number" id="dataId" placeholder="id" />
        <button type="button" id="deleteButton">删除</button>
    </p>
    ```

这段代码展示了一个包含文本输入框和一个按钮的HTML代码段。输入框可以输入数据表名称和数据表的ID。按钮可以用于删除指定的数据表ID。

当点击按钮时，页面会调用一个JavaScript函数，该函数使用OAuth2身份验证客户端SDK中的方法来删除指定数据表ID。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('deleteButton').onclick = function () {
            var  table = $('#table').val();
            var  dataId = $('#dataId').val();
            oauthapp.tableDelete(table,dataId).then(function (res) {
                
            })
        }
    });
    ```

这段代码使用了OAuthApp对象的tableDelete方法。首先，它使用了oauthapp.allReady()方法，确保OAuthApp对象已经准备就绪。

接着，它给"deleteButton"按钮添加了点击事件，当按钮被点击时，它将从"table"和"dataId"输入框中获取表名和数据行id，并将它们作为参数传递给tableDelete方法。

然后，它等待tableDelete方法完成并返回结果。

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
        <title>tableDelete</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>
            <input type="text" id="table" placeholder="数据表名称" />
            <input type="number" id="dataId" placeholder="id" />
            <button type="button" id="deleteButton">删除</button>
        </p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('deleteButton').onclick = function () {
                    var  table = $('#table').val();
                    var  dataId = $('#dataId').val();
                    oauthapp.tableDelete(table,dataId).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

