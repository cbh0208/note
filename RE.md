# 元字符

## 断言

- 表示一个匹配在某些条件下发生。断言包含先行断言、后行断言和条件表达式。





### `^`

- 匹配输入的**开头**(在[]内为取反)

- `^A` 匹配不了 "an A" 里面的 "A"，但是可以匹配 "An A" 里面第一个 "A"

  ```python
  >>>import re
  >>>re.search('^A',"an A")
  None
  >>>re.search('^A',"An A")
  <re.Match object; span=(0, 1), match='A'>
  ```

  



### `$`

- 匹配输入的**结束**

- `t$` 不能匹配 "eater" 中的 "t"，但是可以匹配 "eat" 中的 "t"

  ```python
  >>>import re
  >>>re.search('t$',"eater")
  None
  >>>re.search('t$',"eat")
  <re.Match object; span=(2, 3), match='t'>
  ```

  

### `\b`

- 匹配单词头或单词尾

- `\b`是转义符(退格)

- `[\b]`匹配一个退格

- `r'\bfoo\b'` 匹配 'foo', 'foo.', '(foo)', 'bar foo baz' 但不匹配 'foobar' 或者 'foo3'

  ```python
  >>>import re
  >>>re.findall(r'\bfoo\b','foo')
  ['foo'] 
  >>>re.findall(r'\bfoo\b','foo.')
  ['foo'] 
  >>>re.findall(r'\bfoo\b','(foo)')
  ['foo'] 
  >>>re.findall(r'\bfoo\b','bar foo baz')
  ['foo'] 
  >>>re.findall(r'\bfoo\b','foobar')
  [] 
  >>>re.findall(r'\bfoo\b','foo3')
  []
  ```

  



### `\B`

- 匹配一个非单词边界

- 与`\b`含义相反

- `\B..`匹配"noonday"中的'oo', 而`y\B..`匹配"possibly yesterday"中的’yes‘

  ```python
  >>>import re
  >>>re.search('\B..','noonday')
  <re.Match object; span=(1, 3), match='oo'>
  >>>re.search('y\B..','possibly yesterday')       
  <re.Match object; span=(9, 12), match='yes'>
  ```

  



### `(?=...)`

- 用于正则表达式之后,表示如果=后的内容在字符串中**出现**则匹配,但不返回=之后的内容



### `(?!...)`

- 用于正则表达式之后,表示如果!后的内容在字符串中**不出现**则匹配,但不返回!之后的内容



### `(?<=...)`

- 用于正则表达式之前,与`(?=...)`含义相同



### `(?<!...)`

- 用于正则表达式之前,与(?!...)含义相同



| `字符`   | `含义`                                                       |
| :------- | :----------------------------------------------------------- |
| `x(?=y)` | **向前断言:** x 被 y 跟随时匹配 x。例如，对于/`Jack(?=Sprat)`/，“Jack”在跟有“Sprat”的情况下才会得到匹配．`/Jack(?=Sprat|Frost)/` “Jack”后跟有“Sprat”或“Frost”的情况下才会得到匹配。不过， 匹配结果不包括“Sprat”或“Frost”。 |
| x(?!y)   | **向前否定断言:** x 没有被 y 紧随时匹配 x。例如，对于`/\d+(?!\.)/`，数字后没有跟随小数点的情况下才会得到匹配。对于`/\d+(?!\.)/.exec(3.141)`，匹配‘141’而不是‘3’。 |
| (?<=y)x  | **向后断言:** x 跟随 y 的情况下匹配 x。例如，对于`/(?<=Jack)Sprat/`，“Sprat”紧随“Jack”时才会得到匹配。对于`/(?<=Jack|Tom)Sprat`，“Sprat”在紧随“Jack”或“Tom”的情况下才会得到匹配。不过，匹配结果中不包括“Jack”或“Tom”。 |
| (?<!y)x  | **向后否定断言:** x 不跟随 y 时匹配 x。例如，对于`/(?<!-)\d+/`，数字不紧随-符号的情况下才会得到匹配。对于`/(?<!-)\d+/.exec(3)` ，“3”得到匹配。 而`/(?<!-)\d+/.exec(-3)`的结果无匹配，这是由于数字之前有-符号。 |




## 字符类

- 字符类（`Character Classes`）区分不同类型的字符，例如区分字母和数字。






### `.`

- 匹配除**行终止符**(`\n`, `\r`, `\u2028` or `\u2029`)之外的**任何单个字符** 

- `[.]`中匹配.

- `\.`匹配.

- 例如, `.y` 在“yes make my day”中匹配“my”和“ay”，而不是“yes”

  ```python
  >>>import re
  >>>re.findall('.y',"yes make my day")
  ['my', 'ay']
  ```



