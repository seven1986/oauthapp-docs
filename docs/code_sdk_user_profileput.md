---
tags:
  - 教程 - 用户 - 脚本库与API
---

# 更新个人信息

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
        <div id="userProfile"></div>
        <p>
            昵称
            <input type="text" id="nickName" />
        </p>
        <p>
            头像
            <img id="userAvatar" width="64px" />
            <button type="button" class="btn btn-link" onclick="uploadImage()">上传头像</button>
        </p>
        <div>
            <textarea id="data" rows="10" placeholder=" 自定义数据"></textarea>
        </div>
        <div>
            <button type="button" onclick="updateProfile()">更新用户资料</button>
        </div>
    </div>
    ```

这是一个包含用户个人资料信息的HTML表单，其中包括用户的昵称、头像、自定义数据等信息。页面上显示了用户当前的昵称和头像，以及一个用于上传新头像的按钮。
用户可以在自定义数据文本框中输入任意文本。此外，还有一个更新用户资料的按钮，点击该按钮将会调用相应的JavaScript函数来更新用户的个人资料。


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
     oauthapp.allReady().then(function () {
         $('#userProfile').html(`
         <p>ID： ${oauthapp.appUser.id}<br />
         账号：${oauthapp.appUser.userName}<br />
         邮箱：${oauthapp.appUser.email}, ${oauthapp.appUser.emailIsValid ? '已验证' : ''}<br />
         手机：${oauthapp.appUser.phone}, ${oauthapp.appUser.phoneIsValid ? '已验证' : ''}<br />
         来源：${oauthapp.appUser.platform}<br />
         unionID：${oauthapp.appUser.unionID}<br />
         角色：${oauthapp.appUser.role}<br />
         加入时间：${oauthapp.appUser.createDate}<br />
         最后更新：${oauthapp.appUser.lastUpdate}</p>`);
         $('#data').val(oauthapp.appUser.data);
         $('#nickName').val(oauthapp.appUser.nickName);
         $('#userAvatar').attr('src', oauthapp.appUser.avatar);
     })

     function uploadImage() {
         var ele = document.createElement('input');
         ele.type = 'file';
         ele.onchange = function (_event) {
             oauthapp.upload(event.target.files[0]).then(function (res) {
                 oauthapp.appUser.avatar = JSON.parse(res).data;
                 $('#userAvatar').attr('src', oauthapp.appUser.avatar);
             });
         };
         ele.click();
     }

     function updateProfile() {
         var nickName = document.getElementById('nickName').value;
         var data = document.getElementById('data').value;
         oauthapp.profilePut(oauthapp.appUser.avatar, nickName, data).then(function (res) {
            
         });
     }
    ```

此代码片段实现了一个用户资料的页面，其中包括显示用户的个人信息、修改用户的昵称、上传头像、以及编辑自定义数据并更新用户资料。

代码中首先通过 oauthapp.allReady() 方法确保用户已经登录并且授权应用的全部权限。接下来，将用户的信息展示在 #userProfile 元素中，并且将用户的头像、昵称和自定义数据加载到页面的对应元素中。

如果用户点击了“上传头像”按钮，代码将创建一个文件选择器，用户可以选择要上传的图片。选择后，通过 oauthapp.upload() 方法上传图片并更新用户头像。

最后，如果用户点击“更新用户资料”按钮，代码将获取用户输入的昵称和自定义数据，然后通过 oauthapp.profilePut() 方法将这些数据更新到用户资料中。

## 步骤四：测试结果

=== "Javascript"
    ```Javascript
     alert(JSON.stringify(res));
    ```



## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>profilePut</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    <body>
        <div>
            <div id="userProfile"></div>
            <p>
                昵称
                <input type="text" id="nickName" />
            </p>
            <p>
                头像
                <img id="userAvatar" width="64px" />
                <button type="button" class="btn btn-link" onclick="uploadImage()">上传头像</button>
            </p>
            <div>

                <textarea id="data" rows="10" placeholder=" 自定义数据"></textarea>
            </div>
            <div>
                <button type="button" onclick="updateProfile()">更新用户资料</button>
            </div>
        </div>
        <script type="text/javascript">
            oauthapp.allReady().then(function () {
                $('#userProfile').html(`
                <p>ID： ${oauthapp.appUser.id}<br />
                账号：${oauthapp.appUser.userName}<br />
                邮箱：${oauthapp.appUser.email}, ${oauthapp.appUser.emailIsValid ? '已验证' : ''}<br />
                手机：${oauthapp.appUser.phone}, ${oauthapp.appUser.phoneIsValid ? '已验证' : ''}<br />
                来源：${oauthapp.appUser.platform}<br />
                unionID：${oauthapp.appUser.unionID}<br />
                角色：${oauthapp.appUser.role}<br />
                加入时间：${oauthapp.appUser.createDate}<br />
                最后更新：${oauthapp.appUser.lastUpdate}</p>`);
                $('#data').val(oauthapp.appUser.data);
                $('#nickName').val(oauthapp.appUser.nickName);
                $('#userAvatar').attr('src', oauthapp.appUser.avatar);
            })

            function uploadImage() {
                var ele = document.createElement('input');
                ele.type = 'file';
                ele.onchange = function (_event) {
                    oauthapp.upload(event.target.files[0]).then(function (res) {
                        oauthapp.appUser.avatar = JSON.parse(res).data;
                        $('#userAvatar').attr('src', oauthapp.appUser.avatar);
                    });
                };
                ele.click();
            }

            function updateProfile() {
                var nickName = document.getElementById('nickName').value;
                var data = document.getElementById('data').value;
                oauthapp.profilePut(oauthapp.appUser.avatar, nickName, data).then(function (res) {
                    alert(JSON.stringify(res));
                });
            }
        </script>
    </body>
    </html>
    ```