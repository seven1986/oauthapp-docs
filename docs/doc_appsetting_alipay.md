# 支付宝

???+ note "提示"

    在使用支付宝的相关功能之前，请确保已经开通支付宝PC支付[^1]和WAP支付产品[^2]。这些产品分别用于处理PC端和移动端的支付请求和交易。


## 说明

- [x] PC 支付
- [x] WAP 支付
- [x] 当面付（用户扫码）
- [x] 退款

## 配置项

### 支付成功返回页 

配置支付成功后用户将返回的页面。支付宝支付成功后，用户会跳转到该页面。

### 支付宝公钥 

配置支付宝的公钥，用于验证支付宝返回的数据的真实性。这个公钥是支付宝用于加密数据的公钥。

### 开发者私钥 

配置开发者的私钥，用于生成签名并对请求数据进行加密。这个私钥必须与支付宝进行通信的接口进行匹配。

### 应用ID 

配置支付宝分配给应用的唯一标识符，用于标识和识别您的应用。

通过适当地配置上述项，您可以启用支付宝的支付功能，让用户可以方便地在PC端和移动端进行支付操作。同时，当需要退款时，您也可以使用相关配置来实现退款功能。请确保配置项的准确性和安全性，避免敏感信息泄露。

## 截图

![](https://docs.oauthapp.com/doc_appsetting_alipay/1.png){ loading=lazy }


## 相关资源

- 如何获取支付宝公钥：[https://opensupport.alipay.com/support/helpcenter/207/201602487431](https://opensupport.alipay.com/support/helpcenter/207/201602487431)

- 支付宝接口排查工具：
[https://opensupport.alipay.com/support/checktoolst](https://opensupport.alipay.com/support/checktoolst)

- 如何生成及配置RSA2密钥：[https://opensupport.alipay.com/support/helpcenter/207/201602469554](https://opensupport.alipay.com/support/helpcenter/207/201602469554)

- 如何生成及配置公钥证书：[https://opensupport.alipay.com/support/helpcenter/207/201602471154](https://opensupport.alipay.com/support/helpcenter/207/201602471154)

[^1]:支付宝PC支付：[https://b.alipay.com/page/ar-center/merchant-sign/form?productCode=I1011000100000000005](https://b.alipay.com/page/ar-center/merchant-sign/form?productCode=I1011000100000000005)

[^2]:支付宝WAP支付：[https://b.alipay.com/page/ar-center/merchant-sign/form?productCode=I1011000100000000003](https://b.alipay.com/page/ar-center/merchant-sign/form?productCode=I1011000100000000003)