### `\d`

- 匹配一个**数字**

- 等价于**[0-9]**

- 例如， `\d` 或者 `[0-9]` 匹配"B2 is the suite number."中的'2'

  ```python
  >>>import re
  >>>re.search('\d',"B2 is the suite number.")
  <re.Match object; span=(1, 2), match='2'>
  >>>re.findall('\d',"B2 is the suite number.")
  ['2']
  ```

  

### `\D`

- 匹配一个**非数字字符**

- 等价于**[^0-9]**

- 例如， `\D `或者 `[^0-9]` 匹配"B2 is the suite number."中的'B' 。

  ```python
  >>>import re
  >>>re.search('\D',"B2 is the suite number.")
  <re.Match object; span=(0, 1), match='B'>
  ```



### `\s`

- 匹配任何**空白字符**

- 等价于 `[ \t\n\r\f\v]`

- `\s\w*` (空格之后数个单字字符)匹配"foo bar."中的' bar'

  ```python
  >>>import re
  >>>re.search('\s\w*',"foo bar.")
  <re.Match object; span=(3, 7), match=' bar'>
  ```

  



### `\S`

- 匹配任何**非空白字符**

- 相当于 `[^ \t\n\r\f\v]`

- `\S\w*` 匹配"foo bar."中的'foo'

  ```python
  >>>import re
  >>>re.search('\s\w*',"foo bar.")
  <re.Match object; span=(0, 3), match='foo'>
  ```

  





### `\w`

- 匹配一个**单字字符**（**字母、数字或者下划线**）

- 等价于 **[A-Za-z0-9_]**

- 例如, `\w` 匹配 "apple," 中的 'a'，"$5.28,"中的 '5' 和 "3D." 中的 '3'

  ```python
  >>>import re
  >>>re.search('\w',"apple,")
  <re.Match object; span=(0, 1), match='a'>
  >>>re.search('\w',"$5.28,")
  <re.Match object; span=(1, 2), match='5'>
  >>>re.search('\w',"3D.")
  <re.Match object; span=(0, 1), match='3'>
  ```

  



### `\W`

- 匹配一个**非单字字符**

- 等价于 **[^A-Za-z0-9_]**

- 例如, `\W `或者 `[^A-Za-z0-9_]` 匹配 "50%." 中的 '%'

  ```python
  >>>import re
  >>>re.search('\W',"50%.")
  <re.Match object; span=(2, 3), match='%'>
  ```





### `\f`

- **换页符**匹配



### `\n`

- **换行符**匹配



### `\r`

- 匹配一个**回车符**







## 组和范围

- 组和范围（`Groups and Ranges`）表示表达式字符的分组和范围。



### `|`

- 匹配|之前或之后的字符串

- 例如，`green|red`匹配“green apple”中的‘green’和“red apple”中的‘red’

  ```python
  >>>import re
  >>>re.search('green|red',"green apple")
  <re.Match object; span=(0, 5), match='green'>
  >>>re.search('green|red',"red apple")
  <re.Match object; span=(0, 3), match='red'>
  ```




### `-`

- 用在`[]`中表示范围



### `[]`

- 匹配位于[]中的任意一个字符
- `[^xyz]`反向字符集,匹配除x,y,z的任意字符
- `[a-z]`字符范围,匹配指定范围内的任意字符
- `[^a-z]`反向字符范围,匹配除小写英文字母之外的任何字符







### `()`

- 将位于`()`内的内容作为一个整体来对待



### `(?:...)`

- 匹配但是不捕捉该匹配的子表达式



### `(?P<name>...)`

- 为子模式命名



### `(?P=name)`

- 表示在此之前的命名为name的子模式




## 量词

- 量词（`Quantifiers`）表示匹配的字符或表达式的数量





#### `*`

- 匹配位于*之前的字符或子模式的**0次或多次**出现

- 等价于 **{0,}**

- `bo*` 会匹配 "A ghost boooooed" 中的 'booooo' 和 "A bird warbled" 中的 'b'，但是在 "A goat grunted" 中不会匹配任何内容

  ```python
  >>>import re
  >>>re.search('bo*',"A ghost boooooed")
  <re.Match object; span=(8, 14), match='booooo'>
  >>>re.search('bo*',"A bird warbled")
  <re.Match object; span=(2, 3), match='b'>
  >>>re.search('bo*',"A goat grunted")
  None
  ```

  



#### `+`

- 匹配位于+之前的字符或子模式的**1次或多次**出现

- 等价于 **{1,}**

