# Vue实例

### 构造器

每个Vue.js应用都是通过构造函数Vue创建一个**Vue的根实例**启动的 :

```
var vm = new Vue({
  // 选项
})
```

实例化时需要传入一个选项对象 , 它可以包括数据、模板、挂载元素、方法、生命周期钩子等选项 . API文档中有完整列表 .

可以预定义一个Vue的扩展构造器 , 从而用预定义选项创建可复用的**组件构造器 . **

    var MyComponent = Vue.extend({
      // 扩展选项
    });

    // 所有的 `MyComponent` 实例都将以预定义的扩展选项被创建
    var myComponentInstance = new MyComponent();

一般情况下会将组建构造器注册为一个自定义元素 , 然后声明式的用在模板中 . 后面的组建系统有更详细的描述 .

### 属性与方法

每个 Vue 实例都会**代理**其`data`对象里所有的属性 , 意思是 :

```
var data = { a: 1 }
var vm = new Vue({
  data: data
})
vm.a === data.a // -> true,他们是完全相等的
// 设置属性也会影响到原始数据
vm.a = 2
data.a // -> 2
// ... 反之亦然
data.a = 3
vm.a // -> 3
```

注意只有这些被代理的属性是**响应的 . **实例创建之后添加的属性不会触发视图更新 .

除了 data 属性 , Vue 实例暴露了一些有用的实例属性与方法 . 这些属性与方法都有前缀`$` , 以便与代理的 data 属性区分 .

    var data = { a: 1 }
    var vm = new Vue({
      el: '#example',
      data: data
    })
    vm.$data === data // -> true
    vm.$el === document.getElementById('example') // -> true
    // $watch 是一个实例方法
    vm.$watch('a', function (newVal, oldVal) {
      // 这个回调将在 `vm.a`  改变后调用
    })

> 注意 , 不要在实例属性或者回调函数中使用箭头函数 , 因为箭头函数绑定的是父上下文 , this不是Vue实例 , 而是未定义 . 例如 :
>
> ```
> vm.$watch('a', newVal => this.myMethod())
> ```

### 实例的生命周期

每个 Vue 实例在被创建之前都要经过一系列的初始化过程 , 这个过程中会调用一些**生命周期钩子** , 可以用来执行自定义逻辑 , 组件的自定义逻辑也可以分布在这些钩子中 . 不同的周期的不同阶段会有不同的钩子 , 例如 , mounted , updated , destroyed等 . 钩子的`this`指向调用它的 Vue 实例 .

    var vm = new Vue({
      data: {
        a: 1
      },
      created: function () {
        // `this` 指向 vm 实例
        console.log('a is: ' + this.a)
      }
    })
    // -> "a is: 1"

### 生命周期图![](/assets/vuelife.png)



