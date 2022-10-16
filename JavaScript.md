​		 

# 基础语法

## `数据类型`

### 概述

最新的 ECMAScript 标准定义了 8 种数据类型:

- 7 种原始类型，使用`typeof`运算符检查:

  - **undefined**			`typeof instance === "undefined"`
  - **Boolean**：			`typeof instance === "boolean"`
  - **Number**：	 	   `typeof instance === "number"`
  - **String**：                 `typeof instance === "string`
  - **BigInt**：                 `typeof instance === "bigint"`
  - **Symbol** ：             `typeof instance === "symbol"`
  - **null**：                    `typeof instance === "object"`。

- **Object**：`typeof instance === "object"`。

  检查 Object 种类的合适方式是使用 `instanceof` 关键字。但即使这样也存在误差

  任何 constructed 对象实例的特殊非数据结构类型，也用做数据结构：new [Object](https://developer.mozilla.org/zh-CN/docs/Glossary/Object)，new [Array](https://developer.mozilla.org/zh-CN/docs/Glossary/array)，new Map，new Set，new WeakMap，new WeakSet，new Date，和几乎所有通过 new keyword 创建的东西







### `Number`

- 整数15位,浮点17位

  

  

  

#### `NaN`   

- 非数值
- 用`isNaN()`判断



#### `Infinity`

- `Infinity` 是*全局对象*（*global object*）的一个属性，即它是一个全局变量
- `Infinity` 的初始值是 `Number.POSITIVE_INFINITY`
- `Infinity`（正无穷大）大于任何值。

```js
console.log(Infinity          ); /* Infinity */
console.log(Infinity + 1      ); /* Infinity */
console.log(Math.pow(10, 1000)); /* Infinity */
console.log(Math.log(0)       ); /* -Infinity */
console.log(1 / Infinity      ); /* 0 */
```





#### 进制

- 二进制

  ```js
  var a=0b10
  console.log(a);							// 2
  console.log(typeof a);					// number			
  ```

  

- 八进制

  ```js
  var a=010
  console.log(a);							// 8
  console.log(typeof a);					// number	
  ```

  

- 十六进制

  ```js
  var a=0x10
  console.log(a);							// 8
  console.log(typeof a);					// number	
  ```

  

- 4

- 4

- 4













#### 转换

##### 数字转字符串

```javascript
// toString()
// 把数字转换为字符串(可进行进制转换)

var a=10;
var b=a.toString()
console.log(b);			// 10
console.log(typeof b)	// string

console.log(a.toString(2));	 // 1010
```

```javascript
// String()
// 把数字转换为字符串

var a=10;
var b=String(b)
```

```js
// Number.prototype.toExponential()
// toExponential() 方法以指数表示法返回该数值字符串表示形式

var numObj = 77.1234;
alert("numObj.toExponential() is " + numObj.toExponential()); 	//输出 7.71234e+1
alert("numObj.toExponential(4) is " + numObj.toExponential(4)); //输出 7.7123e+1
alert("numObj.toExponential(2) is " + numObj.toExponential(2)); //输出 7.71e+1
alert("77.1234.toExponential() is " + 77.1234.toExponential()); //输出 7.71234e+1
alert("77 .toExponential() is " + 77 .toExponential()); 		//输出 7.7e+1
```

```js
// Number.prototype.toFixed()
// toFixed() 方法使用定点表示法来格式化一个数值

function financial(x) {
  return Number.parseFloat(x).toFixed(2);//指定返回2位小数
}

console.log(financial(123.456));
// expected output: "123.46"

console.log(financial(0.004));
// expected output: "0.00"

console.log(financial('1.23e+5'));
// expected output: "123000.00"
```

```js
// Number.prototype.toPrecision()
// toPrecision() 方法以指定的精度返回该数值对象的字符串表示(c)
```



##### 字符串转数字

```javascript
// Number() 
// 把对象的值转换为数字
// 如果是Boolean值，true和false值将分别被转换为1和0。
// 如果是数字值，只是简单的传入和返回。
如果是null值，返回0。
如果是undefined，返回NaN。

var a='666.666'
b=Number(a)
console.log(b);
```

```javascript
// parseInt() 函数
// 可解析一个字符串，并返回一个整数

parseInt("10");			//返回 10
parseInt("19",10);		//返回 19 (10+9)
parseInt("11",2);		//返回 3 (2+1)
parseInt("17",8);		//返回 15 (8+7)
parseInt("1f",16);		//返回 31 (16+15)
parseInt("010");		//未定：返回 10 或 8
```

```javascript
// parseFloat() 
// 可解析一个字符串，并返回一个浮点数
// 字符串中只返回第一个数字
// 开头和结尾的空格是允许的
// 如果字符串的第一个字符不能被转换为数字，那么 parseFloat() 会返回 NaN

document.write(parseFloat("10") + "<br>");				// 10
document.write(parseFloat("10.33") + "<br>");			// 10.33
document.write(parseFloat("34 45 66") + "<br>");		// 34
document.write(parseFloat(" 60 ") + "<br>");			// 60
document.write(parseFloat("40 years") + "<br>");		// 40 
document.write(parseFloat("He was 40") + "<br>");		// NaN
```





### `BigInt`







## 运算符

#### `||`

- 只要“||”前面为false,不管“||”后面是true还是false，都返回“||”后面的值。
- 只要“||”前面为true,不管“||”后面是true还是false，都返回“||”前面的值。
- 总结：真前假后

#### `&&`

- 只要“&&”前面是false，无论“&&”后面是true还是false，结果都将返“&&”前面的值;
- 只要“&&”前面是true，无论“&&”后面是true还是false，结果都将返“&&”后面的值;
- 总结：假前真后

## 变量声明

#### var

- var定义的变量，没有块的概念，可以跨块访问, 不能跨函数访问。

  ```js
  var a='鸢一折纸'
  if(true)
      var a='五河琴里'
  console.log(a);//五河琴里
  ```

- 在循环绑定事件过程中，var定义的变量无法保存，循环会在瞬间执行完。

- 可以变量提升(只此一家)



#### let(ES6)

- let不可对一变量重复声明

- let定义的变量，只能在块作用域里访问，不能跨块访问，也不能跨函数访问。

  ```js
  let a='鸢一折纸'
  if(true)
  { // 有{}js才承认是块作用域
      // console.log(a);   //ReferenceError: Cannot access 'a' before initialization
      let a='五河琴里'
      console.log(a);      // 五河琴里
  }
      
  console.log(a);   // 鸢一折纸
  ```

- 由于let是块级作用域，在循环绑定事件过程中let会在这个循环中生效，再次循环时let会重新定义生效。



#### const(ES6)

- const用来定义常量，使用时必须初始化(即必须赋值)，只能在块作用域里访问，而且不能修改。


- 在数组，对象里面，const的值是允许被修改的，因为const存储的是地址，值的内容可以变化（**用const声明数组，对象**）。



## 函数

### 箭头函数(ES6)

- this值**静态**，无法被call()改变

- 不能作为**构造函数**去实例化对象

- 不能使用arguments

- 获取**上下文this**作为自己this(不要再this=this)

- 适合与this无关回调，**定时器**，**数组方法回调**


```javascript
let fn=(a,b)=>{
return a+b;}
```

```javascript
let fn=a=>a*a;//简写
```

```javascript
const result=arr.filter(item=>item%2===0)
```



### 函数柯里化

将多变量函数拆解为单变量的多个函数的依次调用， 可以从高元函数动态地生成批量的低元的函数。

简单讲：就是利用函数执行，可以形成一个不销毁的私有作用域，把预先处理的内容都存在这个不销毁的作用域里面，并且返回一个函数，以后要执行的就是这个函数。

```js
// 函数封装后
function check(reg, txt) {
    return reg.test(txt)
}

check(/\d+/g, 'test')       //false
check(/[a-z]+/g, 'test')    //true

// Currying后
function curryingCheck(reg) {
    return function(txt) {
        return reg.test(txt)
    }
}

var hasNumber = curryingCheck(/\d+/g)
var hasLetter = curryingCheck(/[a-z]+/g)

hasNumber('test1')      // true
hasNumber('testtest')   // false
hasLetter('21212')      // false
```



### 函数形参初值(ES6)

```javascript
		let add=(a,b,c=10)=>a+b+c//为c设初值10
        console.log(add(1,2,3));//6
        console.log(add(1,2));//13
```



### 构造函数

- 需要使用new关键字来调用
- 内部用this 来构造属性和方法
- 构造函数会马上创建一个新对象，并将该新对象作为返回值返回
- 构造函数默认返回 this 对象;如果构造函数内使用了 return 语句，并 且 return 后跟的是一个对象，则这个构造函数返回的是这个对象，否则返回 this .



## `内部对象`

JS中，可以将对象分为“内部对象”、“宿主对象”和“自定义对象”三种

- **内部对象**

  js中的内部对象包括`Array`、`Boolean`、`Date`、`Function`、`Global`、`Math`、`Number`、`Object`、`RegExp`、`String`以及各种错误类对象，包括Error、EvalError、RangeError、ReferenceError、SyntaxError和TypeError

  其中Global和Math这两个对象又被称为“内置对象”，这两个对象在脚本程序初始化时被创建，不必实例化这两个对象。

- **宿主对象**

  宿主对象就是执行JS脚本的环境提供的对象。对于嵌入到网页中的JS来说，其宿主对象就是浏览器提供的对象，所以又称为浏览器对象，如IE、Firefox等浏览器提供的对象。不同的浏览器提供的宿主对象可能不同，即使提供的对象相同，其实现方式也大相径庭！这会带来浏览器兼容问题，增加开发难度。

  浏览器对象有很多，如Window和Documen，Element，form，image，等等。

- **自定义对象**

  顾名思义，就是开发人员自己定义的对象。JS允许使用自定义对象，使JS应用及功能得到扩充











### `String`

```javascript
// length 属性返回字符串的长度
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length;
```

#### 转义

```js
\\

\'
console.log('\'a\'');	// 'a'

\"
console.log("\"a\"");	// "a"

\t	制表符

\n	换行

\r	截断之后,替换开头
```



#### 方法:查找

##### indexOf() 

```javascript
// String.prototype.indexOf() 
// 方法返回字符串中指定文本首次出现的索引（位置）：
//无法设置更强大的搜索值（正则表达式）(除此外与search() 相同)

var str = "The full name of China is the People's Republic of China.";
var pos = str.indexOf("China");//17
```



##### search()

```javascript
// String.prototype.search()
// 搜索特定值的字符串，并返回匹配的位置：
// 无法设置第二个开始位置参数(除此外与indexOf() 相同)

var str = "The full name of China is the People's Republic of China.";
var pos = str.search("locate");//17
```



##### slice()

```javascript
// String.prototype.slice()
// 提取字符串的某个部分并在新字符串中返回被提取的部分。

```



##### charAt()

```javascript
// String.prototype.charAt()
// 返回字符串中指定下标（位置）的字符串：

var str = "HELLO WORLD";
str.charAt(0);            // 返回 H
```

#### 方法:修改

##### trim()

```javascript
// String.prototype.trim()
// 从字符串中删除前导和尾随空格以及行结束符。

var str="    hello world   "
str.trim() // "hello world"
```

#### 方法:转换

##### split()

```js
String.prototype.split()
// split() 方法使用指定的分隔符字符串将一个String对象分割成子字符串数组，以一个指定的分割字串来决定每个拆分的位置。 
const str = 'The quick brown fox jumps over the lazy dog.';

const words = str.split(' ');
console.log(words[3]);
// expected output: "fox"

const chars = str.split('');
console.log(chars[8]);
// expected output: "k"

const strCopy = str.split();
console.log(strCopy);
// expected output: Array ["The quick brown fox jumps over the lazy dog."]

```



#### 模板字符串(ES6)

```javascript
// 可多行
	let str=`<ul>
        <li>鸢一折纸</li>
        <li>五河琴里</li>
        <li>夜刀神十香</li>
        </ul>`;
```

```javascript
// 可插入JS表达式
var a = 5;
var b = 10;
console.log(`Fifteen is ${a + b} and
not ${2 * a + b}.`);
// "Fifteen is 15 and
// not 20."
```





### `Array`

#### 方法:转换

##### toString()

```javascript
//Array.prototype.toString()
//toString() 返回一个字符串，表示指定的数组及其元素

const array1 = [1, 2, 'a', '1a'];

console.log(array1+'');
// expected output: "1,2,a,1a"
```

##### join()

```javascript
Array.prototype.join()
// 将一个数组（或一个类数组对象）的所有元素连接成一个字符串并返回这个字符串。如果数组只有一个项目，那么将返回该项目而不使用分隔符

const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// expected output: "Fire,Air,Water"

console.log(elements.join(''));
// expected output: "FireAirWater"

console.log(elements.join('-'));
// expected output: "Fire-Air-Water"
```





#### 方法:增加

##### push()

```javascript
Array.prototype.push()
// （在数组结尾处）向数组添加一个新的元素，返回新数组的长度
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.push("Kiwi");       //  向 fruits 添加一个新元素
```



##### unshift()

```javascript
Array.prototype.unshift()
// （在开头）向数组添加新元素，并“反向位移”旧元素：返回新数组的长度
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon");    // 返回 5
```





#### 方法:删改

##### pop()

```javascript
// Array.prototype.pop()
// 方法从数组中删除最后一个元素，并返回该元素的值。此方法更改数组的长度。

let myFish = ["angel", "clown", "mandarin", "surgeon"];
let popped = myFish.pop();
console.log(myFish);// ["angel", "clown", "mandarin"]
console.log(popped);// surgeon
```



##### shift() 

```javascript
// Array.prototype.shift()
// 会删除首个数组元素，并把所有其他元素“位移”到更低的索引。返回被删除的元素

var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift();             // 返回 "Banana"
```



#####  splice()

```javascript
// Array.prototype.splice()
// splice() 方法通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回被修改的内容
// 此方法会改变原数组

// array.splice(start[, deleteCount[, item1[, item2[, ...]]]])

// start
// 指定修改的开始位置（从0计数）。如果超出了数组的长度，则从数组末尾开始添加内容；如果是负值，则表示从数组末位开始的第几位（从-1计数，这意味着-n是倒数第n个元素并且等价于array.length-n）；如果负数的绝对值大于数组的长度，则表示开始位置为第0位

// deleteCount 可选
// 整数，表示要移除的数组元素的个数。
// 如果 deleteCount 大于 start 之后的元素的总数，则从 start 后面的元素都将被删除（含第 start 位）。
// 如果 deleteCount 被省略了，或者它的值大于等于array.length - start(也就是说，如果它大于或者等于start之后的所有元素的数量)，那么start之后数组的所有元素都会被删除。
// 如果 deleteCount 是 0 或者负数，则不移除元素。这种情况下，至少应添加一个新元素

// item1, item2, ... 可选
// 要添加进数组的元素,从start 位置开始。如果不指定，则 splice() 将只删除数组元素。

const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// replaces 1 element at index 4
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "May"]

```



#### 方法:裁剪

##### slice()

```js
Array.prototype.slice()
// slice() 方法返回一个新的数组对象，这一对象是一个由 begin 和 end 决定的原数组的浅拷贝（包括 begin，不包括end）。原始数组不会被改变。

// arr.slice([begin[, end]])

// begin 可选
//提取起始处的索引（从 0 开始），从该索引开始提取原数组元素。
//如果该参数为负数，则表示从原数组中的倒数第几个元素开始提取，slice(-2) 表示提取原数组中的倒数第二个元素到最后一个元素（包含最后一个元素）。
//如果省略 begin，则 slice 从索引 0 开始。
//如果 begin 超出原数组的索引范围，则会返回空数组。

// end 可选
// 提取终止处的索引（从 0 开始），在该索引处结束提取原数组元素。slice 会提取原数组中索引从 begin 到 end 的所有元素（包含 begin，但不包含 end）。
// slice(1,4) 会提取原数组中从第二个元素开始一直到第四个元素的所有元素 （索引为 1, 2, 3的元素）。
// 如果该参数为负数， 则它表示在原数组中的倒数第几个元素结束抽取。 slice(-2,-1) 表示抽取了原数组中的倒数第二个元素到最后一个元素（不包含最后一个元素，也就是只有倒数第二个元素）。
// 如果 end 被省略，则 slice 会一直提取到原数组末尾。
// 如果 end 大于数组的长度，slice 也会一直提取到原数组末尾。


const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]

```





#### 方法:查找

##### indexOf()

```js
// Array.prototype.indexOf()
// indexOf()方法返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回-1

const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// expected output: 1

// start from index 2
console.log(beasts.indexOf('bison', 2));
// expected output: 4

console.log(beasts.indexOf('giraffe'));
// expected output: -1
```

##### lastIndexOf()

```js
// Array.prototype.lastIndexOf()
// lastIndexOf() 方法返回指定元素（也即有效的 JavaScript 值或变量）在数组中的最后一个的索引，如果不存在则返回 -1。从数组的后面向前查找，从 fromIndex 处开始。

const animals = ['Dodo', 'Tiger', 'Penguin', 'Dodo'];

console.log(animals.lastIndexOf('Dodo'));
// expected output: 3

console.log(animals.lastIndexOf('Tiger'));
// expected output: 1
```



```js
// Array.prototype.find()
// find() 方法返回数组中满足提供的测试函数的第一个元素的值。否则返回 undefined。
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// expected output: 12
```

```js
// Array.prototype.findIndex()
// findIndex()方法返回数组中满足提供的测试函数的第一个元素的索引。若没有找到对应元素则返回-1。
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// expected output: 3
```





##### includes()

```javascript
Array.prototype.includes()
// ES7
// 确定数组是否在其条目中包含某个值，并根据需要返回 true 或 false。

["鸢一折纸","五河琴里"].includes("鸢一折纸")    //true
["鸢一折纸","五河琴里"].includes("夜刀神十香")   //false
```



#### 方法:排序

##### sort()

```javascript
// Array.prototype.sort()
// sort() 方法用原地算法对数组的元素进行排序，并返回数组。默认排序顺序是在将元素转换为字符串，然后比较它们的UTF-16代码单元值序列时构建的
// 由于它取决于具体实现，因此无法保证排序的时间和空间复杂性。

const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]



// arr.sort([compareFunction])
// compareFunction 可选
// 用来指定按某种顺序进行排列的函数。如果省略，元素按照转换为的字符串的各个字符的Unicode位点进行排序。
// firstEl
// 第一个用于比较的元素。
// secondEl
// 第二个用于比较的元素。



var numbers = [4, 2, 5, 1, 3];
numbers.sort(function(a, b) {
  return a - b;
});
console.log(numbers);

也可以写成：
var numbers = [4, 2, 5, 1, 3];
numbers.sort((a, b) => a - b);//返回正数,a<b
console.log(numbers);

// [1, 2, 3, 4, 5]
```

##### reverse()

```javascript
// Array.prototype.reverse()
// reverse() 方法将数组中元素的位置颠倒，并返回该数组。数组的第一个元素会变成最后一个，数组的最后一个元素变成第一个。该方法会改变原数组。
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);
// expected output: "array1:" Array ["three", "two", "one"]
```

#### 方法:合并

##### concat()

```js
// Array.prototype.concat()
// concat() 方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```



#### 方法:迭代

##### map()

```javascript
Array.prototype.map()
// 创建一个新数组，其结果是该数组中的每个元素是调用一次提供的函数后的返回值。

const array1 = [1, 4, 9, 16];
const map1 = array1.map(x => x * 2); // pass a function to map
console.log(map1);// expected output: Array [2, 8, 18, 32]
```



##### filter()

```javascript
Array.prototype.filter()
// 创建一个新数组, 其包含通过所提供函数实现的测试的所有元素

const arr=[1,2,3,4,5]
const result=arr.filter(item=>item%2===0) //Array [2,4]
```



##### forEach()

```javascript
Array.prototype.forEach()
// 数组的每个元素执行一次给定的函数

const array1 = ['a', 'b', 'c'];
array1.forEach(element => console.log(element));
// expected output: "a"
// expected output: "b"
// expected output: "c"

// arr.forEach(callback(currentValue [, index [, array]])[, thisArg])
callback
为数组中每个元素执行的函数，该函数接收一至三个参数：

currentValue
数组中正在处理的当前元素。

index 可选
数组中正在处理的当前元素的索引。

array 可选
forEach() 方法正在操作的数组。

thisArg 可选
可选参数。当执行回调函数 callback 时，用作 this 的值。
```



##### reduce()

```javascript
Array.prototype.reduce()
// reduce() 方法对数组中的每个元素执行一个提供的reducer函数(升序执行)，将其结果汇总为单个返回值。

array.reduce(function(accumulator, currentValue, currentIndex, arr), initialValue)
// accumulator	:初始值, 或者计算结束后的返回值
// currentValue	:数组中正在处理的元素
// currentIndex	:(可选)数组中正在处理的当前元素的索引。  				
//				 如提供initialValue，则起始索引号为0，否则从1起始。
// arr			:(可选)当前元素所属的数组对象						
// initialValue	:(可选)传递给函数的初始值								
```



##### every()

```js
// Array.prototype.every()
// every() 方法测试一个数组内的所有元素是否都能通过某个指定函数的测试。它返回一个布尔值。

const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// expected output: true
```



#### 去重



















### `Object`

#### Object.keys()

- `Object.keys()` 方法会返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和正常循环遍历该对象时返回的顺序一致 

- ```markdown
  Object.keys(obj)
  
  #参数
  	obj
  		要返回其枚举自身属性的对象
  #返回值
  	一个表示给定对象的所有可枚举属性的字符串数组。
  ```

  

```js
// simple array
var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // console: ['0', '1', '2']

// array like object
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.keys(obj)); // console: ['0', '1', '2']

// array like object with random key ordering
var anObj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(anObj)); // console: ['2', '7', '100']

// getFoo is a property which isn't enumerable
var myObj = Object.create({}, {
  getFoo: {
    value: function () { return this.foo; }
  }
});
myObj.foo = 1;
console.log(Object.keys(myObj)); // console: ['foo']
```







#### Object.defineProperty()

- `Object.defineProperty()` 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象。

- vue2双向绑定(3用proxy代替)

- 

- ```markdown
  Object.defineProperty(obj, prop, descriptor)
  
  #参数
  	obj
  		要定义属性的对象
  	prop
  		要定义或修改的属性的名称或 Symbol 
  	descriptor
  		要定义或修改的属性描述符
  #返回值
  	被传递给函数的对象
  ```

```html
    <input type="text" id="input">
    <p id="p"></p>
    <script>
        var input=document.getElementById('input')
        var p=document.getElementById('p')
        var obj={}
        Object.defineProperty(obj,'name',{
            set:function(val){
                input.value=val
                p.innerHTML=val
            },
            get:function(){
                return val
            }
        })
        input.addEventListener('input',function(e){
            obj.name=e.target.value
        })
    </script>
```





### `Set`

- **`Set`** 对象允许你存储任何类型的**唯一**值，无论是原始值或者是对象引用

- 可以按照插入的顺序迭代它的元素

- **创建**

  ```js
  let s1=new Set();
  let s2=new Set(["五河琴里","鸢一折纸","夜刀神十香"]);
  ```

- **添加** `add`

  ```js
  s2.add("洛天依");
  ```

- **检测** `has`

  ```js
  s2.has('鸢一折纸')
  ```

- **删除** `delete`

  ```js
  s2.delete('夜刀神十香');
  ```

- **清空** `clear`

  ```js
  s2.clear()
  ```

- **查看大小**

  ```js
  let n=s2.size
  ```

  



### `Map`

- 可以按照插入的顺序迭代它的元素

- **创建**

  ```js
  let m=new Map();
  ```

- **添加** `set`

  ```js
  m.set("name","鸢一折纸");
  m.set("hh"); //value 为 undefined 
  m.set("hh",function(){
        console.log("呵呵"); // hh被覆盖
  });
  let key={
        age:16
  }
  m.set(key,[""])
  ```

- **获取** `get`

  ```js
  data=m.get(key)
  // 没有返回undefined
  ```

- **删除** `delete`

  ```js
  m.delete("name")
  ```

- **清空** `clear`

  ```js
  m.clear()
  ```

- **查看大小**

  ```js
  let n=m.size
  ```

  

### `WeakSet`

- `WeakSet`中的对象不重复且不可枚举。
- `WeakSet`的“*weak*”指的是，对集合中的对象，如果不存在其他引用，那么该对象将可被垃圾回收
- 于是不存在一个当前可用对象组成的列表，所以`WeakSets`不可枚举





### `WeakMap`

- 它的**键必须是对象类型**，值可以是任意类型
- 它的键被弱保持，也就是说，当其键所指对象没有其他地方引用的时候，它会被GC回收掉
- `WeakMap`提供的接口与`Map`相同。
- `WeakMap`的键是不可枚举的



### `Symbol`

- 第七种数据类型

- `Symbol()`函数会返回**symbol**类型的值
- 每个从`Symbol()`返回的symbol值都是**唯一**的。一个symbol值能作为**对象属性的标识符**；这是该数据类型仅有的目的。

- 不能运算对比


```javascript
const symbol1 = Symbol();
const symbol2 = Symbol(42);
const symbol3 = Symbol('foo');
```





### `Math`

- `Math` works with the `Number` type. It doesn't work with`BigInt`
- 与其他全局对象不同的是，`Math` 不是一个构造器
- `Math` 的所有属性与方法都是静态的。引用圆周率的写法是 `Math.PI`，调用正余弦函数的写法是 `Math.sin(x)`，`x` 是要传入的参数。`Math` 的常量是使用 JavaScript 中的全精度浮点数来定义的。

#### 属性

```js
Math.E			// 欧拉常数，也是自然对数的底数，约等于 2.718。
Math.LN2		// 2 的自然对数，约等于 0.693。
Math.LN10		// 10 的自然对数，约等于 2.303。
Math.LOG2E		// 以 2 为底的 E 的对数，约等于 1.443。
Math.LOG10E		// 以 10 为底的 E 的对数，约等于 0.434。
Math.PI			// 圆周率，一个圆的周长和直径之比，约等于 3.14159。
Math.SQRT1_2	// 二分之一 ½ 的平方根，同时也是 2 的平方根的倒数 12，约等于 0.707。
Math.SQRT2		// 2 的平方根，约等于 1.414。
```

#### 方法

##### Math.abs()

```js
// Math.abs()
// Math.abs(x) 函数返回指定数字 “x“ 的绝对值

Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs("string"); // NaN
Math.abs();         // NaN
```



##### Math.round()

```js
// Math.round()
// Math.round() 函数返回一个数字四舍五入后最接近的整数
// 如果参数的小数部分恰好等于0.5，则舍入到相邻的在正无穷（+∞）方向上的整数

Math.round(20.49);   //20
Math.round(20.5);    //21
Math.round(-20.5);   //-20
Math.round(-20.51);  //-21
```

##### Math.ceil()

```js
// Math.ceil()
// Math.ceil() 函数返回大于或等于一个给定数字的最小整数(向上取整)

Math.ceil(.95);		//  1
Math.ceil(4);		//  4
Math.ceil(7.004);	//  8
Math.ceil(-7.004);	// -7
```

##### Math.floor()

```js
// Math.floor()
// Math.floor() 返回小于或等于一个给定数字的最大整数(向下取整)

Math.floor( 45.95);		// 45
Math.floor( 45.05);		// 45
Math.floor( 4 );		// 4
Math.floor(-45.05);		// -46
Math.floor(-45.95);		// -46
```



##### Math.random()

```js
// Math.random()
// Math.random() 函数返回一个浮点数,范围[0,1)

function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}

console.log(getRandomInt(3));
// expected output: 0, 1 or 2

console.log(getRandomInt(1));
// expected output: 0

console.log(Math.random());
// expected output: a number from 0 to <1
```



##### Math.pow()

```javascript
// Math.pow()
// The Math.pow() function returns the base to the exponent power, as in base^exponent.
console.log(Math.pow(2,10));  //1024
console.log(2**10);           //1024   ES7
```

##### Math.max()

```javascript
// Math.max()
// Math.max() 函数返回一组数中的最大值。

console.log(Math.max(1, 3, 2));
// expected output: 3

console.log(Math.max(-1, -3, -2));
// expected output: -1

const array1 = [1, 3, 2];

console.log(Math.max(...array1));
// expected output: 3
```



### `Date`

#### 创建

- 未创建直接使用为当前时间

```js
new Date();
// 如果没有提供参数，那么新创建的Date对象表示实例化时刻的日期和时间

new Date(value);
// value
// 一个 Unix 时间戳（Unix Time Stamp），它是一个整数值，表示自1970年1月1日00:00:00 UTC（the Unix epoch）以来的毫秒数，忽略了闰秒。大多数 Unix 时间戳功能仅精确到最接近的秒。

new Date(dateString);
// dateString
// 表示日期的字符串值。该字符串应该能被 Date.parse() 正确方法识别(等价)
//  由于浏览器之间的差异与不一致性,强烈不推荐使用

new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]);
// year	表示年份的整数值。 0到99会被映射至1900年至1999年，其它值代表实际年份。参见 示例。
// monthIndex	表示月份的整数值，从 0（1月）到 11（12月）。
// date可选	表示一个月中的第几天的整数值，从1开始。默认值为1。
// hours 可选	表示一天中的小时数的整数值 (24小时制)。默认值为0（午夜）。
// minutes 可选	表示一个完整时间（如 01:10:00）中的分钟部分的整数值。默认值为0。
// seconds 可选	表示一个完整时间（如 01:10:00）中的秒部分的整数值。默认值为0。
// milliseconds 可选	表示一个完整时间的毫秒部分的整数值。默认值为0。
```

#### 属性

```js
Date.prototype
// 允许为 Date 对象添加属性。
Date.length
// Date.length 的值是 7。这是该构造函数可接受的参数个数。
```



#### 方法

##### Date.now()

```js
// Date.now()
// Date.now() 方法返回自 1970 年 1 月 1 日 00:00:00 (UTC) 到当前时间的毫秒数
```

##### Date.parse()

```js
// Date.parse()
//Date.parse() 方法解析一个表示某个日期的字符串，并返回从1970-1-1 00:00:00 UTC 到该日期对象（该日期对象的UTC时间）的毫秒数，如果该字符串无法识别，或者一些情况下，包含了不合法的日期数值（如：2015-02-31），则返回值为NaN。
const unixTimeZero = Date.parse('01 Jan 1970 00:00:00 GMT');
const javaScriptRelease = Date.parse('04 Dec 1995 00:12:00 GMT');
const a=Date.parse('1995-12-04 00:12:00 GMT')
console.log(unixTimeZero);			// expected output: 0
console.log(javaScriptRelease);		// expected output: 818035920000
console.log(a);						// expected output: 818035920000
```

| 方法                               | 描述                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| `Date.prototype.getFullYear()`     | （**几年**）从 Date 对象返回年份 (以四位数字)                |
| `Date.prototype.getMonth()`        | （**几月**）从 Date 对象返回月份 (0 ~ 11)(月份-1)            |
| `Date.prototype.getDate()`         | （**几号**）从 Date 对象返回一个月中的某一天 (1 ~ 31)        |
| `Date.prototype.getDay()`          | （**周几**）从 Date 对象返回一周中的某一天 (0 ~ 6)(0为sunday) |
| `Date.prototype.getHours()`        | （**几时**）返回 Date 对象的小时 (0 ~ 23)                    |
| `Date.prototype.getMinutes()`      | （**几分**）返回 Date 对象的分钟 (0 ~ 59)                    |
| `Date.prototype.getSeconds()`      | （**几秒**）返回 Date 对象的秒数 (0 ~ 59)                    |
| `Date.prototype.getMilliseconds()` | （**几毫秒**）返回 Date 对象的毫秒(0 ~ 999)                  |
| `Date.prototype.getTime()`         | （**时间戳**）返回 1970 年 1 月 1 日至今的毫秒数             |

```javascript
//当前毫秒数(时间戳)
	let a = Date.now();
	let b = new Date().getTime();
	let c = new Date().valueOf();
	let d = +new Date();	
	let e = Date.parse(new Date())
```



### `JSON`

```javascript
var obj = {a: 'Hello', b: 'World'}; 
//这是一个js对象，注意js对象的键名也是可以使用引号包裹的,这里的键名就不用引号包含

var json = '{"a": "Hello", "b": "World"}'; 
//这是一个 JSON 字符串，本质是一个字符串
```

```javascript
// JSON.parse()
// 将JSON字符串转换为JS对象

var obj = JSON.parse('{"a": "Hello", "b": "World"}'); 
//结果是 {a: 'Hello', b: 'World'}  一个对象
```

```javascript
// JSON.stringify()
// 将JS对象转换为JSON字符串

var json = JSON.stringify({a: 'Hello', b: 'World'}); 
//结果是 '{"a": "Hello", "b": "World"}'  一个JSON格式的字符串
```





### `RegExp`

```js
var re = new RegExp("\\w+");
var re = new RegExp(/\w+/);
var re = /\w+/;

var re = new RegExp("\\w+",'g);
var re = new RegExp(/\w+/,'g');
var re = new RegExp(/\w+/g);
var re = /\w+/g;
```

- `g` （全局匹配）

  找到所有的匹配，而不是在第一个匹配之后停止。

- `i` （忽略大小写）

  如果`u`标志也被启用，使用Unicode大小写折叠。

- `m` （多行匹配）

  将开始和结束字符(`^` and `$`)视为在多行上工作。换句话说，匹配每一行的开头或结尾*each* line (由`\n`或者`\r` 分隔)，而不仅仅是整个输入字符串的开头或结尾。

- `s` （点号匹配所有字符）

  允许`.` 去匹配新的行

###### RegExp.prototype.compile()

```js
RegExp.prototype.compile()
// 运行脚本的期间（重新）编译正则表达式

var regexObj = new RegExp("foo", "gi");
regexObj.compile("new foo", "g");
```

###### RegExp.prototype.exec()



```js
RegExp.prototype.exec()
// 在该字符串中执行匹配项的搜索。

const regex1 = RegExp(/foo*/, 'g');
const str1 = 'table football, foosball';
let array1;
while ((array1 = regex1.exec(str1)) !== null) {
  console.log(`Found ${array1[0]}. Next starts at ${regex1.lastIndex}.`);
  // expected output: "Found foo. Next starts at 9."
  // expected output: "Found foo. Next starts at 19."
}


re = /\d/y;
while (r = re.exec("123 456")) console.log(r, "AND re.lastIndex", re.lastIndex);

// [ '1', index: 0, input: '123 456', groups: undefined ] AND re.lastIndex 1
// [ '2', index: 1, input: '123 456', groups: undefined ] AND re.lastIndex 2
// [ '3', index: 2, input: '123 456', groups: undefined ] AND re.lastIndex 3
//   ... and no more match.
```







###### RegExp.prototype.test()

```js
RegExp.prototype.test()
// 该正则在字符串里是否有匹配。
```



## 实用技巧

### for...in

- **`for...in`语句**以任意顺序遍历一个对象的除**Symbol**以外的**可枚举**属性。

- ```javascript
  for (variable in object)
    statement
    
  variable
  	在每次迭代时，variable会被赋值为不同的属性名。
  object
  	非Symbol类型的可枚举属性被迭代的对象。
  ```

```javascript
var obj = {a:1, b:2, c:3};

for (var prop in obj) {
  console.log("obj." + prop + " = " + obj[prop]);
}

// Output:
// "obj.a = 1"
// "obj.b = 2"
// "obj.
```



### 解构赋值

可以将属性/值从对象/数组中取出,赋值给其他变量。

```javascript
//解构数组
	const yh=["鸢一折纸","五河琴里","夜刀神十香"];
    let [one,five,ten]=yh;
    console.log(one);//鸢一折纸
    console.log(five);//五河琴里
    console.log(ten);//夜刀神十香

    console.log(yh[0]);
    console.log(yh[1]);
    console.log(yh[2]);
```

```javascript
//解构对象
	const Sherry={
        name:"宫野志保",
        age:18,
        small:function(){
            console.log("APTX4869");
        }
    };
    let {name,age,small}=Sherry;
    console.log(name);
    console.log(age);
    console.log(small);
    
    small();
    console.log(Sherry.name);
    console.log(Sherry.age);
    console.log(Sherry.small);
    Sherry.small();
```

```javascript
//连续解构赋值
let obj={a:{b:{c:2}}}
const {a:{b:{c}}}=obj//连续解构赋值
const {a:{b:{c:data}}}=obj//连续解构赋值+重命名

console.log(obj.a.b.c)//2
console.log(c)        //2
console.log(data)     //2
```







### arguments对象

- arguments对象是所有（非箭头）函数中都可用的**局部变量**
- 可以使用arguments对象在函数中**引用函数的参数**。

```javascript
function func1(a, b, c) {
  console.log(arguments[0]);
  // expected output: 1

  console.log(arguments[1]);
  // expected output: 2

  console.log(arguments[2]);
  // expected output: 3
}

func1(1, 2, 3);
```



### rest参数(ES6)

```javascript
//rest参数是数组，arguments是对象（只是可以下标访问）
function sumRest (...arg) { //格式：    ...变量
	var total = 0; 
	for(var i of arg){
	    total += i;
	}
	return total;
}
console.log(sumRest(1,2,3));//6
```



### 扩展运算符(ES6)

```javascript
//数组合并
		const yh=["鸢一折纸","五河琴里"]
        const ys=["甘雨","刻晴"]
        const nv=[...yh,...ys]
        console.log(nv);       
```

```javascript
//伪数组转数组
        const divs=document.querySelectorAll("div")
        const divarr=[...divs]
        console.log(divarr);
```



### 对象写法简化(ES6)

```javascript
//ES6允许在{}内直接写入属性与方法，作为对象函数与方法
    var name="宫野志保";
    var age=18;
    const Sherry={
        name,
        age:18,
        small(){
            console.log("APTX4869");
        }
    };
    console.log(Sherry);
```







## 原型与原型链

实例.`__proto__` === 原型 

原型.`constructor` === 构造函数 

构造函数.`prototype` === 原型

- 当原型对象的属性值为基本类型的数据值时，通过实例对象修改属性值从而引起原型对象的属性值发生变化的情况不会发生。
- 当原型对象的属性值为引用类型的数据值时，通过实例对象修改属性值就可能引起原型对象的属性值发生变化

## 闭包

`闭包(Closure)`是有权访问**另一个函数作用域中变量**的**函数**

```markdown
	1）函数嵌套
	2）内部函数使用外部函数的变量
	3）外部函数的返回值为内部函数
```

```js
function f1(){
　　var n=999;
　　nAdd=function(){n+=1}
　　function f2(){
　　　　　alert(n);
　　　　}
　　　　return f2;
　　}

　　var result=f1();
　　result(); // 999
　　nAdd();
　　result(); // 1000
```



#### 立即执行函数

立即执行函数会形成一个单独的作用域，可以封装一些临时变量或者局部变量，避免污染全局变量

小闭包

```javascript
(function(){
    //...
})()
```



## 异步

```js
// 1.事件中回调函数
// 2.定时器中回调函数
// 3.Ajax中回调函数
```

### Ajax

#### **XMLHttpRequest** 

XMLHttpRequest 用于在**后台与服务器交换数据**。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。

```javascript
function Ajax(URL){
  var req = new XMLHttpRequest();
  console.log(req);
  req.open('GET', URL, true);
  req.send()
  req.onload=function(){
    if(req.status === 200) {
      console.log(req.response);
    }
    else{
      console.log(new Error(req.statusText));
    }
  }
}

Ajax("https://api.apiopen.top/getJoke")
```





#### readyState

每当 readyState **改变**时，就会触发 **onreadystatechange** 事件

 **0** － （未初始化）还没有调用send()方法
 **1** － （载入）已调用send()方法，正在发送请求
 **2** － （载入完成）send()方法执行完成，已经接收到全部响应内容
 **3** － （交互）正在解析响应内容
 **4** － （**完成**）响应内容解析完成，可以在客户端调用了

#### status

**200**——"OK"

**404**——未找到页面

















### promise(ES6)

- **Promise** 对象用于表示一个异步操作的最终完成 (或失败)及其结果值。
- 异步方法并不会立即返回最终的值，而是会返回一个 *promise*，以便在未来某个时候把值交给使用者

- 一个 `Promise` 必然处于以下几种状态之一：
  - *待定（pending）*: 初始状态，既没有被兑现，也没有被拒绝
  - *已兑现（fulfilled）*: 意味着操作成功完成
  - *已拒绝（rejected）*: 意味着操作失败



```javascript
var myFirstPromise = new Promise(function(resolve, reject){
    //当异步代码执行成功时，才会调用resolve(...), 当异步代码失败时就会调用reject(...)
    //在本例中，我们使用setTimeout(...)来模拟异步代码，实际编码时可能是XHR请求或是HTML5的一些API方法.
    setTimeout(function(){
        resolve("成功!"); //代码正常执行！
    }, 250);
});
 
myFirstPromise.then(function(successMessage){
    //successMessage的值是上面调用resolve(...)方法传入的值.
    //successMessage参数不一定非要是字符串类型，这里只是举个例子
    document.write("Yay! " + successMessage);
});

```

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

```javascript
// 链式操作
// 因为 Promise.prototype.then 和  Promise.prototype.catch 方法返回的是 promise， 所以它们可以被链式调用。
doSomething().then(function(result) {
  return doSomethingElse(result);
})
.then(function(newResult) {
  return doThirdThing(newResult);
})
.then(function(finalResult) {
  console.log('Got the final result: ' + finalResult);
})
.catch(failureCallback);
// then 里的参数是可选的，catch(failureCallback) 是 then(null, failureCallback) 的缩略形式。

const myPromise =
  (new Promise(myExecutorFunc))
  .then(handleFulfilledA,handleRejectedA)
  .then(handleFulfilledB,handleRejectedB)
  .then(handleFulfilledC,handleRejectedC);

// 或者，这样可能会更好...

const myPromise =
  (new Promise(myExecutorFunc))
  .then(handleFulfilledA)
  .then(handleFulfilledB)
  .then(handleFulfilledC)
  .catch(handleRejectedAny);
```



#### all()

- 接收一个promise的iterable类型
- 只返回一个Promise实例
-  等待所有都完成（或第一个失败）

```js
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3]).then((values) => {
  console.log(values);
});
// expected output: Array [3, 42, "foo"]
```

#### allSettled()

- 接收一个promise的iterable类型
- 只返回一个Promise实例
- 每一个 promise 已经完成，无论是成功的达成或被拒绝

```js
const promise1 = Promise.resolve(3);
const promise2 = new Promise((resolve, reject) => setTimeout(reject, 100, 'foo'));

Promise.allSettled([promise1, promise2]).
  then((results) => results.forEach((result) => console.log(result.status)));

// expected output:
// "fulfilled"
// "rejected"
```



#### any()

- 实验性的
- 接收一个promise的iterable类型
- 第一个成功的 `promise` 

```


```



#### race()

- 接收一个promise的iterable类型
- 返回一个第一个解决或拒绝promise的值

```js
const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, 'one');
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'two');
});

Promise.race([promise1, promise2]).then((value) => {
  console.log(value);
  // Both resolve, but promise2 is faster
});
// expected output: "two"
```





### async/await

async函数是使用`async`关键字声明的函数。 async函数是AsyncFunction构造函数的实例， 并且其中允许使用`await`关键字。

`async`和`await`关键字可以用一种更简洁的方式写出基于Promise的异步行为，而无需刻意地链式调用promise。

`await`  操作符用于等待一个Promise 对象.它只能在异步函数 async function 中使用

await 表达式会暂停当前 `async function` 的执行，等待 Promise 处理完成。若 Promise 正常处理(fulfilled)，其回调的resolve函数参数作为 await 表达式的值，继续执行 `async function`。

若 Promise 处理异常(rejected)，await 表达式会把 Promise 的异常原因抛出。

另外，如果 await 操作符后的表达式的值不是一个 Promise，则返回该值本身。

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



### defer和async

```html
<!-- 在没有defer或者async的情况下：会立即执行脚本,所以通常建议把script放在body最后-->
<script src="script.js"></script>

<!--有async的话,加载和渲染后续文档元素的过程将和 script.js 的加载与执行并行进行（异步）
	但是多个js文件的加载顺序不会按照书写顺序进行-->
<script async src="script.js"></script>

<!--有derer的话,加载后续文档元素的过程将和 script.js 的加载并行进行（异步）
但是 script.js 的执行要在所有元素解析完成之后，DOMContentLoaded 事件触发之前完成,并且多个defer会按照顺序进行加载-->
<script defer src="script.js"></script>
```



## 严格模式

```HTML
<!-- 开启 -->

<!-- 1.为脚本开启 -->
<script>
   'use strict'; 
</script>

<!-- 2.为某函数开启 -->
<script>
    function fn(){
        'use strict';    
    }
</script>
```

```html
<script>
   'use strict'; 
    
    // 1.变量需声明再使用
    num=10;		//×
    var num=10;	//√
    
    // 2.不能随意删除已声明变量
    delete num; //×
    
    // 3.在全局作用域中this指向为undefined(正常为window)
    
    // 4.构造函数要用new(this指向为undefined,无法像正常一样为window添加属性)
    
    // 5.定时器this指向window
    
    // 6.不能有重名函数
    
    // 7.保留一些关键字
    
</script>
```



## this指向

- 在方法中，this 表示该方法所属的**对象**。
- 如果单独使用，this 表示**全局对象**(window)。
- 在函数中，this 表示**全局对象**(window)。
- 在函数中，在严格模式下，this 是未定义的(undefined)。
- 在事件中，this 表示**接收事件的HTML元素**。
- 类似 call() 和 apply() 方法可以将 this 引用到任何对象。

##### call()和apply()

- `call(thisobj,arg1,arg2,arg3,......)`
- `apply(obj,args)`

call()和apply()作用相同只是参数列表不同，apply()用数组传参。

作用：**改变this指向**

传入对象为null时，this指向为window，传入其他对象this则指向传入对象。

```javascript
    var obj1={
        name:"wang"
    };
    var obj2={
        name:"li"
    };
    window.name="chen";
    function getName(){
        console.log(this.name);
    }
    getName();//chen
    getName.call(obj1);//wang
    getName.call(null);//chen
    getName.call(obj2);//li
```

```javascript
    function Person(name,age,sex){
        this.name=name;
        this.age=age;
        this.sex=sex;
    }
    function Student(name,age,sex,grad){
        Person.apply(this,arguments);
        this.grad=grad;
    }
    var std=new Student("wan",20,"女",90);
    console.log("name:"+std.name+" age:"+std.age+" sex:"+std.sex+" grad:"+std.grad);
```

```javascript
    function Person(name,age,sex){
        this.name=name;
        this.age=age;
        this.sex=sex;
    }
    function Student(name,age,sex,grad){
        Person.call(this,name,age,sex);
        this.grad=grad;
    }
    var std=new Student("wan",20,"女",90);
    console.log("name:"+std.name+" age:"+std.age+" sex:"+std.sex+" grad:"+std.grad);
```

```javascript
//Math.max()参数不支持数组，用apply()可实现数组操作
Math.max.apply(null,[13,45,85,99]);
```







## 类(ES6)

```javascript
//类声明(函数声明会提升，类声明不会-需要声明类，然后再访问它)
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

```javascript
//类继承
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name); // 调用超类构造函数并传入name参数
  }

  speak() {//方法重载
    super.speak();//使用 super 调用超类
    console.log(`${this.name} barks.`);
  }
}

