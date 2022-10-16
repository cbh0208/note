# 选择器

### 基本选择器

#### 元素选择器

```css
/* 元素选择器根据元素名称来选择 HTML 元素*/
p {
  text-align: center;
  color: red;
}
/* 页面上的所有 <p> 元素都将居中对齐，并带有红色文本颜色*/
```



#### id 选择器

```css
/* id 选择器使用 HTML 元素的 id 属性来选择特定元素*/
#para1 {
  text-align: center;
  color: red;
}
/* 应用于 id="para1" 的 HTML 元素*/
```



#### 类选择器

```css
/* 类选择器选择有特定 class 属性的 HTML 元素*/
/* HTML 元素也可以引用多个类*/
.center {
  text-align: center;
  color: red;
}
/* 所有带有 class="center" 的 HTML 元素将为红色且居中对齐*/
```

```css
/* 可以指定只有特定的 HTML 元素会受类的影响*/
p.center {
  text-align: center;
  color: red;
}
/* 只有具有 class="center" 的 <p> 元素会居中对齐*/
```



#### 通用选择器

```css
/* 通用选择器（*）选择页面上的所有的 HTML 元素*/
* {
  text-align: center;
  color: blue;
}
```



#### 属性选择器

```markdown
[attr]
	表示带有以 attr 命名的属性的元素。

[attr=value]
	表示带有以 attr 命名的属性，且属性值为 value 的元素。

[attr~=value]
	表示带有以 attr 命名的属性的元素，并且该属性是一个以空格作为分隔的值列表，其中至少有一个值为 value。

[attr|=value]
	表示带有以 attr 命名的属性的元素，属性值为“value”或是以“value-”为前缀（"-"为连字符，Unicode 编码为 U+002D）开头。典型的应用场景是用来匹配语言简写代码（如 zh-CN，zh-TW 可以用 zh 作为 value）。

[attr^=value]
	表示带有以 attr 命名的属性，且属性值是以 value 开头的元素。

[attr$=value]
	表示带有以 attr 命名的属性，且属性值是以 value 结尾的元素。	

[attr*=value]
	表示带有以 attr 命名的属性，且属性值至少包含一个 value 值的元素。	

[attr operator value i]  
	在属性选择器的右方括号前添加一个用空格隔开的字母 i（或 I），可以在匹配属性值时忽略大小写（支持 ASCII 字符范围之内的字母）。

[attr operator value s] 
	在属性选择器的右方括号前添加一个用空格隔开的字母 s（或 S），可以在匹配属性值时区分大小写（支持 ASCII 字符范围之内的字母）。
```

```css
/* 存在title属性的<a> 元素 */
a[title] {
  color: purple;
}

/* 存在href属性并且属性值匹配"https://example.org"的<a> 元素 */
a[href="https://example.org"] {
  color: green;
}


/* 存在class属性并且属性值包含以空格分隔的"logo"的<a>元素 */
a[class~="logo"] {
  padding: 2px;
}

/*------------------------------------正则-----------------------------------------*/

/* 存在href属性并且属性值包含"example"的<a> 元素 */
a[href*="example"] {
  font-size: 2em;
}

/* 存在href属性并且属性值结尾是".org"的<a> 元素 */
a[href$=".org"] {
  font-style: italic;
}

/* 存在href属性并且属性值开头是"www"的<a> 元素 */
a[href^="www"] {
  font-style: italic;
}

```



### 分组选择器

#### 选择器列表

```css
/*  选择h1,h2,p标签 */
h1, h2, p {
  text-align: center;
  color: red;
}
```



### 组合器

#### 后代选择器

```css
/*  选择div中的p标签*/
div p {
  text-align: center;
  color: red;    
}
```



#### 直接子代选择器

```css
/* 选择div为p的子标签*/
div>p {
  text-align: center;
  color: red; 
}
```



#### 紧邻兄弟选择器

```css
/* 选择div之后的第一个兄弟p */
div + p {
  text-align: center;
  color: red;     
}
```



#### 一般兄弟组合器

```css
/* 选择div之后的所有兄弟p */
div ~ p {
  text-align: center;
  color: red;     
}
```



### 伪选择器

#### 伪类

- 伪类用于向某些选择器添加特殊的效果

##### 状态伪类

```css
/* :link */
/* 是用来选中元素当中的链接 */
/* 它将会选中所有尚未访问的链接，包括那些已经给定了其他伪类选择器的链接（例如:hover选择器，:active选择器，:visited选择器）*/
/* 为了可以正确地渲染链接元素的样式，:link伪类选择器应当放在其他伪类选择器的前面，并且遵循LVHA的先后顺序，即：:link — :visited — :hover — :active。:focus伪类选择器常伴随在:hover伪类选择器左右，需要根据你想要实现的效果确定它们的顺序 */
a:link {color: slategray;}
.external:link {background-color: lightblue;}
```

```css
/* :visited */
/* 表示用户已访问过的链接 */
/* 出于隐私原因，可以使用此选择器修改的样式非常有限 */
```

```css
/* :hover */
/* 适用于用户使用指示设备虚指一个元素（没有激活它）的情况 */
/* 这个样式会被任何与链接相关的伪类重写，像:link, :visited, 和 :active等。为了确保生效，:hover规则需要放在:link和:visited规则之后，但是在:active规则之前，按照LVHA的循顺序声明:link－:visited－:hover－:active */
/* :hover伪类可以任何伪元素上使用 */
```

