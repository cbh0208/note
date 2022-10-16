# react

## JSX
```html
<script type="text/babel"></script>
```

- JavascriptXML


- 本质是 React.createElement(component,props,...children)`语法糖`

  ```jsx
  // 1、JSX
  const element = (
    <h1 className="greeting">
      Hello, world!
    </h1>
  )
  
  // 2、JSX -> createElement
  const element = React.createElement(
    'h1',
    {className: 'greeting'},
    'Hello, world!'
  )
  
  // React elements: 使用对象的形式描述页面结构
  // Note: 这是简化后的对象结构
  const element = {
    type: 'h1',
    props: {
      className: 'greeting',
    },
    children: ['Hello, world']
  }
  ```

  

```jsx
// 定义虚拟DOM时，直接写HTML标签，不用加引号""
const VD= <h1>hello,world</h1>;
```

```jsx
// 标签中混入JS表达式是用{}
const myId="a"
const myData="鸢一折纸"

const VD= <h1 id={myId}><span>{myData}</span></h1>
```

```jsx
// 样式类名指定用className(避免与类冲突)
const VD= <h1 className="title">hello,world</h1>;
```

```jsx
//内联样式：style={{key:value}}
const VD= <h1 style={{color:"gold",fontSize:"250px"}}>hello,world</h1>;
```

```jsx
// 标签必须闭合
const VD= <input type="text"/>;
```

```jsx
// 标签首字母小写，转为HTML同名标签，无则报错
// 标签首字母大写，渲染对应组件，无则报错
const VD= <div><good></good></div>
//Warning: The tag <good> is unrecognized in this browser.
const VD= <div><Good></Good></div>
//Uncaught ReferenceError: Good is not defined
```





## 组件

#### 声明

##### 函数式

```jsx
import React, { useState } from 'react';
export default function F(props) {
    const {name}=props//
    const [name3,setName3]=useState('宵宫')//
    function handle(){
        setName3('胡桃')
    }
	return (<div>
                <h1>刻晴</h1>
                <h1>{name}</h1>
                <h1>{name3}</h1>
                <button onClick={handle}>click</button>
            </div>)
}
```

##### 类式

```jsx
import React, { Component } from 'react'
export default class C extends Component{
    constructor(props){
        super(props)
        this.state={name3:'宵宫'}
    };
    handle=()=>{
        //箭头函数绑定this
        this.setState({name3:'胡桃'})
    } 
	render(){
        const {name}=this.props
		return (<div>
                    <h1>刻晴</h1>
                    <h1>{name}</h1>
                    <h1>{this.state.name3}</h1>
                    <button onClick={this.handle}>click</button>
                </div>)
	}
}
```

#### 卸载

```jsx
death(){

}
```

#### 容器

```jsx
// Fragment可传key
<Fragment key="xxx"></Fragment>

<></>
```

#### PureComponent

```jsx
// PureComponent自带通过props和state的浅对比来实现 shouldComponentUpate()

// 缺点
// 可能会因深层的数据不一致而产生错误的否定判断，从而shouldComponentUpdate结果返回false，界面得不到更新
```



## 事件处理

```jsx
class LikeButton extends React.Component {
  constructor() {
    super();
    this.state = {liked: false};
      // 绑定this的上下文到LikeButton实例对象
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({liked: !this.state.liked});
  }
  render() {
    const text = this.state.liked ? 'liked' : 'haven\'t liked';
    return (
       // react重载了事件 如onclick ->onClick   onXxx
      <div onClick={this.handleClick}>
        You {text} this. Click to toggle.
      </div>
    );
  }
}
ReactDOM.render(
  <LikeButton />,
  document.getElementById('example')
);
```

```jsx
// 也可以在具体使用该函数的地方绑定this的上下文到LikeButton实例对象
<div onClick={this.handleClick.bind(this)}>
  You {text} this. Click to toggle.
</div>
```

```jsx
//箭头函数将函数的this绑定到其定义时所在的上下文
<div onClick={() => this.handleClick()}>
  You {text} this. Cclick to toggle.
</div>
```



```jsx
// 简化
class LikeButton extends React.Component {
  state = {liked: false};
  handleClick=()=> {
    this.setState({liked: !this.state.liked});
  }
  render() {
    const text = this.state.liked ? 'liked' : 'haven\'t liked';
    return (
      <div onClick={this.handleClick}>
        You {text} this. Click to toggle.
      </div>
    );
  }
}
ReactDOM.render(
  <LikeButton />,
  document.getElementById('example')
);
```







## state

函数式无法使用

```jsx
// 设置state
	class Md extends React.Component{
		constructor(props){
			super(props);
			this.state={name:"五河琴里"}
		}
	 	render(){
	 		return (<div>鸢一折纸</div>)
	 	}
	 }
```

##### setState()

**更改**`state`  只能用`setState()`

```jsx
// 对象式(函数式语法糖)(callback非必须)(callback在rander(后执行))
// setState(stateChange,[callback])
this.setState({count:this.state.count+1},()=>{
    console.log(this.state.count)
})

// 函数式
// setState(updater,[callback])
this.setState((state,props)=>{count:state.count+1},()=>{
    console.log(this.state.count)
})
```



```jsx
// 更改state  用setState()
	 class Md extends React.Component{
		constructor(props){
			super(props);
			this.state={name:"五河琴里"}

		}
	 	render(){
	 		return <div onClick={()=>this.o()}>{this.state.name}</div>
	 	}
		o(){
            // 更改state
			this.setState({name:"鸢一折纸"})
		}
	 }

	ReactDOM.render(
		<Md/>,
		document.getElementById('example')
	);

```





