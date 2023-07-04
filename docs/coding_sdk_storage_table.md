---
tags:
  - 教程 - 数据库 - 脚本库与API
---

# 单表查询


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
        <input type="text" id="table" placeholder="表名" />
        <input type="text" id="tag" placeholder='标签' />
        <input type="text" id="filter" placeholder='筛选条件，{"name":"123"}' />
        <input type="text" id="sort" placeholder='排序条件  {"id":true}' />
        <input type="number" value="10" id="take" placeholder='拉取条数' />
        <input type="number" value="0" id="skip" placeholder='跳过条数' />
        <button type="button" id="queryButton">查询</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

在HTML中定义了一个包含输入框和查询按钮的div，并且定义了一个结果展示的span。

当用户点击查询按钮时，会调用JavaScript中的queryButton的onclick函数。

函数中获取了用户在输入框中输入的表名、标签、筛选条件、排序条件、拉取条数和跳过条数，并且使用这些参数调用了oauthapp.tableGet方法进行查询。

查询结果将在oauthapp.tableGet方法的回调函数中进行处理，处理后的结果会显示在页面上。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('queryButton').onclick = function () {
            var table = $('#table').val();
            var tag = $('#tag').val();
            var filter = $('#filter').val();
            var sort = $('#sort').val();
            var take = $('#take').val();
            var skip = $('#skip').val();
            oauthapp.table(table, tag, filter, sort, take, skip).then(function (res) {
               
            })
        }
    });
    ```

这段代码使用了 OAuthApp 的 JavaScript SDK 来进行数据查询操作。

首先在网页中渲染了一个查询界面，其中包含了表名、标签、筛选条件、排序条件、拉取条数和跳过条数等参数的输入框以及一个查询按钮。

然后通过 JavaScript 代码来处理点击查询按钮的事件，获取输入框中用户输入的各个参数的值，然后通过 OAuthApp SDK 的 table 方法来发起查询请求，并在查询成功后对返回的数据进行处理。

查询成功后，可能会将数据展示在网页上，但在这段代码中并没有展示的部分，只是用注释表示可能需要进一步处理。


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
        <title>table</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="table" placeholder="表名" />
            <input type="text" id="tag" placeholder='标签' />
            <input type="text" id="filter" placeholder='筛选条件，{"name":"123"}' />
            <input type="text" id="sort" placeholder='排序条件  {"id":true}' />
            <input type="number" value="10" id="take" placeholder='拉取条数' />
            <input type="number" value="0" id="skip" placeholder='跳过条数' />
            <button type="button" id="queryButton">查询</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var table = $('#table').val();
                    var tag = $('#tag').val();
                    var filter = $('#filter').val();
                    var sort = $('#sort').val();
                    var take = $('#take').val();
                    var skip = $('#skip').val();
                    oauthapp.table(table, tag, filter, sort, take, skip).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

