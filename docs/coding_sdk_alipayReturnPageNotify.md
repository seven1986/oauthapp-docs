---
tags:
  - 教程 - 支付宝 - 脚本库与API
---

# 支付同步通知

用户在支付宝完成支付后，回携带订单相关参数回跳指定的地址，可参考如下示例，同步支付宝回传的订单号、付款时间2个字段。

**您可以继续调用oauthapp.alipayOrder同步支付宝订单信息，或等待支付宝异步通知自动同步订单数据**


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
    <textarea rows="10" id="postData">
        {
            "charset": "UTF-8",
            "out_trade_no": "1687167960218",
            "method": "alipay.trade.page.pay.return",
            "total_amount": "0.01",
            "sign": "UCXw1EQGluYUXrJF+891QFeM0VdZslt+ejxz88MiBHKlFg1nH1hgsWam3hmAyaKvWF4GIfsB       +GwZRBvOpEoyO8bjefLZswOJ9hLSyxQe4ZON8PaJe4R6k1WEZ6nEkU3qIqxZj5ubN13kUvEOeJMkOA1oNvjszLgs13Uso3AmZ1GFC+1nTt      +hOemwrPH0D2OsYkuBKqooQtgKIJyXfGuAFBDm3KW6xx716tbwnXgU840N89LkkX97YjX0yinHy9yh0BnNkIQpj/dKFTWIifq0prH7WR/    2kBIVuXnAUsE7UX7/  y9vuyEdThnkcT3cR5Fn6Gg3Iiin5wg1BUHo3A2jFZg==",
            "trade_no": "2023061922001406381432294248",
            "auth_app_id": "2021003192659285",
            "version": "1.0",
            "app_id": "2021003192659285",
            "sign_type": "RSA2",
            "seller_id": "2088502858687065",
            "timestamp": "2023-06-19 17:47:02"
        }
    </textarea>
    <button type="button" id="actionButton">提交</button>
    <p>结果</p>
    <div id="result"></div>
    ```


## 步骤三：调用方法

=== "Javascript"
    ```Javascript
    oauthapp.alipayReturnPageNotify(data)
    ```



## 步骤三：测试结果

=== "Javascript"
    ```Javascript
    $('#result').html(JSON.stringify(res));
    ```


## 完整代码示例

=== "HTML"
    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>alipayReturnPageNotify</title>
        <!-- data-appid 属性替换为你的 OAuthApp 应用的 ID -->
        <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="2"></script>
    </head>

    <body>
        <textarea rows="10" id="postData">
            {
                "charset": "UTF-8",
                "out_trade_no": "1687167960218",
                "method": "alipay.trade.page.pay.return",
                "total_amount": "0.01",
                "sign": "UCXw1EQGluYUXrJF+891QFeM0VdZslt+ejxz88MiBHKlFg1nH1hgsWam3hmAyaKvWF4GIfsB       +GwZRBvOpEoyO8bjefLZswOJ9hLSyxQe4ZON8PaJe4R6k1WEZ6nEkU3qIqxZj5ubN13kUvEOeJMkOA1oNvjszLgs13Uso3AmZ1GFC+1nTt      +hOemwrPH0D2OsYkuBKqooQtgKIJyXfGuAFBDm3KW6xx716tbwnXgU840N89LkkX97YjX0yinHy9yh0BnNkIQpj/dKFTWIifq0prH7WR/    2kBIVuXnAUsE7UX7/  y9vuyEdThnkcT3cR5Fn6Gg3Iiin5wg1BUHo3A2jFZg==",
                "trade_no": "2023061922001406381432294248",
                "auth_app_id": "2021003192659285",
                "version": "1.0",
                "app_id": "2021003192659285",
                "sign_type": "RSA2",
                "seller_id": "2088502858687065",
                "timestamp": "2023-06-19 17:47:02"
            }
        </textarea>
        <button type="button" id="actionButton">提交</button>
        <p>结果</p>
        <div id="result"></div>
        <script>

            oauthapp.allReady().then(function () {

                document.getElementById('actionButton').onclick = function () {

                    var data = JSON.parse(document.getElementById('postData').value);

                    oauthapp.alipayReturnPageNotify(data).then((res) => {

                        console.log(res);

                        $('#result').html(JSON.stringify(res));

                        // 查询支付宝订单详情，下发支付成功消息
                        // oauthapp.alipayOrder(data.out_trade_no).then((res2) => {
                        //     console.log(res2);
                        //     $('#result').html(JSON.stringify(res2));
                        //     //替换 url
                        //     history.replaceState(null, null, '?completed=true');
                        // })
                    })
                };
            });
        </script>
    </body>
    </html>
    ```