var d = new Dog('Mitzie');
d.speak();
```

```javascript
//类合并Object.assign
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }

```

```javascript
//设置原型对象Object.setPrototypeOf
var Animal = {
  speak() {
    console.log(this.name + ' makes a noise.');
  }
};

class Dog {
  constructor(name) {
    this.name = name;
  }
}

Object.setPrototypeOf(Dog.prototype, Animal);// 如果不这样做，在调用speak时会返回TypeError

var d = new Dog('Mitzie');
d.speak(); // Mitzie makes a noise.
```











## 模块化(ES6)

##### 导入

```html
	<script type="module">
        //模块引入 1.通用
        import * as m1 from './m1.js'
        console.log(m1);
    </script>
```

```html
	<script type="module">
        //模块引入 2.结构赋值
		import {hh,name} from './m3.js'
		import {hh as h,name as n} from './m2.js' //重复取别名
		import {default as m1} from './m1.js'     //默认暴露
        console.log(hh);
    </script>
```

```html
	<script type="module">
        //模块引入 3.简便
		import m1 from './m1.js' //针对默认暴露
    </script>
```

##### 导出

```javascript
//分别暴露
export let name="鸢一折纸"
export function hh(){
    console.log(521)
}
```

```javascript
//统一暴露
let name="鸢一折纸"
function hh(){
    console.log(521)
}
export{name,hh}
```

```javascript
//默认暴露
export default{
    name:"鸢一折纸",
    hh:function(){
        console.log(521)
    }
}
```











## proxy

**Proxy** 对象用于创建一个对象的代理，从而实现基本操作的拦截和自定义（如属性查找、赋值、枚举、函数调用等）。

```

