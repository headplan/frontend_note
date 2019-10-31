# Class与Style绑定

数据绑定一个常见需求是操作元素的 class 列表和它的内联样式 . 他们都是属性 , 用v-bind处理就好了 . 在v-bind用于class和style时 , Vue增强了表达式类型 , 除了字符串外 , 还可以是对象或数组 .

### 绑定HTML的Class

**对象语法**

传给v-bind:class一个对象 , 以动态的切换class . 还可以传入多个属性用来动态切换多个class . 而且v-bind:class指令可以和普通的class属性共存 .

```
<div class="static"
     v-bind:class="{ active: isActive, 'text-danger': hasError }">
</div>
# data
data: {
  isActive: true,
  hasError: false
}
# 渲染为
<div class="static active"></div>
# hasError为true时,渲染为
<div class="static active hasError"></div>
```

还可以直接绑定data中的一个对象

```
<div v-bind:class="classObject"></div>
# data
data: {
  classObject: {
    active: true,
    'text-danger': false
  }
}
```

还可以绑定前面的计算属性

```
<div v-bind:class="classObject"></div>
# data
data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal',
    }
  }
}
```

**数组语法**

基本用法

```
<div v-bind:class="[activeClass, errorClass]">
# data
data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
# 渲染为
<div class="active text-danger"></div>
```

数组语法上的切换 , 需要使用三元运算符

```
<div v-bind:class="[isActive ? activeClass : '', errorClass]">
```

但是如果多个数组元素都需要判断切换 , 会很繁琐 , 可以在数组中传入对象解决这个问题 :

```
<div v-bind:class="[{ active: isActive }, errorClass]">
```

**用在组件上**

在定制组件上使用class属性时 , 都会添加到更元素上 , 如果根元素原来有类 , 不会覆盖 , 会添加到其后面 .

```
Vue.component('my-component', {
  template: '<p class="foo bar">Hi</p>'
})
<my-component class="baz boo"></my-component>
# 渲染为
<p class="foo bar baz boo">Hi</p>
```

同样可以使用上面说的传入对象或数组的方式

```
<my-component v-bind:class="{ active: isActive }"></my-component>
```

### 绑定Style内联样式

**对象语法**

v-bind:style的对象语法很像CSS , 其实是个JS对象 . CSS属性可以用驼峰,也可以短横线分割 . 其他用法和Class语法一样 .

```
<div v-bind:style="{ color: activeColor, fontSize: fontSize }"></div>
```

**数组语法**

数组语法可以将多个样式对象应用到一个元素上

```
<div v-bind:style="[baseStyles, overridingStyles]">
```

**自动添加前缀**

当`v-bind:style`使用需要特定前缀的 CSS 属性时 , 如`transform`, Vue.js 会自动侦测并添加相应的前缀 .

