# npm

### install

- `npm install -S <module_name>`即`npm install --save <module_name>`

- `yarn add <module_name>`

  写入dependencies



- `npm install -D <module_name>`即`npm install --save-dev <module_name>`

  写入devDependencies



- `npm install -g <module_name>`

- `yarn global add <module_name>`

  全局安装

  







### `package.js`

- `~`
  - 匹配最近的`小`版本依赖包
  - 比如~1.2.3会匹配所有1.2.x版本，但是不包括1.3.0
- `^`
  - 匹配最新的`大`版本依赖包
  - 比如^1.2.3会匹配所有1.x.x的包，包括1.3.0，但是不包括2.0.0
- `*`
  - 安装最新版本的依赖包







# 核心模块

## fs

- 文件系统


```javascript
//导入模块
const fs=require('fs')
//读文件  (文件路径,回调函数(err,data))
//data默认二进制数据 要toString()
fs.readFile("./text.md",(err,data)=>{
    if(err) console.log(err);
    console.log(data.toString());
})
```

```javascript
const fs=require('fs')
//写文件  (文件路径,写入内容,回调函数(err))
fs.writeFile("./txt.md","满船清梦压星河",err=>{
    if(err) console.log(err);
})
```



## path

- 操作路径


```javascript
const path=require("path")
//获取拓展名
console.log(path.extname("./txt.md"));
```







## os

operating system  操作系统 用来获取机器信息

```javascript
const os=require("os")
//cpu信息
console.log(os.cpus());
```

```javascript
const os=require("os")
//内存  (字节)
console.log(os.totalmem());
```





## http

```javascript
const http=require("http")

const server=http.createServer()

server.on('request',(request,response)=>{

    var url=request.url;
    if(url==="/")
    {
        response.end("index page")
    }
    else if(url==="/login")
    {
        response.end("login page")
    }
    else if(url==="/girl")
    {
        const girl=[
            {
                name:"鸢一折纸",
                id:"angel"
            },
            {
                name:"五河琴里",
                id:"5"
            }]
        response.end(JSON.stringify(girl))
    }
    else{
        response.end("404")
    }
    
    
})

server.listen(3000,()=>{
    console.log("Link Start!");
})
```

















# 集成数据库

#### MySQL

```shell
$ npm install mysql
```

```javascript
var mysql = require('mysql')
var connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: '123456',
  database: 'ssmbuild'
})

connection.connect()

connection.query('SELECT * from books', function (err, rows, fields) {
  if (err) throw err

  console.log(rows)
})

connection.end()
```



#### MongoDB

```shell
$ npm install mongodb
```

```javascript
var MongoClient = require('mongodb').MongoClient

MongoClient.connect('mongodb://localhost:27017/music', function (err, client) {
  if (err) throw err

  var db = client.db('music')

  db.collection('love').find().toArray(function (err, result) {
    if (err) throw err

    console.log(result)
  })
})
```



# Express







### 路由

```javascript
const express=require("express")
const { list } = require("../controller")

// 路由中间件
const router=express.Router()

router.get('/index',(req,res,next)=>{
    res.send("hhhhh")
})

router.get('/api/list',list)

module.exports=router
```



# koa

```sh
npm i koa
npm i --save-dev @types/koa
```



```typescript
import Koa,{ Context,Next }  from 'koa'
const app = new Koa();

app.use(async (ctx:Context,next:Next)=>{
    ctx.body = 'Hello World';
})

app.listen(300,()=>{
    console.log('link start!');
    
})
```

