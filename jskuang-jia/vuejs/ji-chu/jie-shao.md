# 介绍

> Vue.js是一套构建用户界面的**渐进式框架 . **Vue 的核心库只关注视图层，它不仅易于上手 , 还便于与**第三方库或既有项目整合** .
>
> 当与单文件组件和 Vue 生态系统支持的库结合使用时 , Vue 也完全能够为**复杂的单页应用程序**提供驱动 .

### 基本功能介绍

JSFiddle在线测试工具

[https://jsfiddle.net/chrisvfritz/50wL7mdz/](https://jsfiddle.net/chrisvfritz/50wL7mdz/)

下面的例子在Learning Vue的init文件中找到 .

**声明式渲染**

所有元素都是响应式的 , 打开控制台修改app.message , 马上回看到相应的更新 .

除了文本插值还可以使用`v-bind:title="message"`方式绑定DOM元素属性 . 打开控制台输入`app2.message = '新消息'`就可以看到更闹心了.

**条件与循环**

Vue不仅可以绑定 DOM 文本到数据 , 也可以绑定 DOM**结构**到数据 . 这里使用了v-if="seen"判断元素的显示与隐藏 . 另外 , 在 Vue 插入/更新/删除元素时可以自动应用过渡效果 , 这个后面在说 .

引用v-for指令绑定数组渲染一个列表 . 在控制台输入`app4.todos.push({ text: '新项目' })`给数组添加一条数据 .

**处理用户输入**

用v-on指令绑定时间监听器 , 然后用它调用Vue实例中定义的方法 . 在`reverseMessage`方法中 , 更新了应用的状态 , 所有DOM操作都由Vue来处理 , 不需要关注底层逻辑 .

使用v-model指令 , 可以轻松实现表单输入和应用状态之间的双向绑定 .

### 组件化应用构建

组件系统是 Vue 的另一个重要概念 , 允许我们使用小型、自包含和通常可复用的组件构建大型应用 .

在 Vue 里 , 一个组件本质上是一个拥有预定义选项的一个 Vue 实例 .

```
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
```

component预定义的第一个选项是组件名字 ,第二个对象参数预定义了很多参数 . 例如 , 组件可以使用props自定义属性 , 所以可以使用v-bind绑定数据到DOM .

在模板中以组件第一个参数为名字渲染标签\(有结束标签,并且需要手工转换驼峰为-连接标签\) , 标签上同样可以使用v-for等指令 , 子单元通过`props`接口实现了与父单元很好的解耦 .

### 与自定义元素的关系

Vue 组件非常类似于**自定义元素 , **但又区别与Web组件规范 , 因为其仍然处于草案阶段，并且尚无浏览器原生实现 . 另外 , 跨组件数据流 , 自定义事件通信以及构建工具集成等功能也是纯自定义元素也是不具备的 .

