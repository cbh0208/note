## 嵌套

### 基本嵌套

```scss
#content {
  article {
    h1 { color: #333 }
    p { margin-bottom: 1.4em }
  }
  aside { background-color: #EEE }
}
```

```css
 /* 编译后 */
#content article h1 { color: #333 }
#content article p { margin-bottom: 1.4em }
#content aside { background-color: #EEE }
```

### 属性嵌套

```scss
p {
　　border: {  /* border后有: */
　　　　color: red;
　　}
}
```

```css
 /* 编译后 */
P {
    border-color:red;
}
```



### 自身嵌套

```scss
a { /* 可以使用&引用父元素 */
　　&:hover { color: #ffb3ff; }
}
```

```css
 /* 编译后 */
a:hover {
    color:#ffb3ff
}
```





## 变量

```scss
// 所有变量以$开头。
$red: red;
$g: green;

body {
  p {
    color: $red;
    &:hover {
      color: $g;
    }
  }
}
```

```scss
// 如果变量需要镶嵌在字符串之中，就必须需要写在#{}之中
$side : left;

.rounded {
　　border-#{$side}-radius: 5px;
}
```





## 注释

```scss
/* 会保留到编译后的文件 */ 

// 只保留在SASS源文件中，编译后被省略

/*! 即使是压缩模式编译，也会保留这行注释 */ 
```





## 继承

```scss
/* 使用@extend命令实现继承 */
.class2 {
　　@extend .class1;
　　font-size:120%;
}
```





## Mixin

### 基本

```scss
/* 使用@mixin命令，定义一个代码块 */
@mixin left {
　　float: left;
　　margin-left: 10px;
}

/* 使用@include命令，调用mixin */
div {
　　@include left;
}
```

```css
div {
  　　float: left;
  　　margin-left: 10px;
}
```



### 传参

```scss
@mixin left($a) {
　　float: left;
　　margin-left: $a;
}


div {
　　@include left(10px);
}
```

```css
div {
  　　float: left;
  　　margin-left: 10px;
}
```



### 默认值

```scss
@mixin left($a:20px) {
　　float: left;
　　margin-left: $a;
}


div {
　　@include left;
}
```

```css
div {
  　　float: left;
  　　margin-left: 20px;
}
```


























## 颜色函数



## 插入文件

```scss
/* @import命令，用来插入外部文件 */
@import "path/filename.scss";
```

```css
/* 如果插入的是.css文件，则等同于css的import命令 */
@import "foo.css";
```



## 条件语句



## 循环语句



## 自定义函数