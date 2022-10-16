```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>标题</title>
</head>
<body>
    Hello World
</body>
</html>
```

## 元相关元素

用于修改文档的其他部分的表现或行为，设置到其他文档的链接，或传送其他 *外带* 信息。

### `<base>`

```html
	<!-- 规定页面中所有相对链接的基准 URL -->
	<base href="http://www.w3school.com.cn/i/" />
	
	<!-- 在何处打开页面中所有的链接 -->
	<base target="_black"/>
```

### `<link>`

```html
	<!-- 配置网页图标 -->
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />	

	<!-- 配置网页添加到手机屏幕图标(仅支持IOS) -->
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />

	<!-- 应用加壳时配置文件 -->
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />

```



### `<meta>`

```html
<!-- charset属性:声明了文档的字符编码 -->
	<meta charset="utf-8" />设置页面字符集

<!-- http-equiv属性:与content连用,编译指令,(告知浏览器行为)-->
	<!-- content-security-policy:允许页面作者定义当前页的内容策略 -->
	<!-- content-type:其值必须是"text/html; charset=utf-8" -->
	<!-- default-style:设置默认 CSS 样式表组的名称 -->
	<!-- x-ua-compatible:如果指定，则 content 属性必须具有值 "IE=edge"。用户代理必须忽略此指示-->
	<!-- refresh: 如果 content 只包含一个正整数，则为重新载入页面的时间间隔(秒)；如果 content 包含一个正整数，并且后面跟着字符串 ';url=' 和一个合法的 URL，则是重定向到指定链接的时间间隔(秒)-->
	<meta http-equiv="refresh" content="3"/>3秒刷新一次
	<meta http-equiv="refresh" content="3;url=https://www.baidu.com/"/>3秒跳到百度

<!-- name属性:与content连用,以名-值对的方式给文档提供元数据(告知浏览器内容) -->
	<!--  -->
	<!--  -->
	<!--  -->
	<meta name="keywords" content="关键词" />
	<meta name="description" content="描述" />

	<!-- 配置理想视口,用于移动端网页配置 -->
    <meta name="viewport" content="width=device-width, initial-scale=1" />

	<!-- 配置浏览器页签+地址栏颜色(仅支持安卓手机浏览器) -->
    <meta name="theme-color" content="#000000" />

	<!-- 配置描述信息 -->
    <meta name="description" content="Web site created using create-react-app" />
```

### `<noscript>`

```html
	<!-- 不支持js使显示(没有吊用) -->
	<noscript>You need to enable JavaScript to run this app.</noscript>
```



### `<style>`

```html

```



### `<script>`

```html

```



### `<title>`

```HTML
    <!-- 配置文档的标题，显示在浏览器的标题栏或标签页上 -->
	<title>I Love You</title>
```







## 文本

### `<h1>`~`<h6>`

```html
<!-- 标题 -->
<h1>标题</h1>
```



### `<p>`

```html
<!-- 段落 -->
<!-- p 元素会自动在其前后创建一些空白。浏览器会自动添加这些空间，也可以在样式表中规定 -->
<p>This is some text in a very short paragraph</p>
```



### `<b>`

```html
<!-- 粗体文本 -->
<!-- 效果与<strong>类似 -->
<p>这是普通文本 - <b>这是粗体文本</b>。</p>
```

> <p>这是普通文本 - <b>这是粗体文本</b>。</p>



### `<strong>`

```html
<!--强调为加粗-->
<!--把文本定义为语气更强的强调的内容,表现形式为加粗-->
<strong>强调内容<strong/>
```

> <strong>强调内容<strong/>



### `<i>`

```html
<!-- 斜体文本 -->
<!-- 效果与<em>类似 -->
<i>斜体文本</i>
```

><i>斜体文本</i>



### `<em>`

```html
<!--强调为斜体-->
<!--把文本定义为语气更强的强调的内容,表现形式为斜体-->
<em>强调内容</em>
```

