# 项目结构

```markdown
	-page
		-index
			-index.js  		页面逻辑
			-index.json		页面配置
			-index.wxml 	页面结构
			-index.wxss		页面样式表
			
	-app.js  				小程序逻辑
	-app.json 				小程序公共配置
	-app.wxss				小程序公共样式表
	
	-project.config.json 	工具配置
	-sitemap.json
```



# 配置

## 全局配置

### `pages`

- 页面路径列表(必填)
- 第一项为home



### `entryPagePath`

- 小程序默认启动首页
- 默认为`pages`第一项



### `window`

- 全局的默认窗口表现



### `sitemapLocation`	

- 指明 `sitemap.json` 的位置(必填)





## 页面配置

### `navigationBarTitleText`

- 导航栏标题文字内容



### `usingComponents`

- 页面自定义组件配置



## sitemap 配置

- 用于配置小程序及其页面是否允许被微信索引
- 如果没有 `sitemap.json` ，则默认为所有页面都允许被索引

### `rules`

- rules 配置项指定了索引规则，每项规则为一个JSON对象

#### `action`

- 命中该规则的页面是否能被索引

- 取值`allow`、`disallow`(默认`allow`)



#### `page`



#### `params`



#### `matching`



#### `priority`



# 框架接口 

### 小程序

#### `App`

- `App(Object object)`
- 注册小程序。接受一个 `Object` 参数，其指定小程序的生命周期回调等。
- App() 必须在 `app.js` 中调用，必须调用且只能调用一次。不然会出现无法预期的后果

```js

```





#### `getApp`

- `AppObject getApp(Object object)`

- 获取到小程序全局唯一的 `App` 实例



### 页面

#### `page`

- `Page(Object object)`
- 注册小程序中的一个页面
- 接受一个 `Object` 类型参数，其指定页面的初始数据、生命周期回调、事件处理函数等。

```js
// pages/demo/demo.js
Page({

  /**
   * 页面的初始数据
   */
  data: {

  },

  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function (options) {

  },

  /**
   * 生命周期函数--监听页面初次渲染完成
   */
  onReady: function () {

  },

  /**
   * 生命周期函数--监听页面显示
   */
  onShow: function () {

  },

  /**
   * 生命周期函数--监听页面隐藏
   */
  onHide: function () {

  },

  /**
   * 生命周期函数--监听页面卸载
   */
  onUnload: function () {

  },

  /**
   * 页面相关事件处理函数--监听用户下拉动作
   */
  onPullDownRefresh: function () {

  },

  /**
   * 页面上拉触底事件的处理函数
   */
  onReachBottom: function () {

  },

  /**
   * 用户点击右上角分享
   */
  onShareAppMessage: function () {

  }
})
```



#### `getCurrentPages`

- `PageObject[] getCurrentPages()`
- 获取当前页面栈。数组中第一个元素为首页，最后一个元素为当前页面









# WXML 

## 模板

### 数据绑定

```xml
<view> {{ message }} </view>
```



### 条件渲染

```xml
<view wx:if="{{length > 5}}"> 1 </view>
<view wx:elif="{{length > 2}}"> 2 </view>
<view wx:else> 3 </view>
```



### 列表渲染

```xml
<!--默认数组的当前项的下标变量名默认为 index，数组当前项的变量名默认为 item-->
<!--wx:key="unique" 即 item.unique-->
<view wx:for="{{array}}" wx:key="unique">
  {{index}}: {{item.message}}
</view>
```

```xml
<!--使用 wx:for-item 指定数组当前元素的变量名，使用 wx:for-index 指定数组当前下标的变量名-->
<view wx:for="{{array}}" wx:for-index="idx" wx:for-item="itemName">
  {{idx}}: {{itemName.message}}
</view>
```



### 模板

```xml
<!--
item: {
  index: 0,
  msg: 'this is a template',
  time: '2016-06-18'
}
-->


<template name="msgItem">
  <view>
    <text> {{index}}: {{msg}} </text>
    <text> Time: {{time}} </text>
  </view>
</template>


<template is="msgItem" data="{{...item}}"/>

<!-- 输出
0: this is a template Time: 2016-06-18
-->
```

```xml
<template name="odd">
  <view> odd </view>
</template>


<template name="even">
  <view> even </view>
</template>


<block wx:for="{{[1, 2, 3, 4, 5]}}">
  <template is="{{item % 2 == 0 ? 'even' : 'odd'}}"/>
</block>



<!-- 输出
odd
even
odd
even
odd
-->
```



### 引用

-  import 有作用域的概念，即只会 import 目标文件中定义的 template，而不会 import 目标文件中 import 的 template

```xml
<!-- item.wxml -->
<template name="item">
  <text>{{text}}</text>
</template>

<!-- index.wxml -->
<import src="item.wxml"/>
<template is="item" data="{{text: 'forbar'}}"/>
```



## 组件

### 视图容器

#### `<view>`

- 类似`<div>`



#### `<scroll-view>`

- 可滚动视图区域
- 滚动列表





#### `<swiper>`

- 轮播图容器



#### `<swiper-item>`

- 轮播图item



### 基本内容

#### `<text>`

-  `user-select` :文本是否可选，该属性会使文本节点显示为 inline-block

#### `<rich-text>`

### 表单组件



### 导航组件

### 媒体组件

### 地图组件(map)

### 画布组件(canvas)

### 开放能力

### 无障碍







# WXSS 样式



# 路由 

## `wx.navigateTo`

- `wx.navigateTo(Object object)`
- 保留当前页面，跳转到应用内的某个页面。但是不能跳到 tabbar 页面
- 使用 `wx.navigateBack`可以返回到原页面
- 小程序中页面栈最多十层



# 网络

## `wx.request`

- `RequestTask wx.request(Object object)`

```js
wx.request({
  url: 'example.php', //仅为示例，并非真实的接口地址
  data: {
    x: '',
    y: ''
  },
  header: {
    'content-type': 'application/json' // 默认值
  },
  success (res) {
    console.log(res.data)
  }
})
```



# 存储

## `wx.setStorageSync`

- `wx.setStorageSync(string key, any data)`

- 将数据存储在本地缓存中指定的 key 中

- 会覆盖掉原来该 key 对应的内容

- 除非用户主动删除或因存储空间原因被系统清理，否则数据都一直可用

- 单个 key 允许存储的最大数据长度为 1MB，所有数据存储上限为 10MB

  







## `wx.getStorageSync`

- `any wx.getStorageSync(string key)`
- 从本地缓存中同步获取指定 key 的内容



## `wx.removeStorageSync`

- `wx.removeStorageSync(string key)`
- wx.removeStorage 的同步版本

