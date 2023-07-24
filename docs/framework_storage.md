---
tags:
  - 文档
---

# 数据库

### 数据表集合

oauthapp.tables

???+ note "提示"
    获取当前用户可访问的数据表集合。该方法不需要传入参数，会返回一个包含当前用户可访问的数据表集合的数组，每个数组元素代表1个表名。
=== "方法"

    ```JavaScript linenums="1"
    oauthapp.tables().then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>tables</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.tables().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                })
            });
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/tables.html){ .md-button }   [教程](https://docs.oauthapp.com/coding_sdk_storage_tables.html){ .md-button }


### 创建数据表

oauthapp.tableCreate

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.tableCreate(table, uniqueData).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>创建数据表</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></ script>
    </head>
    <body>
        <div>
            <h3>创建数据表</h3>
            <p>table：<input type="text" id="table" /></p>
            <p>uniqueData:<input type="checkbox" id="uniqueData" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var table = $('#table').val();
                    var uniqueData = document.getElementById('uniqueData').checked;
                    oauthapp.tableCreate(table, uniqueData).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                });
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | table | 表名称 |  |
    | uniqueData | 防重复数据 | 默认为false |

[演示](https://web.oauthapp.com/4/examples/apidemo/tableCreate.html){ .md-button }  
<!-- [教程](){ .md-button } -->

### 单表查询

oauthapp.table

???+ note "提示"
    用于查询指定表中的数据，返回一个 Promise 对象，当 Promise 对象 resolve 时，返回一个数组，数组中的每个元素都是一个数据记录。每个数据记录是一个对象，它的属性是表中的字段名，属性值是对应的字段值。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.table(table,tag,filter,sort,take,skip).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML linenums="1"
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
            <input type="text" id="sort" placeholder='排序条件	{"id":true}' />
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | table | 必需，指定要查询的表的名称。 |  |
    | tag | 可选，指定要查询的标签。 | 可空 |
    | filter | 可选，指定要筛选的条件。它应该是一个对象，对象的属性名是要筛选的字段名，属性值是对应的值。 | {"name":"123"} |
    | sort | 可选，指定数据的排序方式。它应该是一个对象，对象的属性名是要排序的字段名，属性值是 true 或 false，true 表示升序排列，false 表示降序排列。 | {"id":true} |
    | take | 可选，指定要拉取的数据条数。 | 10 |
    | skip | 可选，指定要跳过的数据条数。 | 0 |

[演示](https://web.oauthapp.com/4/examples/apidemo/table.html){ .md-button }    [教程](https://docs.oauthapp.com/coding_sdk_storage_table.html){ .md-button }


### 提交数据

oauthapp.tablePost

数据为自定义JSON对象。

???+ note "提示"
    用于向指定的数据表 table 中提交一条数据记录。该方法返回一个 Promise 对象，可使用 .then() 方法来获取提交数据的结果。

=== "方法"

    ```JavaScript linenums="1"
     // 示例：
     // 假设我们有一个名为 user 的数据表，
     // 有 name 和 age 两个字段。我们可以使用以下代码将一条数据记录提交到该表中：
    
    let table = "user";
    let data = { 
        showIndex:0, // 排序
        tags:"", // 自定义标签
        //content字段可传入自定义json
        content: {
            "name": "Tom",
            "age": 20
        }
    };

    let jsonString = JSON.stringify(data);
    
    oauthapp.tablePost(table, jsonString).then(function(res) {
        console.log(res);
    });

    // 在上述代码中，我们首先定义了要提交数据的数据表名称 table 和要提交的数据记录 data，
    // 然后将 data 转换为 JSON 字符串格式，并将其作为参数传递给 oauthapp.tablePost() 方法。
    // 当提交成功后，我们在 .then() 方法中打印了返回结果 res。
    ```

=== "示例"

    ```HTML linenums="1"
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

=== "参数说明"

    | 参数  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | table | 表名称 |  |
    | jsonString | 字符串形式的json数据 | 格式： {showIndex:0,tags:"",content: {a:1,b:2}}  //showIndex 排序，tags 标签 content 自定义json |