> <em>强调内容</em>



### `<u>`

```html
<!-- 下划线 -->
<p>如果文本不是超链接，就不要<u>对其使用下划线</u>。</p>
```

><p>如果文本不是超链接，就不要<u>对其使用下划线</u>。</p>



### `<ins>`

- `<ins>` 标签定义已经被插入文档中的文本
- 和`<u>`效果一样,是语义化

```html
a dozen is <del>20</del> <ins>12</ins> pieces
```

> a dozen is <del>20</del> <ins>12</ins> pieces





###`<del>`

```html
<!-- 删除线 -->
a dozen is <del>20</del> 12 pieces
```

> a dozen is <del>20</del> 12 pieces



### `<hr>`

```html
<!-- 水平分割线 -->
<p>This is header 1</p>
<hr />
<p>This is some text</p>
```

><p>This is header 1</p>
><hr />
><p>This is some text</p>





### `<br>`

```html
<!-- 换行符 -->
<br/>
```

> <br/>

###`<bdo>`

```html
<!-- bdo 元素可覆盖默认的文本方向。 -->
<!-- 通过dir属性控制(默认为ltr(left to right),可设为rtl使文本从右向左) -->

<bdo dir="rtl">right to left</bdo>
```

><bdo dir="rtl">right to left</bdo>



###`<sub>`

```html
<!--<sub> 标签可定义下标文本。 -->
<!-- 包含在 <sub> 标签和其结束标签 </sub> 中的内容将会以当前文本流中字符高度的一半来显示，但是与当前文本流中文字的字体和字号都是一样的 -->
H<sub>2</sub>O
```

> H<sub>2</sub>O



###`<sup>`

```html
<!-- <sup> 标签可定义上标文本。 -->
<!-- 包含在 <sup> 标签和其结束标签 </sup> 中的内容将会以当前文本流中字符高度的一半来显示，但是与当前文本流中文字的字体和字号都是一样的 -->

10<sup>10</sup>
```

> 10<sup>10</sup>



### `<details>`

- `<details> `标签用于描述文档或文档某个部分的细节
- 与 `<summary>` 标签 配合使用可以为 details 定义标题。标题是可见的，用户点击标题时，会显示出 details

```html
<details >
<summary>约会大作战</summary>
<p>鸢一折纸,五河琴里,夜刀神十香</p>
</details>

<!-- open	定义 details 是否可见 -->
```

><details >
><summary>约会大作战</summary>
><p>鸢一折纸,五河琴里,夜刀神十香</p>
></details>



### `<summary>`

- `<summary>` 标签包含 details 元素的标题





###`<dialog>`

```html
<dialog open>这是打开的对话窗口</dialog>
<!-- open	定义 dialog 是否可见 -->
```

> <dialog open>这是打开的对话窗口</dialog>





###`<pre>`

- pre 元素可定义预格式化的文本。
- 被包围在 pre 元素中的文本通常会保留空格和换行符。而文本也会呈现为等宽字体。
- `<pre>` 标签的一个常见应用就是用来表示计算机的源代码



###`<figure>`

- `<figure>` 标签规定独立的流内容（图像、图表、照片、代码等等）
- figure 元素的内容应该与主内容相关，但如果被删除，则不应对文档流产生影响





### `<mark>`

- 突出显示部分文本：

```html
<p>Do not forget to buy <mark>milk</mark> today.</p>
```

> <p>Do not forget to buy <mark>milk</mark> today.</p>



### `<small>`

- `<small>` 标签呈现小号字体效果。
- `<small>` 标签和它所对应的 `<big>` 标签一样，但它是缩小字体而不是放大。如果被包围的字体已经是字体模型所支持的最小字号，那么 `<small>` 标签将不起任何作用。
- 与 `<big>` 标签类似，`<small>` 标签也可以嵌套，从而连续地把文字缩小。每个 `<small>` 标签都把文本的字体变小一号，直到达到下限的一号字。

