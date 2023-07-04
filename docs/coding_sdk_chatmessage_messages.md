---
tags:
  - 教程 - 消息 - 脚本库与API
---

# 消息列表


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
        <input type="text" id="table" placeholder="聊天表名称" />
        <input type="text" id="category" placeholder="聊天组" />
        <input type="text" id="search" placeholder='查询关键字' />
        <input type="text" id="tag" placeholder='消息标签' />
        <input type="number" value="10" id="take" placeholder='拉取条数' />
        <input type="number" value="0" id="skip" placeholder='跳过条数' />
        <button type="button" id="queryButton">查询</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

这是一个包含输入框和查询按钮的界面，用于从聊天记录表中查询聊天信息。界面包含以下输入框：

 - table 输入框：用于输入聊天记录表的名称；

 - category 输入框：用于输入聊天记录所属的组；

 - search 输入框：用于输入查询关键字，可以为空；

 - tag 输入框：用于输入消息标签，可以为空；

 - take 输入框：用于输入需要拉取的聊天信息条数，默认值为 10；

 - skip 输入框：用于输入需要跳过的聊天信息条数，默认值为 0。

用户可以填写这些输入框中的信息，并点击查询按钮进行查询。查询结果会显示在页面下方，其中包括所查询到的聊天信息。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
        oauthapp.allReady().then(function () {
            document.getElementById('queryButton').onclick = function () {
                var table = $('#table').val();
                var category = $('#category').val();
                var search = $('#search').val();
                var tag = $('#tag').val();
                var take = $('#take').val();
                var skip = $('#skip').val();
                oauthapp.messages(table, category, tag,search, take, skip).then(function (res) {
                    
                })
            }
        });
    ```

这段代码使用了 OAuthApp 的 JavaScript SDK 实现了查询指定聊天表中的消息功能。

代码首先调用了 oauthapp.allReady() 方法确保 OAuthApp SDK 已经加载完毕，然后设置了一个点击事件监听器，当用户点击查询按钮时，会从输入框中获取聊天表名称、聊天组、查询关键字、消息标签、拉取条数和跳过条数等查询参数，并将它们作为参数调用 oauthapp.messages() 方法来获取指定条件下的消息数据。

查询结果将通过 Promise 对象返回，但在当前代码中并未处理查询结果，而是空白地占据了 then 方法的回调函数。

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
        <title>messages</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="table" placeholder="聊天表名称" />
            <input type="text" id="category" placeholder="聊天组" />
            <input type="text" id="search" placeholder='查询关键字' />
            <input type="text" id="tag" placeholder='消息标签' />
            <input type="number" value="10" id="take" placeholder='拉取条数' />
            <input type="number" value="0" id="skip" placeholder='跳过条数' />
            <button type="button" id="queryButton">查询</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var table = $('#table').val();
                    var category = $('#category').val();
                    var search = $('#search').val();
                    var tag = $('#tag').val();
                    var take = $('#take').val();
                    var skip = $('#skip').val();
                    oauthapp.messages(table, category, tag,search, take, skip).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

