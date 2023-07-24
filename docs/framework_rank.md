---
tags:
  - 文档
---

# 排行榜

### 榜单集合

oauthapp.ranks

榜单的名称集合

???+ note "提示"
    该方法将返回一个 Promise 对象，可通过 then() 方法将获取一个包含所有榜单名称的数组。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.ranks().then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>ranks</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                oauthapp.ranks().then(function (res) {
                    $('#result').text(JSON.stringify(res));
                })
            });
        </script>
    </body>
    </html>
    ```

[演示](https://web.oauthapp.com/4/examples/apidemo/ranks.html){ .md-button }    [教程](https://docs.oauthapp.com/coding_sdk_rank_ranks.html){ .md-button }

### 创建榜单

oauthapp.rankCreate

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.rankCreate(table).then(function(res){
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
        <title>创建榜单</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <h3>创建榜单</h3>
            <p>table：<input type="text" id="table" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var table = $('#table').val();
                    oauthapp.rankCreate(table).then(function (res) {
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

[演示](https://web.oauthapp.com/4/examples/apidemo/rankCreate.html){ .md-button }  
<!-- [教程](){ .md-button } -->
    
### 榜单数据

oauthapp.rank

用于查询指定榜单上的数据

???+ note "提示"
    该方法会返回一个 Promise 对象，成功时会返回榜单数据。如果失败，Promise 对象会被拒绝并返回错误信息

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.rank(table, platform, unionId,nickName, tag, skip,take).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

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

=== "参数说明"

    | 名称  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | table | 字符串类型，必填，指定要查询的榜单名称。 |  |
    | platform | 字符串类型，可选，第三方平台标识字符串，  | 如"web"、"weibo"、"wexin"、"qq"等。如果不传递该参  数，则默认为"web"，表示当前应用的网站平台。 |
    | unionId | 字符串类型，可选，第三方平台的用户ID。 | 如果不传递该参数，则默认为当前登录用户的ID。 |
    | nickName | 字符串类型，可选，用户昵称。 |  |
    | tag | 字符串类型，可选，自定义标签。 |  |
    | skip | 数字类型，可选，表示要跳过的记录数 | 默认为0 |
    | take | 数字类型，可选，表示要获取的记录数 | 默认为10 |

[演示](https://web.oauthapp.com/4/examples/apidemo/rank.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_rank_rank.html){ .md-button }


### 榜单统计

oauthapp.rankStatistics

查看指定榜单的的统计信息。

???+ note "提示"
    用于获取指定榜单，包括当前榜单总人数、总分数、最高分数、平均分数等。该方法需要传入榜单名称作为参数，
    该方法返回一个Promise对象，当Promise对象的状态变为resolved时，会返回一个包含统计信息的JSON对象

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.rankStatistics(table).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

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

=== "参数说明"

    | 名称  | 说明 | 参数 |
    | ----------- | ----------- | ----------- |
    | table | 榜单名称 | 必须 |

[演示](https://web.oauthapp.com/4/examples/apidemo/rankStatistics.html){ .md-button }   [教程](https://docs.oauthapp.com/coding_sdk_rank_rankstatistics.html){ .md-button }


### 用户排名 / 我的排名

oauthapp.rankOfUser

获取当前用户在指定榜单上的排名情况，或者获取指定 unionid 的用户在指定榜单上的排名情况。

???+ note "提示"
    返回一个 Promise 对象，成功时会返回包含用户在指定榜单上的排名信息的对象

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.rankOfUser(table, platform, unionid).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>rankOfMe</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <input type="text" id="table" placeholder="table" />
            <input type="text" id="platform" placeholder="platform" />
            <input type="text" id="unionid" placeholder="unionid" />
            <button type="button" id="queryButton">查询</button>
        </div>
        <div>结果：<span id="result"></span></div>
        <script>
            oauthapp.allReady().then(function () {
                document.getElementById('queryButton').onclick = function () {
                    var table = $('#table').val();
                    var platform = $('#platform').val();
                    var unionid = $('#unionid').val();
                    oauthapp.rankOfUser(table, platform, unionid).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    })
                }
            });
        </script>
    </body>
    </html>
    ```

=== "参数说明"

    | 名称  | 说明 |  |
    | ----------- | ----------- | ----------- |
    | table | 榜单名称，必填。 |  |
    | platform | 第三方平台标识字符串  | 可空（web、weibo、wexin、qq / 自定义），默认读取当前登录用户platform |
    | unionId | 第三方平台的用户ID  | 可空（oauthapp.settings.fingerIdentity / 自定义），默认读取当前登录用户platform  |

[演示](https://web.oauthapp.com/4/examples/apidemo/rankOfUser.html){ .md-button }   [教程](https://docs.oauthapp.com/coding_sdk_rank_rankofuser.html){ .md-button }


### 提交分数

oauthapp.rankSubmit

提交分数到指定的榜单中

???+ note "提示"
    如果提交的分数已经存在于榜单中，则会更新该用户的分数和其他信息。

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.rankSubmit(table,jsonData).then(function(res){
        console.log(res);
    });
    ```

=== "示例"

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

=== "参数说明"

    | 名称  | 说明 | 参数 |
    | ----------- | ----------- | ----------- |
    | table | 榜单名称 |  |
    | jsonData.tags | 自定义标签  |  |
    | jsonData.platform | 第三方平台标识字符串  | web、weibo、wexin、qq / 自定义 |
    | jsonData.unionID | 第三方平台的用户ID  | oauthapp.settings.fingerIdentity / 自定义 |
    | jsonData.score | 分数 |  |
    | jsonData.maximumScore | 最高分数 |  |
    | jsonData.remark | 备注 |  |
    | jsonData.nickName | 用户昵称 |  |
    | jsonData.avatar | 用户头像 |  |
    | jsonData.data | 字符串形式JSON对象 |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/rankSubmit.html){ .md-button }   [教程](https://docs.oauthapp.com/coding_sdk_rank_ranksubmit.html){ .md-button }