```html
<p>
    9<small>8<small>77</small>8</small>9
</p>
```

> <p>
>     9<small>8<small>77</small>8</small>9
> </p>





## 语义化

###`<div>`

- 块元素
- `<div>` 可定义文档中的分区或节（division/section）。
- `<div>` 标签可以把文档分割为独立的、不同的部分。它可以用作严格的组织工具，并且不使用任何格式与其关联
- 如果用 id 或 class 来标记 `<div>`，那么该标签的作用会变得更加有效



### `<span>`

- 行内元素
- `<span>` 标签被用来组合文档中的行内元素



### `<header>`

- `<header>` 标签定义文档的页眉(介绍信息)



### `<footer>`

- `<footer>` 标签定义文档或节的页脚。
- `<footer>` 元素应当含有其包含元素的信息。
- 页脚通常包含文档的作者、版权信息、使用条款链接、联系信息等等。
- 可以在一个文档中使用多个 `<footer>` 元素



### `<nav>`

- `<nav>` 标签定义导航链接的部分



### `<address>`

- `<address>` 标签定义文档或文章的作者/拥有者的联系信息。
- 如果 `<address>` 元素位于 `<body>` 元素内，则它表示文档联系信息。
- 如果 `<address>` 元素位于 `<article>` 元素内，则它表示文章的联系信息。
- `<address>` 元素中的文本通常呈现为斜体。大多数浏览器会在 address 元素前后添加折行
- `<address>` 元素通常连同其他信息被包含在 `<footer>` 元素中



### `<section>`

- `<section>` 标签定义文档中的节（section、区段）。比如章节、页眉、页脚或文档中的其他部分



### `<article>`

- `<article>` 标签规定独立的自包含内容。
- 一篇文章应有其自身的意义，应该有可能独立于站点的其余部分对其进行分发



### `<aside>`

- `<aside>` 标签定义其所处内容之外的内容。
- aside 的内容应该与附近的内容相关









## 列表

### `<ul>`

- `<ul>` 标签定义无序列表

```html
<ul>
    <li>鸢一折纸</li>
    <li>五河琴里</li>
    <li>夜刀神十香</li>
</ul>

<!-- type	disc|square|circle|none	规定列表的项目符号的类型。 -->
```

><ul >
>    <li>鸢一折纸</li>
>    <li>五河琴里</li>
>    <li>夜刀神十香</li> 
></ul>



### `<ol>`

- `<ol>` 标签定义有序列表

```html
<ol>
    <li>鸢一折纸</li>
    <li>五河琴里</li>
    <li>夜刀神十香</li>   
</ol>

<!-- reversed	reversed	规定列表顺序为降序。(9,8,7...) -->
<!-- start		number		规定有序列表的起始值 -->
<!-- type		1|A|a|I|i  	规定在列表中使用的标记类型-->
```

><ol>
>    <li>鸢一折纸</li>
>    <li>五河琴里</li>
>    <li>夜刀神十香</li>   
></ol>



### `<li>`

- `<li>` 标签定义列表项目
- `<li>` 标签可用在有序列表 (`<ol>`) 和无序列表 (`<ul>`) 中





### `<dl>`

- `<dl>` 标签定义了定义列表（definition list）
- `<dl>` 标签用于结合 `<dt>` （定义列表中的项目）和 `<dd>` （描述列表中的项目）

```html
<dl>
   <dt>Princess</dt>
   <dd>夜刀神十香</dd>
   <dt>Angel</dt>
   <dd>鸢一折纸</dd>
</dl>
```

><dl>
>   <dt>Princess</dt>
>   <dd>夜刀神十香</dd>
>   <dt>Angel</dt>
>   <dd>鸢一折纸</dd>
></dl>



### `<dt>`

-  `<dt>` 定义列表中的项目



###`<dd>`

-  `<dd>` 描述定义列表中的项目



## 表格

### `<table >`

