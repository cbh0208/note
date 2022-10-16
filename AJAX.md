

# XMLHttpRequest 

XMLHttpRequest 用于在**后台与服务器交换数据**。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。

```javascript
		//1.创建对象
		var xmlhttp = new XMLHttpRequest(); 
		//2.初始化(GET或POST)(默认async=true)
		xmlhttp.open("GET","https://api.apiopen.top/getJoke",true);
		//3.发送(将请求发送到服务器)(send(string)：仅用于 POST 请求)
		xmlhttp.send();
		//4.绑定事件处理，响应结果
		xmlhttp.onreadystatechange=function()
 		{
  			if (xmlhttp.readyState==4 && xmlhttp.status==200)
    		{
    			console.log(xmlhttp.response);
    		}
            else
            {
                console.log(xmlhttp.status);
            }
  		}
```

## readyState

每当 readyState **改变**时，就会触发 **onreadystatechange** 事件

 **0** － （未初始化）还没有调用send()方法
 **1** － （载入）已调用send()方法，正在发送请求
 **2** － （载入完成）send()方法执行完成，已经接收到全部响应内容
 **3** － （交互）正在解析响应内容
 **4** － （**完成**）响应内容解析完成，可以在客户端调用了

## status

**200**——"OK"

**404**——未找到页面



## 取消请求

```
abort()
```





# promise(ES6)

```javascript
//Ajax
function ajax(URL) {
    return new Promise(function (resolve, reject) {
        var req = new XMLHttpRequest(); 
        req.open('GET', URL, true);
        req.onload = function () {
        if (req.status === 200) { 
                resolve(req.responseText);
            } else {
                reject(new Error(req.statusText));
            } 
        };
        req.onerror = function () {
            reject(new Error(req.statusText));
        };
        req.send(); 
    });
}
var URL = "https://api.apiopen.top/getJoke"; 
ajax(URL).then(function onFulfilled(value){
    document.write('内容是：' + value); 
}).catch(function onRejected(error){
    document.write('错误：' + error); 
});


//IE的script 元素只支持onreadystatechange事件，不支持onload事件。
//FF的script 元素不支持onreadystatechange事件，只支持onload事件。
```











# async/await

```javascript
//Ajax
function ajax(URL) {
    return new Promise(function (resolve, reject) {
        var req = new XMLHttpRequest(); 
        req.open('GET', URL, true);
        req.onload = function () {
        if (req.status === 200) { 
                resolve(req.responseText);
            } else {
                reject(new Error(req.statusText));
            } 
        };
        req.onerror = function () {
            reject(new Error(req.statusText));
        };
        req.send(); 
    });
}
// var URL = "https://api.apiopen.top/getJoke"; 
// ajax(URL).then(function onFulfilled(value){
//     document.write('内容是：' + value); 
// }).catch(function onRejected(error){
//     document.write('错误：' + error); 
// });
var URL = "https://api.apiopen.top/getJoke"; 
async function m(){
  let result=await ajax(URL);
  document.write('内容是：' + result);
}
m()
```







# axios

```sh
npm install axios
```

## 基础

```js
axios.get('http://localhost:3000/api1/tt').then(
            res=>{console.log('成功',res.data);},
            err=>{console.log('失败',err);}
        )
```





## 配置默认值



### 全局的 axios 默认值

```js
axios.defaults.baseURL = 'https://api.example.com';
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
```





### 自定义实例默认值

```js
// Set config defaults when creating the instance
const instance = axios.create({
  baseURL: 'https://api.example.com'
});

// Alter defaults after instance has been created
instance.defaults.headers.common['Authorization'] = AUTH_TOKEN;

```





## 拦截器

- 在请求或响应被 `then` 或 `catch` 处理前拦截它们

```js
// 添加请求拦截器
axios.interceptors.request.use(function (config) {
    // 在发送请求之前做些什么
    return config;
  }, function (error) {
    // 对请求错误做些什么
    return Promise.reject(error);
  });

// 添加响应拦截器
axios.interceptors.response.use(function (response) {
    // 对响应数据做点什么
    return response;
  }, function (error) {
    // 对响应错误做点什么
    return Promise.reject(error);
  });
```

### 拦截器清除

```js
const myInterceptor = axios.interceptors.request.use(function () {/*...*/});
axios.interceptors.request.eject(myInterceptor);
```

### 为自定义 axios 实例添加拦截器

```js
const instance = axios.create();
instance.interceptors.request.use(function () {/*...*/});

```

## 取消请求

- 使用 *cancel token* 取消请求
- 可以使用 `CancelToken.source` 工厂方法创建 cancel token

```js
const CancelToken = axios.CancelToken;
const source = CancelToken.source();

axios.get('/user/12345', {
  cancelToken: source.token
}).catch(function(thrown) {
  if (axios.isCancel(thrown)) {
    console.log('Request canceled', thrown.message);
  } else {
     // 处理错误
  }
});

axios.post('/user/12345', {
  name: 'new name'
}, {
  cancelToken: source.token
})

// 取消请求（message 参数是可选的）
source.cancel('Operation canceled by the user.');
```

