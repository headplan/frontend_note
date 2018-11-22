# Columns列

生成响应列的简单方法 . 使用Bulma构建列布局非常简单 :

* 添加容器
* 按需要添加尽可能多的列元素

每一列的宽度都相等 , 无论列数是多少 .

```html
<div class="columns">
  <div class="column">
    First column
  </div>
  <div class="column">
    Second column
  </div>
  <div class="column">
    Third column
  </div>
  <div class="column">
    Fourth column
  </div>
</div>
```

---

#### Columns大小

分别定义每个列的大小 .

如果要更改单个列的大小 , 可以使用下列类之一 :

* `is-three-quarters`
* `is-two-thirds`
* `is-half`
* `is-one-third`
* `is-one-quarter`

其他列将自动填充剩余的空间 . 现在 , 还可以使用以下20%倍数 :

* `is-four-fifths`
* `is-three-fifths`
* `is-two-fifths`
* `is-one-fifth`

![](/assets/lie.png)

```html
<div class="columns">
  <div class="column is-four-fifths">is-four-fifths</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>

<div class="columns">
  <div class="column is-three-quarters">is-three-quarters</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>
```

#### 12栏系统

由于网格可分为12列 , 因此每个分区都有大小类 :

* `is-2`
* `is-3`
* `is-4`
* `is-5`
* `is-6`
* `is-7`
* `is-8`
* `is-9`
* `is-10`
* `is-11`

每个修饰符类都是以12中所需的列数命名的 .

![](/assets/12lan.png)

#### Offset偏移

虽然可以使用空列\(如 : &lt;div class="column"&gt;&lt;/div&gt;\)来创建周围的水平空间 , 当然 , 列元素也可以使用偏移修饰符来创建.is-offset-x :

```
<div class="columns is-mobile">
  <div class="column is-half is-offset-one-quarter"></div>
</div>
```

#### 窄列

如果希望列只占用所需的空间 , 请使用 "窄\(is-narrow\)" 修饰符 . 其他列将填满剩余的空间 .

```html
<div class="columns">
  <div class="column is-narrow">
    <div class="box" style="width: 200px;">
      <p class="title is-5">Narrow column</p>
      <p class="subtitle">This column is only 200px wide.</p>
    </div>
  </div>
  <div class="column">
    <div class="box">
      <p class="title is-5">Flexible column</p>
      <p class="subtitle">This column will take up the remaining space available.</p>
    </div>
  </div>
</div>
```

对于大小修饰符 , 可以对不同的断点具有窄列 :

* `is-narrow-mobile`
* `is-narrow-tablet`
* `is-narrow-desktop`