## props

**props** 是不可变的        子组件只能通过 props 来传递数据

### 类式

```jsx
class Love extends React.Component { 
	render() {
    	return (
      		<ul>
				<li>{this.props.name}</li>
				<li>{this.props.code}</li>
			</ul>
    	);
  	}
}
ReactDOM.render(
  <Love name="鸢一折纸" code="angel"/>,
  document.getElementById('example')
);
```

```jsx
class Love extends React.Component { 
	render() {
	  	const {name,code}=this.props
    	return (
      		<ul>
				<li>{name}</li>
				<li>{code}</li>
			</ul>
    	);
  	}
}

const angel={name:"鸢一折纸",code:"angel"}
ReactDOM.render(
  <Love {...angel}/>,
  document.getElementById('example')
);
```

### 函数式

```jsx
function Love(props){
	const {name,code,age}=props
	return (
      		<ul>
				<li>{name}</li>
				<li>{code}</li>
				<li>{age}</li>
			</ul>
    	);
}
Love.propTypes={
    name:PropTypes.string.isRequired,  //name限制为字符串，且必传
	age:PropTypes.number,              //age限制为数值
    speak:PropTypes.func               //speak限制为方法
    
}
Love.defaultProps={
	age:16      //age默认值为16
}
const angel={name:"鸢一折纸",code:"angel",age:16}
ReactDOM.render(
  <Love {...angel}/>,
  document.getElementById('example')
);
```

### 验证

```jsx
// props验证  React.PropTypes 在 React v15.5 版本后已经移到了 prop-types 库。
class Love extends React.Component {       
	render() { 	
        const {name,code,age}=this.props
    	return (
      	<ul>
			<li>{name}</li>
			<li>{code}</li>
			<li>{age+1}</li>
		</ul>
    );
  }
}
Love.propTypes={
    name:PropTypes.string.isRequired,  //name限制为字符串，且必传
	age:PropTypes.number,              //age限制为数值
    speak:PropTypes.func               //speak限制为方法
    
}
const angel={name:"鸢一折纸",code:"angel",age:16}
ReactDOM.render(
  <Love {...angel}/>,
  document.getElementById('example')
);
```

### 默认

```jsx
// props 默认  defaultProps
class Love extends React.Component { 
 	render() {
	  	const {name,code,age}=this.props
    	return (
      	<ul>
			<li>{name}</li>
			<li>{code}</li>
			<li>{age}</li>
		</ul>
    );
  }
}
Love.defaultProps={
	age:16      //age默认值为16
}
const angel={name:"鸢一折纸",code:"angel"}
ReactDOM.render(
  <Love {...angel}/>,
  document.getElementById('example')
);
```

```jsx
// 简写  defaultProps propTypes看写为类静态属性
class Love extends React.Component {
	static defaultProps={age:16};
	static propTypes={age:PropTypes.number};
  	render() {
	  	const {name,code,age}=this.props
    	return (
      		<ul>
				<li>{name}</li>
				<li>{code}</li>
				<li>{age+1}</li>
			</ul>
    	);
  	}
}

const angel={name:"鸢一折纸",code:"angel"}
ReactDOM.render(
  <Love {...angel}/>,
  document.getElementById('example')
);
```





### childrenProps

`this.props.children`表示组件所有的**子节点**

```jsx
<NavLink to="/about" children="about" ></NavLink> 
<NavLink to="/about" >about</NavLink>
```



### renderProps

相当于vue的插槽

与children相比可携带数据

```jsx
<A render={(name)=><B name={name} />}/>

{this.props.render(name)}
```




## refs

函数式无法使用

##### String

```jsx
// String 类型的 Refs
// 过时 效率不高 可能废弃
class Love extends React.Component {
	showData=()=>{
		const {input1}=this.refs;
		alert(input1.value)
	}
  	render() {
	  	const {name,code,age}=this.props
    	return (
      		<div>
				<input ref="input1" type="text" placeholder="请输入数据"/>
				<button onClick={this.showData}>点击显示数据</button>
			</div>
    	);
  	}
}
```

##### 回调 

```jsx
// 回调 Refs
// 如果ref回调函数是内联函数,更新过程中将执行两次(第一次传入null,第二次传入DOM元素)(用类绑定回调可避免)
class Love extends React.Component {
	showData=()=>{
        const {input1}=this
		alert(this.input1.value)
	}
  	render() {
	  	const {name,code,age}=this.props
    	return (
      		<div>
				<input ref={(c)=>{this.input1=c}} type="text" placeholder="请输入数据"/>
				<button onClick={this.showData}>点击显示数据</button>
			</div>
    	);
  	}
}
```

##### createRef()

```jsx
// createRef()
// React.createRef()调用后返回一个容器,可存储被ref标记节点(只能存一个)
class Love extends React.Component {
	myRef=React.createRef();
	showData=()=>{
		alert(this.myRef.current.value)
	}
  	render() {
	  	const {name,code,age}=this.props
    	return (
      		<div>
				<input ref={this.myRef} type="text" placeholder="请输入数据"/>
				<button onClick={this.showData}>点击显示数据</button>
			</div>
    	);
  	}
}
```





## 表单

### 受控

#### `<input>`

```jsx
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('提交的名字: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          名字:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="提交" />
      </form>
    );
  }
}
```





