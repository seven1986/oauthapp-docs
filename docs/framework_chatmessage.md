---
tags:
  - 客户端
---

# 消息

### 消息表集合

获取当前应用中所有的消息表名称

???+ note "提示"
    消息表是用来存储不同类型消息的，例如：系统通知、私信消息、好友申请等等。这个方法可以用于列举所有的消息表，以便其他方法可以对指定的表进行增删改查等操作。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.messageTables().then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>messageTables</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.messageTables().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                })
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/messageTables.html){ .md-button }
    [教程](https://docs.oauthapp.com/coding_sdk_chatmessage_messagetables/){ .md-button }
    


### 消息分类

获取指定消息表中的所有消息分类

???+ note "提示"
    消息分类是对消息进行分组管理的方式之一，可以将相关主题的消息放在同一分类下，方便用户进行查看和管理。
    该方法返回一个 Promise 对象，当获取成功时，Promise 对象的状态为 resolved，返回一个数组，包含所有分类名称。如果获取失败，Promise 对象的状态为 rejected，返回一个错误对象。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.messageCategories(table).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

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
    [演示](https://web.oauthapp.com/4/examples/apidemo/messageCategories.html){ .md-button }
    [教程](https://docs.oauthapp.com/coding_sdk_chatmessage_messagecategories/){ .md-button }
    
| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| table | 表名称  |  |


### 消息列表

获取指定消息表中的消息列表。

???+ note "提示"
    你可以选择按照消息组、标签、关键词搜索、以及分页的方式来获取消息列表。
    返回一个 Promise 对象，解析结果为一个消息数组，其中每个元素都包含消息的详细信息，例如消息 ID、分类、标签、内容、备注、创建时间等。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.messages(table,category,tag, search, take,skip).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
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
    [演示](https://web.oauthapp.com/4/examples/apidemo/messages.html){ .md-button }
    [教程](https://docs.oauthapp.com/coding_sdk_chatmessage_messages/){ .md-button }
    

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| table | 表名称  |  |
| category | 消息组  |  |
| tag | 消息标签  |  |
| search | 查询关键词  |  |
| take | 拉取条数 | 10 |
| skip | 跳过条数 | 0 |

### 发送消息

 向指定消息表中添加一条新的消息。需要提供消息的分类、标签、内容等相关信息。

???+ note "提示"
    该方法返回一个 Promise 对象，如果消息发布成功，Promise 对象会 resolve，返回新发布的消息的 ID；否则会 reject，返回错误信息。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.messagePost(table,msgData).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
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
    [演示](https://web.oauthapp.com/4/examples/apidemo/messagePost.html){ .md-button }
    [教程](https://docs.oauthapp.com/coding_sdk_chatmessage_messagepost/){ .md-button }
    

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| table | 消息所在的表名称。  |  |
| msgData.category | 消息分类。  |  |
| msgData.tags | 消息标签，用英文逗号分隔。  |  |
| msgData.content | 消息内容。  |  |
| msgData.remark | 消息备注。 |  |
| msgData.unionId | 第三方平台的用户ID。 | 可以使用 oauthapp.settings.fingerIdentity 或者自定义 |
| msgData.nickName | 用户昵称 |  |
| msgData.avatar | 用户头像 |  |
| msgData.platform | 第三方平台标识字符串  | 可以是 web、weibo、weixin、qq 或者自定义。 |
| msgData.messageType | 消息类型  | 可以是 TEXT、IMAGE、FILE 或者自定义 |
| msgData.showIndex | 排序  |  |

### 修改消息

修改指定消息表中的一条消息。需要提供需要修改的消息的ID，以及修改后的分类、标签、内容等相关信息。

???+ note "提示"
    修改成功时返回一个 JSON 对象，其中包含一个字段 success 表示是否修改成功，如果修改失败，还会包含一个 error 字段表示错误信息。

=== "API"

    ```JavaScript linenums="1"
    oauthapp.messagePut(table,id,msgData).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
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
    [演示](https://web.oauthapp.com/4/examples/apidemo/messagePut.html){ .md-button }
    [教程](https://docs.oauthapp.com/coding_sdk_chatmessage_messageput/){ .md-button }
    

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| table | 字符串，必填项，表示消息所在的表名。  |  |
| id |  字符串，必填项，表示待修改消息的 ID。  |  |
| msgData.category | 字符串，选填项，表示消息分类。  |  |
| msgData.tags | 字符串数组，选填项，表示消息标签。  |  |
| msgData.content |  字符串，必填项，表示消息内容。  |  |
| msgData.remark | 字符串，选填项，表示消息备注。 |  |
| msgData.unionID | 字符串，必填项，表示第三方平台的用户 ID。 | 可以使用 oauthapp.settings.fingerIdentity 表示当前用户的 ID。 |
| msgData.nickName | 字符串，必填项，表示用户昵称。 |  |
| msgData.avatar | 用户头像 |  |
| msgData.platform | 第三方平台标识字符串 | 可以是 web、weibo、weixin、qq 或者自定义。 |
| msgData.messageType | 消息类型  | 可以是 TEXT、IMAGE、FILE 或者自定义 |
| msgData.showIndex | 排序  |  |

### 删除消息

删除指定消息表中的一条消息。需要提供需要删除的消息的ID。

???+ note "提示"
    该方法将返回一个 Promise，其中包含更新成功或失败的信息
    
=== "API"

    ```JavaScript linenums="1"
    oauthapp.messageDelete(table,id).then(function(res){
        console.log(res);
    });
    ```

=== "示例代码"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>messageDelete</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="table" placeholder="table" />
            <input type="number" id="dataId" placeholder="id" />
            <button type="button" id="deleteButton">删除</button>
        </div>
        <p>结果：<span id="result"></span></p>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('deleteButton').onclick = function () {
                    var  table = $('#table').val();
                    var  dataId = $('#dataId').val();
                    oauthapp.messageDelete(table,dataId).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```
    [演示](https://web.oauthapp.com/4/examples/apidemo/messageDelete.html){ .md-button }
    [教程](https://docs.oauthapp.com/coding_sdk_chatmessage_messagedelete/){ .md-button }
    

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| table | 表名称  |  |
| id | 消息ID  |  |