[演示](https://web.oauthapp.com/4/examples/apidemo/tablePost.html){ .md-button }    [教程](https://docs.oauthapp.com/coding_sdk_storage_tablepost.html){ .md-button }
    


### 数据详情

oauthapp.tableDetail

用于获取指定数据表中的某一条数据记录的详细信息。

???+ note "提示"
    该方法返回一个 Promise 对象，它的 then() 方法接受一个参数，即获取到的数据记录的详细信息，以 JSON 格式表示。数据记录的详细信息包含该记录的所有属性和属性值。如果查询失败，则会返回一个错误信息。

=== "方法"

    ```JavaScript linenums="1"
    //示例：

    //假设我们有一个名为 "users" 的数据表，其中每个数据记录表示一个用户，拥有以下属性：

    //id: 用户的唯一标识符；
    //name: 用户名；
    //email: 用户邮箱；
    //age: 用户年龄。
    //如果我们要获取 id 为 1 的用户的详细信息，可以使用以下代码：

    oauthapp.tableDetail("users", 1).then(function(user) {
        console.log(user);
    }).catch(function(error) {
      console.error(error);
    });

    //该方法会返回一个 Promise 对象。如果查询成功，则会在控制台打印出如下内容：
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>tableDetail</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>
            <input type="text" id="table" placeholder="数据表名称" />
            <input type="number" id="dataId" placeholder="id" />
            <button type="button" id="queryButton">查询</button>
        </p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var  table = $('#table').val();
                    var  dataId = $('#dataId').val();
                    oauthapp.tableDetail(table,dataId).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 名称  | 说明 | 参数 |
    | ----------- | ----------- | ----------- |
    | table | 表名称 |  |
    | id | 数据ID |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/tableDetail.html){ .md-button }  [教程](https://docs.oauthapp.com/coding_sdk_storage_tabledetail.html){ .md-button }


### 删除数据

oauthapp.tableDelete

用于删除指定表格中的数据。

???+ note "提示"
    返回一个 Promise 对象，在 Promise 中返回删除结果。

=== "方法"

    ```JavaScript linenums="1"
     oauthapp.tableDelete('table1', 123)
    .then(function(res){
        console.log(res);
    });

    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>tableDelete</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <p>
            <input type="text" id="table" placeholder="数据表名称" />
            <input type="number" id="dataId" placeholder="id" />
            <button type="button" id="deleteButton">删除</button>
        </p>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('deleteButton').onclick = function () {
                    var  table = $('#table').val();
                    var  dataId = $('#dataId').val();
                    oauthapp.tableDelete(table,dataId).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 名称  | 说明 | 参数 |
    | ----------- | ----------- | ----------- |
    | table | 表名称 |  |
    | id | 数据ID |  |


[演示](https://web.oauthapp.com/4/examples/apidemo/tableDelete.html){ .md-button }  [教程](https://docs.oauthapp.com/coding_sdk_storage_tabledelete.html){ .md-button }


### 更新数据

oauthapp.tablePut

用于更新一条数据表中指定 ID 的记录。

???+ note "提示"
    该方法将返回一个 Promise，其中包含更新成功或失败的信息。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.tablePut('myTable', '123', '{"name": "NewName", "age": 25}')
    .then(function(res) {
        console.log(res);
    });

    // 上述代码将更新 myTable 表中 ID 为 123 的记录的 name 和 age 字段。
    // 更新的内容为 { "name": "NewName", "age": 25 }。
    // 注意，这里的 jsonString 参数必须是一个有效的 JSON 字符串。
    // 如果格式不正确，可能会导致更新失败。同时，如果要更新的记录不存在，也会导致更新失败。
    ```

=== "示例"

    ```HTML linenums="1"
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

=== "参数说明"

    | 名称  | 说明 | 参数 |
    | ----------- | ----------- | ----------- |
    | table | 表名称 |  |
    | id | 数据ID |  |
    | jsonString | 字符串形式的json数据 | 格式： {showIndex:0,tags:"",content: {a:1,b:2}}  //showIndex 排序，tags 标签 content 自定义json |

[演示](https://web.oauthapp.com/4/examples/apidemo/tablePut.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_storage_tableput.html){ .md-button }