```

















# API

文档对象模型



## 元素



### 获取元素

##### getElementById()

```javascript
// getElementById() 
// 可返回对拥有指定 ID 的第一个对象的引用。
// 返回对象 HTMLElement(第一个)
var a=document.getElementById("oo");
```

##### getElementsByTagName()

```javascript
// getElementsByTagName() 
// 可返回带有指定标签名的对象的集合。
// 返回集合 HTMLCollection
var a=document.getElementsByTagName("li");
console.log(a);
console.log(a[1]);//打印第1个

var a=document.getElementById("oo");
var b=a.getElementsByTagName("li");//
console.log(b);
```

##### getElementsByClassName() 

```javascript
// getElementsByClassName() 
// 返回文档中所有指定类名的元素集合
// 返回集合 HTMLCollection 
var a=document.getElementsByClassName("oo");
```

##### querySelector()

```javascript
// querySelector()
// 返回文档中与指定选择器或选择器组匹配的第一个 HTMLElement对象
// 返回对象 HTMLElement(第一个)
var a=document.querySelector(".pp");
```

##### querySelectorAll()

```javascript
// querySelectorAll()
// 返回与指定的选择器组匹配的文档中的元素列表
// 返回集合 NodeList
var a=document.querySelectorAll(".pp")
```

##### body

```javascript
//获取body元素
var bodyEle=document.body;
console.log(bodyEle);
```

##### documentElement

```javascript
//获取html元素
var htmlEle=document.documentElement;
console.log(htmlEle);
```



### 元素操作

##### innerText

```javascript
//innerText可获取或设置指定元素标签内的文本值
//不识别Html标签
//强调空格和换行