```css
/* :active  */
/* 匹配被用户激活的元素 */
/* 它让页面能在浏览器监测到激活时给出反馈 */
/* 当用鼠标交互时，它代表的是用户按下按键和松开按键之间的时间 */

```

```css
/*:focus */
/* 表示获得焦点的元素（如表单输入） */
/* 当用户点击或触摸元素或通过键盘的 “tab” 键选择它时会被触发 */
```



##### 结构伪类

```css
/* :root */
/* :root 这个 CSS 伪类匹配文档树的根元素。对于 HTML 来说，:root 表示 <html> 元素，除了优先级更高之外，与 html 选择器相同*/
/* 常用来存放变量 */
:root{
    --color-background:#ffffff;
}
```

```css
/* :not() */ 
/* :not() 用来匹配不符合一组选择器的元素。由于它的作用是防止特定的元素被选中，它也被称为反选伪类（negation pseudo-class）。 */

/* 选择所有没有o类的p元素 */
p:not(.o) {
  color: blue;
}
```

```css
/* :empty */
/* :empty 代表没有子元素的元素。子元素只可以是元素节点或文本（包括空格）。注释或处理指令都不会产生影响 */

/* Selects any <div> that contains no content */
div:empty {
  background: lime;
}
```

```css
/* :target */
/* :target代表一个唯一的页面元素(目标元素)，其id 与当前URL片段匹配 .*/

/* 选择一个ID与当前URL片段匹配的元素*/
:target {
  border: 2px solid black;
}
```





##### 其他

```css
/* :first-child */
/* 表示在一组兄弟元素中的第一个元素*/

/* Selects any <p> that is the first element among its siblings */
p:first-child {
  color: lime;
}
```

```css
/* :last-child */
/* 代表父元素的最后一个子元素 */

li:last-child {
  background-color: lime;
}
```



```css
/* :nth-child(an+b) */
/* 首先找到所有当前元素的兄弟元素，然后按照位置先后顺序从1开始排序，选择的结果为:nth-child括号中表达式（an+b）匹配到的元素集合（n=0，1，2，3...）。*/

tr:nth-child(odd) {
	/* 表示HTML表格中的奇数行 */  
    /* 等同于tr:nth-child(2n+1) */
}	


tr:nth-child(even) {
    /* 表示HTML表格中的偶数行 */
    /* 等同于tr:nth-child(2n) */
}	
```

```css
/* :nth-last-child() */
/* 从兄弟节点中从后往前匹配处于某些位置的元素 */
/* 这个伪类和 :nth-child 基本一致, 但它是从结尾计数, 而不是从开始计数 */
```



```css
/* :nth-of-type() */ 
/* 针对具有一组兄弟节点的标签, 用 n 来筛选出在一组兄弟节点的位置 */
/* 只匹配同种标签*/
```

```css
/* :nth-last-of-type() */ 
/* 从兄弟节点中从后往前匹配处于某些位置的元素 */
/* 只匹配同种标签*/
```



```css
/* :only-child */
/* 匹配没有任何兄弟元素的元素 */
/* 等效的选择器还可以写成 :first-child:last-child或者:nth-child(1):nth-last-child(1),当然,前者的权重会低一点 */
```

```css
/* :only-of-type */
/* 代表了任意一个元素，这个元素没有其他相同类型的兄弟元素 */
```

##### 表单相关

```css
/* :enabled */
/* 表示任何被启用的（enabled）元素 */
/* 如果一个元素能够被激活（如选择、点击或接受文本输入），或者能够获取焦点，则该元素是启用的 */
/* 元素也有一个禁用的状态（disabled state），在被禁用时，元素不能被激活或获取焦点 */

/* 选择任何启用状态的 <input> */
input:enabled {
  color: blue;
}
```

```css
/* :disabled */
/* 表示任何被禁用的元素 */
/* 如果一个元素不能被激活（如选择、点击或接受文本输入）或获取焦点，则该元素处于被禁用状态 */
/* 元素还有一个启用状态（enabled state），在启用状态下，元素可以被激活或获取焦点 */

/* Selects any disabled <input> */
input:disabled {
  background: #ccc;
}
```



```css
/* :checked */
/* 表示任何处于选中状态的radio(<input type="radio">), checkbox (<input type="checkbox">) 或("select") 元素中的option HTML元素("option") */

/* 匹配任意被勾选/选中的radio(单选按钮),checkbox(复选框),或者option(select中的一项) */
:checked {
  margin-left: 25px;
  border: 1px solid blue;
} 
```



#### 伪元素

- 伪元素是一个附加至选择器末的关键词，允许对被选择元素的特定部分修改样式
- 伪元素用于将特殊的效果添加到某些选择器

```css
/* ::before (:before) */
/* ::before 创建一个伪元素，其将成为匹配选中的元素的第一个子元素。常通过 content 属性来为一个元素添加修饰性的内容。此元素默认为行内元素。*/

/* 在每一个p元素前插入内容 */
p::before { 
    content: "Hello world!"; 
} 
```

```css
/* ::after (:after) */
/* ::after用来创建一个伪元素，作为已选中元素的最后一个子元素。通常会配合content属性来为该元素添加装饰内容。这个虚拟元素默认是行内元素。*/

/* Add an arrow after links */
a::after {
  content: "→";
}
```



