# 简单总结

**参考资料 **

[http://www.jianshu.com/p/dc5057e7ad0d](http://www.jianshu.com/p/dc5057e7ad0d)

#### 基础知识点

* 下载安装\(直接引入\)
* 实例化绑定数据
  * **new Vue**\({}\) - 实例化
    * **el:** '\#id' - 绑定标签
    * **data:** {数据对象} - 数据\(可以在html中使用\)
    * **methods** - 用v-on绑定事件使用
    * **computed** - 对于代码逻辑和业务逻辑的出来非常有用 , 可以理解为闭包代码块 , 之后直接当成变量在html中使用 . 
* 数据双向绑定v-model - 操作数据时候绑定,很有用.绑定了想要终止,用事件清空绑定的数据终止
  * `<input type="text" class="form-control" v-model="msg">`
* 循环数据**v-for** - 循环所在标签中所有内容,常用用在li中,循环声明的变量\(val,key in items\)
* 事件绑定**v-on** - 绑定事件
  * v-on:**click**="func"
  * v-on:**submit.prevent**="func" - 后面的prevent可以阻止提交的刷新
* 样式状态**v-bind:class** - 则是应用于页面的样式和渲染方面 , 使得 Web 应用更具体验性 . 
  * 可以直接用bool判断是否使用属性样式,可用用作初始值 : 
    * `v-bind:class="{'status':i.status}"`
  * 可以用三元运算符判断使用那个属性样式
    * `v-bind:class="[ i.status ? 'btn-success' : 'btn-danger']"`

#### 组件化开发

* 定义**Vue-component**
  * `Vue-component('list-items', {})` - 第一个参数是要在HTML中用的自定义标签
  * 第二个参数是一个对象,在里面配置这个组件
    * **template: '\#list-items-template'** - 定义模板ID,或者直接写HTML标签
    * **props: \['lists'\]** - 给组件定义了一个接口用来绑定new Vue实例中data属性的数据
    * **methods: {}** - 这个参数和new Vue实例中一样,所以可以把这个组件用到的方法到这里
    * **data:function \(\) {}** - 这里的data是专门给组件提供的数据
* 定义template模板,如果没有直接把HTML写在template参数里,就要重新定义一个模板
  * `<scritp type="text/x-template" id="list-items-template">`
  * 注意这里的type是text/x-template
  * id是刚才template中定义的\#id
* 写自定义的HTML标签
  * `<list-items :lists='lists'></list-items>`
  * 这里的`list-items`就是Vue-component的第一个参数,和HTML一样要有结束标签
  * 其中`:lists='lists'`的前者是接口名称,完整写法是v-bind:lists,后者是传入的数据
    * 因为这里在props中绑定了vue实例中的数据 , 接口和数据变量是一样的.



