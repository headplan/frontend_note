# Vue2.x快速使用

> **前言：Vue主要是“面向数据”编程。当数据发生改变时使用虚拟DOM来更改某一DOM节点，避免将整个页面渲染..**

#### 1.关于Vue

```js
# about-vue.html

/* html代码，view层，模板 */
   <div id="app">
        {{ message }}
    </div>
/* 引入相关文件，然创建实例，在实例中写各种方法就ok了 */
<script src="vue_2.2.0.js"></script>
<script type="text/javascript">
    document.addEventListener('DOMContentLoaded',function () {
        let data = {
            message: 'hello,Vue'
        }
      //vm实例
        var vm = new Vue({
            el: '#app',  //挂载元素
            data: data
        });
    },false);
</script>
```

特色 - 数据双向绑定 : 数据模型\(model\)与视图\(view\)组件的自动同步

```js
# v-model.html

<div id="app">
   <input type="text" placeholder="请输入" v-model="message" /> /* 将message绑定到当前元素并监听其变化 */
   <br />
   <p>数据：{{ message }}</p>
</div>
<script src="vue_2.2.0.js"></script>
<script type="text/javascript">
    document.addEventListener('DOMContentLoaded',function () {
        var vm = new Vue({
            el: '#app',
            data: {
                message: 'hello,Datura!!!'
            }
        });
    },false);
</script>
```

#### 2.Vue实例

> **Vue实例 **-** **每一个应用都是通过Vue这个构造函数创建根实例（root instance）启动New Vue（选项对象）。需要传入选项对象，对象包含挂在元素，数据，模板、方法等。

**实例的属性和方法**

* _el - _挂载元素选择器 --- String\|HtmlElement

* _data - _代理数据 --- Object\|Function

  * 每个vue实例都会代理其data对象里所有的属性 , 这些被代理的属性是响应的 .

  * **新添加**的属性不具备响应功能 , 改变后不会更新视图 .

* _methods - _定义方法 --- Object

* compontents - 定义组件

* computed - 定义计算逻辑

**Vue实例自身属性和方法 , **暴露自身的属性和方法,以“$”开头的 , 例如 : $el , $data ...

```js
# new-vue.html

var vm = new Vue({
       el: '#app',
       data: {
          message: 'hello,Datura!!!'
        }，
        methods: {
            test (){
                alert(1);
            }
        },
        compontents:{
        //这里存放组件
        }
     });
  /* vm就是new出来的实例 */
    console.time('test');
    console.log(vm.$el);
    console.dir(vm.$data); # 显示一个对象所有的属性和方法,document树
    console.log(vm.$data.message);
    console.timeEnd('test'); # 统计运行时间
```

### 3.声明式渲染概念

1. 声明式 - 只需要声明在哪里\(where\)做什么\(what\), 而无需关心如何实现\(how\)
2. 命令式 - 需要具体代码表达在哪里\(where\)做什么\(what\),如何实现\(how\)

```
例子:求数组中每一项的倍数

# 命令式:使用for循环拿出每一项,然后计算完成后,再放到另一个数中
//定义一个新的空数组，然后利用for循环，每一步每一步地放入其中
var arrNew = [];
for (var i=0;i<arr.length;i++){
  arrNew.push(arr[i]*2);
}

# 声明式:使用es6的map方法,关注如何取值
//将原数组（arr）中利用map函数，传入每一项
var arrNew = arr.map(function (item) {
  return item*2
})
```

**声明式渲染**

初始化根实例 , vue自动将数据绑定到DOM模板上 . 数据在vue实例中定义 , 利用`{{ xxx }}`在模板中展示 , 具体怎么传输过去的不关注 .

### 4.Vue指令

指令是一种特殊的自定义行间属性\(也就是在html标签内写\) . 指令的职责就是当其表达式的值改变时相应地将某些行为应用到DOM上 , 在Vue中 , 指令以“v-”开头 .

