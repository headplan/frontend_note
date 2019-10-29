# webpack快速使用

**安装与使用**

```
# 如果安装了cnpm可以使用cnpm安装
# npm install cnpm -g --registry=https://registry.npm.taobao.org
# 全局安装
cnpm install --global webpack
# 安装完成查看帮助
webpack -h
# 创建Learning_Webpack
# 命令行进入目录,使用webpack打包
webpack js/entry.js bundle.js
# 第一参数是入口文件,就是需要打包的都有哪些文件的列表,第二个是打包输出的文件
# 执行成功,现在在浏览器中访问页面,里面js中两个输出log的命令就输出了日志
# js文件的内容是
./js
./entry.js
require('./module-one.js');
require('./module-two.js');
./module-one.js
console.log('Module One');
./module-two.js
console.log('Module Two');
```

**引入配置文件**

```
# 创建配置文件
touch webpack.config.js
# 下面是一个简单的基本配置
module.exports = {
    devtool: "sourcemap", # 生成时加载的开发工具,一个映射关系的工具
    entry: "./js/entry.js", # 入口文件
    output: {
        filename: "bundle.js" # 输出的文件名
    }
};
# 如果有配置文件,执行命令时就不用指定入口和输出的文件名之类的了,直接运行webpack
webpack
# 运行之后会生成两个文件
bundle.js
bundle.js.map
```

**引入其他框架**

这里我们尝试引入jquery,这也体现了使用webpack的好处,这里引入jquery,只会在使用到他的时候才加载

```
# 初始化npm
npm init
# 这里和composer一样,会生成一个package.json文件
# 然后安装jquery
cnpm install jquery --save-dev
# 修改module-one.js文件,简单使用jquery
var $ = require('jquery');
$('h1').html('Hello Baby!');
```

此时再访问index.html时,遇到了h1标签,才会去加载jquery,其他时候都不会去加载jquery.

**loader机制**

> 在面对静态文件多种多样的应用场景之下 , Webpack 提供了 loaders 的机制来实现对不同类型的静态文件进行打包 , 这样不仅可以减少 http 请求 , 也对文件压缩进行了优化 .

```
# 先安装两个loader
cnpm install css-loader style-loader --save-dev
```

设置不同的文件使用不同的loader

```
module.exports = {
    devtool: "sourcemap",
    entry: "./js/entry.js",
    output: {
        filename: "bundle.js"
    }
    module: {
        # 这里是旧版本的用法,也就是webpack1.0的用法
        loaders: [
            {
                test: /\.css$/,
                loader: "style!css"
            }
        ]
        # 在webpack2.0中应该这样写
        rules: [{
            test: /\.css$/,
            use: [ 'style-loader', 'css-loader' ]
        }]
    }
};
```

使用babel转码器

> Babel是一个广泛使用的转码器 , 可以将ES6代码转为ES5代码 , 从而在现有环境执行 .

```
# 安装loader
cnpm install babel-loader babel-core babel-preset-es2015 webpack --save-dev
```

> 注意 : 由于npm@3 , npm不推荐peerDependencies的自动安装自动安装 , 所以需要对等依赖关系像 babel-core 和 webpack 必须在你的package.json中明确列出 . 最后添加了webpack就不会报错了 .

**配置babel**

```
module.exports = {
  // …

  module: {
    rules: [
      {
        test: /\.js$/,
        use: 
        [
          {
            loader: 'babel-loader',
            options: {
              presets: ['es2015'],
            }
          }
        ],
        // babel-loader 执行很慢的话,可以排除node_modules文件夹或其他不需要的源文件
        exclude: [/(node_modules|bower_components)/],
      },
    ],
  },
};
```

```
# 其中选项还可以写成这样传参的方式.
babel-loader?presets[]=es2015
# 还可以写成webpack1.0的方式,这里是用query传入的参数
module: {
  loaders: [
    {
      test: /\.js$/,
      exclude: /(node_modules|bower_components)/,
      loader: 'babel-loader',
      query: {
        presets: ['es2015']
      }
    }
  ]
}
# 其他babel参数参考Loaders中的资料整理
```

其他可以做的

```
# 引入 babel runtime 作为一个独立模块，来避免重复引入
cnpm install babel-runtime --save
cnpm install babel-plugin-transform-runtime --save-dev
# 安装stage-0插件对ES7一些提案的支持,具体查看babel-loader下的资料
cnpm install babel-preset-stage-0 --save-dev
# 修改配置文件
options: {
    presets: ['es2015','stage-0'],
    plugins: ['transform-runtime']
}
```

**loader的inline加载**

```
# 文件引入时使用
require('!style-loader!css-loader!../css/style.css');
```