document.querySelector("#de1").innerText="<strong>521</strong>"
// <strong>521</strong>
```



##### innerHTML

```javascript
//innerHTML可获取或设置指定元素标签内的 html内容
//识别Html标签
//保留空格和换行

document.querySelector("#de2").innerHTML="<strong>521</strong>"
// 521
```







## 事件

- **事件源** 事件被触发的对象 HTMLElement
- **事件类型** 如何触发 鼠标点击，鼠标经过，键盘按下
- **事件处理程序** 函数赋值

### 事件绑定

```html
<!-- d -->
	<button id="btn1">按钮1</button>
    <script>
        document.getElementById("btn1").onclick=()=>{
            alert(1)
        }
    </script>
```

```html
<!-- 监听器 -->
	<button id="btn2">按钮2</button>
    <script>
        document.getElementById("btn2").addEventListener("click",()=>{
            alert(2)
        })
    </script>
```

```html
<!-- html绑定 -->
	<button onclick="btn3()">按钮3</button>
    <script>
        function btn3(){
            alert(3)
        }
    </script>
```











| 事件     | 事件名(监听器注册事件) | 属性名(节点设置属性) |
| -------- | ---------------------- | -------------------- |
| 点击     | `click`                | `onclick`            |
| 大小变化 | `resize`               | `onresize`           |
|          |                        |                      |
|          |                        |                      |
|          |                        |                      |
|          |                        |                      |
|          |                        |                      |
|          |                        |                      |
|          |                        |                      |



### 事件阻止

#### Event.preventDefault()

- 阻止默认事件

#### Event.stopPropagation()

- 阻止冒泡

#### Event.stopImmediatePropagation()

- 阻止监听同一事件的其他事件监听器被调用



### 冒泡与捕获

#### 冒泡

```jsx
target.addEventListener(type, listener, useCapture);//false(默认)

