# 条件渲染

#### v-if

使用`v-if`指令实现显示隐藏的功能

```
<h1 v-if="ok">Yes</h1>
```

也可以用`v-else`添加一个 “else” 块

```
<h1 v-if="ok">Yes</h1>
<h1 v-else>No</h1>
```

#### template v-if

可以在template上使用v-if指令 , 包装元素的渲染结果 .

```
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

#### v-else

可以用`v-else`指令给`v-if`或`v-show`添加一个 “else” 块

```
<div v-if="Math.random() > 0.5">
  Sorry
</div>
<div v-else>
  Not sorry
</div>
```

使用v-else指令的元素必须紧跟在v-if或v-show元素的后面 , 否则无法识别 .

#### v-show

v-show指令达到的效果和用法跟v-if指令一样 . 区别是v-show的渲染结果让元素保持在DOM中 , 和css的display属性一样 .

> v-show指令不能用在&lt;template&gt;上 .

#### v-if VS v-show

`v-if`是真实的条件渲染 , 因为它会确保条件块在切换当中适当地销毁与重建条件块内的事件监听器和子组件 .

`v-if`是**惰性的 : **如果在初始渲染时条件为假 , 则什么也不做——在条件第一次变为真时才开始局部编译\(编译会被缓存起来\) .

相比之下 , `v-show`简单得多——元素始终被编译并保留 , 只是简单地基于 CSS 切换 .

一般来说 , `v-if`有更高的切换消耗而`v-show`有更高的初始渲染消耗 . 因此 , 如果需要频繁切换使用`v-show`较好 , 如果在运行时条件不大可能改变则使用`v-if`较好 .

