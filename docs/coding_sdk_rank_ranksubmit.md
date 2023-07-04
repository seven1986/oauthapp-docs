---
tags:
  - 教程 - 排行榜 - 脚本库与API
---

# 提交分数


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
    <p><input type="number" id="userID" placeholder="userID" /></p>
    <p><input type="text" id="tags" placeholder="tags" /></p>
    <p><input type="text" id="data" placeholder="data" /></p>
    <p><input type="text" id="remark" placeholder="remark" /></p>
    <p><input type="text" id="unionID" placeholder="unionID" /></p>
    <p><input type="text" id="platform" placeholder="platform" /></p>
    <p><input type="text" id="avatar" placeholder="avatar" /></p>
    <p><input type="text" id="nickName" placeholder="nickName" /></p>
    <p><input type="number" id="score" placeholder="score" /></p>
    <p><input type="number" id="maximumScore" placeholder="maximumScore" /></p>
    <p><button type="button" id="putButton">提交</button></p>
    <div>结果：<span id="result"></span></div>
    ```

该代码段是一个包含HTML表单元素和一个提交按钮的HTML表单。表单中包含一些输入框，包括表名（table）、用户ID（userID）、标签（tags）、数据（data）、备注（remark）、用户unionID（unionID）、平台（platform）、头像（avatar）、昵称（nickName）、得分（score）和最高分（maximumScore）。

当用户填写了表单并点击提交按钮时，JavaScript代码将使用OAuth进行身份验证，然后将表单数据存储到相应的表中。点击提交按钮时，表单数据将使用OAuthApp的tablePut方法进行提交。

此代码还包含一个结果区域，该区域将在数据提交后显示提交结果。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
        oauthapp.allReady().then(function () {
            document.getElementById('putButton').onclick = function () {
                var table = $('#table').val();
                var userID = $('#userID').val()||0;
                var tags = $('#tags').val();
                var data = $('#data').val();
                var remark = $('#remark').val();
                var unionID = $('#unionID').val() || oauthapp.appUser.unionID;
                var platform = $('#platform').val() || oauthapp.appUser.platform;
                var avatar = $('#avatar').val() || oauthapp.appUser.avatar;
                var nickName = $('#nickName').val() || oauthapp.appUser.nickName;
                var score = $('#score').val();
                var maximumScore = $('#maximumScore').val();
                oauthapp.rankSubmit(table, {
                    userID,
                    tags,
                    data,
                    remark,
                    unionID,
                    platform,
                    avatar,
                    nickName,
                    score,
                    maximumScore
                }).then(function (res) {
                    
                });
            }
        });
    ```

这段代码实现了一个排行榜提交功能。当页面中的提交按钮被点击时，代码会获取页面中的各个输入框中的值，将这些值封装成一个对象，作为参数传递给oauthapp.rankSubmit函数。

该函数会将这些数据提交到服务器上，用于更新排行榜。其中，如果一些输入框的值没有被填写，会使用默认值（如unionID和platform会使用当前登录用户的信息）。

该代码是在前提条件oauthapp.allReady()满足时执行的。

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
        <title>rankSubmit</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p><input type="text" id="table" placeholder="table" /></p>
        <p><input type="number" id="userID" placeholder="userID" /></p>
        <p><input type="text" id="tags" placeholder="tags" /></p>
        <p><input type="text" id="data" placeholder="data" /></p>
        <p><input type="text" id="remark" placeholder="remark" /></p>
        <p><input type="text" id="unionID" placeholder="unionID" /></p>
        <p><input type="text" id="platform" placeholder="platform" /></p>
        <p><input type="text" id="avatar" placeholder="avatar" /></p>
        <p><input type="text" id="nickName" placeholder="nickName" /></p>
        <p><input type="number" id="score" placeholder="score" /></p>
        <p><input type="number" id="maximumScore" placeholder="maximumScore" /></p>
        <p><button type="button" id="putButton">提交</button></p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('putButton').onclick = function () {
                    var table = $('#table').val();
                    var userID = $('#userID').val()||0;
                    var tags = $('#tags').val();
                    var data = $('#data').val();
                    var remark = $('#remark').val();
                    var unionID = $('#unionID').val() || oauthapp.appUser.unionID;
                    var platform = $('#platform').val() || oauthapp.appUser.platform;
                    var avatar = $('#avatar').val() || oauthapp.appUser.avatar;
                    var nickName = $('#nickName').val() || oauthapp.appUser.nickName;
                    var score = $('#score').val();
                    var maximumScore = $('#maximumScore').val();
                    oauthapp.rankSubmit(table, {
                        userID,
                        tags,
                        data,
                        remark,
                        unionID,
                        platform,
                        avatar,
                        nickName,
                        score,
                        maximumScore
                    }).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

