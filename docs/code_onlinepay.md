---
tags:
  - 功能应用
---

# 在线支付

## 说明

本文档提供了如何实现支付、订单相关的开发说明。

!!! quote "请确认您已开通支付宝 电脑网站支付[^1]、手机网站支付[^2]，并配置了 支付宝节点[^3]"

## 新建订单并支付

完整的的下单流程

``` mermaid
graph LR
  A[创建系统订单] --> B{成功};
  B -->|Yes| C[创建支付宝订单];
  C --> D{成功};
  D -->|Yes| F[跳转支付宝在线支付];
  D ---->|NO| G[提示错误信息];
  B ---->|No| E[提示错误信息];
```


步骤 1：创建系统订单，获取订单号。

需提供订单相关信息

| 参数 | 说明 |
| --- | --- |
| amount | 订单金额 |
| productType | 商品类型 |
| productID | 商品ID |
| productName | 商品名称 |

步骤 2：调用支付宝下单方法

在获取系统订单号后，就可以调用支付宝下单方法来生成支付宝订单。需提供订单相关信息

| 参数 | 说明 |
| --- | --- |
| orderNo | 系统订单号 |
| amount | 订单金额 |
| productName | 商品名称 |
| returnUrl | 返回URL |


=== "参考代码示例 Javascript"
    ```Javascript
    	// 系统订单请求参数
    	var orderData = {
    	    amount: 0.01,
    	    productType: "point",
    	    productID: "1",
    	    productName: "测试商品"
    	};

    	// 创建系统订单
    	oauthapp.orderCreate(orderData).then(res => {
    	    if (res.code != 200) {
    	        alert(res.err);
    	        return;
    	    }

            // 支付宝订单请求参数
            var alipayOrderData = {
    	        orderNo: res.data.orderNo,
    	        amount: orderData.amount,
    	        subject: orderData.productName,
    	        returnUrl: location.href
    	    };

    	    // 创建支付宝订单
    	    oauthapp.alipayCreateOrderPagePay(alipayOrderData).then(function(res2) {
    	        if (res2.code != 200) {
    	            alert(res2.err);
    	            return;
    	        }
    	        // 将支付宝返回的表单代码添加到页面并提交
    	        document.body.innerHTML = res2.data;
    	        setTimeout(() => {
    	            document.forms[0].submit();
    	        }, 500);
    	    });
    	});
    ```

