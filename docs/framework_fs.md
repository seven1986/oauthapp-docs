---
tags:
  - 客户端
---

# 存储

### 上传文件

???+ note "提示"
    用于将文件上传到OAuthApp服务器上，并返回上传后的文件路径

=== "API"

    ```JavaScript linenums="1"
    oauthapp.upload(file,path).then(function(res){
        console.log(res);
    })
    ```

=== "示例代码"

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
    [演示](https://web.oauthapp.com/4/examples/apidemo/upload.html){ .md-button }
    [教程](https://docs.oauthapp.com/coding_sdk_fs_upload/){ .md-button }

| 参数  | 说明 |  |
| ----------- | ----------- | ----------- |
| file | 上传表单文件的file  |  |
| path | 上传路径，可空  |  |
| service | 存储服务  | 默认为空，或填写：**azure** （需先配置azure blob密钥） |
