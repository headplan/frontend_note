# axios API

可以通过向`axios`传递相关配置来创建请求 .

**axios\(config\)**

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

##### axios\(url\[, config\]\)

```js
// 发送 GET 请求（默认的方法）
axios('/user/12345');
```

#### 请求方法的别名

```
axios.request(config)
axios.get(url[, config])
axios.delete(url[, config])
axios.head(url[, config])
axios.post(url[, data[, config]])
axios.put(url[, data[, config]])
axios.patch(url[, data[, config]])
```

在使用别名方法时 , `url`、`method`、`data`这些属性都不必在配置中指定 . 

