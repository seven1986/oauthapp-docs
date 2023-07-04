# 代码生成器

## 1，上传zip压缩包方式

 创建生成器后，上传zip压缩包，然后得到网址。

![上传zip压缩包](https://blob.oauthapp.com/4/app/2/codegen/1.png)

 粘贴网址到代码框，完成制作

![复制网址](https://blob.oauthapp.com/4/app/2/codegen/2.png)

## 2，代码方式

实现 **async function codegen** 方法

=== "Javascript"
    ``` javascript
    // 实现该方法体
    async function codegen(swaggerUri) {
        return [
            {path:'a.txt',content:'hello world'},
            {path:'dist/b.txt',content:'hello world'},
            {path:'dist/dist/c.txt',content:'hello world'},
            {path:'img/a.json',content:'hello world'},
        ];
    }
    ```
 粘贴代码到代码框，完成制作

![复制网址](https://blob.oauthapp.com/4/app/2/codegen/3.png)