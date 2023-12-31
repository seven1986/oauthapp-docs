# 自定义域名

## 域名管理

自定义域名功能允许您为您的应用程序绑定自定义的域名，使用户可以通过您提供的域名访问您的应用。在域名管理页面，您可以查看和管理已经添加的自定义域名。

操作步骤

1，单击下拉菜单中的“自定义域”

=== "图例 1-1"
    ![](https://docs.oauthapp.com/doc_app_domains/1-1.png){ loading=lazy }
=== "图例 1-2"
    ![](https://docs.oauthapp.com/doc_app_domains/1-2.png){ loading=lazy }

## 添加域名

要添加新的自定义域名，您需要在域名管理页面点击"添加域名"按钮，并填写所需的域名信息。添加成功后，系统将自动为您生成相应的CNAME记录或A记录，您只需要按照系统提供的指引在您的域名注册商或DNS服务商进行相应的配置即可。

操作步骤

1，单击“添加域名”

=== "图例 2-1"
    ![](https://docs.oauthapp.com/doc_app_domains/2-1.png){ loading=lazy }
=== "图例 2-2"
    ![](https://docs.oauthapp.com/doc_app_domains/2-2.png){ loading=lazy }
=== "图例 2-3"
    ![](https://docs.oauthapp.com/doc_app_domains/2-3.png){ loading=lazy }

## 上传证书

为了保证通信安全性，您可以选择上传SSL证书，从而启用HTTPS协议，保护用户数据和隐私。在上传证书页面，您可以选择上传您的SSL证书文件，并根据系统指引进行相应的配置。

操作步骤

1，单击“上传证书”

=== "图例 3-1"
    ![](https://docs.oauthapp.com/doc_app_domains/3-1.png){ loading=lazy }
=== "图例 3-2"
    ![](https://docs.oauthapp.com/doc_app_domains/3-2.png){ loading=lazy }

## 更改绑定证书

如果您需要更改绑定的SSL证书，您可以在更改绑定证书页面选择新的证书文件，系统将自动更新相应的证书配置，从而保证您的应用在使用新的证书进行加密通信。

操作步骤

1，单击域名右侧下拉菜单中的“更改绑定”

2，选择下拉菜单中的证书，点击“绑定证书”

=== "图例 4-1"
    ![](https://docs.oauthapp.com/doc_app_domains/4-1.png){ loading=lazy }
=== "图例 4-2"
    ![](https://docs.oauthapp.com/doc_app_domains/4-2.png){ loading=lazy }

## 删除绑定证书

如果您不再需要绑定某个SSL证书，您可以在删除绑定证书页面选择要删除的证书，并按照系统指引进行相应的操作。请注意，删除绑定证书后，相关的HTTPS配置将失效，建议在删除前确认不再需要该证书。

操作步骤

1，单击域名右侧下拉菜单中的“删除绑定”

=== "图例 5-1"
    ![](https://docs.oauthapp.com/doc_app_domains/5-1.png){ loading=lazy }

## 删除自定义域

如果您不再需要某个自定义域名，您可以在域名管理页面选择要删除的域名，并按照系统指引进行相应的操作。请注意，删除自定义域名后，该域名将不再被绑定到您的应用，用户将无法通过该域名访问您的应用。

操作步骤

1，单击域名右侧下拉菜单中的“删除自定义域”

=== "图例 6-1"
    ![](https://docs.oauthapp.com/doc_app_domains/6-1.png){ loading=lazy }