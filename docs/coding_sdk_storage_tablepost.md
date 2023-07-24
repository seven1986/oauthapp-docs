---
tags:
  - 开发教程 - 数据库
---

# 提交数据


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

这段代码是一个HTML表单，包含以下输入框和按钮：

一个文本输入框，id为"tableName"，用于输入表名称；

一个文本输入框，id为"tags"，用于输入标签；

一个数字输入框，id为"showIndex"，用于输入排序；

一个文本域，id为"content"，用于输入自定义数据，必须是JSON格式；

一个提交按钮，id为"addButton"。

在表单下方还有一个显示结果的区域，id为"result"，用于在提交表单后显示返回的结果。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('addButton').onclick = function () {
            var tableName = $('#tableName').val();
            var tags = $('#tags').val();
            var showIndex = $('#showIndex').val();
            var content = $('#content').val();
            var data = JSON.stringify({
                showIndex: showIndex,
                tags: tags,
                content: content
            });
            oauthapp.tablePost(tableName, data).then(function (res) {
                
            })
        }
    });
    ```

该代码段是一个JavaScript脚本，使用了客户端SDK中的oauthapp对象和相关方法实现对数据表进行添加操作。具体描述如下：

首先，使用oauthapp.allReady()方法来确保SDK已经准备好，即用户已经成功登录。然后，给提交按钮addButton添加一个onclick事件，用来响应用户的点击操作。

在点击事件中，通过jQuery选择器获取输入框中用户输入的表名称、标签、排序和自定义数据，并使用JSON.stringify()方法将这些数据格式化为JSON字符串。

最后，调用oauthapp.tablePost(tableName, data)方法将数据提交到对应的数据表中，其中tableName为表名称，data为需要添加的数据，是一个JSON格式的字符串。该方法返回一个Promise对象，在then()方法中可以获取到添加数据的结果。

该页面还包含一个<div>元素用于显示添加结果，并且在该元素中包含一个<span>元素，用来显示操作结果。

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
        <title>tablePost</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>
            <input type="text" id="tableName" placeholder="表名称" />
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
                    var tags = $('#tags').val();
                    var showIndex = $('#showIndex').val();
                    var content = $('#content').val();
                    var data = JSON.stringify({
                        showIndex: showIndex,
                        tags: tags,
                        content: content
                    });
                    oauthapp.tablePost(tableName, data).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

