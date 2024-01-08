# 文档 1.1

!!! warning "该文档已废弃"

**oauthapp.js 已包含如下脚本库，无需再次引入。**

| 名称 | 版本 | 说明 |
| ----------- | ----------- | ----------- |
| jquery | 3.6.1 | https://github.com/jquery/jquery |
| fingerprintjs2 | 2.1.5 | https://github.com/Valve/fingerprintjs2.git |
| js-cookie | 3.0.1 | https://github.com/js-cookie/js-cookie |


## 应用初始化

!!! note ""
    先[创建应用](https://www.oauthapp.com/tenant/index) ，然后复制下面代码到html文件的**head**标签内，并替换 **{{appid}}** 。

``` HTML
<script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="{{appid}}"></script>
```

### 获取应用信息

该方法会自动重置页面的title、icon、描述信息，具体可在后台配置。

=== "HTML"
``` HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.9.8.js" data-appid="{{appid}}"></script>
    <script type="text/javascript">
        oauthapp.ready().then(function () {
            console.log(oauthapp.app);
        })
</script>
</head>
<body>
</body>
</html>
```

## 用户

### 获取用户信息

自动登录用户（新用户会根据web指纹自动注册）。

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.allReady().then(function(){
        console.log(oauthapp.app);
        console.log(oauthapp.appUser);
    })
</script>
```

### 更新用户资料

!!! note ""
    参数为自定义的json对象。

=== "HTML"
``` HTML
<script type="text/javascript">
     oauthapp.profilePut({a:1,b:2,c:3}).then(function(res){
        console.log(res)
    });
</script>
```

## 排行榜

### 榜单集合

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.ranks().then(function(res){
        console.log(res)
    });
</script>
```

### 单个榜单数据

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.rank({{rankKey}}, {{platform}}, {{take}}).then(function(res){
        console.log(res)
    });
</script>
```


| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| rankKey | 是 | 自定义的榜单key字符串(小写字母+数字，6-32位) |
| platform | 是 | 默认为：web，可自定义 |
| take | 否 | 默认为：10 |

### 提交分数

会根据rankKey自动创建榜单。

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.rankSubmit({{rankKey}}, {{data}}).then(function(res){
        console.log(res)
    });
</script>
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| rankKey | 是 | 自定义的榜单key字符串(小写字母+数字，6-32位) |
| data | 是 | JSON类型，字段如下： |

```json
 {
   unionID: oauthapp.appUser.unionID,
   avatar: oauthapp.appUser.avatar,
   nickName: oauthapp.appUser.nickName,
   platform: 'web',
   score: 100,
   data: JSON.stringify({ a: 1, b: 2, c: 3, d: 4 })  // 自定义数据
 }
```



### 我的排名

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.rankOfMe({{rankKey}}, {{platform}}, {{unionid}}).then(function(res){
        console.log(res)
    })
</script>
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| rankKey | 是 | 自定义的榜单key字符串(小写字母+数字，6-32位) |
| platform | 是 | 默认为：web，可自定义 |
| unionid | 是 | 用户的unionid |

## 数据库

### 数据表集合

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.tables().then(function(res){
        console.log(res)
    })
</script>
```

### 查询数据

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.table({{tableName}}, {{filter}}, {{sort}},{{take}},{{skip}}).then(function(res){
        console.log(res)
    })
</script>
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| tableName | 是 | 自定义的榜单key字符串(小写字母+数字，6-32位) |
| filter | 否 | json格式，如{id:"1"} |
| sort | 否 | json格式，如{id:true} |
| take | 否 | 拉取数据条数，默认10 |
| skip | 否 | 跳过数据条数，默认0 |


### 添加数据

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.tablePost({{tableName}}, {{jsonStr}}).then(function(res){
        console.log(res)
    })
</script>
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| tableName | 是 | 自定义的榜单key字符串(小写字母+数字，6-32位) |
| jsonStr | 是 | json字符串 |


### 删除数据

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.tableDelete({{id}}).then(function(res){
        console.log(res)
    })
</script>
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| id | 是 | 数据的ID |

### 更新数据

=== "HTML"
``` HTML
<script type="text/javascript">
    oauthapp.tablePut({{id}}, {{jsonStr}}).then(function(res){
        console.log(res)
    })
</script>
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| id | 是 | 数据的ID |
| jsonStr | 是 | json字符串 |
