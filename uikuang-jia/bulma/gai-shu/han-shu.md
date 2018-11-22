# 函数

计算颜色和其他值的实用工具函数 .

Bulma使用3自定义函数来帮助动态定义值和颜色 :

* `powerNumber($number, $exp)`: 计算暴露给另一数字的数值 . 返回一个数字 . 
* `colorLuminance($color)` : 定义颜色是深色还是浅色 . 返回介于0和1之间的十进制数, 其中 &lt;= 0.5 暗色 , &gt;0.5 是明色 . 
* `findColorInvert($color)` : 返回70%透明黑色或100%不透明白色 , 取决于颜色的亮度 . 

#### findColorInvert\(\)

`findColorInvert()`函数以颜色作为输入 , 并输出透明黑色rgba\(\#000, 0.7\)或白色\(\#fff\) :

如果colorLuminance\($color\)&gt;0.55 , 它输出rgba\(\#000, 0.7\) . 否则它输出\#fff .

它的目的是在使用输入颜色作为背景时保证文本的可读的底纹 . 意思就是字体颜色和背景色别太靠色了 .

对于具有接近0.55阈值的亮度的颜色 , 可以尝试覆盖`findColorInvert()`的颜色 , 直接手动输入也可以 . 例如浅紫色的反转色 :

```
$purple-invert: findColorInvert($purple)
# 计算亮度colorLuminance($purple)是0.5529,反转色透明黑色,也可以直接手动反转为白色
$purple-invert: #fff
```