[https://cn.vuejs.org/v2/api/\#指令](https://cn.vuejs.org/v2/api/#指令)

```
v-bind - 动态绑定数据.简写为':'.例:class="{red:boolean}"
v-on - 绑定时间监听器.简写为'@'.例:@click="xxx"
v-text - 更新数据,会覆盖已有结构.类似{{ msg }}
v-show - 根据值的真假,切换元素的display属性
v-if - 根据值的真假,切换元素会被销毁,重建.在dom中已消失
v-else-if - 多条件判断,为真则渲染
v-else - 条件都不符合时渲染
v-for - 基于源数据多次渲染元素或模块
v-model - 在表单控件元素(input等)上创建双向数据绑定(数据源)
v-pre - 跳过元素和子元素的编译过程
v-once - 只渲染一次,随后数据更新也不重新渲染
v-cloak - 隐藏未编译的Mustache语法,在css中设置[v-cloak]{display:none;}
```

#### 列表渲染 — v-for=""

* 功能 : 根据一组数据的选项列表进行渲染（自动for循环）
* 语法 : value,key in items / value,key for items

**变异方法** - vue提供一组方法 , 对**数组**进行操作的时候 , 会触发视图更新\(map\(\)不会触发\) , 但其并不是原生的方法 , 原生的方法是不会触发视图的更新 .

```
 push()   |  pop()   |  shift()  |  unshift()
 splice() | sort()   | reverse()
```

```js
<body>
    <div id="app">
        <ul>
            <li v-for="(val,key) in fruitsArr">{{ val }} => {{ key }}</li>  // 循环出来的列表项
            <li v-for="(val,key) in fruitsArr" v-text="key+'=>'+val"></li>  // v-text也可以
        </ul>
    </div>
</body>
<script src="../vue.js"></script>
<script type="text/javascript">
    document.addEventListener('DOMContentLoaded',function () {
        var vm = new Vue({
            el: '#app',
            data:{
                fruitsArr:['apple','banana','orage','pear']   //数据源
            }
        });
    },false);
</script>
```

#### 事件处理器\(指令,绑定事件\) — v-on=""

* 功能 : 用来监听DOM事件触发代码。
* 语法 : v-on:eventName = "eventHandle"
* 指令简写 : @eventName = "eventHandle"

事件处理函数 - 写在Vue实例的methods中统一进行管理 . 事件对象是事件系统提供的 , 在事件处理函数中获取 .

获取方式 :

a\) 当行间不触发的时候

```
v-on:keyup.enter = "addTodo"   
addTodo(ev){  ｝  // 这里的ev就是事件对象
```

b\) 当行间触发的时候\(也就是加了个执行的括号\)

```
v-on:keyup.enter = "addTodo(123,$event)"   //行间传入事件对象$event
addTodo(data,ev){  }  // 需要在页面传参的时候,第一个参数为传入的参数,第二个参数才是事件对象.
```

##### 事件修饰符与按键修饰符

事件处理函数只有纯粹的逻辑判断 , 不处理DOM事件的细节 .

例如 , 阻止冒泡 , 取消默认行为 , 判断按键等等

**修饰符位置 - **以"."写在事件名称后面 . 例 , v-on:eventName.修饰符 = "xxx"