- `<table>` 标签定义 HTML 表格。
- 
  简单的 HTML 表格由 `<table>` 元素以及一个或多个 `<tr>`、`<th>` 或 `<td>` 元素组成。

- `<tr>` 元素定义表格行，`<th>` 元素定义表头，`<td>` 元素定义表格单元。

- 更复杂的 HTML 表格也可能包括 `<caption>`、`<col>`、`<colgroup>`、`<thead`、`<tfoot>` 以及 `<tbody>` 元素。

- | 属性名      | 含义                                     | 常用属性值          |
  | ----------- | ---------------------------------------- | ------------------- |
  | border      | 设置表格的边框（默认border="0"无边框）   | 像素值              |
  | cellspacing | 设置单元格与单元格边框之间的空白间距     | 像素值（默认2像素） |
  | cellpadding | 设置单元格内容与单元格边框之间的空白间距 | 像素值（默认1像素） |
  | width       | 设置表格的宽度                           | 像素值              |
  | height      | 设置表格的高度                           | 像素值              |
  | align       | 设置表格在网页中的水平对齐方式           | left、right、center |



### `<caption>` 

- caption 元素定义表格标题



### `<thead>`

- 用于组合 HTML 表格的表头内容。
- 语义化标签,方便绑定样式
- `<thead>` 元素应该与 `<tbody>` 和 `<tfoot>` 元素结合起来使用。



### `<tbody>`

- `<tbody>` 元素用于对 HTML 表格中的主体内容进行分组



### `<tfoot>`

-  `<tfoot>` 元素用于对 HTML 表格中的表注（页脚）内容进行分组




### `<th>`

- **`<th>` 元素**定义表格内的表头单元格
- 自动加粗
- 方便绑定样式





### `<tr>`

- **`<tr>` 元素**定义表格中的行

- **t**able**r**ow（表格行）



### `<td>`

-  **`<td>` 元素** 定义了一个包含数据的表格单元格

- **t**able**d**ata（表格数据）

- 单元格合并

  - `colspan`  当前行跨列合并
    
    - ---
    
    - --
    
  - `rowspan` 当前列跨行合并
  
    - -
    - -
    
    



### `<col>`

- `<col>` 标签为表格中一个或多个列定义属性值。



|            |                      |
| ---------- | -------------------- |
|            |                      |
|            |                      |
|            |                      |
| <caption>  | 定义表格标题         |
| <colgroup> | 定义表格列的组       |
| <col>      | 定义用于表格列的属性 |
|            |                      |















##表单

### `<form>` 

- `<form>` 标签用于为用户输入创建 HTML 表单。
- 表单能够包含 input 元素，比如文本字段、复选框、单选框、提交按钮等等。
- 表单还可以包含 menus、textarea、fieldset、legend 和 label 元素。
- 表单用于向服务器传输数据
- 加novalidate可取消验证
- **表单分类**(表单在form之外)
  - 使表单`form`属性与form的`id`属性一致

```html
<form action="form_action.asp" method="get" >
  <p>First name: <input type="text" name="fname" /></p>
  <p>Last name: <input type="text" name="lname" /></p>
  <input type="submit" value="Submit" />
</form>
```







###`<input>`

```markdown
name
-控件名称

value
- 默认文本值

checked
- 控制单选框和多选框的默认选中

size
- 控件在页面中的显示宽度	

maxlength
- 控件允许输入的最多字符

min
-用于设置表单最小值(适用于数值类型表单 number range)

max
-用于设置表单最大值(适用于数值类型表单 number range)

readonly
-只读 输入域可以选择,但无法修改

disabled
-禁用 输入域无法获取焦点,无法选择.以灰色显示

autofocus
-自动获取焦点属性

placeholder
-表单信息提示

required
-必须要赋值

multiple
-设置表单可同时选多个 适用于file

pattern
-用于自定义验证规则(配合正则)

step
-设置数值步长(数值表单中)

tabindex
-tab索引切换
```