如果没有指定， useCapture 默认为 false 
```



#### 捕获

```js
target.addEventListener(type, listener, useCapture);//true
当useCapture(设为true) 时，沿着DOM树向上冒泡的事件，不会触发listener
```





## 页面宽高

```javascript
window.innerHeight//页面高度
window.innerWidth//页面宽度
```

```js
// 显示浏览器的屏幕的可用高度，以像素计
screen.availHeight

// 返回窗口中水平方向可用空间的像素值。
screen.availWidth
```





## 定时器

#### setTimeout()

- 执行一次

```javascript
//执行一次
var time1=setTimeout(function(){
	console.log(521);
	console.log(this);//全局对象
},3000)//(函数,延迟毫秒数)

var time2=setTimeout("console.log(521)",3000)

function timex(){
	console.log(521);
}
var time1=setTimeout(timex,3000)
```

```javascript
//停止计时器
clearTimeout(time1)
```



#### setInterval()

- 反复执行

```javascript
//反复执行
var time1=setInterval(function(){
	console.log(521);
},3000)//(函数,延迟毫秒数)
```

```javascript
//停止计时器
clearInterval(time1)
```







## 对话框

##### alert()

```javascript
// Window.alert()
// 弹出提示框

alert("666")
```



##### confirm()

```javascript
// Window.confirm()
// 弹出确定框

