# 文档 1.0

!!! warning "该文档已废弃"

oauthapp 1.0.js 文件封装了所有接口，可直接引入到项目文件中，进行开发。



## 应用初始化

!!! note ""
    先去 [创建应用](https://www.oauthapp.com/tenant/index) ，然后替换 **{{appid}}** 。

``` HTML
<script id="appcore" src="https://www.oauthapp.com/lib/sdk/oauthapp.1.0.0.js" data-appid="{{appid}}"></script>
```


   
   
**框架已集成如下脚本库，无需再次引入。**

| 名称 | 版本 | 说明 |
| ----------- | ----------- | ----------- |
| jquery | 3.5.0 | https://github.com/jquery/jquery |
| fingerprintjs2 | 2.1.0 | https://github.com/Valve/fingerprintjs2.git |
| js-cookie | 2.1.2 | https://github.com/js-cookie/js-cookie |
| jweixin | 1.6.0 | http://res2.wx.qq.com/open/js/jweixin-1.6.0.js |

## 用户

### 获取应用、用户信息

=== "JavaScript"
``` JavaScript
    $(async () => {
         // 自动注册用户
         await AppOnReady(true);
         // 只获取应用数据 await AppOnReady();
         console.log(App);
         console.log(AppUser);
    })
```

### 更新用户资料

!!! note ""
    参数为自定义的json对象。

=== "JavaScript"
``` JavaScript
     PutProfile({a:1,b:2,c:3}).then(x =>{
        console.log(x)
    });
```

## 排行榜

### 榜单集合

=== "JavaScript"
``` JavaScript
    AppRanks().then(x=>{
        console.log(x)
    });
```

### 单个榜单数据

=== "JavaScript"
``` JavaScript
    AppRank({{rankKey}}, {{platform}}, {{take}}).then(x=>{
        console.log(x)
    });
```


| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| rankKey | 是 | 自定义的榜单key字符串 |
| platform | 是 | 默认为：web，可自定义 |
| take | 否 | 默认为：10 |

### 提交分数

=== "JavaScript"
``` JavaScript
    AppRankPostScore({{rankKey}}, {{data}}).then(x=>{
        console.log(x)
    });
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| rankKey | 是 | 自定义的榜单key字符串 |
| data | 是 | JSON类型，字段如下： |

```json
 {
   unionID: AppUser.unionID,
   avatar: AppUser.avatar,
   nickName: AppUser.nickName,
   platform: 'web',
   score: 100,
   data: JSON.stringify({ a: 1, b: 2, c: 3, d: 4 })  // 自定义数据
 }
```



### 我的排名

=== "JavaScript"
``` JavaScript
    AppRankMyIndex({{rankKey}}, {{platform}}, {{unionid}}).then(x=>{
        console.log(x)
    })
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| rankKey | 是 | 自定义的榜单key字符串 |
| platform | 是 | 默认为：web，可自定义 |
| unionid | 是 | 用户的unionid |

## 数据库

### 数据表集合

=== "JavaScript"
``` JavaScript
    AppStorageTables().then(x=>{
        console.log(x)
    })
```

### 查询数据

=== "JavaScript"
``` JavaScript
    AppStorage({{tableName}}, {{filter}}, {{sort}},{{take}},{{skip}}).then(x=>{
        console.log(x)
    })
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| tableName | 是 | 自定义的榜单key字符串 |
| filter | 否 | json格式，如{id:"1"} |
| sort | 否 | json格式，如{id:true} |
| take | 否 | 拉取数据条数，默认10 |
| skip | 否 | 跳过数据条数，默认0 |


### 添加数据

=== "JavaScript"
``` JavaScript
    AppStoragePost({{tableName}}, {{jsonStr}}).then(x=>{
        console.log(x)
    })
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| tableName | 是 | 自定义的榜单key字符串 |
| jsonStr | 是 | json字符串 |


### 删除数据

=== "JavaScript"
``` JavaScript
    AppStorageDelete({{id}}).then(x=>{
        console.log(x)
    })
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| id | 是 | 数据的ID |

### 更新数据

=== "JavaScript"
``` JavaScript
    AppStoragePut({{id}}, {{jsonStr}}).then(x=>{
        console.log(x)
    })
```

| 参数 | 必传 | 说明 |
| ----------- | ----------- | ----------- |
| id | 是 | 数据的ID |
| jsonStr | 是 | json字符串 |

## 属性

### AppData

应用数据（需在AppOnReady方法后使用）

### AppUser

用户数据（需在AppOnReady方法后使用）