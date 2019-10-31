# 模板语法

Vue.js 使用了基于 HTML 的模版语法 , 允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据 .

> 在底层的实现上 , Vue 将模板编译成虚拟 DOM 渲染函数 . 结合响应系统 , 在应用状态改变时 , Vue 能够智能地计算出重新渲染组件的最小代价并应用到 DOM 操作上 .
>
> 如果你熟悉虚拟 DOM 并且偏爱 JavaScript 的原始力量 , 你也可以不用模板 , 直接写渲染\(render\)函数 , 使用可选的 JSX 语法 .
>
> 代码例子参考Learning Vue中init-template

### 插值

**文本**

使用大括号插值 ,也可以使用指令v-text="msg"插值 .

使用v-once指令执行一次性插值 , 当数据改变时内容不会更新内容 , 会影响这个节点上所有的数据绑定 . 即使使用v-model绑定表单输入也无法修改 .

```
<p v-text="msg"></p>
<div id="app" v-once>{{ msg }}</div>
```

**纯HTML**

插入的数据如果有html标签 , 也会被当成文本输出出来 . 如果想输出html则使用v-html指令 . 数据绑定也会被忽略 , 这个指令不适合用来当做UI重用的单元 .

```
<div v-html="rawHtml"></div>
# 数据里写
rawHtml:'<h1>Hi!</h1>'
```

> 动态渲染HTML , 小心XSS攻击

**属性**

在html属性中使用v-bind指令 , 对布尔值属性也有效 , 例如disabled

```
<button v-bind:disabled="someDynamicCondition">Button</button>
```

**JS表达式**

所有的数据绑定都支持完全的JS表达式支持 . 表达式会在所属 Vue 实例的数据作用域下作为 JS 被解析 .

```
{{ number + 1 }}
{{ ok ? 'YES' : 'NO' }}
{{ message.split('').reverse().join('') }}
<div v-bind:id="'list-' + id"></div>
```

但限制是每个绑定只是单个表示 , 例如下面的就不会生效 :

```
<!-- 这是语句，不是表达式 -->
{{ var a = 1 }}
<!-- 流控制也不会生效，请使用三元表达式 -->
{{ if (ok) { return message } }}
```

> 模板表达式都被放在沙盒中，只能访问全局变量的一个白名单，如`Math`和`Date`

**过滤器**

过滤器就是一些常见文本的格式化 , 由filters对象中的函数定义 . 但是在模板中只能用在双大括号中\(就是**mustache**语法\) 而且在后面 , 用管道符隔开 , 可以多个过滤器 . 不能用在v指令中 , 所以最好还是使用**计算属性** , 这个后面说 .

```
{{ message | capitalize }}
{{ message | filterA | filterB }}
```

过滤器函数总接受表达式的值\(就这里的message\)作为第一个参数 . 如果还想传参数直接写 . **这里要注意的是 , 如果串联两个过滤函数 , message只传给第一个函数 . **

```
{{ message | filterA('arg1', arg2) }}
```

这里第一个参数arg1会作为过滤器的第二个值 , 后面的被当做第三个值 .

### 指令

指令是带有v-前缀的特殊属性 . 大部分指令的值是单一的\(除了v-for\) . 指令的职责就是当其表达式的值改变时相应的将其某些行为应用到DOM上 .

例如

```
<p v-if="seen">Now you see me</p>
```

这里v-if指令将根据表达式seen的值的真假来移除或插入&lt;p&gt;元素 .

**参数**

一些指令能够接受一个参数 , 在指令后以冒号指明 . 例如v-bind , v-on

```
<a v-bind:href="url"></a>
<a v-on:click="doSomething">
```

**修饰符**

用于指出一个指令应该以特殊的方式绑定 . 例如.prevent修饰符告诉指令v-on对于触发的事件调用event.preventDefault\(\)

```
<form v-on:submit.prevent="onSubmit"></form>
```

**修饰符**

### 缩写

Vue.js 为两个最为常用的指令提供了特别的缩写：

**v-bind缩写**

```
<!-- 完整语法 -->
<a v-bind:href="url"></a>
<!-- 缩写 -->
<a :href="url"></a>
```

**v-on缩写**

```
<!-- 完整语法 -->
<a v-on:click="doSomething"></a>
<!-- 缩写 -->
<a @click="doSomething"></a>
```



