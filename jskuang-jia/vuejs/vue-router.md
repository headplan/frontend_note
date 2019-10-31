# Vue-Router

**安装**

```
cnpm install vue-router
```

**引入应用**

```
import Vue from 'vue'
import Router from 'vue-router'

Vue.use(Router)
```

**定义路由**

```
const routes = [
  {
    path: '/',
    name: 'Hello',
    component: Hello
  },
  {
    path: '/testroute',
    name: 'TestRoute',
    component: TestRoute
  }
];

export default new Router({routes})
```

**视图展示标签**

```
<router-view></router-view>
```

```
# <router-link> 组件支持用户在具有路由功能的应用中（点击）导航
<router-link to="home">Home</router-link>
```