[https://cn.vuejs.org/v2/guide/events.html\#事件修饰符](https://cn.vuejs.org/v2/guide/events.html#事件修饰符)

```
事件修饰符:
.stop（冒泡）  |  .prevent（默认事件）   |  .capture（捕获）   |  .self   |  .once（执行一次）

按键修饰符:
.enter  |  .tab  |  .delete  |  .esc
.space  |  .up   |  .down    |  .left  |  .right
.ctrl   |  .alt  |  .shift   |  .meta
.键值
```

```
//等价
@keyup.enter = "addTodo()"
@keyup.13 = "addTodo()"
```

#### 条件渲染 — v-show=""

根据表达式的值 , 用来显示/隐藏元素 .

**语法** - v-show="表达式" , 根据表达式的值true和false , 来判断显示或隐藏 . **元素会被**渲染到页面中 , **只是根据表达式的值进行css切换\(display:none\)**

```
# 例如判断list长度决定是否显示内容
v-show="!list.length"
```

> 和v-if = "xxx"的区别是 , v-if不在页面渲染

#### 动态绑定class — v-bind=""

class也为元素的属性 , 可以使用v-bind:class

**语法**

* :class = "{className:表达式}"
* 表达式值为true添加className\(add\)
* 表达式值为flase不添加className\(remove\)

```
:class="{completed: item.isChecked}"
```

#### 自定义指令

##### 注册全局指令 : 所有人都可以用

```js
<body>
<div id="app">
    <div v-color="colorStatus">{{ msg }}</div>
</div>
<script src="js/vue.js"></script>
<script>
    document.addEventListener('DOMContentLoaded',function () {
        Vue.directive('color', function(el,binding){ // 这里的指令名称注意不要加**v-**
            console.log(el); // 当前绑定自定义指令的元素，可以用来直接操作DOM
            console.log(binding); // 一些参数,常用的  => binding.value(指令的值)
            console.log(binding.value);
            el.style.backgroundColor = 'green';
        });
        var vm = new Vue({
            el: '#app',
            data: {
                colorStatus: true,
                msg: 'Hello World!'
            }
        });
    },false);
</script>
</body>
```

##### 注册局部指令 : 当前组件下可用

```
<body>
<div id="app">
    <div v-color="color" v-content="msg"></div>
</div>
<script src="js/vue.js"></script>
<script>
    document.addEventListener('DOMContentLoaded',function () {
        Vue.directive('color', function(el,binding){ // 这里的指令名称注意不要加**v-**
            console.log(el); // 当前绑定自定义指令的元素，可以用来直接操作DOM
            console.log(binding); // 一些参数,常用的  => binding.value(指令的值)
            console.log(binding.value);
            el.style.backgroundColor = 'greenyellow';
        });
        var vm = new Vue({
            el: '#app',
            data: {
                color: true,
                msg: 'Hello World!'
            },
            directives: {
                content(el,binding){
                    el.innerHTML=binding.value;
                    el.style.textAlign='center';
                }
            }
        });
    },false);
</script>
</body>
```

### 5.Vue模板

**1.html模板**

html模版:基于DOM的模版,模版都是可解析的有效的HTML.

**插值**

* **文本** - 使用'Mustache'语法`{{ value }}`
  * 替换实例上的属性值,当值改变时,插值内容会被自动更新.也可使用v-text="value"代替.
  * `<p>{{ value }}<p>`等价于`<p v-text="value"></p>`
  * 原生的HTML中 , 双大括号输出的文本 , 不会解析html标签 , 也就是说当实例的data为html标签时 , 不能解析而是直接输出 . 此时想要解析 , 可使用v-html="value"代替 . 

```js
new Vue({
    data:{
        value:'<span>我是一个span标签</span>'
    }
});
<p>{{ value }}<p> # 页面展示:<span>我是一个span标签</span> 
<p v-html="value"><p> # 页面展示:我是一个span标签
```

> **需要注意的是 , 有时候因为一些网络延迟等原因 , 用户会在页面中先看到**`{{ xxx }}`** , 然后才有数据 . 为了避免此效果 , 可使用v-text="xxxx"代替**

* **属性** - 使用v-bind进行绑定 , 可以响应变化 . 

```
# 注意此处的show为data内的一个布尔值数据,若真则添加red的class,若假则移除red的class.
<h2 :class="{red:show}">标题</h2>
# 使用javascript表达式,可以写简单的表达式.
# 可以简单的三目运算,但是不可以写if语句.
{ 1+2 }
{ true? "yes":"no" }
```

**2.字符串模板**

**template模板**

* tempalte属性 - 模板会**替换**挂载的元素 . 即`<div id="box">`会被替换掉 . 说明权重比较高 , 直接“代替”挂载点 , 把原来的html替换后显示 . 

```js
# template.html
<body>
    <div id="box1"></div>
    <div id="box2"></div>
    <div id="box3"></div>

<template id="tem">
    <h2>hello box3!</h2>
</template>
<script src="vue.js"></script>
<script type="x-template" id="str">
    <h2>hello box2!</h2>
</script>
<script type="text/javascript">
    document.addEventListener('DOMContentLoaded',function () {
        // 方式一 =====
        let str = '<h2>hello pink!</h2>'
        let vm1 = new Vue({
            el: '#box1',
            template: str
        });
        // 方式二 =====
            var vm2 = new Vue({
            el: '#box2',
            template: '#str'
        }); 
        // 方式三 =====
        var vm3 = new Vue({
            el: '#box3',
            template: '#tem'
        });               
    },false);
</script>
</body>
```

**3.render函数**

> Vue 推荐在绝大多数情况下使用 template 来创建 HTML 模板 . 然而在一些场景中 , 还是需要 JavaScript 的完全编程的能力 , 它比 template 更接近编译器 .

这里暂时介绍render函数的createElement参数 , 更多细节参考[https://cn.vuejs.org/v2/guide/render-function.html](https://cn.vuejs.org/v2/guide/render-function.html)

```
createElement(标签名,[数据对象],子元素);
```

```
数据对象属性
class: {}, => 绑定class，和v-bind:class一样的API
style: {}, => 绑定样式，和v-bind:style一样的API
attrs: {}, => 添加行间属性
domProps: {}, => DOM元素属性
on: {}, => 绑定事件
nativeOn: {}, => 监听原生事件
directives: {}, => 自定义指令
scopedSlots: {}, => slot作用域
slot: {}, => 定义slot名称 和组件有关系，插曹
key: "key", => 给元素添加唯一标识
ref: "ref", => 引用信息
```

举个例子

```js
# render.html
<script>
    document.addEventListener('DOMContentLoaded',function () {
        let vm = new Vue({
            el:'#app',
            render(createrElement){
                console.log(createrElement);
                return createrElement(
                    "ul", // 第一个参数:标签名
                    { // 第二个参数:数据对象
                        class:{ // 绑定class,相当于v-bind:class="{bg:true}
                            'col-md-6':true,
                            'list-group':true,
                            st:true
                        },
                        style:{fontSize:"20px"}, // 绑定样式，和v-bind:style一样的API
                        attrs:{data:"数据"},
                        domProps:{
                            // DOM元素属性
                            // innerHTML:"<li>霸屏</li>" // 这个权重要高于第三个元素添加的子元素
                        }
                    },
                    [ // 第三个参数:子元素
                        createrElement("li",{class:{'list-group-item':true}},'第一个'),
                        createrElement("li",{class:{'list-group-item':true}},'第二个'),
                        createrElement("li",{class:{'list-group-item':true}},'第三个'),
                    ]
                );
            }
        });
    },false);
</script>
```

### 6.计算属性

模版是未来描述视图的结构 , 在模版中放入太多逻辑 , 导致模版过重难以维护 .

在计算一个计算属性时 , Vue.js更新它的依赖列表并缓存结果 , 只有当其中一个依赖发生了变化 , 缓存的结果才无效 .

```js
# computed.html
<div class="col-md-5"></div>
<div class="app col-md-2">
    {{ myData }}
    <input class="btn btn-xs" type="button" value="改变" @click="change" />
</div>
<div class="col-md-5"></div>
<script src="js/vue.js"></script>
<script>
    var vm = new Vue({
        el:'.app',
        data:{
            num:1
        },
        computed:{
            myData:{
                get(){
                    alert('get');
                    return this.num+2;
                },
                set(val){
                    alert('set');
                    return this.num=val;
                }
            }
        },
        methods:{
            change(){
                this.myData=10;
            }
        }
    });
</script>
</body>
```

**解析 : **计算属性和数据使用的方式一样 . 页面加载的时候后触发get函数 , 当点击事件后会触发set函数 .