#### `<textarea>`

```jsx
class EssayForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: '请撰写一篇关于你喜欢的 DOM 元素的文章.'
    };

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('提交的文章: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          文章:
          <textarea value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="提交" />
      </form>
    );
  }
}
```



#### `<select>`

```jsx
class FlavorForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: 'coconut'};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('你喜欢的风味是: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          选择你喜欢的风味:
          <select value={this.state.value} onChange={this.handleChange}>
            <option value="grapefruit">葡萄柚</option>
            <option value="lime">酸橙</option>
            <option value="coconut">椰子</option>
            <option value="mango">芒果</option>
          </select>
        </label>
        <input type="submit" value="提交" />
      </form>
    );
  }
}
```



### 非受控

## 组件通信

```markdown
1.props

2.消息订阅-发步
	-pub-sub

3.集中式管理
	-redux

4.context
```



#### 通过props

```jsx
import React, { Component } from 'react'
export default class Parent extends Component {
    state={a:"鸢一折纸",b:""}
    updateB=(b)=>{
        this.setState(b)
    }
    render() {
        return (
            <div style={{backgroundColor:'orange',width:'500px',padding:'5px'}}>
                <h1>parent组件</h1>
                <h2>parent属性:{this.state.a}</h2>
                <h2>grand属性:{this.state.b}</h2>
                <Child a={this.state.a} updateB={this.updateB} />
            </div>
        )
    }    
}
class Child extends Component {
    state={b:""};
    updateB=(b)=>{
        this.setState(b)
    }
    send=()=>{
        this.props.updateB({b:this.state.b})
    }
    render() {
        return (
            <div style={{backgroundColor:'skyblue',width:'490px',padding:'5px'}}>
                <h1>child组件</h1>
                <h2>parent属性:{this.props.a}</h2>
                <h2>grand属性:{this.state.b}<button onClick={this.send}>send</button></h2>
                <Grand a={this.props.a} updateB={this.updateB}/>
            </div>
        )
    }
}
class Grand extends Component {
    state={b:"五河琴里"}
    send=()=>{
        this.props.updateB({b:this.state.b})
    }
    render() {
        return (
            <div style={{backgroundColor:'gray',width:'480px',padding:'5px'}}>
                <h1>grand组件</h1>
                <h2>parent属性:{this.props.a}</h2>
                <h2>grand属性:{this.state.b}<button onClick={this.send}>send</button></h2>
            </div>
        )
    }
}
```

#### 通过context

```jsx
import React, { Component } from 'react'
// 1.创建context
const MyContext=React.createContext();

export default class Parent extends Component {
    state={a:"鸢一折纸"}
    static contextType=MyContext;
    render() {
        return (
            <div style={{backgroundColor:'orange',width:'500px',padding:'5px'}}>
                <h1>parent组件</h1>
                <h2>parent属性:{this.state.a}</h2>
                <h2>grand属性:</h2>
                {/* 2.为context注入value */}
                <MyContext.Provider value={this.state.a}><Child /></MyContext.Provider>
                
            </div>
        )
    }    
}
class Child extends Component {
	// 3.接收context的value
    // (1)通过contextType(仅类式可用)
    static contextType=MyContext;
	
    render() {
        return (
            <div style={{backgroundColor:'skyblue',width:'490px',padding:'5px'}}>
                <h1>child组件</h1>
                <h2>parent属性:{this.context}</h2>
                <h2>grand属性:{}</h2>
                <Grand />
            </div>
        )
    }    
}
class Grand extends Component {
    state={b:"五河琴里"}
    static contextType=MyContext;
    render() {
        return (
            <div style={{backgroundColor:'gray',width:'480px',padding:'5px'}}>
                <h1>grand组件</h1>
                {/* (2)通过Consumer*/}
                <h2>parent属性:<MyContext.Consumer>{value=>value}</MyContext.Consumer></h2>
                <h2>grand属性:{this.state.b}</h2>
            </div>
        )
    }    
}
```



## 生命周期

### 旧

**16.4之前**

