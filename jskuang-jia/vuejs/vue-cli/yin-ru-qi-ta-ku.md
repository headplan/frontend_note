# 引入其他库

**CSS文件引入**

```
# 直接在模板或入口组件引入即可
<link ...>
# 组件
<style>
@import ' ... .css'
</style>
```

**JS文件引入**

```
# 可以在想引入的地方引入,这里的路径可以直接写npm安装的地址,或者完整的路径
# 也可以在build/webpack.base.conf.js中创建alias
import {} from '路径'

# 还有一种方式就是全局加载的方式,同样配置build/webpack.base.conf.js文件
# 全局加载webpack内置插件
plugins: [
  new webpack.ProvidePlugin({
    $: "jquery",
    jQuery: "jquery",
  }),
]

# 针对jQuery的引入看下面的资料,因为jQuery的$变量在组件中总是找不到给出了解决方案
# 官方解决方案:https://webpack.js.org/loaders/expose-loader/
# 重新声明变量:http://blog.csdn.net/yiifaa/article/details/51916560

# 全局加载内置插件的方式还是会在引入jQuery插件时丢失$变量
```



