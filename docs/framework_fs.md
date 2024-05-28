---
tags:
  - 文档
---

# 存储

### 上传文件

oauthapp.upload

???+ note "提示"
    用于将文件上传到OAuthApp服务器上，并返回上传后的文件路径

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.upload(file,path).then(function(res){
        console.log(res);
    })
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>upload</title>
      <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
      <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
      <div>选择文件：<input id="fileUploader" type="file"></div>
      <div>结果：<span id="result"></span></div>
      <script>
        oauthapp.allReady().then(function () {
          document.getElementById('fileUploader').onchange = function (event) {
            var file = event.target.files[0];
            oauthapp.upload(file).then(function (res) {
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
    | file | 上传表单文件的file  |  |
    | path | 上传路径，可空  |  |
    | service | 存储服务  | 默认为空，或填写：**azure** （需先配置azure blob密钥） |

[演示](https://web.oauthapp.com/4/examples/apidemo/upload.html){ .md-button } [教程](https://docs.oauthapp.com/coding_sdk_fs_upload.html){ .md-button }


### 删除文件

oauthapp.fsDelete

=== "方法"

    ```JavaScript linenums="1"
    oauthapp.fsDelete(path).then(function(res){
        console.log(res);
    })
    ```

=== "示例"

    ```HTML linenums="1"
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>删除文件</title>
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></   script>
    </head>
    <body>
        <div>
            <h3>删除文件</h3>
            <p>path：<input type="text" id="path" /></p>
            <p>
                <button type="button" id="actionButton">提交</button>
            </p>
        </div>
        <div id="result"></div>
        <script>
            oauthapp.ready().then(function () {
                $('#actionButton').click(function () {
                    var path = $('#path').val();
                    oauthapp.fsDelete(path).then(function (res) {
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
    | path | 文件或文件夹的路径，必填  |  |

[演示](https://web.oauthapp.com/4/examples/apidemo/fsDelete.html){ .md-button } 
<!-- [教程](https://docs.oauthapp.com/coding_sdk_fs_upload/){ .md-button } -->