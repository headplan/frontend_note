# 计算属性

在模板中绑定表达式是非常便利的 , 但是它们实际上只用于简单的操作 . 对于复杂的逻辑 , 应该使用计算属性 .

> 相关例子查看Learning Vue中init-computed.html

### 基础例子

例子中声明了一个计算属性reversedMessage . 这个属性提供的函数作用在vm.reversedMessage的getter上 . 他的值始终取决于vm.message的值 . 可以把他当成是一个依赖于vm.message属性的属性 .

在控制台测试一下 :

```
console.log(vm.reversedMessage) // -> 'olleH'
vm.message = 'Goodbye'
console.log(vm.reversedMessage) // -> 'eybdooG'
```

### 计算缓存 VS Methods

使用计算属性和定义一个函数达到的效果是一样的 . 不同的是 , **计算属性是基于它的依赖缓存 . 意思是计算属性只有在它相关的依赖发生变化时候才会重新取值. **就是我们刚才在控制台测试的 , 所以在多次使用计算属性后 , 返回的结果是不变的 , 而不像Mehods函数一样 , 调用了就总会执行哈数 . 两者的使用可以根据实际情况去取舍 .

### 计算属性 VS Watched Property

Vue提供了一个$watch方法 , 用于观察Vue实例上的数据变动 . 但这个应用场景上 , 使用计算属性要好过使用命令式的$watch回调 .

```
# 对比
var vm = new Vue({
  el: '#demo',
  data: {
    firstName: 'Foo',
    lastName: 'Bar',
    fullName: 'Foo Bar'
  },
  watch: {
    firstName: function (val) {
      this.fullName = val + ' ' + this.lastName
    },
    lastName: function (val) {
      this.fullName = this.firstName + ' ' + val
    }
  }
})
# ==========
var vm = new Vue({
  el: '#demo',
  data: {
    firstName: 'Foo',
    lastName: 'Bar'
  },
  computed: {
    fullName: function () {
      return this.firstName + ' ' + this.lastName
    }
  }
})
```

### 计算setter

计算属性默认有getter , 当然可以自定义提供一个setter . 意思就是修改了计算属性时 , 触发setter函数 .

```
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
```

### 观察Watchers

计算属性用在大多数数据变化的计算上 . 但是watch选项 , 在想要响应数据变化时 , 执行异步操作等昂贵操作时 , 是很有用的 .

例子中watch选项允许我们执行异步操作\(访问API\) , 限制执行该操作的频率 , 并在得到最终结果前 , 设置中间状态 , 这都是计算属性无法做到的 .

除了watch选项外 , 还可以使用vm.$watch命令 .

