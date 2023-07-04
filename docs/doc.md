# 使用指南

## 创建项目

操作步骤：

1，点击“新项目” 

2，输入项目名称、描述，

3，点击创建

![image](https://2.fs.oauthapp.com/doc/1.png)

## 项目配置

### 服务器

功能说明：配置应用发布服务器清单

操作步骤：

1，点击“操作” 

2，点击“项目配置” 

3，点击“服务器”

![image](https://2.fs.oauthapp.com/doc/2.png)

![image](https://2.fs.oauthapp.com/doc/3.png)

### 小程序
功能说明：统一为应用配置微信小程序ClientID 、 ClientSecret。

操作步骤：

1，点击“操作” 

2，点击“项目配置” 

3，点击 “微信小程序”

![image](https://2.fs.oauthapp.com/doc/4.png)

![image](https://2.fs.oauthapp.com/doc/5.png)

### 项目配置
功能说明：使用 Vs Code 快速打开本地项目

操作步骤：

1，点击“操作” 

2，点击“项目配置” 

3，点击 “项目配置”

![image](https://2.fs.oauthapp.com/doc/6.png)

![image](https://2.fs.oauthapp.com/doc/7.png)

## 创建应用
操作步骤：

1，点击“创建应用” 

2，输入应用名称、站点路径、描述 

3，点击创建

![image](https://2.fs.oauthapp.com/doc/8.png)

![image](https://2.fs.oauthapp.com/doc/9.png)

## 应用管理
### 应用发布
功能描述：将本地文件夹的网页、图片、脚本发布到服务器。

操作步骤：

1，选择指定服务器，点击“发布” 

2，首次会弹出选择本地文件夹对话框，选择项目所在目录，点击确认 

3，输入”版本号“、“更新内容”，点击“确认”

![image](https://2.fs.oauthapp.com/doc/10.png)

![image](https://2.fs.oauthapp.com/doc/11.png)

![image](https://2.fs.oauthapp.com/doc/12.png)

### 发布通知

![image](https://2.fs.oauthapp.com/doc/59.png)

![image](https://2.fs.oauthapp.com/doc/60.png)

功能说明：应用发布成功后，通知到钉钉群。

操作步骤：

1，打开要接收发布通知的钉钉群、群设置、智能群助手、添加自定义机器人，复制机器人的access_token

2，打开应用配置、钉钉应用、机器人令牌，按照1行1个的格式，配置好后，提交更新即可

![image](https://2.fs.oauthapp.com/doc/61.png)

![image](https://2.fs.oauthapp.com/doc/62.png)

![image](https://2.fs.oauthapp.com/doc/63.png)

![image](https://2.fs.oauthapp.com/doc/64.png)

![image](https://2.fs.oauthapp.com/doc/65.png)

![image](https://2.fs.oauthapp.com/doc/66.png)

![image](https://2.fs.oauthapp.com/doc/67.png)

![image](https://2.fs.oauthapp.com/doc/68.png)

![image](https://2.fs.oauthapp.com/doc/69.png)

![image](https://2.fs.oauthapp.com/doc/70.png)

![image](https://2.fs.oauthapp.com/doc/71.png)


### 在线编辑
功能说明：在线编辑已发布到服务器上的文件

操作步骤：

1，选择已发布的服务器 

2，点击“编辑”按钮 

3，在弹出的模态窗口中，单击文件，进行编辑

![image](https://2.fs.oauthapp.com/doc/13.png)

### 版本管理
功能说明：查看发布历史版本、版本回滚。

操作步骤：

1，点击“服务器图标“，筛选该服务下的发布记录 

2，点击”版本号“ 

3，单击”预览备份“，查看下历史发布文件 / 单击”版本回滚“，将该历史版本发布到服务器。

![image](https://2.fs.oauthapp.com/doc/14.png)

### 基本信息
功能说明：设置应用的基本信息，如图标、描述、站点路径等。
操作步骤：

1，单击“应用图标” 

2，编辑相关信息 

3，单击 ”提交“保存

![image](https://2.fs.oauthapp.com/doc/15.png)

### 应用配置

模块说明：应用配置中心，所有功能的配置都在这里设置。

#### 角色管理
功能说明：定义用户可使用的角色。（定义角色后，可配置权限管理）

操作步骤：

1，点击”角色管理“ 

2，定义角色，1行1个角色 

3，点击”更新“保存设置

![image](https://2.fs.oauthapp.com/doc/16.png)

![image](https://2.fs.oauthapp.com/doc/17.png)

![image](https://2.fs.oauthapp.com/doc/18.png)

#### Azure 
功能说明：azure blob 上传文件

操作步骤：

1，点击“azure”

2，输入从azure 平台获取的azue blob 连接密钥字符串

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/19.png)

![image](https://2.fs.oauthapp.com/doc/20.png)

#### 钉钉应用
功能说明：

1，应用发布推送到钉钉群

2，oauthapp统一登陆，使用钉钉登录（限钉钉酷应用）

操作步骤：

1，点击“钉钉应用”

2，输入对应的配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/21.png)

![image](https://2.fs.oauthapp.com/doc/22.png)

#### Client

功能说明：oauthapp统一登陆，使用Web ID登录。

操作步骤：

1，点击“client”

2，输入对应的配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/23.png)

![image](https://2.fs.oauthapp.com/doc/24.png)

#### 微信小程序
功能说明：

1，发送订阅消息 

2，生成网页跳转地址 

3，获取小程序码 

4，oauthapp统一登录 

5，使用小程序扫码登录

操作步骤：

1，点击“微信小程序”

2，输入对应的配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/25.png)

![image](https://2.fs.oauthapp.com/doc/26.png)

#### 自定义
功能说明：自定义场景开发。需要开启配置节点接口权限

操作步骤：	

1，点击“自定义”

2，输入对应的配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/27.png)

![image](https://2.fs.oauthapp.com/doc/28.png)

#### 微信 H5 API配置
功能说明：初始化网页需要使用的JS SDK

操作步骤：

1，点击“微信H5 API配置”

2，输入对应的配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/29.png)

![image](https://2.fs.oauthapp.com/doc/30.png)

#### 应用分享配置
功能说明：自定义场景开发。需要开启配置节点接口权限

操作步骤：

1，点击“应用分享配置”

2，输入对应的配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/31.png)

![image](https://2.fs.oauthapp.com/doc/32.png)

#### QQ开放平台
功能说明：QQ oauth登录

操作步骤：

1，点击“QQ开放平台”

2，输入对应配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/33.png)

![image](https://2.fs.oauthapp.com/doc/34.png)

#### 微博开放平台
功能说明：微博oauth登录

操作步骤：

1，点击“微博开放平台”

2，输入对应配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/35.png)

![image](https://2.fs.oauthapp.com/doc/36.png)

#### 微信开放平台
功能说明：微信 网页PC端 扫码登录

操作步骤：

1，点击“微信开放平台”

2，输入对应配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/37.png)

![image](https://2.fs.oauthapp.com/doc/38.png)

#### 微信公众平台
功能说明：微信 APP H5 登录

操作步骤：

1，点击“微信公众平台”

2，输入对应配置项信息

3，点击“更新”

![image](https://2.fs.oauthapp.com/doc/39.png)

![image](https://2.fs.oauthapp.com/doc/40.png)

### 统计分析
功能说明：

1，查看每日新增用户数

2，按今日、7日、30日、90日查看模块接口访问量

3，查看站点流量、IP访问次数、服务器响应时间等指标

操作说明：

1，单击“操作”下拉菜单

2，单击“统计分析”

![image](https://2.fs.oauthapp.com/doc/41.png)

![image](https://2.fs.oauthapp.com/doc/42.png)

### 权限管理
功能说明：根据角色配置系统权限。

操作步骤：

1，单击“操作”下拉菜单

2，勾选角色对应的权限

3，单击“更新”

4，单击“用户”面板，勾选指定用户，依次点击“操作”、“设置角色”

5，选择对应角色，单击“确认”

![image](https://2.fs.oauthapp.com/doc/43.png)

![image](https://2.fs.oauthapp.com/doc/44.png)

### 数据备份
功能说明：针对当前应用整个数据库的，备份/还原/下载/上传操作。

操作步骤：

1，单击“操作”下拉菜单

2，单击“数据库备份”

3，单击“备份”，可为应用的整个数据库生成备份文件

4，单击“还原”，可将对应的备份数据库还原到当前应用

5，单击“删除”，可删除当前备份文件

6，单击“上传”，可从本地上传数据库文件

![image](https://2.fs.oauthapp.com/doc/45.png)

### 文件存储
功能说明：应用文件存储站点，可绑定独立域名。

操作步骤：

1，单击“存储”按钮

2，单击“新建文件夹”，可在当前目录创建文件夹

3，单击“上传文件”，可上传本地文件到站点

4，单击文件列表中的单个文件，可查看文件详情

![image](https://2.fs.oauthapp.com/doc/46.png)

### 用户
功能说明：应用的用户库模块

操作步骤：

1，单击“用户”按钮

2，单击“操作”下拉菜单

3，单击“设置角色”，可批量设置用户的角色

4，单击“导入用户”，可导入本地json用户数据到用户数据库

5，单击“导出用户”，可将用户数据导出为json格式为数据文件

6，单击“ID”列，可查看、编辑用户信息

7，单击“删除”，可删除指定用户

![image](https://2.fs.oauthapp.com/doc/47.png)

### 数据库
功能说明：应用的数据库存储模块。

操作步骤：

1，单击“数据库”按钮

2，单击“操作”图标按钮、“创建数据表”，可创建数据表

3，单击指定数据表，可查看数据列表

4，单击“ID”列，可编辑单条数据详情

5，单击“操作”下来菜单，可新增、导入、导出、清空、删除数据表

![image](https://2.fs.oauthapp.com/doc/48.png)

![image](https://2.fs.oauthapp.com/doc/49.png)

![image](https://2.fs.oauthapp.com/doc/50.png)

### 排行榜
功能说明：应用的排行榜模块。

操作步骤：

1，单击“排行榜”按钮

2，单击“操作”图标按钮，“创建榜单”，可创建一个榜单表

3，单击单个榜单，可查看排行榜信息

4，单击“操作”下拉菜单，可进行新增、导出、清空、删除数据

![image](https://2.fs.oauthapp.com/doc/51.png)

![image](https://2.fs.oauthapp.com/doc/52.png)

![image](https://2.fs.oauthapp.com/doc/53.png)

### 消息
功能说明：应用消息聊天室功能模块。

操作步骤：

1，单击“消息”按钮

2，单击“操作”图标按钮，“创建消息表”，可新建一张消息表

3，单击“操作”下拉菜单，可进行新增、导出、清空、删除删除

4，单击单条数据详情，可查看、编辑消息信息。

![image](https://2.fs.oauthapp.com/doc/54.png)

![image](https://2.fs.oauthapp.com/doc/55.png)

## 服务器
功能说明：公共、私有的web服务器，用于应用的发布托管

操作步骤：

1，单击“服务器”

2，单击“添加”/“删除”按钮，可启用对应的服务器。

3，单击“添加服务器”，可对接私有的web服务器（需要支持FTP协议）

![image](https://2.fs.oauthapp.com/doc/56.png)

![image](https://2.fs.oauthapp.com/doc/57.png)

## 证书管理
功能说明：管理私有的SSL证书。

操作步骤：

1，单击“上传证书”按钮

2，填写自定义名称，上传本地的“.Pfx”证书文件，并输入证书密码

3，单击“确认上传”

![image](https://2.fs.oauthapp.com/doc/58.png)