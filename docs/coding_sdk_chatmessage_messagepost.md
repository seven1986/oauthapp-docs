---
tags:
  - 开发教程 - 消息
---

# 发送消息


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

这段代码展示了一个包含多个输入框和一个提交按钮的HTML表单。每个输入框都有一个占位符和一个唯一的ID来标识它们。其中包含的输入框包括：

 - "table"：用于输入数据表的名称。
 
 - "category"：用于输入信息分类的标签。

 - "tags"：用于输入额外的信息标签，以逗号分隔。

 - "content"：用于输入消息内容。

 - "remark"：用于输入消息的备注信息。

 - "unionID"：用于输入用户的唯一标识符。

 - "nickName"：用于输入用户的昵称。

 - "avatar"：用于输入用户头像的URL。

 - "platform"：用于输入用户平台的名称。

 - "messageType"：用于选择消息的类型（文本、文件或图像）。
 
 - "showIndex"：用于输入消息在列表中的显示顺序。

当用户填写这些字段并点击提交按钮时，会执行一个JavaScript函数来将这些值发送到服务器。提交按钮的单击事件已经绑定到该函数。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        document.getElementById('addButton').onclick = function () 
        {
            var table = $('#table').val();
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
            oauthapp.messagePost(table,{
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

这段代码是使用OAuthApp SDK在前端页面上添加聊天消息的代码。首先使用oauthapp.allReady()方法确保SDK已准备就绪。

然后在按钮点击事件中获取页面输入的聊天信息，并使用oauthapp.messagePost()方法将其提交到指定的聊天表中。

其中，table代表聊天表名称，category代表聊天组名称，tags代表消息标签，content代表消息内容，remark代表备注信息，unionID代表用户唯一ID，nickName代表用户昵称，avatar代表用户头像，platform代表所在平台，messageType代表消息类型，showIndex代表在聊天界面中展示的顺序。最后使用then()方法来处理提交结果。

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
        <title>messagePost</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
           <p><input type="text" id="table" placeholder="table" /></p>
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

                    oauthapp.messagePost(table,{
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

