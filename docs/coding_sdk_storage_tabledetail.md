---
tags:
  - 开发教程 - 数据库
---

# 数据详情


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
        <button type="button" id="queryButton">查询</button>
    </p>
    <div>结果：<span id="result"></span></div>
    ```

这段代码展示了一个简单的查询数据表中指定数据id的功能。页面上有一个文本框用于输入数据表名称，一个数字文本框用于输入数据id，以及一个查询按钮。

当用户输入完数据表名称和数据id后，点击查询按钮，就会触发一个查询操作，并将查询结果显示在页面上方的结果区域中，这里用一个span元素的文本内容来展示查询结果。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('queryButton').onclick = function () {
            var  table = $('#table').val();
            var  dataId = $('#dataId').val();
            oauthapp.tableDetail(table,dataId).then(function (res) {
                
            })
        }
    });
    ```

这段代码使用了 OAuth 应用程序客户端 SDK 提供的方法来查询指定数据表中特定数据行的详细信息。

首先，在 oauthapp.allReady() 成功返回后，当用户单击页面上的 "查询" 按钮时，document.getElementById('queryButton').onclick 事件将触发一个函数，其中提取了 table 和 dataId 输入框的值，并调用了 oauthapp.tableDetail(table, dataId) 方法，以向服务器请求指定数据表中特定数据行的详细信息。

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
        <title>tableDetail</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>
            <input type="text" id="table" placeholder="数据表名称" />
            <input type="number" id="dataId" placeholder="id" />
            <button type="button" id="queryButton">查询</button>
        </p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var  table = $('#table').val();
                    var  dataId = $('#dataId').val();
                    oauthapp.tableDetail(table,dataId).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

