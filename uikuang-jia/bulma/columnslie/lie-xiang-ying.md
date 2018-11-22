# 列响应

为每个断点处理不同的列布局 .

#### Mobile列

默认情况下 , 仅从 tablet 开始激活列 . 这意味着在移动中 , 列堆叠在彼此的顶部 .

如果希望列在移动时也起作用 , 只需在 "列" 容器中添加 "is-mobile" 移动修饰符 :

```
<div class="columns is-mobile">
  <div class="column">1</div>
  <div class="column">2</div>
  <div class="column">3</div>
  <div class="column">4</div>
</div>
```

如果只希望桌面上的列向上, 只需在 "列" 容器上使用 "is-desktop" 修饰符 :

```
<div class="columns is-desktop">
  <div class="column">1</div>
  <div class="column">2</div>
  <div class="column">3</div>
  <div class="column">4</div>
</div>
```

#### 每个断点的不同列大小

可以为每个视区大小定义一个列大小 : mobile、tablet和desktop .

```
<div class="columns is-mobile">
  <div class="column is-three-quarters-mobile is-two-thirds-tablet is-half-desktop is-one-third-widescreen is-one-quarter-fullhd">
    <code>is-three-quarters-mobile</code><br>
    <code>is-two-thirds-tablet</code><br>
    <code>is-half-desktop</code>
    <code>is-one-third-widescreen</code>
    <code>is-one-quarter-fullhd</code>
  </div>
  <div class="column">1</div>
  <div class="column">1</div>
</div>
```



