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

#### 用 npm run 执行任意命令

前面已经生成了package.json文件 , 里面包含script字段 :

```
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1"
},
```

现在运行测试项目的命令 , 看看错误输出 :

```
npm run test
npm test
npm t
```

和test一样 , start也是npm内置支持的命令 , 但是也需要在scripts字段中声明一下 , 没有声明则会直接报错 .

npm run实际上是npm run-script命令的简写 , 运行步骤基本是 :

* 从package.json文件读取scripts对象里面的全部配置
* 以传给npm run的第一个参数为键 , 在scripts对象里面获取对应的值作为要执行的命令
* 在系统默认的shell中执行前面的命令

流程中还可以设置hook机制 .

举个例子 , package.json的内容如下 :

```
{
  "name": "my-npm-script",
  "devDependencies": {
    "eslint": "latest"
  },
  "scripts": {
    "eslint": "eslint **.js"
  }
}
```

直接运行npm run , 会列出可执行的所有命令列表 . 运行npm run eslint会在shell中运行eslint \*\*.js

> 这里执行命令的时候 , 会自动调用环境变量 , 也就是./node\_modules/.bin/eslint \*\*.js

#### 创建自定义npm script