以上代码示例中，首先调用[oauthapp.orderCreate](https://docs.oauthapp.com/framework_order/#_3)方法创建系统订单并获取订单号。接着传入**系统订单号（orderNo）、订单金额(amount)、商品名称(productName)、返回URL(returnUrl)**调用[oauthapp.alipayCreateOrderPagePay](https://docs.oauthapp.com/framework_alipay/#_2)方法创建支付宝订单。最后，将支付宝返回的表单代码添加到页面并提交表单，以进行支付流程。

## 已存在订单支付

在订单列表中，如果要为**待支付**状态的订单再次发起支付，可参考下面的流程：

``` mermaid
graph LR
  A[查询支付宝订单状态] --> B{查询成功};
  B -->|已支付 状态| C[提示已经支付];
  B ---->|非 已支付 状态| E[发起支付];
```


步骤 1：查询支付宝关联订单的交易状态

为了防止重复支付，首先需要查询支付宝关联的订单交易状态（防止重复支付）。通过调用[oauthapp.alipayOrder](https://docs.oauthapp.com/framework_alipay/#_4)订单查询方法，将系统订单号作为参数传入，获取支付宝订单的交易状态。

步骤 2：判断交易状态并发起支付

根据支付宝订单交易状态进行判断，如果交易状态不是**已支付**，则可以再次调用支付宝创建下单方法来发起支付。

=== "参考代码示例 Javascript"
    ```Javascript

    // 支付宝下单
    function payOrder(data) {
        oauthapp.alipayCreateOrderPagePay(data).then(function (res2) {
            if (res2.code != 200) {
                toast(res2.err, 'error');
                return;
            }

            document.body.innerHTML = res2.data;
            setTimeout(() => {
                document.forms[0].submit();
            }, 500);
        });
    }

    // orderItem是从订单列表接口返回的单个 json object
    // 根据系统订单号查询支付宝交易状态
    oauthapp.alipayOrder(orderItem.orderNo).then(res => {
        // 如果code不是200，代表不存在的交易
        if (res.code != 200) {
            // 创建支付宝订单，并支付
            payOrder({
                orderNo: orderItem.orderNo,
                amount: orderItem.amount,
                subject: orderItem.productName,
                returnUrl: location.href
            });
        }

        else {
            if (res.data.tradeStatus == 'TRADE_SUCCESS') {
                toast('订单已付款，无需再次支付。您可以刷新页面查看同步状态', 'success');
            }
            else {
                // 创建支付宝订单，并支付
                payOrder({
                    orderNo: orderItem.orderNo,
                    amount: orderItem.amount,
                    subject: orderItem.productName,
                    returnUrl: location.href
                });
            }
        }
    })
    ```

以上代码示例中，首先调用[oauthapp.alipayOrder](https://docs.oauthapp.com/framework_alipay/#_4)方法查询支付宝订单的交易状态。如果交易状态为**已支付**，则提示订单已付款；否则，调用封装好的**payOrder**函数创建支付宝订单并发起支付，然后将支付宝返回的表单代码添加到页面中，并提交表单。


## 支付成功着陆页

???+ note "提示"
    用户支付成功后支付宝会推送支付状态到后台并同步，因此在没有UI上的需求的情况下，您可以选择无需设置支付成功着陆页。
    但如果您有自定义的UI展示需求，可以按照以下步骤进行设置。

步骤 1：设置着陆页地址

在调用支付宝下单接口时，通过设置**返回URL(returnUrl)**参数，指定用户支付成功后自动跳转的地址。在用户支付成功后，支付宝会将相关参数附加在**返回URL(returnUrl)**中，并将用户重定向到该地址。

步骤 2：获取参数并展示

支付成功着陆页需要获取URL中的query参数，其中包含了支付宝的订单号及下单时间等相关参数。根据您的UI界面需求，可以提取这些参数并进行展示。

**如果担心支付宝的异步通知有延时**，页面可以立即调用[oauthapp.alipayReturnPageNotify](https://docs.oauthapp.com/framework_alipay/#_6)方法，同步订单号(TradeNo)、下单时间(OrderPayTime)两个字段。

> 系统订单的**支付状态**始终通过：支付宝异步通知、[oauthapp.alipayOrder](https://docs.oauthapp.com/framework_alipay/#_4)查询支付宝订单方法自动同步。

## 订单状态说明

| 状态码 | 说明 |
| --- | --- |
| TRADE_CLOSED | 交易关闭 |
| TRADE_FINISHED | 已完成 |
| TRADE_SUCCESS | 已支付 |
| WAIT_BUYER_PAY | 待支付 |

## 系统订单商品类型

???+ note "提示"
    **productType**为**point**时，支付成功后，将触发充值积分操作。
    积分与金额对应比率（后期将更新为自定义配置）

    - 9.9元 = 10,000积分
    - 19.9元 = 25,000积分
    - 99.9元 = 125,000积分

如果不需要充值积分，productType可以任意设置，仅作为查询订单的筛选条件。

[^1]:电脑网站支付:[https://open.alipay.com/api/detail?code=I1080300001000041203](https://open.alipay.com/api/detail?code=I1080300001000041203)

[^2]:手机网站支付:[https://open.alipay.com/api/detail?code=I1080300001000041949](https://open.alipay.com/api/detail?code=I1080300001000041949)

[^3]:支付宝配置：对接支付宝支产品，具体配置参考：[https://docs.oauthapp.com/doc_appsetting_alipay.html](https://docs.oauthapp.com/doc_appsetting_alipay.html)