![](https://upload-images.jianshu.io/upload_images/16775500-8d325f8093591c76.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/740/format/webp)

```markdown
#初始化:由ReactDOM.render触发--初次渲染
	-constructor()
	-componentWillMount()
	-render()===>必须用
	-componentDidMount()===>常用
		-常做初始化的事:开启定时器,发送网络请求,订阅信息

#更新阶段:由组件内部this.setState()或父组件render()触发
	-shouldComponentUpdate
	-componentWillUpdate
	-render()
	-componentDidUpdate()

#卸载组件:由ReactDOM.unmountComponentAtNode()触发
	-componentWillUnmount()===>常用
		-常做收尾的事:关闭定时器,取消订阅信息
```



### 新

**16.4之后**

![](https://upload-images.jianshu.io/upload_images/16775500-102dbe772034e8fa.png?imageMogr2/auto-orient/strip|imageView2/2/w/1002/format/webp)

```markdown
#过时(需加前缀 UNSAFE_ )
	-componentWillMount
	-componentWillReceiveProps
	-componentWillUpdate
#新增
	-getDervedStateFromProps
	-getSnapshotBeforeUpdate
```

```
componentDidMount
组件挂载完毕

componentWillUnmount
组件将要卸载

render
初始化渲染,状态更新后
```

#### 挂载

当组件实例被创建并插入 DOM 中时，其生命周期调用顺序如下：

- **`constructor()`**
- `static getDerivedStateFromProps()`
- **`render()`**
- **`componentDidMount()`**

> 注意:
>
> 下述生命周期方法即将过时，在新代码中应该避免使用它们：
>
> - `UNSAFE_componentWillMount()`

#### 更新

当组件的 props 或 state 发生变化时会触发更新。组件更新的生命周期调用顺序如下：

- `static getDerivedStateFromProps()`
- `shouldComponentUpdate()`
- **`render()`**
- `getSnapshotBeforeUpdate()`
- **`componentDidUpdate()`**

> 注意:
>
> 下述方法即将过时，在新代码中应该避免使用它们：
>
> - `UNSAFE_componentWillUpdate()`
> - `UNSAFE_componentWillReceiveProps()`



#### 卸载

当组件从 DOM 中移除时会调用如下方法：

- `componentWillUnmount()`



## Hooks

*Hooks* 是 `React 16.8` 的新增特性。可以在不编写 class 的情况下使用 state 以及其他的 React 特性。

### 基础Hook

#### useState

```jsx
// 让函数组件使用state状态
// React.useState()

// 语法:	const [xxx,setXxx]=React.useState(initvalue)
// useState() 接收状态初值 返回包含2个元素数组(一个为状态值,一个为更新状态函数) 第一次初始化值作缓存
// 更新状态函数两种写法 setXxx(newVaule) setXxx(value=>newValue) 
const [count,setCount]=React.useState(0);
function add(){
    setCount(count+1);
    //setCount(count=>count+1)
}
```



#### useEffect

```jsx
// 让函数组件使用生命周期钩子
// React.useEffect()

// 第二个参数为空,全部检测
React.useEffect(()=>{
    console.log('666')
})

// 第二个参数为[],  (componentDidMount 使用)
React.useEffect(()=>{
    console.log('666')// 挂载时调用一次
},[])


// 第二个参数为变量, (componentDidUpdate)
const [count,setCount]=React.useState(0);
React.useEffect(()=>{
    console.log('666')
},[count])// count改变时调用(挂载时也调用一次)


// 第二个参数为return 函数( componentWillUnmount) 
React.useEffect(()=>{
    console.log('666')
},return ()=>{
    console.log('卸载时调用')
})
```



#### useContext

### 额外Hook

#### useRef

```jsx
// 让函数组件使用ref
// React.useRef()

//
// 使用同React.createRef()
```

useContext





























































## 错误边界

捕捉后代组件错误,渲染备用组件

```

```



# creat-react-app

```
npx create-react-app my-app
```

```
npx create-react-app my-app --template typescript 
```



## 配置代理

```json
//1
// package.json
"proxy":"http://localhost:5000"

//请求原端口不存在资源时,向5000发请求
```

```js
//2
// src/setupProxy.js
const proxy=require('http-proxy-middleware')

module.exports=function(app){
    app.use(
        proxy('/api1',{ // 需转发请求
            target:'http://localhost:5000', //转发目标地址
            changeOrigin:true,  // 控制服务器收到请求头中host地址 (默认false)
            pathRewrite:{'^/api1':''} //去除请求前缀
        })
    )
}


// 请求要加前缀
// axios.get('http://localhost:3000/api1/students')
```



# react-router

## react-router-dom

用于浏览器

```shell
npm install react-router-dom
```



```jsx
import { Routes, Route, Outlet, Link } from "react-router-dom";
import { NoMatch } from "../inbox/no-match";
import "./index.css";

export default function HomeApp() {
  return (
    <Routes>
      <Route path="/" element={<Layout />}>
        <Route index element={<Home />} />
        <Route path="about" element={<About />} />
        <Route path="*" element={<NoMatch />} />
      </Route>
    </Routes>
  );
}

function Layout() {
  return (
    <div>
      <h1>Welcome to the Home app!</h1>

      <p>
        This example demonstrates how you can stitch two React Router apps
        together using the <code>`basename`</code> prop on{" "}
        <code>`BrowserRouter`</code> and <code>`StaticRouter`</code>.
      </p>

      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            {/* Use a normal <a> when linking to the "Inbox" app so the browser
                does a full document reload, which is what we want when exiting
                this app and entering another so we execute its entry point in
                inbox/main.jsx. */}
            <a href="/inbox">Inbox</a>
          </li>
        </ul>
      </nav>

      <hr />

      <Outlet />
    </div>
  );
}

function Home() {
  return (
    <div>
      <p>This is the home page.</p>
    </div>
  );
}

function About() {
  return (
    <div>
      <p>This is the about page.</p>
    </div>
  );
}


```

#### 内置组件

##### BrowserRouter

```jsx
// 在最外层,包裹所有组件
<BrowserRouter></BrowserRouter>
```

```markdown
使用H5的history API,不兼容E9及以下版本
路径中没有#
刷新后对路由state参数无影响,state保存在history对象中
```



##### HashRouter

```jsx
// 在最外层,包裹所有组件
<HashRouter></HashRouter>
```

```
使用URL的哈希值
路径中包含#
刷新后对路由state参数有影响,会丢失
```



##### Route

在其路径与当前 URL 匹配时呈现一些 UI。

```jsx
<Route path="/home" component={Home} />
```

```jsx
// 开启精准匹配(默认模糊匹配)(可简写为exact)(可能导致二级路由开启)
<Route exact={true} path="/home" component={Home} />
```



##### Redirect

渲染 `<Redirect>` 将导航到新位置。 新位置将覆盖历史堆栈中的当前位置，就像服务器端**重定向** (HTTP 3xx) 那样。

```jsx
// 设置默认状态
<Redirect to="/home" />
```



##### Link

围绕应用程序提供声明性的、可访问的**导航**

```jsx
<Link to="/home">home</Link>
```

```jsx
// 开启replace模式(默认push模式)(可简写为replace)
// replace不会向history插入记录
<Link replace={true} to="/home">home</Link>
```



##### NavLink

`<Link>` 的特殊版本，当它与当前 URL 匹配时，它将向呈现的元素添加**样式属性**。

```jsx
//Link升级 可设置响应时类名(activeClassName)(默认为active)
<NavLink activeClassName="o" to="/home">home</NavLink>
```







#### 嵌套路由

注册子路由时要带上父路由path

路由匹配按注册路由顺序进行





#### 路由传参

##### params参数

```jsx
// 传递params参数

	{/* 向路由组件传params参数 */}
	<Link to={`/home/anime/detail/${obj.id}/${obj.name}`} >{obj.name}</Link>

	{/* 声明接受params参数 */}
	<Route path="/home/anime/derail/:id/:name" component={Detail} />

	{/* 接受params参数 */}
	const {id,name} =this.props.match.params;
```

##### search参数

```jsx
// 传递search参数

	{/* 向路由组件传search参数 */}
    <Link to={`/home/anime/detail/?id=${obj.id}&name=${obj.name}`} >{obj.name}</Link>

	{/* search参数无需声明接收 */}
	<Route path="/home/anime/detail/" component={Detail} />

	{/* 接受search参数(是urlencoded编码字符串,要用querystring解开) */}
	const {search} =this.props.location;//?id=05&name=abc
    const {id,name}=qs.parse(search.slice(1));
```

```jsx
	import qs from 'querystring'   

	let str="id=pricess&age=16";
	console.log(qs.stringify(str))//{id:"pricess",age:"16"}
	let obj={id:"pricess",age:"16"};
	console.log(qs.parse(obj))//"id=pricess&age=16"
```

##### state参数

```jsx
// 传递state参数

	{/* 向路由组件传state参数 */}
	<Link to={{pathname:"/home/anime/detail/",state:{id:obj.id}}} >{obj.id}</Link>

	{/* state参数无需声明接收 */}
	<Route path="/home/anime/detail/" component={Detail} />

	{/* 接受state参数 */}
	const {id}=this.location.state
```



#### 编程跳转

借助`this.props.history`上的API

##### 路由组件

```jsx
// 跳转
	this.props.history.replace("/home",{id:01});// replace不会向history插入记录

	this.props.history.push("/home",{id:01});// push会向history插入记录
```

```jsx
// 回退
	this.props.history.goBack();
    
    this.props.history.go(-1);
```

```jsx
// 前进
	this.props.history.goForward();
    
    this.props.history.go(1);
```



##### 一般组件

使一般组件带有路由组件API

```jsx
import React, { Component } from 'react'
import {withRouter} from 'react-router-dom'

class Demo extends Component {
    render() {
        return (
            <div></div>
        )
    }
}
export default withRouter(Demo);
```





#### 懒加载

```jsx
const Home=lazy(()=>import("./Home"))
```

```jsx
<Suspense fallback={Loading}>
    <Route  path="/home" component={Novel} />
</Suspense>
```



#### 常见问题

##### 多级路径刷新css丢失

```
http://localhost:3000/css/index.css
http://localhost:3000/home/hh/css/index.css
// 由于路由变化,导致css请求路径变化
```

```html
 <!-- 方1 -->
 <!-- 变为公共路径 -->
	<link rel="stylesheet" href="%PUBLIC_URL%/css/index.css">
```

```html
 <!-- 方2 -->
 <!-- 使用HashRouter -->
```



## react-router-native

用于原生应用



## react-router

浏览器和原生应用的通用部分



# redux

## 基础

非官方状态管理工具



```

```

### 三大原则

#### 单一数据源

整个应用的 state 被储存在一棵 object tree 中，并且这个 object tree 只存在于**唯一一个** `store` 中。

#### State 是只读的

唯一改变 state 的方法就是**触发** `action`，action 是一个用于描述已发生事件的普通对象

#### 使用纯函数来执行修改

为了描述 action 如何改变 state tree ，你需要编写 `reducer`s。







### action

- `type`:**标识**属性,值为字符串,唯一,必要属性
- `data`:**数据**属性,值类型任意,可选属性

```json
{
    type:"girl",
    data:{
        name:'',
        age:''
    }
}
```

#### 异步action

```
npm i redux-thunk
```

```

```



### reducer

用于更新状态。任何通过dispatch派发的action都会通过这里来改变store状态



### store

**Redux库提供的createStore函数**：第一个参数代表更新状态的reducer，第二个参数是状态的初始值，第三个参数可选，代表StoreEnhancer。状态通过getStore()获取

## react-redux

React-Redux 将所有组件分成两大类：**UI 组件**（presentational component）和**容器组件**（container component）







# React Native

## 准备

### 环境配置





```
 npx react-native init bang --template react-native-template-typescript
```

### 打包

###### 生成密钥

- 在用`keytool`命令生成一个私有密钥。在 Windows 上`keytool`命令放在 JDK 的 bin 目录中（比如`C:\Program Files\Java\jdkx.x.x_x\bin`）

- ```shell
  keytool -genkeypair -v -storetype PKCS12 -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000 -storepass 123456 -keypass 123456
  
  # PKCS12					证书标准
  # my-release-key.keystore	密钥文件名
  # my-key-alias				密钥别名
  # RSA						加密算法
  # 2048						密钥位数
  # 10000						有效期（天）
  # storepass					库密码
  # keypass					密钥密码
  ```



###### gradle配置

- 把`my-release-key.keystore`文件放到你工程中的`android/app`文件夹下

- 编辑`~/.gradle/gradle.properties`（全局配置，对所有项目有效）或是`项目目录/android/gradle.properties`（项目配置，只对所在项目有效）

- ```properties
  MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
  MYAPP_RELEASE_KEY_ALIAS=my-key-alias
  MYAPP_RELEASE_STORE_PASSWORD=123456
  MYAPP_RELEASE_KEY_PASSWORD=123456
  ```



###### 应用

- 编辑你项目目录下的`android/app/build.gradle`，添加如下的签名配置：

- ```gradle
  ...
  android {
      ...
      defaultConfig { ... }
      signingConfigs {
          release {
              if (project.hasProperty('MYAPP_RELEASE_STORE_FILE')) {
                  storeFile file(MYAPP_RELEASE_STORE_FILE)
                  storePassword MYAPP_RELEASE_STORE_PASSWORD
                  keyAlias MYAPP_RELEASE_KEY_ALIAS
                  keyPassword MYAPP_RELEASE_KEY_PASSWORD
              }
          }
      }
      buildTypes {
          release {
              ...
              signingConfig signingConfigs.release
          }
      }
  }
  ...
  ```
  
  

###### 生成

- ```
  $ cd android
  $ ./gradlew assembleRelease
  ```

- 生成的 APK 文件位于`android/app/build/outputs/apk/release/app-release.apk`




## 内置组件

### Basic Components

| REACT NATIVE UI COMPONENT | ANDROID VIEW   | IOS VIEW         | WEB ANALOG               | 说明                                                         |
| :------------------------ | :------------- | :--------------- | :----------------------- | :----------------------------------------------------------- |
| `<View>`                  | `<ViewGroup>`  | `<UIView>`       | A non-scrollling `<div>` | A container that supports layout with flexbox, style, some touch handling, and accessibility controls |
| `<Text>`                  | `<TextView>`   | `<UITextView>`   | `<p>`                    | Displays, styles, and nests strings of text and even handles touch events |
| `<Image>`                 | `<ImageView>`  | `<UIImageView>`  | `<img>`                  | Displays different types of images                           |
| `<ScrollView>`            | `<ScrollView>` | `<UIScrollView>` | `<div>`                  | A generic scrolling container that can contain multiple components and views |
| `<TextInput>`             | `<EditText>`   | `<UITextField>`  | `<input type="text">`    | Allows the user to enter text                                |



#### `<View>`

- 搭建用户界面的最基础组件





#### `<Text>`

- 显示文本内容的组件



#### `<Image>`

- 显示图片内容的组件



#### `<ScrollView>`

- 可滚动的容器视图





#### `<TextInput>`

- 文本输入框





### User Interface

#### `Button`





#### `Switch`







### List Views

#### `FlatList`





#### `SectionList`







### Android 

#### `BackHandler`



#### `DrawerLayoutAndroid`



#### `PermissionsAndroid`



#### `ToastAndroid`





### iOS 

#### `ActionSheetIOS`



### Others

#### `ActivityIndicator`

#### `Alert`

#### `Animated`

#### `KeyboardAvoidingView`

#### `Linking`

#### `Modal`

#### `PixelRatio`

#### `RefreshControl`

#### `StatusBar`

## 内置api

### Common

#### `Dimensions`

- 用于获取设备屏幕的宽高

- 更推荐使用`useWindowDimensions`这个 Hook API

- ```tsx
  import {Dimensions} from 'react-native';
  const {height, width} = Dimensions.get('window');
  ```



#### `Platform`

- 用于获取平台信息

- ```tsx
  import {Platform} from 'react-native';
  
  ```

  





### Hooks

#### `useColorScheme`

- 获取主题

- ```tsx
  import { useColorScheme } from 'react-native';
  
  const isDarkMode = useColorScheme() === 'dark';
  ```

  



#### `useWindowDimensions`

- 在屏幕尺寸变化时自动更新获取到的设备`width`和`height`值

- ```tsx
  import { useWindowDimensions } from 'react-native';
  
  const { height, width } = useWindowDimensions();
  ```

  



### Android API



### IOS API



## 样式

- 通过`StyleSheet`（提供了一种类似 CSS 样式表的抽象）

```tsx
import { StyleSheet, Text, View } from "react-native";

const styles = StyleSheet.create({
  t1: {
    margin: 10,
  },
});
```



### Text 文本

| 属性名                       | 取值                                                         | 描述                                                         |
| ---------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| color                        | <color>                                                      | 对应 `CSS` color属性                                         |
| fontFamily                   | string                                                       | 对应 `CSS` font-family属性                                   |
| fontSize                     | <number>                                                     | 对应 `CSS` font-size 属性                                    |
| fontStyle                    | `normal`, `italic`                                           | 对应 `CSS` font-style属性，但阉割了 `oblique` 取值           |
| fontWeight                   | `normal`, `bold` `100~900`                                   | 对应 `CSS` font-weight属性，但阉割了 `bolder, lighter` 取值  |
| lineHeight                   | <number>                                                     | 对应 `CSS` line-height 属性                                  |
| textAlign                    | `auto`, `left`, `right`, `center`, `justify`                 | 对应 `CSS` text-align属性，但增加了 `auto` 取值。当取值为 `justify` 时，在 `Android` 上会变为 `left` |
| textDecorationLine           | `none`, `underline`, `line-through`, `underline line-through` | 对应 `CSS` text-decoration-line 属性，但阉割了 `overline`, `blink` 取值 |
| textShadowColor              | <color>                                                      | 对应 `CSS` text-shadow 属性中的颜色定义                      |
| textShadowOffset             | { width:<number>, height:<number> }                          | 对应 `CSS` text-shadow 属性中的阴影偏移定义                  |
| textShadowRadius             | <number>                                                     | 在 `CSS` 中，阴影的圆角大小取决于元素的圆角定义，不需要额外定义 |
| includeFontPadding `Android` | <bool>                                                       | Android在默认情况下会为文字额外保留一些padding，以便留出空间摆放上标或是下标的文字。对于某些字体来说，这些额外的padding可能会导致文字难以垂直居中。如果你把textAlignVertical设置为center之后，文字看起来依然不在正中间，那么可以尝试将本属性设置为false |
| textAlignVertical `Android`  | `auto`, `top`, `bottom`, `center`                            | 对应 `CSS` vertical-align 属性，增加了 `auto` 取值，`center` 取代了 `middle`，并阉割了 `baseline, sub` 等值 |
| fontVariant `iOS`            | `small-caps`, `oldstyle-nums`, `lining-nums`, `tabular-nums`, `proportional-nums` | 对应 `CSS` font-variant属性，但取值更丰富                    |
| letterSpacing `iOS`          | <number>                                                     | 对应 `CSS` letter-spacing 属性                               |
| textDecorationColor `iOS`    | <color>                                                      | 对应 `CSS` text-decoration-color 属性                        |
| textDecorationStyle `iOS`    | `solid`, `double`, `dotted`, `dashed`                        | 对应 `CSS` text-decoration-style 属性，但阉割了 `wavy` 取值  |
| writingDirection `iOS`       | `auto`, `ltr`, `rtl`                                         | 对应 `CSS` direction 属性，增加了 `auto` 取值                |



### Dimension 尺寸

| 属性名    | 取值     | 描述                                                         |
| --------- | -------- | ------------------------------------------------------------ |
| width     | <number> | 对应 `CSS` width 属性 |
| minWidth  | <number> | 对应 `CSS` min-width 属性 |
| maxWidth  | <number> | 对应 `CSS` max-width 属性 |
| height    | <number> | 对应 `CSS` height 属性 |
| minHeight | <number> | 对应 `CSS` min-height 属性 |
| maxHeight | <number> | 对应 `CSS` max-height 属性 |



### Positioning 定位

| 属性名   | 取值                   | 描述                                                         |
| -------- | ---------------------- | ------------------------------------------------------------ |
| position | `absolute`, `relative` | 对应 `CSS` position 属性，但阉割了 `static, fixed` 取值 |
| top      | <number>               | 对应 `CSS` top 属性 |
| right    | <number>               | 对应 `CSS` right 属性 |
| bottom   | <number>               | 对应 `CSS` bottom 属性 |
| left     | <number>               | 对应 `CSS` left 属性 |
| left     | <number>               | 对应 `CSS` left 属性 |



### Margin 外边距

| 属性名           | 取值     | 描述                                                         |
| ---------------- | -------- | ------------------------------------------------------------ |
| margin           | <number> | 对应 `CSS` margin 属性，不同的是，它只能定义一个参数，如需分别定义`上、右、下、左`4个方位的外补白，可以通过下面的单向外部白属性 |
| marginHorizontal | <number> | 无对应的 `CSS` 属性。其效果相当于同时设置 `marginRight` 和 `marginLeft` |
| marginVertical   | <number> | 无对应的 `CSS` 属性。其效果相当于同时设置 `marginTop` 和 `marginBottom` |
| marginTop        | <number> | 对应 `CSS` margin-top 属性 |
| marginRight      | <number> | 对应 `CSS` margin-right 属性 |
| marginBottom     | <number> | 对应 `CSS` margin-bottom 属性 |
| marginLeft       | <number> | 对应 `CSS` margin-left 属性 |



### Padding 内边距

| 属性名            | 取值     | 描述                                                         |
| ----------------- | -------- | ------------------------------------------------------------ |
| padding           | <number> | 对应 `CSS` padding 属性，不同的是，它只能定义一个参数，如需分别定义`上、右、下、左`4个方位的内补白，可以通过下面的单向内部白属性 |
| paddingHorizontal | <number> | 无对应的 `CSS` 属性。其效果相当于同时设置 `paddingRight` 和 `paddingLeft` |
| paddingVertical   | <number> | 无对应的 `CSS` 属性。其效果相当于同时设置 `paddingTop` 和 `paddingBottom` |
| paddingTop        | <number> | 对应 `CSS` padding-top 属性 |
| paddingRight      | <number> | 对应 `CSS` padding-right 属性 |
| paddingBottom     | <number> | 对应 `CSS` padding-bottom 属性 |
| paddingLeft       | <number> | 对应 `CSS` padding-left 属性 |



### Border 边框

| 属性名                  | 取值                                  | 描述                                                         |
| ----------------------- | ------------------------------------- | ------------------------------------------------------------ |
| borderStyle             | `solid`, `dotted`, `dashed`           | 对应 `CSS` `border-style` 属性，但阉割了 `none, hidden, double, groove, ridge, inset, outset` 取值，且无方向分拆属性 |
| borderWidth             | <number>                              | 对应 `CSS` `border-width` 属性                               |
| borderTopWidth          | <number>                              | 对应 `CSS` `border-top-width` 属性                           |
| borderRightWidth        | <number>                              | 对应 `CSS` `border-right-width` 属性                         |
| borderBottomWidth       | <number>                              | 对应 `CSS` `border-bottom-width` 属性                        |
| borderLeftWidth         | <number>                              | 对应 `CSS` `border-left-width` 属性                          |
| borderColor             | <color>                               | 对应 `CSS` `border-color` 属性                               |
| borderTopColor          | <color>                               | 对应 `CSS` `border-top-color` 属性                           |
| borderRightColor        | <color>                               | 对应 `CSS` `border-right-color` 属性                         |
| borderBottomColor       | <color>                               | 对应 `CSS` `border-bottom-color` 属性                        |
| borderLeftColor         | <color>                               | 对应 `CSS` `border-left-color` 属性                          |
| borderRadius            | <number>                              | 对应 `CSS` `border-radius` 属性                              |
| borderTopLeftRadius     | <number>                              | 对应 `CSS` `border-top-left-radius` 属性                     |
| borderTopRightRadius    | <number>                              | 对应 `CSS` `border-top-right-radius` 属性                    |
| borderBottomLeftRadius  | <number>                              | 对应 `CSS` `border-bottom-left-radius` 属性                  |
| borderBottomRightRadius | <number>                              | 对应 `CSS` `border-bottom-right-radius` 属性                 |
| shadowColor             | <color>                               | 对应 `CSS` box-shadow 属性中的颜色定义 |
| shadowOffset            | { width: <number>, height: <number> } | 对应 `CSS` box-shadow 属性中的阴影偏移定义 |
| shadowRadius            | <number>                              | 在 `CSS` 中，阴影的圆角大小取决于元素的圆角定义，不需要额外定义 |
| shadowOpacity           | <number>                              | 对应 `CSS` box-shadow 属性中的阴影透明度定义 |



### Background 背景

| 属性名          | 取值    | 描述                               |
| --------------- | ------- | ---------------------------------- |
| backgroundColor | <color> | 对应 `CSS` `background-color` 属性 |



### Transform 转换

| 属性名             | 取值                                                         | 描述                                                         |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| transform          | [{perspective: <number>}, {rotate: <string>}, {rotateX: <string>}, {rotateY: <string>}, {rotateZ: <string>}, {scale:  <number>}, {scaleX:  <number>}, {scaleY:  <number>}, {translateX:  <number>}, {translateY:  <number>}, {skewX: <string>}, {skewY: <string>}] | 对应 CSS transform 属性                                      |
| transformMatrix    | `TransformMatrixPropType`                                    | 类似于 `CSS` 中 `transform` 属性的 `matrix()` 和 `matrix3d()` 函数 |
| backfaceVisibility | `visible`, `hidden`                                          | 对应 `CSS` `backface-visibility` 属性                        |



### Flexbox 弹性盒

| 属性名         | 取值                                                         | 描述                                                         |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| flex           | <number>                                                     | 对应 `CSS` `flex` 属性，但只能为整数值                       |
| flexGrow       | <number>                                                     | 对应 `CSS` `flex-grow` 属性                                  |
| flexShrink     | <number>                                                     | 对应 `CSS` `flex-shrink` 属性                                |
| flexBasis      | <number>                                                     | 对应 `CSS` `flex-basis` 属性                                 |
| flexDirection  | `row`, `row-reverse`, `column`, `column-reverse`             | 对应 `CSS` `flex-direction` 属性                             |
| flexWrap       | `wrap`, `nowrap`                                             | 对应 `CSS` `flex-wrap` 属性，但阉割了 `wrap-reverse` 取值    |
| justifyContent | `flex-start`, `flex-end`, `center`, `space-between`, `space-around` | 对应 `CSS` `justify-content` 属性，但阉割了 `stretch` 取值。 |
| alignItems     | `flex-start`, `flex-end`, `center`, `stretch`                | 对应 `CSS` `align-items` 属性，但阉割了 `baseline` 取值。    |
| alignSelf      | `auto`, `flex-start`, `flex-end`, `center`, `stretch`        | 对应 `CSS` `align-self` 属性，但阉割了 `baseline` 取值       |





### Other 其他

| 属性名                 | 取值                          | 描述                                                         |
| ---------------------- | ----------------------------- | ------------------------------------------------------------ |
| opacity                | <number>                      | 对应 `CSS` `opacity` 属性                                    |
| overflow               | `visible`, `hidden`, `scroll` | 对应 `CSS` `overflow` 属性，但阉割了 `auto` 取值             |
| elevation `Android`    | <number>                      | `CSS`中没有对应的属性，只在 `Android5.0+` 上有效             |
| resizeMode             | `cover`, `contain`, `stretch` | `CSS`中没有对应的属性，可以参考 `background-size` 属性       |
| overlayColor `Android` | string                        | `CSS`中没有对应的属性，当图像有圆角时，将角落都充满一种颜色  |
| tintColor `iOS`        | <color>                       | `CSS`中没有对应的属性，`iOS` 图像上特殊的色彩，改变不透明像素的颜色 |

