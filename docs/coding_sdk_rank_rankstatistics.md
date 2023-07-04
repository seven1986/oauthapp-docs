---
tags:
  - 教程 - 排行榜 - 脚本库与API
---

# 榜单统计


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
        <button type="button" id="queryButton">查询</button>
    </div>
    <div>结果：<span id="result"></span></div>
    ```

这段代码是一个HTML片段，包含一个文本输入框和一个查询按钮。文本输入框的placeholder属性设置了输入框的占位符文本，提示用户输入内容的格式或用途。

按钮的type属性设置为"button"，表示这是一个普通的按钮而非提交按钮，点击按钮不会提交表单。按钮的id属性为"queryButton"，可以通过该id来获取该按钮并添加事件监听器。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('queryButton').onclick = function () {
            var table = $('#table').val();
            oauthapp.rankStatistics(table).then(function (res) {
                
            })
        }
    });
    ```

这段代码使用了oauthapp对象中的方法，调用了rankStatistics方法。

在点击按钮时，会将输入框中的table值传入该方法中，并在方法执行完毕后得到结果。

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
        <title>rankStatistics</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="table" placeholder="table" />
            <button type="button" id="queryButton">查询</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var table = $('#table').val();
                    oauthapp.rankStatistics(table).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

