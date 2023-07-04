---
tags:
  - 教程 - 数据库 - 脚本库与API
---

# 更新数据


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
        <input type="text" id="tableName" placeholder="表名称" />
    </p>
    <p>
        <input type="text" id="dataId" placeholder="数据ID" />
    </p>
    <p>
        <input type="text" id="tags" placeholder="标签" />
    </p>
    <p>
        <input type="number" id="showIndex" placeholder="排序" />
    </p>
    <p>
        <textarea rows="5" id="content" placeholder="自定义数据，必须是JSON格式"></textarea>
    </p>
    <p>
        <button type="button" id="addButton">提交</button>
    </p>
    <div>结果：<span id="result"></span></div>
    ```

这是一个表单，包含表格名称、数据ID、标签、排序和自定义数据输入框，以及一个提交按钮和一个结果显示区域。用户可以在输入框中填写相应的信息，点击提交按钮将信息提交到指定的数据表中，并在结果显示区域中显示提交结果。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('addButton').onclick = function () {
            var tableName = $('#tableName').val();
            var dataId = $('#dataId').val();
            var tags = $('#tags').val();
            var showIndex = $('#showIndex').val();
            var content = $('#content').val();
            var data = JSON.stringify({
                showIndex: showIndex,
                tags: tags,
                content: content
            });
            oauthapp.tablePut(tableName, dataId, data).then(function (res) {
                
            })
        }
    });
    ```

该代码段使调用了一个名为oauthapp.tablePut()的函数，该函数用于在指定的表格中添加或更新一行数据。


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
        <title>tablePut</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>
            <input type="text" id="tableName" placeholder="表名称" />
        </p>
        <p>
            <input type="text" id="dataId" placeholder="数据ID" />
        </p>
        <p>
            <input type="text" id="tags" placeholder="标签" />
        </p>
        <p>
            <input type="number" id="showIndex" placeholder="排序" />
        </p>
        <p>
            <textarea rows="5" id="content" placeholder="自定义数据，必须是JSON格式"></textarea>
        </p>
        <p>
            <button type="button" id="addButton">提交</button>
        </p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('addButton').onclick = function () {
                    var tableName = $('#tableName').val();
                    var dataId = $('#dataId').val();
                    var tags = $('#tags').val();
                    var showIndex = $('#showIndex').val();
                    var content = $('#content').val();
                    var data = JSON.stringify({
                        showIndex: showIndex,
                        tags: tags,
                        content: content
                    });
                    oauthapp.tablePut(tableName, dataId, data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

