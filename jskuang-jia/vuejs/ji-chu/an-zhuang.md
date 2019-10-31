# 安装

**兼容性**

Vue.js 不支持 IE8 及其以下版本

**直接引入**

下载或CDN并用&lt;script&gt;标签引入.Vue会被注册为一个全局变量.

> **开发板和生产版 - 在开发时请用开发版本，遇到常见错误它会给出友好的警告。**

**NPM**

```
$ npm install vue
```

更好的和Webpack或Browserify模块打包器配合使用 .

**命令行工具**

官方提供的命令行工具 .

> 查看快速使用中Vue-cli的内容

### 对不同构建版本的解释

**一些属于**

* 完整版 - 同时包含编译器和运行时的构建
* 编译器 - 用来将模板字符串编译成为JS渲染函数的代码
* 运行时 - 用来创建Vue实例 , 渲染并处理virtual DOM等行为的代码 . 基本上就是除去编译器的其他一切 .

* UMD - UMD构建可以直接通过&lt;script&gt;标签用在浏览器中 .

* CommonJS - CommonJS构建用来配合老的打包工具比如browserify或webpack 1 . 这些打包工具的默认文件\(pkg.main\)只包含运行时的CommonJS构建 . 
* ES Module - 这个构建用来配合现代的打包工具比如webpack 2 或rollup . 这些打包工具的默认文件\(pkg.module\)只包含运行时的ES Module构建 . 

**运行时+编译器 VS 只包含运行时**

如果需要线上编译模板 , 就需要加上编译器 , 即完整版的构建 .

编译模板的意思是 , 比如传入一个字符串的template选项 , 或者挂在到一个元素上并以其内部的HTML作为模板 .

```
// 需要编译器
new Vue({
  template: '<div>{{ hi }}</div>'
})
// 不需要编译器
new Vue({
  render (h) {
    return h('div', this.hi)
  }
})
```

当使用vue-loader或vueify的时候 , \*.vue这种文件内部的模板会在构建时预编译成JS的. 所以最终打好的包里实际上市不需编译器的 , 只用运行时构建即可 .

因为运行时构建比完整版小了30%的体积 , 最好用这个版本 . 如果要使用完整版构建 , 可以在打包工具里配置 .

```
# Webpack
module.exports = {
  // ...
  resolve: {
    alias: {
      'vue$': 'vue/dist/vue.esm.js' // 'vue/dist/vue.common.js' for webpack 1
    }
  }
}
```

**开发环境 VS 生产环境\(两种模式\)**

开发环境和生产环境都是UMD硬编码建构的 , 区别值是压缩和不压缩代码 .

CommonJS和ES Module构建都是给打包工具用的 , 这里不提供压缩后的版本 , 他们都保留了原始的process.env.NODE\_ENV检测 , 用来判断是开发模式还是生产模式 . 可以用打包工具\(Webpack\)来控制process.env.NODE\_ENV来达到开发和生产环境的切换 , 还可以让UglifyJS之类的压缩工具判断仅供开发环境的一些代码片 , 可以减少最终打包文件的尺寸 .

```
# Webpack
var webpack = require('webpack')
module.exports = {
  // ...
  plugins: [
    // ...
    new webpack.DefinePlugin({
      'process.env': {
        NODE_ENV: JSON.stringify('production')
      }
    })
  ]
}
```

**CSP环境兼容**

使用Webpack+vue-loader或Browserify+vueify构建 , 在CSP环境中模板都会被编译到render函数中 , 完美决绝了兼容问题 .

> CSP - 强制应用内容安全策略 . 例如Google Chrome Apps . 不能使用new Function\(\)对表达式求职 .

---

**最新版本 - 到Github上**

```
git clone https://github.com/vuejs/vue.git node_modules/vue
cd node_modules/vue
npm install
npm run build
```

**AMD模块加载器**

所有 UMD 构建都可以直接用作 AMD 模块 .

这里有一篇延伸关于模块的文章 :

[http://web.jobbole.com/82238/](http://web.jobbole.com/82238/)

