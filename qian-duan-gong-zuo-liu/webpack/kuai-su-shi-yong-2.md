# 引入VueJS

```
cnpm install vue vue-loader vue-html-loader vue-style-loader vue-template-compiler --save-dev
```

引入loader , 把vue文件交给vue-loader处理

```
{
    test: /\.vue$/,
    use: ['vue-loader']
}
```

创建Vue模板

```
# js/components/test.vue
<template>
    <h1>{{ msg }}</h1>
<template>
<script>
export default {
    data(){
        return {
            msg: 'Test Vue'
        }
    }
}
</script>
```

主文件实例化VueJS

```
# 引入Vue
import Vue from 'vue/dist/vue.js';
# 引入组件
import Headers from './components/test.vue';

var vm = new Vue({
  el: '#app',
    components:{
      Headers
    }
});
```

```
# 配置引入路径
import Vue from 'vue/dist/vue.js';
import Headers from './components/test.vue';

# 改为
import Vue from 'vue';
import Headers from './components/test';

# 修改webpack配置
resolve: {
  extensions: ['.js', '.vue', '.json'],
  alias: {
    'vue$': 'vue/dist/vue.js',
  }
},
# extensions省略后缀
# alias引入路径
```

在HTML中引入组件标签

```
<div id="app">
  <Headers></Headers>
</div>
```

---

# Webpack常用命令

```
webpack --display-modules # 在输出时显示所有加载的模块(包括排除的也显示)
webpack --display-modules --display-reasons # 把模块加载的require的地方也显示出来
webpack -d # 发生错误时提供debug和devtool(webpack配置中的devtool:sourcemap)
webpack -p # 对webpack打包后的文件进行压缩
# 这里会有一个无法压缩的报错,原因是es6版本无法转换.
# 修改webpack配置,把babel-loader中的配置放到.babelrc中就好了
{
    test: /\.js$/,
    use:
    [
        {
            loader: 'babel-loader',
            options: 
            {
                presets: ['es2015','stage-0'],
                plugins: ['transform-runtime']
            }
        }
    ],
    exclude: [/(node_modules|bower_components)/],
},
webpack -w # 调用watch方法,实时进行打包更新.之后就不用一直webpack打包了.
```

```
# 实现热加载,即保存即刷新页面
# 安装webpack-dev-server
cnpm install webpack-dev-server --save-dev
# 启动(这里没有全局安装,使用硬路径)
node_modules/.bin/webpack-dev-server --inline --hot
```