#### `type="text"`

- 单行文本输入框

```html
用户:<input type="text" value="用户">
```





####`type="password"`

- 密码输入框

```html
密码:<input type="password" value="密码">
```



#### `type="radio"`

- 单选按钮
- name一致才会排斥

```html
<input type="radio" name="sex" id="male" />
<label for="male">Male</label>

<input type="radio" name="sex" id="female" />
<label for="female">Female</label>

```



#### `type="checkbox"`

- 复选按钮

```html
<input type="checkbox" id="jack" value="Jack" />
<label for="jack">Jack</label>
<input type="checkbox" id="john" value="John" />
<label for="john">John</label>
<input type="checkbox" id="mike" value="Mike" />
<label for="mike">Mike</label>
```



#### `type="button"`

- 普通按钮

```html
<input type="button" value="">
```



#### `type="submit"`

- 提交按钮

```html
<input type="submit" value="">
```



#### `type="reset"`

- 重置按钮

```html
<input type="reset" value="">
```



#### `type="image"`

- 图像形式的提交按钮

```html
<input type="image" src="1.jpg" alt="">
```



#### `type="file"`

- 文件域

```html
<input type="file" name="" id="">
```



####`type="date"`

```html
日期:<input type="date" name="" id="">
```





####`type="time"`

```html
时间:<input type="time" name="" id="">
```



#### `type="month"`

```html
月份:<input type="month" name="" id="">
```



#### `type="week"`

```html
周:<input type="week" name="" id="">
```



#### `type="datetime-local"`

```html
完整日期:<input type="datetime-local" name="" id="">
```



#### `type="email"`

```html
邮箱验证:
<input type="email" name="" id="">
```



#### `type="url"`

```html
URL验证:
<input type="url" name="" id="">
```



#### `type="number"`

```html
数值表单验证:
<input type="number" name="" id="">

<!-- max 设置最大值 -->
<!-- min 设置最小值 -->
```



#### `type="range"`

```html
范围验证
<input type="range" name="" id="">

<!-- max 设置最大值 -->
<!-- min 设置最小值 -->
```



#### `type="search"`

```html
搜索表单
<input type="search" name="" id="">
```



#### `type="color"`

```html
颜色选取表单
<input type="color" name="" id="">
```



#### `type="tel"`

```html
电话号码表单
<input type="tel" name="" id="">
```










###`<label>`

- `<label>` 标签为 input 元素定义标注（标记）。
- label 元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。如果您在 label 元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。
- `<label>` 标签的 for 属性应当与相关元素的 id 属性相同



### `<button>`

- type	
  - button
  - reset
  - submit



### `<textarea> `

- `<textarea>` 标签定义多行的文本输入控件
- 文本区中可容纳无限数量的文本，其中的文本的默认字体是等宽字体（通常是 Courier）
- 可以通过 cols 和 rows 属性来规定 textarea 的尺寸，不过更好的办法是使用 CSS 的 height 和 width 属性



###`<select>`

- select 元素可创建单选或多选菜单。

- `<select>` 元素中的 `<option>` 标签用于定义列表中的可用选项

```html
<!-- selected	规定选项（在首次显示在列表中时）表现为选中状态-->
<select>
  <option value ="volvo">Volvo</option>
  <option value ="saab">Saab</option>
  <option value="opel">Opel</option>
  <option value="audi">Audi</option>
</select>
```

><select>
>  <option value ="volvo">Volvo</option>
>  <option value ="saab">Saab</option>
>  <option value="opel">Opel</option>
>  <option value="audi">Audi</option>
></select>



### `<option>`

- option 元素定义下拉列表中的一个选项（一个条目）。

- 浏览器将 `<option>` 标签中的内容作为 `<select>` 标签的菜单或是滚动列表中的一个元素显示。

- option 元素位于 select 元素内部。



###`<optgroup>`

