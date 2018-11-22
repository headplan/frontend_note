# 初识npm script

#### 用npm init快速创建项目

npm为我们提供了快速创建package.json文件的命令npm init , 执行该命令会问几个基本问题 , 如包名称、版本号、作者信息、入口文件、仓库地址、许可协议等 , 多数问题已经提供了默认值 , 可以在问题后敲回车接受默认值 :

```
package name: (test)
version: (1.0.0)
description: test
entry point: (index.js)
test command:
git repository:
keywords: npm, script
author: test
license: (ISC)
```

填写完基本的内容之后 , 会把文件内容打出来 :

```
{
  "name": "test",
  "version": "1.0.0",
  "description": "test",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "npm",
    "script"
  ],
  "author": "test",
  "license": "ISC"
}
```

生成package.json文件 .

文件可以用编辑器编辑 , 或者使用npm init再次修改 , npm默认不会覆盖修改里面已经存在的信息 . 要快速生成package.json文件也可以添加参数 , 直接生成 :

```
npm init --yes
# 或
npm init -f
npm init --force
```

初始化package.json时的字段默认值可以自定义配置 :

```
npm config set init.author.email "headplan@163.com"
npm config set init.author.name "headplan"
npm config set init.author.url "https://github.com/headplan"
npm config set init.license "MIT"
npm config set init.version "0.1.0"
```

现在初始化就可以直接`npm init --yes`了 . 重试一下命令 :

```
mkdir my-npm-script && cd $_
npm init # 生成
npm init --yes # 重排
```



