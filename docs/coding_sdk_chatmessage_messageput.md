---
tags:
  - 教程 - 消息 - 脚本库与API
---

# 修改消息


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
    <p><input type="text" id="dataId" placeholder="dataId" /></p>
    <p><input type="text" id="category" placeholder="category" /></p>
    <p><input type="text" id="tags" placeholder="tags" /></p>
    <p><input type="text" id="content" placeholder="content" /></p>
    <p><input type="text" id="remark" placeholder="remark" /></p>
    <p><input type="text" id="unionID" placeholder="unionID" /></p>
    <p><input type="text" id="nickName" placeholder="nickName" /></p>
    <p><input type="text" id="avatar" placeholder="avatar" /></p>
    <p><input type="text" id="platform" placeholder="platform" /></p>
    <p><input type="text" id="messageType" placeholder="TEXT/FILE/IMAGE" value="TEXT" /></p>
    <p><input type="number" value="1" id="showIndex" placeholder="showIndex" /></p>
    <p><button type="button" id="addButton">提交</button></p>
    <div>结果：<span id="result"></span></div>
    ```

这是一个包含多个文本输入框和一个提交按钮的 HTML 表单。输入框和按钮的描述如下：

 - table：输入要将数据存储到的表格的名称。

 - dataId：输入要更新或删除的数据行的 ID，对于添加数据的操作可以留空。

 - category：输入数据的分类。

 - tags：输入与数据相关的标签，可以是一个或多个。

 - content：输入数据的内容。

 - remark：输入数据的备注信息。

 - unionID：输入用户的联合 ID，对于未登录的用户可以留空。

 - nickName：输入用户的昵称。

 - avatar：输入用户的头像。

 - platform：输入用户使用的平台。

 - messageType：选择数据的类型，可以是 TEXT（文本）、FILE（文件）或 IMAGE（图片），默认为 TEXT。

 - showIndex：输入数据的显示顺序，默认为 1。

点击提交按钮后，表单将使用这些输入数据调用 addButton 函数。

## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('addButton').onclick = function () 
        {
            var table = $('#table').val();
            var dataId = $('#dataId').val();
            var category = $('#category').val();
            var tags = $('#tags').val();
            var content = $('#content').val();
            var remark = $('#remark').val();
            var unionID = $('#unionID').val()||oauthapp.appUser.unionID;
            var nickName = $('#nickName').val()||oauthapp.appUser.nickName;
            var avatar = $('#avatar').val()||oauthapp.appUser.avatar;
            var platform = $('#platform').val() ||oauthapp.appUser.platform;
            var messageType = $('#messageType').val();
            var showIndex = $('#showIndex').val();
            oauthapp.messagePut(table,dataId,{
                category,
                tags,
                content,
                remark,
                unionID,
                nickName,
                avatar,
                platform,
                messageType,
                showIndex
            }).then(function (res) {
               
            });
        }
    });
    ```

首先调用 oauthapp.allReady() 方法来确保 OAuthApp 对象已经初始化完毕，然后在 Promise 的回调函数中定义一个点击事件处理函数。

在点击事件处理函数中，通过 jQuery 的 val() 方法获取表单中用户输入的数据，并将这些数据传递给 oauthapp.messagePut() 方法。

oauthapp.messagePut() 方法用于更新指定数据表中的一条数据记录。其中，table 参数指定要操作的数据表，dataId 参数指定要更新的数据记录的 ID。

category、tags、content、remark、unionID、nickName、avatar、platform、messageType 和 showIndex 参数是要更新的数据字段。这些参数对应表单中的输入框。

最后，通过 then() 方法来注册一个回调函数，该回调函数将在数据更新成功后被调用。

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
        <title>messagePut</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p><input type="text" id="table" placeholder="table" /></p>
        <p><input type="text" id="dataId" placeholder="dataId" /></p>
        <p><input type="text" id="category" placeholder="category" /></p>
        <p><input type="text" id="tags" placeholder="tags" /></p>
        <p><input type="text" id="content" placeholder="content" /></p>
        <p><input type="text" id="remark" placeholder="remark" /></p>
        <p><input type="text" id="unionID" placeholder="unionID" /></p>
        <p><input type="text" id="nickName" placeholder="nickName" /></p>
        <p><input type="text" id="avatar" placeholder="avatar" /></p>
        <p><input type="text" id="platform" placeholder="platform" /></p>
        <p><input type="text" id="messageType" placeholder="TEXT/FILE/IMAGE" value="TEXT" /></p>
        <p><input type="number" value="1" id="showIndex" placeholder="showIndex" /></p>
        <p><button type="button" id="addButton">提交</button></p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('addButton').onclick = function () 
                {
                    var table = $('#table').val();
                    var dataId = $('#dataId').val();
                    var category = $('#category').val();
                    var tags = $('#tags').val();
                    var content = $('#content').val();
                    var remark = $('#remark').val();
                    var unionID = $('#unionID').val()||oauthapp.appUser.unionID;
                    var nickName = $('#nickName').val()||oauthapp.appUser.nickName;
                    var avatar = $('#avatar').val()||oauthapp.appUser.avatar;
                    var platform = $('#platform').val() ||oauthapp.appUser.platform;
                    var messageType = $('#messageType').val();
                    var showIndex = $('#showIndex').val();

                    oauthapp.messagePut(table,dataId,{
                        category,
                        tags,
                        content,
                        remark,
                        unionID,
                        nickName,
                        avatar,
                        platform,
                        messageType,
                        showIndex
                    }).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