result = confirm(message);
// message 是要在对话框中显示的可选字符串。
// result 是一个布尔值，表示是选择确定还是取消 (true表示OK)
```



```js
// window.prompt()
// 弹出输入框

result=prompt(message)
// message 是要在对话框中显示的可选字符串。
// result 是一个字符串，为输入值
```







## 拖拽

- `draggable="true"`

- 拖拽时
  - 开始 `dragstart`
  - 进行中 `drag`
  - 结束 `dragend`
- 进入区域
  - 进入时 `dragenter`
  - 进入后 `dragover`
  - 离开 `dragleave`
  - 放置 `drop`



```html
<div class="dropzone">
  <div id="draggable" draggable="true" ondragstart="event.dataTransfer.setData('text/plain',null)">
    This div is draggable
  </div>
</div>
<div class="dropzone"></div>
<div class="dropzone"></div>
<div class="dropzone"></div>

<style>
  #draggable {
    width: 200px;
    height: 20px;
    text-align: center;
    background: white;
  }

  .dropzone {
    width: 200px;
    height: 20px;
    background: blueviolet;
    margin-bottom: 10px;
    padding: 10px;
  }
</style>

<script>
  var dragged;

  /* 拖动目标元素时触发drag事件 */
  document.addEventListener("drag", function( event ) {

  }, false);

  document.addEventListener("dragstart", function( event ) {
      // 保存拖动元素的引用(ref.)
      dragged = event.target;
      // 使其半透明
      event.target.style.opacity = .5;
  }, false);

  document.addEventListener("dragend", function( event ) {
      // 重置透明度
      event.target.style.opacity = "";
  }, false);

  /* 放置目标元素时触发事件 */
  document.addEventListener("dragover", function( event ) {
      // 阻止默认动作以启用drop
      event.preventDefault();
  }, false);

  document.addEventListener("dragenter", function( event ) {
      // 当可拖动的元素进入可放置的目标时高亮目标节点
      if ( event.target.className == "dropzone" ) {
          event.target.style.background = "purple";
      }

  }, false);

  document.addEventListener("dragleave", function( event ) {
      // 当拖动元素离开可放置目标节点，重置其背景
      if ( event.target.className == "dropzone" ) {
          event.target.style.background = "";
      }

  }, false);

  document.addEventListener("drop", function( event ) {
      // 阻止默认动作（如打开一些元素的链接）
      event.preventDefault();
      // 将拖动的元素到所选择的放置目标节点中
      if ( event.target.className == "dropzone" ) {
          event.target.style.background = "";
          dragged.parentNode.removeChild( dragged );
          event.target.appendChild( dragged );
      }

  }, false);