- `a+` 会匹配 "candy" 中的 'a' 和 "caaaaaaandy" 中所有的 'a'，但是在 "cndy" 中不会匹配任何内容

  ```python
  >>>import re
  >>>re.search('a+',"a")
  <re.Match object; span=(0, 1), match='a'> 
  >>>re.search('a+',"caaaaaaandy")
  <re.Match object; span=(1, 8), match='aaaaaaa'> 
  >>>re.search('a+',"cndy")
  None
  ```

  

#### `?`

- 匹配位于'?'之前的**0个或1个字符**

- 等价于 **{0,1}**

- 例如，`e?le?` 匹配 "angel" 中的 'el'、"angle" 中的 'le' 以及 "oslo' 中的 'l'

  ```python
  >>>import re
  >>>re.search('e?le?',"angel")
  <re.Match object; span=(3, 5), match='el'> 
  >>>re.search('e?le?',"angle")
  <re.Match object; span=(3, 5), match='le'> 
  >>>re.search('e?le?',"oslo")
  <re.Match object; span=(2, 3), match='l'>
  ```

- 如果紧跟在任何量词 *、 +、? 或 {} 的后面，将会使量词变为**非贪婪**（匹配尽量少的字符），和缺省使用的**贪婪**模式（匹配尽可能多的字符）正好相反

- 例如，对 "123abc" 使用 `\d+`/将会匹配 "123"，而使用 `\d+?` 则只会匹配到 "1"

  ```python
  >>>import re
  >>>re.search('\d+',"123abc")
  <re.Match object; span=(0, 3), match='123'> 
  >>>re.search('\d+?',"123abc")
  <re.Match object; span=(0, 1), match='1'>
  ```

  





#### `{}`

- 按{}中的次数进行匹配

- `{n}`与前一项**n次匹配**

  `a{2} `不匹配“candy”中的“a”，但它匹配“caandy”中的所有“a”，以及“caaandy”中的前两个“a”

  ```python
  >>>import re
  >>>re.search('a{2}',"candy")
  None
  >>>re.search('a{2}',"caandy")
  <re.Match object; span=(1, 3), match='aa'> 
  >>>re.search('a{2}',"caaandy")
  <re.Match object; span=(1, 3), match='aa'>
  ```

- `{n,}`与前一项**至少匹配“n”次**

  `a{2，}`不匹配“candy”中的“a”，但匹配“caandy”和“caaaaaaandy”中的所有a

  ```python
  >>>import re
  >>>re.search('a{2,}',"candy")
  None 
  >>>re.search('a{2,}',"caaaaaaandy")
  <re.Match object; span=(1, 8), match='aaaaaaa'>
  ```

- `{n,m}`匹配前面的字符**至少n次，最多m次**。如果 n 或者 m 的值是0， 这个值被忽略

  `a{1,3}`不匹配“cndy”中的“a”，“candy”中的“a”，“caandy”中的两个“a”，以及“caaaaaaandy”中的前三个“a”。注意，当匹配“caaaaaaandy”时，匹配的是“aaa”，即使原始字符串中有更多的“a”。

  ```python
  >>>import re
  >>>re.search('a{1,3}',"cndy")
  None 
  >>>re.search('a{1,3}',"candy")
  <re.Match object; span=(1, 2), match='a'> 
  >>>re.search('a{1,3}',"caaaaaaandy")
  <re.Match object; span=(1, 4), match='aaa'>
  ```

  





```

```



## Unicode 属性转义

Unicode 属性转义（`Unicode Property Escapes`）基于 unicode 字符属性区分字符。例如大写和小写字母、数学符号和标点。







```js
const reg=/(^\d{15}$)|()/

const reg=/[0-9]/

const reg=/^[a-z]+$/i
```

(?i) 表示所在位置右侧的表达式开启忽略大小写模式
(?s) 表示所在位置右侧的表达式开启单行模式
(?m) 表示所在位置右侧的表示式开启指定多行模式
(?is) 更改句点字符 (.) 的含义，以使它与每个字符（而不是除 \n 之外的所有字符）匹配
(?im) 更改 ^ 和 $ 的含义，以使它们分别与任何行的开头和结尾匹配,而不只是与整个字符串的开头和结尾匹配

注意：(?s)通常在匹配有换行的文本时使用
注意：(?m)只有在正则表达式中涉及到多行的“^”和“$”的匹配时，才使用Multiline模式,上面的匹配模式可以组合使用，比如(?is),(?im)
另外，还可以用(?i:exp)或者(?i)exp(?-i)来指定匹配的有效范围

# 常用正则



- ```js
  const ipv4reg = /^([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])(\.([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])){3}$/;
  ```

  ```js
  const ipv6reg = /^[0-9a-fA-F]{1,4}(\:[0-9a-fA-F]{1,4}){7}$/;
  ```

  
