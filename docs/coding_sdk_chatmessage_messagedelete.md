---
tags:
  - 开发教程 - 消息
---

# 删除消息


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
    div>
        <input type="text" id="table" placeholder="table" />
        <input type="number" id="dataId" placeholder="id" />
        <button type="button" id="deleteButton">删除</button>
    </div>
    <p>结果：<span id="result"></span></p>
    ```

这段代码展示了一个HTML页面中的一段代码。页面包含一个输入框和一个按钮，用户可以在输入框中输入表名和要删除的数据的ID，然后点击按钮来执行删除操作。

当删除操作完成后，页面上会显示一个文本，指示操作的结果。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('deleteButton').onclick = function () {
            var  table = $('#table').val();
            var  dataId = $('#dataId').val();
            oauthapp.messageDelete(table,dataId).then(function (res) {
                
            })
        }
    });
    ```

以上代码是一个基于 OAuth 的 JavaScript 实现的消息删除功能。首先，当 oauthapp.allReady() 被调用并返回成功后，点击 deleteButton 按钮会触发一个事件处理函数。

在该函数中，它从页面上的 table 和 dataId 元素获取相应的值，并将它们作为参数传递给 oauthapp.messageDelete() 方法来发送一个消息删除请求。

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
        <title>messageDelete</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="table" placeholder="table" />
            <input type="number" id="dataId" placeholder="id" />
            <button type="button" id="deleteButton">删除</button>
        </div>
        <p>结果：<span id="result"></span></p>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('deleteButton').onclick = function () {
                    var  table = $('#table').val();
                    var  dataId = $('#dataId').val();
                    oauthapp.messageDelete(table,dataId).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

