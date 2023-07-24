---
tags:
  - 开发教程 - 订单
---

# 创建订单


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
    <p>结果</p>
    <div id="result"></div>
    ```


## 步骤三：调用方法

在成功创建订单后，您将获得订单的ID和支付二维码链接，用于支付宝扫码支付。

参数

- amount（必填）：商品金额，最小值为0.01元。

- productType（必填）：point 或自定义，如果为point，支付成功后将自动充值积分，并产生充值记录。

- productID（必填）：自定义。

- productName（必填）：商品名称。

在上述示例中，通过调用 oauthapp.orderCreate() 方法并传入相应的参数，即可创建订单。成功创建订单后，将返回包含订单ID和支付二维码链接的数据结构。您可以根据需要对返回的数据进行处理和展示。

> 请注意，amount 参数表示订单的商品金额，最小值为0.01元，而 productName 参数则表示订单中商品的名称。根据实际需求，您可以自行设置这些参数的值。

=== "Javascript"
    ```Javascript
    oauthapp.allReady().then(function () {
        oauthapp.orderCreate({amount:0.01,productType:"point",productID:"1",productName:"测试商品"}).then(function (res) {
            $('#result').text(JSON.stringify(res));
        });
    });
    ```



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
        <title>orderCreate</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>
    
    <body>
        <label>订单金额</label>
        <input type="text" id="amount" value="0.01" />
    
        <label>商品类型</label>
        <input type="text" id="productType" value="point" />
    
        <label>商品ID</label>
        <input type="text" id="productID" value="1" />
    
        <label>商品名称</label>
        <input type="text" id="productName" value="测试商品" />
    
        <button type="button" id="actionButton">提交</button>
    
        <p>结果</p>
        <div id="result"></div>
        <script>
            oauthapp.allReady().then(function () {
            
                document.getElementById('actionButton').onclick = function () {
                
                    var postData = {};
                    postData.amount = $('#amount').val() || 0.01;
                    postData.productType = $('#productType').val();
                    postData.productID = $('#productID').val();
                    postData.productName = $('#productName').val();
    
                    oauthapp.orderCreate(postData).then(function (res) {
                        $('#result').text(JSON.stringify(res));
                    });
                }
            });
        </script>
    </body>
    </html>
    ```

