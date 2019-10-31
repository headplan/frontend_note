# 组件化开发

> 组件化是现在 Web 开发越来越看重的趋势 , 特别是在前后端分离的情况下 , 组件化不仅可重用 , 可读性更高 , 并且可维护的成本也更低了 .

Web中的组件其实就是页面组成的一部分 , 它是一个具有独立的逻辑和功能或页面 , 同时又能根据规定的接口规则进行相互融合 , 变成一个完整的应用 .

Vue中的组件是一个自定义标签\(元素\) , Vue.js的编译器为它添加特殊功能 . Vue也可以拓展原生的html元素 , 封装可重用的代码 .

**组件的基本组成** : 样式结构 , 行为逻辑 , 数据 .

#### a\).全局注册

```js
# component.html
<body>
    <div class="app">
        <my-component></my-component>
    </div>
<script src="vue.js"></script>
<script>
    //全局注册
    Vue.component('myComponent',{//html中是横杠的，在js中就是驼峰
        template: `<h2>我是全局组件</h2>`
    })
    var vm = new Vue({
        el: '.app'
    });
</script>
</body>
```

#### **b\).**局部注册

```js
# component.html
<script src="js/vue.js"></script>
<script>
    // 全局注册
    Vue.component('myComponent',{ // html中是横杠的,在js中就是驼峰
        template:'<p>全局组件</p>'
    });
    var Child = {
        template:'<p>局部组件A</p>'
    };
    var componentB = {
        template:'<p>全局组件B</p>'
    };
    var vm = new Vue({
        el:'#app',
        components: {
            // 只能在父模板中使用
            componentA:Child,
            componentB // 如果组件定义的名字和在html显示的标签名一致就可以省略
        }
    });
</script>
```

#### **c\).**组件模版

组件模板一般都会在外部定义模板后引入 . 和模板引入的方式一样 .

```js
# component.html
<script id="component1" type="x-template">
        <h3>第一个局部组件——定义方式1</h3>
</script>
<!-- 用 template标签名的方式  推荐-->
<template id="component2">
    <p>第二个局部组件——定义方式2</p>
</template>

var Child = {
    template:'#component1'
};
var componentB = {
    template:'#component2'
};
```

#### **d\).**父子组件

```js
# component.html
var componentC = {
    template:'#component3',
    data(){
        return {
            msg:'父组件C'
        }
    },
    components:{
        componentD:{
            template:'<p>子组件D</p>'
        }
    }
};
var vm = new Vue({
    el:'#app',
    components: {
        componentC
    }
});
```

**定义组件Vue-component**

```js
# 定义组件,第一个参数是自定义标签的名字
# 第二个参数是一个对象,里面也有一些默认的参数
# template:里面是我们要在组件中渲染出来的html元素
Vue-component('list-items', {
    template: '',
})
# 这里有两种定义template参数的方式,一种是直接写在参数里,另一种是在外面定义模板,然后把id值写进去,推荐第二种
<scritp type="text/x-template" id="list-items-template">

</scritp>
# 这里需要注意的就是script中的参数,定义完上面的模板就可以像下面这样写了
Vue-component('list-items', {
    template: '#list-items-template',
})
# Vue-component中还有两个重要的参数,就是props,methods参数和data函数
Vue-component('list-items', {
    template: '#list-items-template',
    # 这里给组件定义了一个接口用来绑定new Vue实例中data属性的数据
    props: ['lists'],
    # 这里可以直接使用methods参数像new Vue实例中一样
    methods: {}
    # 要在Vue-component中定义数据需要使用data函数,注意是函数
    data:function () {
        return {
            // 返回的数据
        }
    }
})
# 组件定义完毕,应用和绑定数据的方式就是下面这样的,其中冒号绑定的完整写法是v-bind:lists=""这样的
<list-items-template :lists='lists'></list-items-template>
```

**完整演示**

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Learning Vue.js</title>
    <link rel="stylesheet" href="./css/bootstrap.min.css">
    <style>
        .status {
            color: #67b168;
            text-decoration: line-through;
        }
        button {
            margin-left: 5px;
        }
    </style>
</head>
<body>
<div class="navbar navbar-default navbar-static-top">
    <span class="navbar-brand">My Todo List</span>
</div>
<div class="container" id="click">
    <div class="row">
        <div class="col-md-8 col-md-offset-2">
            <div class="panel panel-default">
                <div class="panel-heading">Welcome Todolist</div>
                <div class="panel-body">
                    <h3>{{ msg + ' . ' + listNum }}</h3>
                    <list-items :lists="lists"></list-items>
                    <list-form-add :lists="lists"></list-form-add>
                </div>
            </div>
        </div>
    </div>
</div>
<script type="text/x-template" id="list-items-template">
    <ul class="list-group">
        <li class="list-group-item"
            v-bind:class="{'status':i.status}"
            v-for="(i,index) in lists">{{ i.title }}
            <button v-on:click="delList(index)"
                    class="btn btn-warning btn-xs pull-right">删除清单</button>
            <button v-bind:class="[ i.status ? 'btn-success' : 'btn-danger' ]"
                    v-on:click="checkStatus(i)"
                    class="btn btn-success btn-xs pull-right">
                {{ i.status ? '完成' : '未完成' }}
            </button>
        </li>
    </ul>
</script>
<script type="text/x-template" id="list-form-template">
    <form v-on:submit.prevent="addList(newList)">
        <div class="form-group">
            <input v-model="newList.title" type="text" class="form-control" placeholder="添加一个list">
        </div>
        <div class="form-g">
            <button class="btn btn-success">添加清单</button>
        </div>
    </form>
</script>
<script src="js/vue.js"></script>
<script>
    Vue.component('list-items', {
        template: '#list-items-template',
        props: ['lists'],
        methods: {
            delList:function (index) {
                this.lists.splice(index,1)
            },
            checkStatus:function (i) {
                i.status = ! i.status
            }
        }
    });

    Vue.component('list-form-add', {
        template: '#list-form-template',
        props: ['lists'],
        methods: {
            addList:function (newList) {
                if (newList.title.length <= 0) {
                    return false;
                }
                this.lists.push(newList)
                this.newList = {
                    id:null,
                    title:'',
                    status:false
                }
            }
        },
        data:function () {
            return {
                newList: {
                    id:null,
                    title:'',
                    status:false
                }
            }
        }
    });

    new Vue({
        el: '#click',
        data: {
            msg: 'My Todo List',
            lists: [
                {
                    id:1,
                    title:'Test List',
                    status: false
                }
            ]
        },
        computed: {
            listNum:function () {
                return this.lists.length;
            }
        }
    })
</script>
</body>
</html>
```



