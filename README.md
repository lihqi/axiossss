## axios用法
>  原文地址 http://www.kancloud.cn/yunye/axios/234845

### 特征
* 从浏览器中创建 XMLHttpRequests(跟其它ajax库一样)
* 从 node.js 创建 http 请求(后端？)
* 支持 Promise API(解决异步回调)
* 拦截请求和响应
* 转换请求数据和响应数据
* 取消请求
* 自动转换 JSON 数据(不用自己转了么)
* 客户端支持防御 XSRF(防止ajax数据被劫持？)

### 例子

#### 执行 GET 请求
```
// 为给定 ID 的 user 创建请求
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
// 可选地，上面的请求可以这样做
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```
#### 执行 POST 请求
```
axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```
#### 执行多个并发请求
```
function getUserAccount() {
  return axios.get('/user/12345');
}

function getUserPermissions() {
  return axios.get('/user/12345/permissions');
}

axios.all([getUserAccount(), getUserPermissions()])
  .then(axios.spread(function (acct, perms) {
    // 两个请求现在都执行完成
  }));
  ```
