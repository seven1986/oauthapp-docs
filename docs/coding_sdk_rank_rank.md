---
tags:
  - 开发教程 - 排行榜
---

# 榜单数据


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
    <p><input type="text" id="platform" placeholder="platform" /></p>
    <p><input type="text" id="unionId" placeholder="unionId" /></p>
    <p><input type="text" id="nickName" placeholder="nickName" /></p>
    <p><input type="text" id="tag" placeholder="tag" /></p>
    <p><input type="number" value="0" id="skip" placeholder='跳过条数' /></p>
    <p><input type="number" value="10" id="take" placeholder='拉取条数' /></p>
    <p><button type="button" id="queryButton">查询</button></p>
    <div>结果：<span id="result"></span></div>
    ```

这是一个查询排行榜的页面，包含了多个输入框和一个查询按钮以及一个结果展示框。具体的描述如下：

- 有一个文本输入框，id为"table"，用于输入数据表的名称。

- 有一个文本输入框，id为"platform"，用于输入平台名称。

- 有一个文本输入框，id为"unionId"，用于输入用户unionId。

- 有一个文本输入框，id为"nickName"，用于输入用户昵称。

- 有一个文本输入框，id为"tag"，用于输入标签。

- 有一个数字输入框，id为"skip"，初始值为0，用于输入需要跳过的数据条数。

- 有一个数字输入框，id为"take"，初始值为10，用于输入需要拉取的数据条数。

- 有一个按钮，id为"queryButton"，用于触发查询排行榜操作。

- 有一个结果展示框，id为"result"，用于展示查询结果。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('queryButton').onclick = function () {
            var table = $('#table').val();
            var tag = $('#tag').val();
            var platform = $('#platform').val();
            var unionId = $('#unionId').val();
            var nickName = $('#nickName').val();
            var skip = $('#skip').val();
            var take = $('#take').val();
            oauthapp.rank(table, platform, unionId, nickName, tag, skip, take).then(function (res) {
                
            })
        }
    });
    ```

这段代码实现了一个事件监听器，当用户点击页面中的“查询”按钮时，会执行一个函数。

该函数首先获取页面中各个输入框中用户输入的值，包括表名称、标签、平台、unionId、昵称、跳过条数、拉取条数等信息，并将这些值作为参数传递给oauthapp.rank函数。

oauthapp.rank函数会根据传入的参数从指定的数据表中查询符合条件的数据，并将结果返回给调用该函数的代码块。

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
        <title>rank</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p><input type="text" id="table" placeholder="table" /></p>
        <p><input type="text" id="platform" placeholder="platform" /></p>
        <p><input type="text" id="unionId" placeholder="unionId" /></p>
        <p><input type="text" id="nickName" placeholder="nickName" /></p>
        <p><input type="text" id="tag" placeholder="tag" /></p>
        <p><input type="number" value="0" id="skip" placeholder='跳过条数' /></p>
        <p><input type="number" value="10" id="take" placeholder='拉取条数' /></p>
        <p><button type="button" id="queryButton">查询</button></p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var table = $('#table').val();
                    var tag = $('#tag').val();
                    var platform = $('#platform').val();
                    var unionId = $('#unionId').val();
                    var nickName = $('#nickName').val();
                    var skip = $('#skip').val();
                    var take = $('#take').val();
                    oauthapp.rank(table, platform, unionId, nickName, tag, skip, take).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```