</script>
```









### FileReader

```html
<input type="file" id="img" name="img_url" >
	<div id="im"></div>
	<script>   
        document.getElementById("img").onchange=function(){
            var file=this.files[0];
            var reader=new FileReader();
            reader.readAsDataURL(file);
            reader.onload=function(e){
                var result=document.getElementById("im")
                result.innerHTML='<img src="'+this.result+'" alt="">'
            }
        }
    </script>
```

























## 浏览器存储

#### localStorage

```markdown
# Window.localStorage
只读的localStorage 属性允许你访问一个Document 源（origin）的对象 Storage；
存储的数据将保存在浏览器会话中

为键值对形式,都是字符串

localStorage 类似 sessionStorage,但其区别在于：存储在 localStorage 的数据可以长期保留；而当页面会话结束——也就是说，当页面被关闭时，存储在 sessionStorage 的数据会被清除 。
```

```markdown
	-F12->Application->Storage->Local Storage
	-F12->应用程序->存储->本地存储
```

```javascript
// 访问了当前域名下的本地 Storage 对象，并通过 Storage.setItem() 增加了一个数据项目。
localStorage.setItem('myCat', 'Tom');

// 用于读取 localStorage 项
let cat = localStorage.getItem('myCat');

// 该语法用于移除 localStorage 项
localStorage.removeItem('myCat');

