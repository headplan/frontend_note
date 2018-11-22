# 概述

#### **开始使用**

**安装**

```
npm install bulma
```

**使用CDN**

```
https://cdnjs.com/libraries/bulma
<link href="https://cdn.bootcss.com/bulma/0.6.1/css/bulma.min.css" rel="stylesheet">
<link href="https://cdn.bootcss.com/bulma/0.6.1/css/bulma.css" rel="stylesheet">
```

**下载引入**

```
https://github.com/jgthms/bulma/tree/master/css
```

> 如果要使用bulma的图标需要引入font-awesome
>
> ```
> <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
> ```

#### 代码要求

要使bulma正常工作 , 需要让网页响应 .

```
<!DOCTYPE html>
<meta name="viewport" content="width=device-width, initial-scale=1">
```

#### 模板例子

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Hello Bulma!</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.6.1/css/bulma.min.css">
  </head>
  <body>
  <section class="section">
    <div class="container">
      <h1 class="title">
        Hello World
      </h1>
      <p class="subtitle">
        My first website with <strong>Bulma</strong>!
      </p>
    </div>
  </section>
  </body>
</html>
```

---

#### SASS自定义

用一组简单的变量创建自己的主题 . 使用npm安装或者克隆代码后 , 就可以设置变量 , 自定义自己的主题了 .

```sass
// 1. 引入初始变量
@import "../sass/utilities/initial-variables"
@import "../sass/utilities/functions"

// 2. 自定义初始变量
// Update blue
$blue: #72d0eb
// 添加粉红色以及其反转
$pink: #ffb3b3
$pink-invert: #fff
// 添加serif字体
$family-serif: "Merriweather", "Georgia", serif

// 3. 设置派生变量
// 使用新的粉红色作为primary的颜色
$primary: $pink
$primary-invert: $pink-invert
// 使用现有的橙色作为danger的颜色
$danger: $orange
// 使用新的serif字体
$family-primary: $family-serif

// 4. 设置添加一些自定义颜色
// findColorInvert()为自动反转函数
$linkedin: #0077B5
$linkedin-invert: findColorInvert($linkedin)
$twitter: #1DA1F2
$twitter-invert: findColorInvert($twitter)
$github: #222222
$github-invert: findColorInvert($github)

// 5. 新的自定义颜色要添加到映射文件derived-variables.sass中
@import "../sass/utilities/derived-variables.sass"
$addColors: (
  "twitter":($twitter, $twitter-invert),
  "linkedin": ($linkedin, $linkedin-invert),
  "github": ($github, $github-invert)
)
$colors: map-merge($colors, $addColors)

// 6. 导入其余的bulma代码
@import "../bulma"
```

---

#### Classes

Bulma只是一个 CSS 类的集合 . 还是要编写所需的HTML代码的 .

这些CSS类主要分为两种 :

* generic.sass为网页定义基本样式
* .content用于任何文本内容 , 例如WYSIWYG

---

#### 模块

只需导入你需要的内容 .

Bulma是由39个.sass文件单独导入组成的 , 所以直接导入你想使用的样式也可以 . 例如只导入布局 :

```
@import "bulma/sass/utilities/_all"
@import "bulma/sass/grid/columns"
```

```
<div class="columns">
  <div class="column">1</div>
  <div class="column">2</div>
  <div class="column">3</div>
  <div class="column">4</div>
  <div class="column">5</div>
</div>
```

只导入按钮模块 :

```
@import "bulma/sass/utilities/_all"
@import "bulma/sass/elements/button.sass"
<a class="button">
  Button
</a>

<a class="button is-primary">
  Primary button
</a>
```

---

#### 响应

Bulma也是移动先行的框架 .

**默认垂直**

其中的每个元素都是移动优先的 , 并为垂直读取进行优化 , 因此默认情况下为mobile :

* "columns" 列垂直堆叠
* "level" 分级组件将显示其子级垂直堆叠
* "nav" 导航菜单将被隐藏

还可以追加is-mobile修饰符来强制执行列或导航的水平布局 .

**Breakpoints断点**

Bulma有5个断点 :

* `mobile` : up to **768px**
* `tablet` : from **769px**
* `desktop` : from **1024px**
* `widescreen` : from **1216px**
* `fullhd` : from **1408px**

Bulma有9个响应mixins :

* =mobile - until 768px
* =tablet - from 769px
* =tablet-only - from 769px and until 1023px
* =touch - until 1023px
* =desktop - from 1024px
* =desktop-only - from 1024px and until 1215px
* =widescreen - from 1216px
* =widescreen-only - from 1216px and until 1407px
* =fullhd - from 1408px

**自定义响应变量**

和前面自定义SASS的方式一样 , 在导入Bulma之前 , 设置一个或多个这些变量即可 .

| `$gap` | `32px` |
| :--- | :--- |
| `$tablet` | `769px` |
| `$desktop` | `960px + (2 * $gap)` |
| `$widescreen` | `1152px + (2 * $gap)` |
| `$fullhd` | `1344px + (2 * $gap)` |