```css
/* ::first-line (:first-line) */
/* ::first-line在某块级元素的第一行应用样式。第一行的长度取决于很多因素，包括元素宽度，文档宽度和文本的文字大小 */
/* 和其他所有的 伪元素一样，::first-line 不能匹配任何真实存在的html元素。*/
/* ::first-line 伪元素只能在块容器中,所以,::first-line伪元素只能在一个display值为block, inline-block, table-cell 或者 table-caption中有用.。在其他的类型中，::first-line 是不起作用的.*/

/* 将每个段落中的第一行字母转换成大写 */
p::first-line { 
    text-transform: uppercase 
}
```

```css
/* ::first-letter (:first-letter) */
/* ::first-letter会选中某块级元素第一行的第一个字母，并且文字所处的行之前没有其他内容（如图片和内联的表格） */

/* Selects the first letter of a <p> */
p::first-letter {
  font-size: 130%;
}
```



```css
/* ::selection */
/* 应用于文档中被用户高亮的部分（比如使用鼠标或其他选择设备选中的部分）*/

/* 复制时样式 
```



### 选择器优先级

```markdown
	!important
		内联						     1000
			id						  100
				类/属性/伪类			   10
					类型/伪元素		   1
						通配符			0
```





# 盒子

### 宽高

- `height`和`width`属性不包括内边距、边框或外边距.它们设置的是元素的内边距、边框和外边距内的区域的高度/宽度！
- 只有块元素才有宽高
- 可设置最大,最小宽高`max-height`,`max-width`,`min-height` ,`min-width`动态决定

```css
.demo1 {
    height: 100px;
  	width: 500px;
}

.demo2 {
    max-height: 100px;
    max-width: 100px;
    min-height: 50px;
    min-width: 50px;
}
```



### 边框

#### `border`

- 用于设置各种单独的边界属性的简写属性
- border可以用于设置一个或多个以下属性的值： `border-width`, `border-style`, `border-color`
- 可用`border-top`,`border-bottom`,`border-left`,`border-right`对四边分别设置

```markdown
`border-style` 属性指定要显示的边框类型

- dotted - 定义点线边框
- dashed - 定义虚线边框
- solid - 定义实线边框
- double - 定义双边框
- groove - 定义 3D 坡口边框。效果取决于 border-color 值
- ridge - 定义 3D 脊线边框。效果取决于 border-color 值
- inset - 定义 3D inset 边框。效果取决于 border-color 值
- outset - 定义 3D outset 边框。效果取决于 border-color 值
- none - 定义无边框
- hidden - 定义隐藏边框
```



#### `margin`

- 属性为给定元素设置所有四个（上下左右）方向的外边距属性
- 是 `margin-top`，`margin-right`，`margin-bottom`，和 `margin-left` 四个外边距属性设置的简写





#### `padding`

- 控制元素所有四条边的内边距区域。


- 是 `padding-top`，`padding-right`，`padding-bottom`，和 `padding-left` 四个内边距属性设置的简写




### `box-sizing`

- `content-box`
  - 默认
  - **盒子宽度=内容的宽度(width)+左右内间距(padding)+左右边框的宽度(border)**
- `border-box`
  - **盒子宽度为最终宽度(width)**



# 定位

## `display`

### :block

- **块级元素(block)：**独占一行，对宽高的属性值生效；如果不给宽度，块级元素就默认为浏览器的宽度，即就是**100%宽**。

>`<div>`
>
>



### :inline

- **行内元素(inline)：**可以多个标签存在一行，对宽高属性值**不生效**，完全靠内容撑开宽高。

>`<span>`



### :inline-block

- **行内块元素(inline-block)：**结合的行内和块级的优点，既可以设置长宽，可以让padding和margin生效，又可以和其他行内元素并排。




### :none

- `display: none;`

  隐藏元素。该元素将被**隐藏**，并且页面将显示为好像该元素不在其中

- `visibility:hidden;` 

  也可以隐藏元素。但是，该元素仍将占用与之前相同的空间。元素将被隐藏，但仍会影响布局



### :flex

`display: flex;`

弹性布局(CSS3)

#### 容器属性

##### `flex-direction`

- `flex-direction`属性决定主轴的方向（即项目的排列方向）

- ```css
  .box {
    	flex-direction: row | row-reverse | column | column-reverse;
  }
  ```

- ```markdown
  row（默认值）：主轴为水平方向，起点在左端。
  row-reverse：主轴为水平方向，起点在右端。
  column：主轴为垂直方向，起点在上沿。
  column-reverse：主轴为垂直方向，起点在下沿。
  ```

  

##### `flex-wrap`

- `flex-wrap`属性定义，如果一条轴线排不下，如何换行

- ```css
  .box{
    flex-wrap: nowrap | wrap | wrap-reverse;
  }
  ```

- ```
  nowrap（默认）：不换行。
  wrap：换行，第一行在上方。
  wrap-reverse：换行，第一行在下方
  ```

  



##### `flex-flow`

- `flex-flow`属性是`flex-direction`属性和flex-wrap属性的简写形式，默认值为`row nowrap`

- ```css
  .box {
    flex-flow: <flex-direction> || <flex-wrap>;
  }
  ```


##### 

##### `justify-content`