- `<optgroup>` 标签定义选项组。
- optgroup 元素用于组合选项。当使用一个长的选项列表时，对相关的选项进行组合会使处理更加容易

```html
<select>
  <optgroup label="Swedish Cars">
    <option value ="volvo">Volvo</option>
    <option value ="saab">Saab</option>
  </optgroup>
  <optgroup label="German Cars">
    <option value ="mercedes">Mercedes</option>
    <option value ="audi">Audi</option>
  </optgroup>
</select>
```

><select>
>  <optgroup label="Swedish Cars">
>    <option value ="volvo">Volvo</option>
>    <option value ="saab">Saab</option>
>  </optgroup>
>  <optgroup label="German Cars">
>    <option value ="mercedes">Mercedes</option>
>    <option value ="audi">Audi</option>
>  </optgroup>
></select>





### `<fieldset>`

- fieldset 元素可将表单内的相关元素分组

- `<fieldset>` 标签将表单内容的一部分打包，生成一组相关表单的字段
- `<legend>` 标签为 fieldset 元素定义标题。

```html
<form>
  <fieldset>
    <legend>health information</legend>
    height: <input type="text" />
    weight: <input type="text" />
  </fieldset>
</form>
```

><form>
>  <fieldset>
>    <legend>health information</legend>
>    height: <input type="text" />
>    weight: <input type="text" />
>  </fieldset>
></form>



### `<legend>`

- `<legend>` 标签为 fieldset 元素定义标题。



###`<datalist>`

- `<datalist>` 标签定义选项列表。请与 input 元素配合使用该元素，来定义 input 可能的值。
- datalist 及其选项不会被显示出来，它仅仅是合法的输入值列表。
- 请使用 input 元素的 list 属性来绑定 datalist(于其id一致)。

```html
<input id="myCar" list="cars" />
<datalist id="cars">
  <option value="BMW">
  <option value="Ford">
  <option value="Volvo">
</datalist>
```









## 超链接

### `<a>`

```html
<a href="http://www.w3school.com.cn">W3School</a>
```

> <a href="http://www.w3school.com.cn">W3School</a>

```markdown
#target 规定在何处打开链接文档
	- _self  默认		   在当前窗口打开
	- _blank			新窗口打开 
	- _top				顶层打开
```

```html
<!-- a使用mailto能让访问者便捷向网站管理者发送电子邮件 -->
<a href="mailto:yy@imooc.com?cc=tj_ws@163.com&bcc=tj_ws@161.com;tj_ws@162.com&subject=观了不起的盖茨比有感&body=你好，对此评论有些想法">对此影评有何感想，发送邮件给我</a>

<!-- mailto: 	邮箱地址-->
<!-- cc=  		抄送地址 -->
<!-- bcc=  		密件抄送地址-->
<!-- subject= 	邮件主题 -->
<!-- body= 		邮件内容 -->
```







## 多媒体

###`<progress>`

- `<progress> `标签标示任务的进度（进程）

```html
<!-- max	number	规定任务一共需要多少工作 -->
<!-- value	number	规定已经完成多少任务 -->
<progress value="22" max="100"></progress> 
```

> <progress value="22" max="100"></progress> 



###  `<meter>`

- 使用 `<meter>` 元素来度量给定范围（gauge）内的数据：

```HTML
<!-- form	form_id	规定 <meter> 元素所属的一个或多个表单 -->
<!-- high	number	规定被视作高的值的范围 -->
<!-- low	number	规定被视作低的值的范围 -->
<!-- max	number	规定范围的最大值 -->
<!-- min	number	规定范围的最小值 -->
<!-- optimum	number	规定度量的优化值 -->
<!-- value	number	必需。规定度量的当前值 -->
<meter value="3" min="0" max="10">十分之三</meter>

<meter value="0.6">60%</meter> 
```

> <meter value="3" min="0" max="10"> 十分之三</meter>
>
> <meter value="0.6">60%</meter> 





### `<img>`

