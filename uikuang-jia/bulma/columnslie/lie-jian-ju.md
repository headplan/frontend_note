# 列间距

自定义列之间的间隙 .

#### 默认间距

每个列都有一个与变量 $column 间隙相等的间隙, 它的默认值为0.75rem .

由于间隙位于列的两侧, 因此相邻两列之间的间隙将是 $column 间隙值的两倍, 或默认为1.5rem .

#### 无间距

如果要删除列之间的空格, 请在 "列" 容器中添加 "is-gapless" 修饰符 :

```
<div class="columns is-gapless">
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
</div>
```

可以将它与 "is-multiline" 修饰符组合在一起 .

#### 可变间距

可以通过在.column容器上追加0-9的修饰符之一来指定自定义列间隙 .

* is-0 将删除任何间隙 \(类似于is-gapless\)
* is-3 是默认值, 相当于0.75rem 值
* is-8 最大间隙为2rem

此外, ".is-variable" 应添加到 ".columns" 容器中 .

