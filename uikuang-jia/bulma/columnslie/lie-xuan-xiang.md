# 列选项

设计不同类型的列布局 .

#### 多行

无论何时要启动新行 , 都可以关闭列容器并开始新的一行 . 但也可以添加多行修饰符 , 并添加更多适合单行的列元素 .

```html
<div class="columns is-multiline is-mobile">
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-half">
    <code>is-half</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column is-one-quarter">
    <code>is-one-quarter</code>
  </div>
  <div class="column">
    Auto
  </div>
</div>
```

#### 居中列

虽然可以使用空列\(如&lt;div class="column"&gt;&lt;/div&gt;\)来创建周围的水平空间 , 也可以在父级.columns上使用.is-centered :

```html
<div class="columns is-mobile is-centered">
  <div class="column is-half is-narrow">
    <p class="bd-notification is-info">
      <code class="html">is-half</code><br>
      <code class="html">is-narrow</code>
    </p>
  </div>
</div>
```

与 ".is-multiline" 一起使用以创建一个灵活的、居中的列表 \(尝试调整大小以查看不同视区大小的居中\) :

```html
<div class="columns is-mobile is-multiline is-centered">
  <div class="column is-narrow">
    <p class="bd-notification is-info">
      <code class="html">is-narrow</code><br>
      First Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-success">
      <code class="html">is-narrow</code><br>
      Our Second Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-danger">
      <code class="html">is-narrow</code><br>
      Third Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-info">
      <code class="html">is-narrow</code><br>
      The Fourth Column
    </p>
  </div>
  <div class="column is-narrow">
    <p class="bd-notification is-success">
      <code class="html">is-narrow</code><br>
      Fifth Column
    </p>
  </div>
</div>
```