```html
<!-- 必选属性 -->
<!-- alt	text	规定图像的替代文本 -->
<!-- src	URL		规定显示图像的 URL -->

<img src="/i/eg_tulip.jpg"  alt="上海鲜花港 - 郁金香" />
```

```html
<a href="demo_form.asp">
<img src="tulip.gif" ismap />
</a>

<!-- ismap	URL	将图像定义为服务器端图像映射 -->
<!-- 当用户在 ismap 图像上单击了某处时，浏览器会自动把鼠标的 x、y 位置（相对于图像的左上角）发送到服务器端。特殊的服务器端软件（在本例中是 demo_form.asp 程序）可以根据这些坐标来做出响应 -->
```

```html
<img src="planets.gif" alt="Planets" usemap="#planetmap" />
<map name="planetmap">
  <area href="sun.htm" shape="rect" coords="0,0,110,260">Sun</a>
  <area href="mercur.htm" shape="circle" coords="129,161,10">Mercury</a>
  <area href="venus.htm" shape="circle" coords="180,139,14">Venus</a>
</map>
<!-- 将一幅图像 planets.gif 映射为 3 个区域，当用户单击其中某一个区域时，将被链接到不同的文档中 -->

<!-- usemap	URL	将图像定义为客户器端图像映射 --> 
<!-- -->
```





###`<audio>`

```html
<!-- 一段简单的 HTML 5 音频 -->

<audio src="someaudio.wav">
您的浏览器不支持 audio 标签。
</audio>

<!-- controls 如果出现该属性，则向用户显示控件，比如播放按钮 -->
```




###`<video>`

```html
<!-- 一段简单的 HTML5 视频 -->

<video src="movie.ogg" controls="controls">
您的浏览器不支持 video 标签。
</video>

<!-- controls 如果出现该属性，则向用户显示控件，比如播放按钮 -->
```




###`<embed>`

```html
<!-- <embed> 标签定义嵌入的内容，比如插件 -->

<embed src="helloworld.swf" />
```



###`<source>`

- `<source>` 标签为媒介元素（比如 `<video>` 和 `<audio>`）定义媒介资源。
- `<source>` 标签允许规定可替换的视频/音频文件供浏览器根据它对媒体类型或者编解码器的支持进行选择

```html
<!-- 拥有两份源文件的音频播放器。浏览器应该选择它所支持的文件（如果有的话）-->

<audio controls>
   <source src="horse.ogg" type="audio/ogg">
   <source src="horse.mp3" type="audio/mpeg">
 Your browser does not support the audio element.
</audio> 
```













## 框架

### `<iframe>`

- `<iframe>` 会创建包含另外一个文档的内联框架（即行内框架）
- 子窗口通过`window.parent`操作父窗口
- 父窗口获取子窗口元素,再通过其`contentWindow`属性操作子窗口

```html
<iframe src="1.html"></iframe>
```





###`<frameset>	`

- frameset 元素可定义一个框架集
- 它被用来组织多个窗口（框架）。每个框架存有独立的文档
- 在其最简单的应用中，frameset 元素仅仅会规定在框架集中存在多少列或多少行。必须使用 cols 或 rows 属性
- 可嵌套使用
- 子窗口通过`window.parent`操作父窗口
- 父窗口通过frame数组操作子窗口

```html
<!-- cols   pixels|%|*  定义框架集中列的数目和尺寸 -->
<!-- rows	pixels|%|*  定义框架集中行的数目和尺寸 -->

<frameset cols="25%,50%,25%">
  <frame src="frame_a.htm" />
  <frame src="frame_b.htm" />
  <frame src="frame_c.htm" />
</frameset>	
```

## 全局属性

### contenteditable

- contenteditable 属性规定元素内容是否可编辑。
- 如果元素未设置 contenteditable 属性，那么元素会从其父元素继承该属性。

```html
<p contenteditable="true">这是一个可编辑的段落。</p>
```

