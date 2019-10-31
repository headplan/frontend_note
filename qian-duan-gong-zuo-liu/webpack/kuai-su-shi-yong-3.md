# Webpack的配置与插件

**区分线上与线下配置**

```
var debug = process.env.NODE_ENV !== "production";
```

```
module.exports = {
    devtool: debug ? "sourcemap" : null,
    entry: "./js/entry.js",
    output: {
        filename: "bundle.js"
    },
    module: {
        rules: 
        [
            {
                test: /\.css$/,
                use: [ 'style-loader', 'css-loader' ]
            },
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
            {
                test: /\.vue$/,
                use: 'vue-loader'
            }
        ],
    },
    resolve: {
        extensions: ['.js', '.vue', '.json'],
        alias: {
            'vue$': 'vue/dist/vue.js',
        }
    }
};
```

**Plugin**

[https://github.com/webpack/docs/wiki/list-of-plugins](https://github.com/webpack/docs/wiki/list-of-plugins)

```
plugins: debug ? [] : [
    # DefinePlugin允许在编译时(compile time)配置的全局常量，用于允许「开发/发布」构建之间的不同行为
    new webpack.optimize.DedupePlugin(), # webpack2中被删除
    new webpack.optimize.OccurrenceOrderPlugin(),
    new webpack.optimize.UglifyJsPlugin({mangle:false,sourcemap:false})
]
```

**Webpack图形化分析工具**

```
# 输出打包json文件
webpack --profile --json > stats.json
# 将json文件上传到下面的网站,就会展示出分析结果
http://webpack.github.io/analyse/
http://chrisbateman.github.io/webpack-visualizer/
```