// 用于移除所有的 localStorage 项
localStorage.clear();
```

#### sessionStorage

```markdown
# Window.sessionStorage
sessionStorage 属性允许访问一个，对应当前源的 session Storage 对象

它与 localStorage 相似，不同之处在于 localStorage 里面存储的数据没有过期时间设置，而存储在 sessionStorage 里面的数据在页面会话结束时会被清除
```

```markdown
	-F12->Application->Storage->Session Storage
	-F12->应用程序->存储->会话存储
```

```javascript
// 保存数据到 sessionStorage
sessionStorage.setItem('key', 'value');

// 从 sessionStorage 获取数据
let data = sessionStorage.getItem('key');

// 从 sessionStorage 删除保存的数据
sessionStorage.removeItem('key');

// 从 sessionStorage 删除所有保存的数据
sessionStorage.clear();
```









# BOM

浏览器对象模型







### 子窗口

- 子窗口通过`window.opener`操作父窗口
- 父窗口通过open()返回的对象操作子窗口

```js
// Window.open()
// let windowObjectReference = window.open(strUrl, strWindowName, [strWindowFeatures]);
// Window 接口的 open() 方法，是用指定的名称将指定的资源加载到浏览器上下文（窗口 window ，内嵌框架 iframe 或者标签 tab ）。如果没有指定名称，则一个新的窗口会被打开并且指定的资源会被加载进这个窗口的浏览器上下文中。

// strUrl: 描述要打开的窗口的URL地址，如何为空则不打开任何网页

// strWindowName:描述被打开的窗口的民称，可以使用'_top'、'_blank'等内建名称，这里的名称跟<a href="..." target="...">里的target属性是一样的

// [strWindowFeatures]:描述被打开的窗口的参数值，或者说是样貌，其包括窗口的各个属性值，及要传入的参数值。

// top=# 窗口顶部离开屏幕顶部的像素数
// left=# 窗口左端离开屏幕左端的像素数
// width=# 窗口的宽度
// height=# 窗口的高度
// menubar=... 窗口有没有菜单，取值yes或no
// toolbar=... 窗口有没有工具条，取值yes或no
// location=... 窗口有没有地址栏，取值yes或no
// directories=... 窗口有没有连接区，取值yes或no
// scrollbars=... 窗口有没有滚动条，取值yes或no
// status=... 窗口有没有状态栏，取值yes或no
// resizable=... 窗口给不给调整大小，取值yes或no
```

```js
// Window.close()
// Window.close() 方法关闭当前窗口或某个指定的窗口。
// 该方法只能由 Window.open() 方法打开的窗口的 window 对象来调用
var openedWindow;

function openWindow() {
  openedWindow = window.open('moreinfo.htm');
}

function closeOpenedWindow() {
  openedWindow.close();
}
```





### location

- `Location` 接口表示其链接到的对象的位置（URL）。所做的修改反映在与之相关的对象上
- Document 和 Window 接口都有这样一个链接的Location，分别通过 Document.location和Window.location 访问。

```js
// Location.assign()
// 加载给定URL的内容资源到这个Location对象所关联的对象上。
```

```js
// Location.replace()
// 用给定的URL替换掉当前的资源
// 与 assign() 方法不同的是用 replace()替换的新页面不会被保存在会话的历史 History中，这意味着用户将不能用后退按钮转到该页面
```

```js
// Location.reload()
// 重新加载来自当前 URL的资源。他有一个特殊的可选参数，类型为 Boolean (en-US)，该参数为true时会导致该方法引发的刷新一定会从服务器上加载数据。如果是 false或没有制定这个参数，浏览器可能从缓存当中加载页面。
```



### history

- `Window.history`是一个只读属性，用来获取`History `对象的引用
- `History` 对象提供了操作浏览器会话历史（浏览器地址栏中访问的页面，以及当前页面中通过框架加载的页面）的接口

```js
// History.back()
// 在浏览器历史记录里前往上一页, 用户可点击浏览器左上角的返回(←)按钮模拟此方法. 
// 等价于 history.go(-1).
```

```js
// History.forward()
// 在浏览器历史记录里前往下一页，用户可点击浏览器左上角的前进(→)按钮模拟此方法. 
// 等价于 history.go(1)
```

```js
// History.go()
// 通过当前页面的相对位置从浏览器历史记录( 会话记录 )加载页面
// 参数为-1的时候为上一页，参数为1的时候为下一页
// 当整数参数超出界限时( 译者注:原文为When integerDelta is out of bounds )，例如: 如果当前页为第一页，前面已经没有页面了，我传参的值为-1，那么这个方法没有任何效果也不会报错。调用没有参数的 go() 方法或者参数值为0时，重新载入当前页面。( 这点与支持字符串作为url参数的IE有点不同)。
```



### cookie

```js
// 读取所有可从此位置访问的Cookie
allCookies = document.cookie;
```

```js
// 写一个新 cookie
document.cookie = newCookie;

// newCookie是一个键值对形式的字符串。需要注意的是，用这个方法一次只能对一个cookie进行设置或更新

// 以下可选的cookie属性值可以跟在键值对后，用来具体化对cookie的设定/更新，使用分号以作分隔：
// ;path=path (例如 '/', '/mydir') 如果没有定义，默认为当前文档位置的路径

// ;domain=domain (例如 'example.com'， 'subdomain.example.com') 如果没有定义，默认为当前文档位置的路径的域名部分。与早期规范相反的是，在域名前面加 . 符将会被忽视，因为浏览器也许会拒绝设置这样的cookie。如果指定了一个域，那么子域也包含在内

// ;max-age=max-age-in-seconds (例如一年为60*60*24*365)

// ;expires=date-in-GMTString-format 如果没有定义，cookie会在对话结束时过期
// 这个值的格式参见Date.toUTCString() 

// ;secure (cookie只通过https协议传输)


// cookie的值字符串可以用encodeURIComponent()来保证它不包含任何逗号、分号或空格(cookie值中禁止使用这些值).
```



### Navigator

- `Navigator` 接口表示用户代理的状态和标识。 它允许脚本查询它和注册自己进行一些活动。
- 可以使用只读的 `window.navigator`

```js
// 以 DOMString 的形式返回浏览器官方名称。 不能保证此属性返回的值是正确的
navigator.appName

// 以 DOMString 的形式返回浏览器版本。不能保证此属性返回的值是正确的
navigator.appVersion

// 当忽略 cookie 时返回 false，否则返回 true
navigator.cookieEnabled

// 返回DOMString表示用户的首先语言，通常是浏览器用户界面的语言。当未知的时，返回null
navigator.language

// 返回当前浏览器的用户代理。
navigator.userAgent

// 返回浏览器平台名，不确定此值是否有效
navigator.platform
```







```cython

```





# 移动端

## 判断

#### navigator.userAgent

- 分析浏览器的 user agent 字符串，它包含了设备信息

- ```js
  if (/Mobi|Android|iPhone/i.test(navigator.userAgent)) {
    // 当前设备是移动设备
  }
  ```

  

#### window.screen，window.innerWidth

- 通过屏幕宽度，判断是否为手机

- ```js
  if (window.screen.width < 500) {
    // 当前设备是移动设备 
  }
  ```



#### window.orientation

- 侦测屏幕方向，手机屏幕可以随时改变方向（横屏或竖屏），桌面设备做不到

- ```js
  if (typeof window.orientation !== 'undefined') {
    // 当前设备是移动设备 
  }
  ```

- iPhone 的 Safari 浏览器不支持该属性



#### touch 事件

- 手机浏览器的 DOM 元素可以通过`ontouchstart`属性，为`touch`事件指定监听函数。桌面设备没有这个属性

- ```js
  function isMobile() { 
    return ('ontouchstart' in document.documentElement); 
  }
  ```









# 正则



```javascript
// 创建正则表达式
 
	// RegExp对象构造函数
	var re = new RegExp("ab+c");

	// 字面量
	var re = /ab+c/;


```

```ji
	var re=/abc/
	ll='sas'
        console.log(re.test("asdasd"));
        console.log(re.test(ll));
```