- `justify-content`属性定义了项目在主轴上的对齐方式

- ```css
  .box {
    justify-content: flex-start | flex-end | center | space-between | space-around;
  }
  ```

- ```
  flex-start（默认值）：左对齐
  flex-end：右对齐
  center： 居中
  space-between：两端对齐，项目之间的间隔都相等。
  space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
  ```

- ![](https://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png)

##### `align-items`

- `align-items`属性定义项目在交叉轴上如何对齐。

- ```css
  .box {
    align-items: flex-start | flex-end | center | baseline | stretch;
  }
  ```

- ```
  flex-start：交叉轴的起点对齐。
  flex-end：交叉轴的终点对齐。
  center：交叉轴的中点对齐。
  baseline: 项目的第一行文字的基线对齐。
  stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
  ```

- ![](https://www.ruanyifeng.com/blogimg/asset/2015/bg2015071011.png)

##### `align-content`

- `align-content`属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

- ```css
  .box {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
  }
  ```

- ```
  flex-start：与交叉轴的起点对齐。
  flex-end：与交叉轴的终点对齐。
  center：与交叉轴的中点对齐。
  space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
  space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
  stretch（默认值）：轴线占满整个交叉轴。
  ```

  

#### 项目属性

#####  `order`

- `order`属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

- ```css
  .item {
    order: <integer>;
  }
  ```

  

#####  `flex-grow`

- `flex-grow`属性定义项目的放大比例，默认为`0`，即如果存在剩余空间，也不放大
- ![](https://www.ruanyifeng.com/blogimg/asset/2015/bg2015071014.png)
- 如果所有项目的`flex-grow`属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的`flex-grow`属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍



#####  `flex-shrink`

- `flex-shrink`属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
- 如果所有项目的`flex-shrink`属性都为1，当空间不足时，都将等比例缩小。
- 如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小



#####  `flex-basis`

- `flex-basis`属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小
- 它可以设为跟`width`或`height`属性一样的值（比如350px），则项目将占据固定空间



#####  `flex`

- `flex`属性是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选

- ```css
  .item {
    flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
  }
  ```

- 该属性有两个快捷值：`auto` (`1 1 auto`) 和 none (`0 0 auto`)

- 



#####  `align-self`

- `align-self`属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`

- ```css
  .item {
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
  }
  ```

- 该属性可能取6个值，除了auto，其他都与align-items属性完全一致





### :grid

- 默认情况下，容器元素都是块级元素，但也可以设成行内元素`display: inline-grid`
- 注意，设为网格布局以后，容器子元素（项目）的`float`、`display: inline-block`、`display: table-cell`、`vertical-align`和`column-*`等设置都将失效。

#### 容器属性





##### `grid-template-columns`

- 定义每一列的列宽

- 可以使用方括号，指定每一根网格线的名字，方便以后的引用

- ```css
  .container {
    display: grid;
    grid-template-columns: [c1] 100px [c2] 100px [c3] auto [c4];
    grid-template-rows: [r1] 100px [r2] 100px [r3] auto [r4];
  }
  ```

  



##### `grid-template-rows`

- 定义每一行的行高
- 可以使用方括号，指定每一根网格线的名字，方便以后的引用



##### 

##### `grid-template-areas`

- 用于定义区域

- ```css
  .container {
    display: grid;
    grid-template-columns: 100px 100px 100px;
    grid-template-rows: 100px 100px 100px;
    grid-template-areas: "header header header"
                         "main main sidebar"
                         "footer footer footer";
  }
  ```

- 如果某些区域不需要利用，则使用"点"（`.`）表示。

- 注意，区域的命名会影响到网格线。每个区域的起始网格线，会自动命名为`区域名-start`，终止网格线自动命名为`区域名-end`。

##### 

##### `row-gap`

- 属性设置行与行的间隔（行间距）

  



##### `column-gap`

- 属性设置列与列的间隔（列间距）
- 根据最新标准，上面三个属性名的`grid-`前缀已经删除，`grid-column-gap`和`grid-row-gap`写成`column-gap`和`row-gap`，`grid-gap`写成`gap`



##### `gap`

- ``grid-column-gap`和`grid-row-gap`的合并简写形式
- 如果`grid-gap`省略了第二个值，浏览器认为第二个值等于第一个值

##### 

##### `grid-auto-flow`

- 默认值是`row`，即"先行后列"。也可以将它设成`column`，变成"先列后行"
- `grid-auto-flow`属性除了设置成`row`和`column`，还可以设成`row dense`和`column dense`。这两个值主要用于，某些项目指定位置以后，剩下的项目怎么自动放置(尽可能紧密填满，尽量不出现空格)

##### 

##### `justify-items`

- 设置单元格内容的水平位置（左中右）
- 



#####  `align-items`

- 属性设置单元格内容的垂直位置（上中下）

- ```
  start：对齐单元格的起始边缘
  end：对齐单元格的结束边缘
  center：单元格内部居中
  stretch：拉伸，占满单元格的整个宽度（默认值）
  ```

  



##### `place-items`

- 是`align-items`属性和`justify-items`属性的合并简写形式



##### 



##### `justify-content`

- 整个内容区域在容器里面的水平位置（左中右）

- ```markdown
  start - 对齐容器的起始边框。
  end - 对齐容器的结束边框。
  center - 容器内部居中。
  stretch - 项目大小没有指定时，拉伸占据整个网格容器。
  space-around - 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与容器边框的间隔`大一倍`。
  space-between - 项目与项目的间隔相等，项目与容器边框之间`没有间隔`。
  space-evenly - 项目与项目的间隔相等，项目与容器边框之间也是`同样长度`的间隔。
  ```

  

##### `align-content`

- 是整个内容区域的垂直位置（上中下）。



##### `place-content`

- `align-content`属性和`justify-content`属性的合并简写形式

##### 

##### `grid-auto-columns `

- 用来设置，浏览器自动创建的多余网格的列宽
- 写法与`grid-template-columns`和`grid-template-rows`完全相同
- 如果不指定这两个属性，浏览器完全根据单元格内容的大小，决定新增网格的列宽和行高。



##### `grid-auto-rows `

- 用来设置，浏览器自动创建的多余网格的行高
- 写法与`grid-template-columns`和`grid-template-rows`完全相同
- 如果不指定这两个属性，浏览器完全根据单元格内容的大小，决定新增网格的列宽和行高。



##### 



##### `grid-template`

- `grid-template-columns`、`grid-template-rows`和`grid-template-areas`这三个属性的合并简写形式。

##### `grid`

- `grid-template-rows`、`grid-template-columns`、`grid-template-areas`、 `grid-auto-rows`、`grid-auto-columns`、`grid-auto-flow`这六个属性的合并简写形式

#### 项目属性

##### `grid-column-start`
- 左边框所在的垂直网格线

- ```css
  .item-1 {
    /* 指定为第几个网格线 */
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 2;
    grid-row-end: 4;
  }
  ```

- ```css
  .item-1 {
    /* 指定为网格线的名字 */
    grid-column-start: header-start;
    grid-column-end: header-end;
  }
  ```

- ```css
  .item-1 {
    /* span 关键字表示"跨越"，即左右边框（上下边框）之间跨越多少个网格*/
    grid-column-start: span 2;
  }
  ```
##### `grid-column-end`
- 右边框所在的垂直网格线





##### `grid-row-start`
- 上边框所在的水平网格线
##### `grid-row-end`
- 下边框所在的水平网格线

##### 

##### `grid-column`

- `grid-column-start`和`grid-column-end`的合并简写形式

- ```css
  .item {
    grid-column: <start-line> / <end-line>;
    grid-row: <start-line> / <end-line>;
  }
  ```

##### `grid-row`

- `grid-row-start`属性和`grid-row-end`的合并简写形式

##### 

##### `grid-area `

- 指定项目放在哪一个区域(`grid-template-areas`)

- 可用作`grid-row-start`、`grid-column-start`、`grid-row-end`、`grid-column-end`的合并简写形式，直接指定项目的位置。

- ```css
  .item {
    grid-area: <row-start> / <column-start> / <row-end> / <column-end>;
  }
  ```

  

##### 

##### `justify-self `

- 设置单元格内容的水平位置（左中右）

- 跟`justify-items`属性的用法完全一致，但只作用于单个项目

- ```
  start：对齐单元格的起始边缘。
  end：对齐单元格的结束边缘。
  center：单元格内部居中。
  stretch：拉伸，占满单元格的整个宽度（默认值）。
  ```

  



#####  `align-self `

- 设置单元格内容的垂直位置（上中下）
- 跟`align-items`属性的用法完全一致，也是只作用于单个项目



##### `place-self` 



## `float`



## `position`

#### :static

- HTML 元素**默认**情况下的定位方式为 static（静态）。
- 静态定位的元素**不受 top、bottom、left 和 right 属性的影响**。
- `position: static;` 的元素不会以任何特殊方式定位；它始终根据页面的**正常流**进行定位：



#### :relative

- `position: relative;` 的元素**相对于其正常位置**进行定位。
- 设置相对定位的元素的 top、right、bottom 和 left 属性将导致其偏离其正常位置进行调整。**不会对其余内容进行调整**来适应元素留下的任何空间（**其他元素保持不动**）。



#### :fixed

- `position: fixed;` 的元素是相对于视口定位的，这意味着即使滚动页面，它也**始终位于同一位置**。 top、right、bottom 和 left 属性用于定位此元素（**默认原位，定位后相对于视口**）。
- 添加该属性后，该块锁定在原来位置，**后面补上**（固定定位的元素**不会在页面中通常应放置的位置上留出空隙**）。



#### :absolute 

- `position: absolute;` 的元素相对于最近的定位祖先元素进行定位（而不是相对于视口定位，如 fixed）。

- 然而，如果绝对定位的元素没有祖先，它将使用文档主体（body），并随页面滚动一起移动。




#### :sticky

- `position: sticky;` 的元素根据用户的滚动位置进行定位。

- 粘性元素根据滚动位置在相对（relative）和固定（fixed）之间切换。起先它会被相对定位，直到在视口中遇到给定的偏移位置为止 - 然后将其“粘贴”在适当的位置（比如 position:fixed）。






# 背景

#### 背景图片

##### `background-image` 

 定义背景图片地址

```css
div
{
    width:250px;
    height:170px;
    background-image: url(img/demo.png);
    /*   相对路径
    	../    上一级目录
    	./     当前目录
    	/	   根目录
    */
    
}
```

##### `background-repeat` 

定义背景图片的重复方式

| 属性值    | 说明                                         |
| :-------- | :------------------------------------------- |
| repeat    | 在水平方向和垂直方向上同时平铺（**默认值**） |
| repeat-x  | 只在水平方向（x轴）上平铺                    |
| repeat-y  | 只在垂直方向（y轴）上平铺                    |
| no-repeat | 不平铺                                       |

##### `background-position`

定义背景图片的位置



##### `background-attachment` 

定义背景图片是随元素一起滚动还是固定不动





# 文字

### 字体

#### `@font-face`

- 用来定义字体

```css
@font-face
{
    font-family: myFirstFont;
    src: url(sansation_light.woff);
}
 
div
{
    font-family:myFirstFont;
}
```





#### `font-style`

- **字体样式**
- `normal`  默认值
- `italic`  斜体





#### `font-weight`

- 字体粗细

```css
/* Keyword values */
font-weight: normal;     /* 400 */
font-weight: bold;		 /* 700 */
 
/* Keyword values relative to the parent */
font-weight: lighter;
font-weight: bolder;

/* Numeric keyword values */
font-weight: 1
font-weight: 100;
font-weight: 100.6;
font-weight: 123;
font-weight: 200;
font-weight: 300;
font-weight: 321;
font-weight: 400;
font-weight: 500;
font-weight: 600;
font-weight: 700;
font-weight: 800;
font-weight: 900;
font-weight: 1000;

/* Global values */
font-weight: inherit;
font-weight: initial;
font-weight: unset;
```







#### `font-size`

- 字号

```css
/* <absolute-size>，绝对大小值 */
font-size: xx-small;
font-size: x-small;
font-size: small;
font-size: medium;
font-size: large;
font-size: x-large;
font-size: xx-large;

/* <relative-size>，相对大小值 */
font-size: larger;
font-size: smaller;

/* <length>，长度值 */
font-size: 12px;
font-size: 0.8em;

/* <percentage>，百分比值 */
font-size: 80%;

font-size: inherit;
```



#### `font-family`

- 设置字体族科





#### `font`

- font 属性可以用来作为 `font-style`, `font-variant`, `font-weight`, `font-size`, `line-height` 和 `font-family` 属性的简写，或将元素的字体设置为系统字体



#### `color`

- 设置颜色值的前景色以及文本装饰

```css
/* 关键词 */
color: currentcolor;

/* <named-color>值 */
color: red;
color: orange;
color: tan;
color: rebeccapurple;

/* <hex-color>值 */
color: #090;
color: #009900;
color: #090a;
color: #009900aa;

/* <rgb()>值 */
color: rgb(34, 12, 64, 0.6);
color: rgba(34, 12, 64, 0.6);
color: rgb(34 12 64 / 0.6);
color: rgba(34 12 64 / 0.3);
color: rgb(34.0 12 64 / 60%);
color: rgba(34.6 12 64 / 30%);

/* <hsl()>值 */
color: hsl(30, 100%, 50%, 0.6);
color: hsla(30, 100%, 50%, 0.6);
color: hsl(30 100% 50% / 0.6);
color: hsla(30 100% 50% / 0.6);
color: hsl(30.0 100% 50% / 60%);
color: hsla(30.2 100% 50% / 60%);

/* 全局值 */
color: inherit;
color: initial;
color: unset;
```



#### `opacity`

- 指定了一个元素的**不透明度**

```css
/* 完全不透明 */
opacity: 1;
opacity: 1.0;

/* 半透明 */
opacity: 0.6;

/* 完全透明 */
opacity: 0.0;
opacity: 0;

opacity: inherit;
```



### 文本

#### `text-align`

- 定义行内内容（例如文字）如何相对它的块父元素对齐
- `text-align` 并不控制块元素自己的对齐，只控制它的行内内容的对齐。

```css
/* Keyword values */
text-align: left;				/* 行内内容向左侧边对齐 */
text-align: right;				/* 行内内容向右侧边对齐 */
text-align: center;				/* 行内内容居中 */
text-align: justify;			/* 文字向两侧对齐，对最后一行无效 */
text-align: justify-all;		/* 和justify一致，但是强制使最后一行两端对齐 */
text-align: start;				/* 如果内容方向是左至右，则等于left，反之则为right */
text-align: end;				/* 如果内容方向是左至右，则等于right，反之则为left */
text-align: match-parent;      	/* 和inherit类似，区别在于start和end的值根据父元素的direction确定，并被替换为恰当的left或right */

/* Block alignment values (Non-standard syntax) */
text-align: -moz-center;
text-align: -webkit-center;

/* Global values */
text-align: inherit;
text-align: initial;
text-align: unset;
```





#### `text-decoration`

- 用于设置文本的修饰线外观的（下划线、上划线、贯穿线/删除线 或 闪烁）
- 是 `text-decoration-line`, `text-decoration-color`, `text-decoration-style`, 和新出现的 `text-decoration-thickness` 属性的缩写

```
text-decoration-line
文本修饰的位置, 如下划线underline，删除线line-through

text-decoration-color
文本修饰的颜色

text-decoration-style
文本修饰的样式, 如波浪线wavy实线solid虚线dashed

text-decoration-thickness
文本修饰线的粗细
```







#### `text-transform`

- 指定如何将元素的文本大写。
- 可以用于使文本显示为全大写或全小写，也可单独对每一个单词进行操作。

```css
/* Keyword values */
text-transform: capitalize;		/* 这个关键字强制每个单词的首字母转换为大写。其他的字符保留不变 */
text-transform: uppercase;		/* 强制所有字符被转换为大写 */
text-transform: lowercase;		/* 强制所有字符被转换为小写 */ 
text-transform: none;			/* 阻止所有字符的大小写被转换 */
text-transform: full-width;     /* 强制字符 — 主要是表意字符和拉丁文字 — 书写进一个方形里，并允许它们按照一般的东亚文字（比如中文或日文）对齐*/

/* Global values */
text-transform: inherit;
text-transform: initial;
text-transform: unset;
```





#### `text-indent`

- 能定义一个块元素首行文本内容之前的缩进量

```css
/* <length> 长度值 */
text-indent: 3mm;
text-indent: 40px;

/* <percentage>百分比值取决于其包含块（containing block）的宽度*/
text-indent: 15%;

/* 关键字 */
text-indent: 5em each-line;			/* each-line 
文本缩进会影响第一行，以及使用<br>强制断行后的第一行*/
text-indent: 5em hanging;			/* hanging 
该值会对所有的行进行反转缩进：除了第一行之外的所有的行都会被缩进，看起来就像第一行设置了一个负的缩进值 */
text-indent: 5em hanging each-line;

/* 全局值 */
text-indent: inherit;
text-indent: initial;
text-indent: unset;
```



#### `line-height`

- 用于设置多行元素的空间量，如多行文本的间距
- 对于块级元素，它指定元素行盒（line boxes）的最小高度
- 对于非替代的 inline 元素，它用于计算行盒（line box）的高度

```css
/* Keyword value */
line-height: normal;

/* Unitless values: use this number multiplied
by the element's font size */
line-height: 3.5;

/* <length> values */
line-height: 3em;

/* <percentage> values */
line-height: 34%;

/* Global values */
line-height: inherit;
line-height: initial;
line-height: unset;
```





#### `overflow-wrap`

- 用来说明当一个不能被分开的字符串太长而不能填充其包裹盒时，为防止其溢出，浏览器是否允许这样的单词中断换行
- `word-wrap` 属性原本属于微软的一个私有属性，在 CSS3 现在的文本规范草案中已经被重名为 overflow-wrap 。 word-wrap 现在被当作 overflow-wrap 的 “别名”。

```css
/* Keyword values */
overflow-wrap: normal;        	/* 行只能在正常的单词断点处中断。（例如两个单词之间的空格） */
overflow-wrap: break-word;		/* 表示如果行内没有多余的地方容纳该单词到结尾，则那些正常的不能被分割的单词会被强制分割换行 */

/* Global values */
overflow-wrap: inherit;
overflow-wrap: initial;
overflow-wrap: unset;

```





#### **`vertical-align`** 

- 用来指定行内元素（inline）或表格单元格（table-cell）元素的垂直对齐方式。
- 只对行内元素、表格单元格元素生效：不能用它垂直对齐块级元素。

```css
/* Keyword values */
vertical-align: baseline;
vertical-align: sub;
vertical-align: super;
vertical-align: text-top;
vertical-align: text-bottom;
vertical-align: middle;
vertical-align: top;				/* 使元素及其后代元素的顶部与整行的顶部对齐 */
vertical-align: bottom;				/* 使元素及其后代元素的底部与整行的底部对齐 */

/* <length> values */
vertical-align: 10em;
vertical-align: 4px;

/* <percentage> values */
vertical-align: 20%;

/* Global values */
vertical-align: inherit;
vertical-align: initial;
vertical-align: unset;
```









#### `overflow`

-  定义当一个元素的内容太大而无法适应 块级格式化上下文 时候该做什么。
- 是 `overflow-x` 和`overflow-y`的 简写属性 。

```css
/* 默认值。内容不会被修剪，会呈现在元素框之外 */
overflow: visible;

/* 内容会被修剪，并且其余内容不可见 */
overflow: hidden;

/* 内容会被修剪，浏览器会显示滚动条以便查看其余内容 */
overflow: scroll;

/* 由浏览器定夺，如果内容被修剪，就会显示滚动条 */
overflow: auto;

/* 规定从父元素继承overflow属性的值 */
overflow: inherit;
```





#### `text-overflow`

-   确定如何向用户发出未显示的溢出内容信号
- 它可以被剪切，显示一个省略号或显示一个自定义字符串

```css
/* Overflow behavior at line end
   Right end if ltr, left end if rtl */
text-overflow: clip;  		/* 此为默认值。在内容区域的极限处截断文本*/
text-overflow: ellipsis;  	/* 用一个省略号来表示被截断的文本*/
text-overflow: "…";
text-overflow: fade;
text-overflow: fade(10px);
text-overflow: fade(5%);

/* Overflow behavior at left end | at right end
   Directionality has no influence */
text-overflow: clip ellipsis;
text-overflow: "…" "…";
text-overflow: fade clip;
text-overflow: fade(10px) fade(10px);
text-overflow: fade(5%) fade(5%);

/* Global values */
text-overflow: inherit;
text-overflow: initial;
text-overflow: unset;
```





#### `white-space` 

- 用来设置如何处理元素中的 空白 (en-US)。

```css
/* Keyword values */
white-space: normal;          	/* 连续的空白符会被合并，换行符会被当作空白符来处理 */
white-space: nowrap;			/* 和 normal 一样，连续的空白符会被合并。但文本内的换行无效 */
white-space: pre;				/* 连续的空白符会被保留。在遇到换行符或者<br>元素时才会换行 */
white-space: pre-wrap;			/* 连续的空白符会被保留。在遇到换行符或者<br>元素，或者需要为了填充「行框盒子(line boxes)」时才会换行 */
white-space: pre-line;			/* 连续的空白符会被合并。在遇到换行符或者<br>元素，或者需要为了填充「行框盒子(line boxes)」时会换行 */

/* https://github.com/w3c/csswg-drafts/pull/2841 */
white-space: break-spaces;

/* Global values */
white-space: inherit;
white-space: initial;
white-space: unset;
```







#### `word-spacing`

- 用于声明标签和单词直接的间距行为(中文无效)

```css
/* Keyword value */
word-spacing: normal;  		/* 正常的单词间距，由当前字体和/或浏览器定义 */

/* <length> values */
word-spacing: 3px;       
word-spacing: 0.3em;

/* Global values */
word-spacing: inherit;
```



#### `letter-spacing` 

- 用于设置文本字符的间距表现。

```css
/* Keyword value */
letter-spacing: normal;   /* 此间距是按照当前字体的正常间距确定的*/

/* <length> values */
letter-spacing: 0.3em;
letter-spacing: 3px;
letter-spacing: .3px;

/* Global values */
letter-spacing: inherit;
letter-spacing: initial;
letter-spacing: unset;
```



# 标签

##### 链接

```css
a {

}
```



##### 列表

```

```



# 变量

```css
/* 创建(变量的作用域就是它所在的选择器的有效范围,常放:root中)(--前缀) */
:root{
    --color-background:#ffffff;
}

/* 引用(用var()引用) */
body {
    user-select: none;
    background-color: var(--color-background);   
}
```



# 动画

## @keyframes

```css
/* sdsd */
@keyframes demo {
    from{
        transform: translateX(-100px);
    }
    to{
        transform: translateX(0px);
    }
}
.current {
    animation: demo 1s;
}
```



## transform

#### 平移：translate()

```css
#current {
	transform:translate(20px, 40px);
}
```

```css
#current {
	transform:translateX(20px);
	transform:translateY(40px);//不等于上面,只下移40px,会覆盖
}
```

```css
#current {
	transform:translateY(40px) translateX(20px);//等于一例
}
```



#### 缩放：scale()

```css
#current {
	transform:scale(1.2, 1.5);
}
```

```css
#current {
	transform:scaleX(1.2) scaleY(1.5);
}
```

#### 倾斜：skew()

```css
 #current {
	transform:skew(10deg, 20deg);
}
```

```css
 #current {
	transform:skewX(10deg) skewY(20deg);
	//两值和为0时,等效选择
}
```

#### 旋转：rotate()

```css
 #current {
	transform:rotate(30deg);
}
```







# `fliter`

## `bur`

- 将高斯模糊应用于输入图像

- `radius` 定义了高斯函数的标准偏差值，或者屏幕上有多少像素相互融合，因此，较大的值将产生更多的模糊

- ```css
  filter: blur(5px);
  ```

  



## `hue-rotate`

- 色相旋转

- ```css
  filter: hue-rotate(90deg);
  ```



## `drop-shadow`

- 对输入图像应用阴影效果

- （`<offset-x>` ,`<offset-y>`,`<blur-radius>`,`<color>`）

- ```css
  filter: drop-shadow(16px 16px 10px black)
  ```

  











# @规则

- [`@charset`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@charset), 定义样式表使用的字符集.
- [`@import`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@import), 告诉 CSS 引擎引入一个外部样式表.
- [`@namespace`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@namespace), 告诉 CSS 引擎必须考虑XML命名空间。
- 嵌套@规则, 是嵌套语句的子集,不仅可以作为样式表里的一个语句，也可以用在条件规则组里：
  - [`@media`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media), 如果满足媒介查询的条件则条件规则组里的规则生效。
  - [`@page`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@page), 描述打印文档时布局的变化.
  - [`@font-face`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face), 描述将下载的外部的字体。 
  - [`@keyframes`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@keyframes), 描述 CSS 动画的中间步骤 . 
  - [`@supports`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@supports), 如果满足给定条件则条件规则组里的规则生效。 
  - [`@document`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@document), 如果文档样式表满足给定条件则条件规则组里的规则生效。 *(推延至 CSS Level 4 规范)*

# BFC

- 块级格式化上下文

```
1.float的值不为none

2.overflow的值不为visible

3.display的值为table-cell、tabble-caption和inline-block之一

4.position的值不为static或则releative中的任何一个
```





# 案例

## 下拉

```html
		<style>
        .dropdown {
         position: relative;
         display: inline-block;
        }
        
        .dropdown-content {
          display: none;
          position: absolute;
          background-color: #f9f9f9;
          min-width: 160px;
          box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
          padding: 12px 16px;
          z-index: 1;
        }
        
        .dropdown:hover .dropdown-content {
          display: block;
        }
        </style>
        
        <div class="dropdown">
          <span>Mouse over me</span>
          <div class="dropdown-content">
            <p>Hello World!</p>
          </div>
        </div>
```



## 导航

































 