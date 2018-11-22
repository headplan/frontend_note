# Modifiers修饰符

#### 修饰符语法

大多数Bulma元素都有替代样式 . 若要应用它们 , 只需追加其中一个修饰符类 , 像`is-`或`has-`

可以使用6种主要**颜色**之一 :

* `is-primary`
* `is-link`
* `is-info`
* `is-success`
* `is-warning`
* `is-danger`

例子 :

```html
<a class="button is-primary">
  Button
</a>
```

更改**大小** :

* `is-small`
* `is-medium`
* `is-large`

```html
<a class="button is-small">
  Button
</a>
```

更改**样式或状态** :

* `is-outlined`
* `is-loading`
* `[disabled]`

```html
<a class="button is-primary is-outlined">
  Button
</a>
```

---

#### 帮助函数

响应帮助器类应也可以用于几乎任何元素 , 以便根据浏览器的宽度更改其样式 .

| Float | `is-clearfix` | 修复元素的浮动子级 , 清除浮动 |
| :--- | :--- | :--- |
|  | `is-pulled-left` | 向左移动元素 |
|  | `is-pulled-right` | 向右移动元素 |
| **Spacing** | `is-marginless` | 删除任何外边距**margin** |
|  | `is-paddingless` | 删除任何内边距**padding** |
| **Other** | `is-overlay` | 完全覆盖第一个定位的父级 |
|  | `is-clipped` | 将溢出隐藏 |
|  | `is-radiusless` | 删除任何圆角**radius** |
|  | `is-shadowless` | 删除任何透明度**shadow** |
|  | `is-unselectable` | 防止文本被选择**selectable** |
|  | `is-invisible` | 将元素可见隐藏\(占位隐藏visibility\) |

---

#### 响应帮助函数

根据展示屏幕的宽度显示/隐藏内容 .

**显示show**

可以使用下列显示类之一 :

* `block`
* `flex`
* `inline`
* `inline-block`
* `inline-flex`

以flex为例 :

* is-flex-mobile
* is-flex-tablet-only
* is-flex-desktop-only
* is-flex-widescreen-only

**图例**

![](/assets/tuli-1.png)

要显示到特定断点的类 :

* is-flex-touch
* is-flex-tablet
* is-flex-desktop
* is-flex-widescreen
* is-flex-fullhd

![](/assets/tuli-2.png)

对于其他显示选项 , 替换is-flex即可 , 例如`is-block`,`is-inline`,`is-inline-block`等 .

**隐藏hidden**

同上 , 例如 , is-hidden-mobile .

