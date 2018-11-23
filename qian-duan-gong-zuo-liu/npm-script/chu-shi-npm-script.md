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

前面已经生成了package文件 , 也知道了怎么写npm script . 现在在项目中添加eslint脚本 , 它是一个javascript风格检查工具 , 提供了很多现成的规则集 , 比如google , airbnb .

添加eslint自定义脚本的步骤 :

**创建index.js文件 , 写入**

```js
const str = 'Hello World';

function fn()
{
    console.log('Hello World');
}
```

**添加eslint依赖**

将eslint添加为devDependencies

```
npm install eslint -D
```

**初始化eslint配置**

首先需要配置规则集 , 存放规则集的文件就是配置文件

```
./node_modules/.bin/eslint --init
```

> 为了提高可移植性 , 把eslint安装为项目依赖而非全局命令

根据提示回答几个问题

```
./node_modules/.bin/eslint --init
? How would you like to configure ESLint? Answer questions about your style
? Which version of ECMAScript do you use? ES2015
? Are you using ES6 modules? No
? Where will your code run? Node
? Do you use JSX? No
? What style of indentation do you use? Spaces
? What quotes do you use for strings? Single
? What line endings do you use? Unix
? Do you require semicolons? Yes
? What format do you want your config file to be in? JavaScript
Successfully created .eslintrc.js file in /Users/test
```

最后生成配置文件.eslintrc.js

```js
module.exports = {
    "env": {
        "es6": true,
        "node": true
    },
    "extends": "eslint:recommended",
    "parserOptions": {
        "ecmaVersion": 2015
    },
    "rules": {
        "indent": [
            "error",
            4
        ],
        "linebreak-style": [
            "error",
            "unix"
        ],
        "quotes": [
            "error",
            "single"
        ],
        "semi": [
            "error",
            "always"
        ]
    }
};
```

**添加eslint命令**

```js
{
  "name": "my-npm-script",
  "devDependencies": {
    "eslint": "^5.9.0"
  },
  "scripts": {
    "eslint": "eslint *.js"
  },
  "version": "0.1.0",
  "main": "index.js",
  "author": "headplan <headplan@163.com> (https://github.com/headplan)",
  "license": "MIT",
  "keywords": [],
  "description": ""
}
```

**运行eslint**

```
npm run eslint
```

输出结果可以看到 , 有三处不符合官方推荐的规范

```js
npm run eslint

> my-npm-script@0.1.0 eslint /Users/test
> eslint *.js


/Users/test/index.js
  1:7   error  'str' is assigned a value but never used  no-unused-vars
  3:10  error  'fn' is defined but never used            no-unused-vars
  5:5   error  Unexpected console statement              no-console
```

**eslint检查主流前端框架react , vue.js**

使用 eslint-plugin-react 检查 react 代码 , 使用 react-plugin-react-native 检查 react-native 代码 , 可以直接使用 eslint-config-airbnb , 里面内置了 eslint-plugin-react , 新人常遇到 peerDependencies 安装失败问题可参照 npmjs 主页上的如下方法解决 :

```
(
  export PKG=eslint-config-airbnb;
  npm info "$PKG@latest" peerDependencies --json | command sed 's/[\{\},]//g ; s/: /@/g' | xargs npm install --save-dev "$PKG@latest"
)
```

eslint 规则集的官方仓库都列出了各自支持的规则 , 可以在.eslintrc文件中配置 . 

