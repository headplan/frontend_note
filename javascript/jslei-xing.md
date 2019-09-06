# JS类型

JS类型一定是我们最熟悉的概念 , 先来看看下面这几个问题吗 ?

* 为什么有的编程规范要求用void 0代替undefined
* 字符串有最大长度吗 ? 
* 0.1 + 0.2 不是等于 0.3 么 ? 为什么JS里不是这样的 ?
* ES6新加入的Symbol是个什么东西 ? 
* 为什么给对象添加的方法能用在基本类型上 ? 

如果上面这些问题回答起来感觉有些犹豫 , 说明这些知识点还有些遗漏的地方 .

#### 类型

> 运行时类型是代码实际执行过程中我们用到的类型 . 所有的类型数据都会属于7个类型之一 . 从变量 , 参数 , 返回值到表达式中间结果 , 任何JS代码运行过程中产生的数据 , 都具有运行时类型 .

JS语言的每一个值都属于某一种数据类型 . JS语言规定了7种语言类型 . 语言类型广泛用于变量 , 函数参数 , 表达式 , 函数返回值等场合 . 根据最新的语言标准 , 这7种语言类型是 :

1. Undefined
2. Null
3. Boolean
4. String
5. Number
6. Symbol
7. Object

除了ES6中新加入的Symbol类型 , 其他都是我们经常使用到的 .

#### Undefined和Null

为什么有的编程规范要求用vioid 0代替undefined ? 

Undefined类型表示未定义 , 它的类型只有一个值 , 就是undefined . 任何变量在赋值前都是Undefined类型 , 值为undefined , 一般可以用全局变量undefined来表达这个值 , 也就是名为undefined的变量 , 或者void运算来把任意一个表达式变成undefined值 . 

> **JS中函数void\(\)的运用大体是如下形式 : **
>
> * void是运算符 , 对任何值都返回undefined . 和typeof运算符号一样可以 `void(0);`或者`void 0;`
> * `void function main(){};`申明此函数返回的是undefined;没有return的函数默认也是返回undefined . 
> * `javascript:void ''` , `javascript:void "1"` , `javascript:undefined`



