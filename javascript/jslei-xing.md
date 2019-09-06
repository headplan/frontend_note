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
> * `javascript:void '';` , `javascript:void "1";` , `javascript:undefined;`

但是 , JS中undefined是一个变量 , 而并非一个关键字 , 这也是JS工人的设计失误之一 . 所以 , 为了避免无意中被篡改 , 一般都建议使用void 0来获取undefined值 .

Undefined跟Null有一定的表一差别 , Null表示的是 : "定义了但是为空" . 所以 , 在实际编程时 , 一般不会把变量赋值为undefined , 这样可以保证所有值为undefined的变量 , 都是从未赋值的自然状态 .

Null类型也只有一个值 , 就是null , 它的语义表示空值 , 与undefined不同 , null是JS关键字 , 所以在任何代码中 , 都可以放心用null关键字来获取null值 . 

#### Boolean

布尔类型有两个值 , true和false . 用于表示逻辑意义上的真和假 , 同样有关键字true和false来表示两个值 . 

#### String

> 字符串有最大长度吗 ?

String用于表示文本数据 . String的最大长度是2^53-1 , 这在一般开发中都是够用的 , 但是所谓的最大长度 , 并不是通常理解的字符数 . 

因为String的意义并非"字符串" , 而是字符串的UTF16编码 , 字符串操作charAt , charCodeAt , length等方法针对的都是UTF16编码 . 所以 , 字符串的最大长度 , 实际上是受字符串的编码长度影响的 . 

> Note : 现行的字符集国际标准 , 字符是以Unicode的方式表示的 , 每一个Unicode的码点表示一个字符 , 理论上 , Unicode的范围是无限的 . UTF是Unicode的编码方式 , 规定了码点在计算机中的表示方法 , 常见的有UTF16和UTF8 . Unicode的码点通常用U+???来表示 , 其中???是十六进制的码点值 . 0-65536\(U+0000 - U+FFFF\)的码点被称为基本字符区域\(BMP\) .

**JS中的字符串是永远无法变更的 , 一旦字符串构造出来 , 无法用任何方式改变字符串的内容 , 所以字符串具有值类型的特征 . **

JS字符串把每个UTF16单元当作一个字符来处理 , 所以处理非BMP的字符时 , 应该格外小心 . \(超出U+0000 - U+FFFF的字符\)

JS的这个设计继承自Java , 最新标准中是这样解释的 , 这样设计是为了性能和尽可能实现起来简单 . 因为现实中很少用到BMP之外的字符 . 



