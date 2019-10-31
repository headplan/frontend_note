# Vue-axios

#### axios

> vue更新到2.0之后,作者就宣告不再对vue-resource更新,而是推荐axios

[https://www.npmjs.com/package/axios](https://www.npmjs.com/package/axios)

[https://github.com/mzabriskie/axios](https://github.com/mzabriskie/axios)

```
# 兼容VueJS
cnpm install axios vue-axios --save

# 引入应用
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)
```

**应用**

```
# 应用axios
Vue.axios.get(api).then((response) => {
  console.log(response.data)
})

this.axios.get(api).then((response) => {
  console.log(response.data)
})

this.$http.get(api).then((response) => {
  console.log(response.data)
})
```

```
# 要调用实时加载函数mounted
mounted(){
  this.axios.get('http://localhost:8080/api/movies').then((respones) => {
    console.log(respones.data);
  })
}
```

**后端API跨域**

如果跨域请求后端API\(Laravel\) , 可以使用一个package解决 .

> [https://github.com/barryvdh/laravel-cors](https://github.com/barryvdh/laravel-cors)



