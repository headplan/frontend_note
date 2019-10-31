# 小应用

**下载安装**

开发版本 - [http://vuejs.org/js/vue.js](http://vuejs.org/js/vue.js) : 包含完整的警告和调试模式

生产版本 - [http://vuejs.org/js/vue.min.js](http://vuejs.org/js/vue.min.js) : 删除了警告 , 24.72kb min+gzip

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Learning Vue.js</title>
    <link rel="stylesheet" href="./css/bootstrap.min.css">
</head>
<body>
<div class="navbar navbar-default navbar-static-top">
    <span class="navbar-brand">Learning Vue.js</span>
</div>
<div class="container" id="click">
    <div class="row">
        <div class="col-md-8 col-md-offset-2">
            <div class="panel panel-default">
                <div class="panel-heading">Welcome Baby</div>
                <div class="panel-body">
                    <h1>Hello World!</h1>
                </div>
            </div>
        </div>
    </div>
</div>

<script src="js/vue.js"></script>
<script>
    new Vue({

    })
</script>
</body>
</html>
```

**实例化绑定数据**

```js
# 启动vue,实例化vue
new Vue({
  // 选项
})
# 或者
var vm = new Vue({
  // 选项
})
```

```js
new Vue({
    # 绑定html元素
    el: '#app',
    # 绑定数据
    data: {
        msg: 'Hello World!'
    }
})

# HTML部分修改id为app,数据展示使用{{msg}}方式,就会显示msg中的内容了
```

**数据双向绑定v-model**

通常用于表单中

```js
# 在HTML中使用v-model绑定实例中的msg即可
<input type="text" class="form-control" v-model="msg">
```

**循环数组v-for**

```js
# 在Vue实例中的data中创建一个数组
data: {
    msg: 'Hello World!',
    lists: [
        {
            id:1,
            title:'Learning Vue'
        }
    ]
}
# html中使用v-for循环data中的lists,格式是这样的item in items
<ul class="list-group">
    <li class="list-group-item" v-for="i in lists">{{ i.title }}</li>
</ul>
```

**事件绑定v-on**

```js
# 先添加一个表单用来添加list列表清单,使用事件绑定v-on,并使用prevent阻止submit的刷新页面行为,转换成要执行的方法
<form v-on:submit.prevent="addList(newList)">
    <div class="form-group">
        <input type="text" class="form-control" placeholder="添加一个list">
    </div>
    <div class="form-g">
        <button class="btn btn-success">添加清单</button>
    </div>
</form>
# 现在需要添加上面定义的newList对象的初始化和addList方法
new Vue({
    el: '#click',
    data: {
        msg: 'Hello World!',
        lists: [
            {
                id:1,
                title:'Learning Vue'
            }
        ],
        newList: {
            id:null,
            title:''
        }
    }
    methods: {
        addList:function (newList) {
            // 将newList对象push进去
            this.lists.push(newList)
        }
        // 这里也可以使用ES6的写法
        addList(newLIst){

        }
    }
})
# 最后绑定input中输入的数据绑定到newList中,然后addList方法中就会将其push到lists中
# 这里还需要修改一下addList方法,在push之后数据的绑定还是存在的,输入的内容会绑定在上一条add的list中
# 这里还需要一部就是在方法中重新初始化newList
<div class="form-group">
    <input v-model="newList.title" type="text" class="form-control" placeholder="添加一个list">
</div>

addList:function (newList) {
    // 将newList对象push进去
    this.lists.push(newList)
    this.newList = {
        id:null,
        title:''
    }
}
```

**扩展:删除list**

```js
# 删除按钮,并且绑定click事件到这个按钮
# 需要注意的是,这里官方推荐在v-for当中使用新的变量
# 这也引出了vue1.0和vue2.0的区别
<li class="list-group-item" v-for="(i,index) in lists">{{ i.title }}
    <button v-on:click="delLIst(index)"
            class="btn btn-warning btn-xs pull-right">删除清单</button>
</li>

# 添加delList方法
delList:function (index) {
    this.lists.splice(index,1)
}
# vue1.0的时候会这样写,因为没有新的index变量,所以会直接操作list变量
delList:function (list) {
    this.lists.$remove(list)
}
```

**完整演示**

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Learning Vue.js</title>
    <link rel="stylesheet" href="./css/bootstrap.min.css">
</head>
<body>
<div class="navbar navbar-default navbar-static-top">
    <span class="navbar-brand">Learning Vue.js</span>
</div>
<div class="container" id="click">
    <div class="row">
        <div class="col-md-8 col-md-offset-2">
            <div class="panel panel-default">
                <div class="panel-heading">Welcome Baby</div>
                <div class="panel-body">
                    <h1>{{ msg }}</h1>
                    <ul class="list-group">
                        <li class="list-group-item" v-for="(i,index) in lists">{{ i.title }}
                            <button v-on:click="delLst(index)"
                                    class="btn btn-warning btn-xs pull-right">删除清单</button>
                        </li>
                    </ul>
                    <form v-on:submit.prevent="addList(newList)">
                        <div class="form-group">
                            <input v-model="newList.title" type="text" class="form-control" placeholder="添加一个list">
                        </div>
                        <div class="form-group">
                            <button class="btn btn-success">添加清单</button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>

<script src="js/vue.js"></script>
<script>
    new Vue({
        el: '#click',
        data: {
            msg: 'Hello World!',
            lists: [
                {
                    id:1,
                    title:'Learning Vue'
                }
            ],
            newList: {
                id:null,
                title:''
            }
        },
        methods: {
            addList:function (newList) {
                this.lists.push(newList)
                this.newList = {
                    id:null,
                    title:''
                }
            },
            delList:function (index) {
                this.lists.splice(index,1)
            }
        }
    })
</script>
</body>
</html>
```



