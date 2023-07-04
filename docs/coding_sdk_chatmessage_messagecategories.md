---
tags:
  - 教程 - 消息 - 脚本库与API
---

# 消息分类



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
    <p><input type="text" id="table" placeholder="table" /></p>
    <p>
      <button type="button" onclick="queryData()">查询</button>
    </p>
    <div>结果：<span id="result"></span></div>
    ```

这段代码创建了一个包含输入框和一个查询按钮的HTML表单。输入框用于输入查询的表名，查询按钮用于触发查询操作。

当用户点击查询按钮时，将调用名为queryData的JavaScript函数来执行查询操作。查询结果将显示在页面上的结果标签中。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    function queryData(){
      var table = $('#table').val();
        oauthapp.messageCategories(table).then(function (res) {
              
          })
    }
    oauthapp.allReady().then(function () { });
    ```

该代码段包含一个名为queryData的JavaScript函数和一个具有“表格”输入字段和“查询”按钮的HTML表单。当用户单击“查询”按钮时，将调用queryData函数，并将表格名称传递给oauthapp.messageCategories函数进行处理。结果将在页面上显示。

此外，代码中还有一个oauthapp.allReady函数，它将在所有必要的数据和资源准备就绪时执行回调函数。

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
        <title>messageCategories</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
      <p><input type="text" id="table" placeholder="table" /></p>
      <p>
        <button type="button" onclick="queryData()">查询</button>
      </p>
        <div>结果：<span id="result"></span></div>
        <script>
          function queryData(){
            var table = $('#table').val();
              oauthapp.messageCategories(table).then(function (res) {
                    $('#result').text(JSON.stringify(res));
                })
          }
            oauthapp.allReady().then(function () {
            });
        </script>
    </body>
    </html>
    ```

