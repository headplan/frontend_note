# axios API

可以通过向`axios`传递相关配置来创建请求 . 

axios\(config\)

```js
// 发送POST请求
axios({
  method: 'post',
  url: '/user/12345',
  data: {
    firstName: 'Fred',
    lastName: 'Flintstone'
  }
});
```



