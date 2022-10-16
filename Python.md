```python
print("Hello, World!")
```

# 基础

## 基本语法

### 标识符

- 第一个字符必须是字母表中字母或下划线 `_`。
- 标识符的其他的部分由字母、数字和下划线组成。
- 标识符对大小写敏感。

在 Python 3 中，可以用中文作为变量名，非 ASCII 标识符也是允许的了。

### 关键字

```python
import keyword
print(keyword.kwlist)

['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

### 注释

python中单行注释采用 `#` 开头。

python 中多行注释使用三个单引号(`'''`)或三个双引号(`"""`)。()

```python
#单行注释

'''
多行注释
'''
```



### 行和缩进

学习 Python 与其他语言最大的区别就是，Python 的代码块不使用大括号 `{}` 来控制类，函数以及其他逻辑判断。python 最具特色的就是用缩进来写模块。

缩进的空白数量是可变的，但是所有代码块语句必须包含相同的缩进空白数量，这个必须严格执行。

### 多行语句

Python语句中一般以新行作为语句的结束符。

但是可以使用斜杠（ \）将一行的语句分为多行显示，如下：

```python
total = item_one + \
        item_two + \
        item_three
```

语句中包含 [], {} 或 () 括号就不需要使用多行连接符。如下：

```python
days = ['Monday', 'Tuesday', 'Wednesday',
        'Thursday', 'Friday']
```



### 引号

Python 可以使用引号( **'** )、双引号( **"** )、三引号( **'''** 或 **"""** ) 来表示字符串，引号的开始与结束必须是相同类型的。

其中三引号可以由多行组成，编写多行文本的快捷语法，常用于文档字符串，**在文件的特定地点，被当做注释**。

```python
word = 'word'
sentence = "这是一个句子。"
paragraph = """这是一个段落。
包含了多个语句"""
```



### 空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

**记住：**空行也是程序代码的一部分。





### 赋值

```python
a=1
b=2

# 可同时对多个变量赋值
a,b='鸢一折纸','五河琴里'
a,b=b,a   #可用于变量数据交换
```



## `数据类型`

Python3 的六个标准数据类型中：

- 不可变数据 （3 个）：Number（数字）、String（字符串）、Tuple（元组）；
- 可变数据（3 个）：List（列表）、Dictionary（字典）、Set（集合）。

### 数字(number)

python中数字有四种类型：整数、布尔型、浮点数和复数。

- **int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。
- **bool** (布尔), 如 True。
- **float** (浮点数), 如 1.23、3E-2
- **complex** (复数), 如 1 + 2j、 1.1 + 2.2j

```python
# 创建
a=1
print(type(a))	# <class 'int'>

b=True
print(type(b))	# <class 'bool'>

c=1.5
print(type(c))	# <class 'float'>

d=1+2j
print(type(d))	# <class 'complex'>
```

```python
# 删除
del a,b
```

```python
# 自动类型转换
# 向更高精度(bool=>int=>float=>complex)

print(True+666)				# 6
print(type(True+666)) 		# <class 'int'>

print(666+6.18)				# 672.18
print(type(666+6.18))		# <class 'float'>

print(6.18+(3+4j))			# (9.18+4j)
print(type(6.18+(3+4j)))	# <class 'complex'>
```



### 字符串(str)

- python中单引号和双引号使用完全相同。

- 使用三引号('''或""")可以指定一个多行字符串。

- 转义符 '\'

- 反斜杠可以用来转义，使用r可以让反斜杠不发生转义。。 如 r"this is a line with \n" 则\n会显示，并不是换行。

- 按字面意义级联字符串，如"this " "is " "string"会被自动转换为this is string。

- 字符串可以用 + 运算符连接在一起，用 * 运算符重复。

- Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始。

- Python中的字符串不能改变。

- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。

- 字符串的截取的语法格式如下：**变量[头下标:尾下标:步长]**


  ```python
  # 创建
  a='hello world'
  b="hello world"
  c='''hello world'''
  
  print(type(a))  # <class 'str'>
  
  print(len(a))  	# 11           
  ```

  ```python
# 删除
a='hello world'
del a
  ```

```python
# 索引
a='hello world'
print(a[0])		# h  正向取  0  1  2  3 ……
print(a[-1])	# d  反向取 …… -4 -3 -2 -1
```

```python
# 切片 [起始值:终止值[:步长]]		[左闭右开)
a='hello world'
print(a[0:5])	# hello
print(a[0:])	# hello world
print(a[:])	# hello world
print(a[0:-1])	# hello worl

print(a[0:5:1])	# hello
print(a[0:5:2])	# hlo
```

```python
# 成员运算 in     not in
print('hello' in 'hello world')  
```

  ```python
# 字符串拼接	+
a='五河琴里'
print('鸢一折纸|'+a+'|夜刀神十香')			# 鸢一折纸|五河琴里|夜刀神十香
print(f'鸢一折纸|{a}|夜刀神十香')			# 鸢一折纸|五河琴里|夜刀神十香
print('鸢一折纸|{}|夜刀神十香'.format(a))	# 鸢一折纸|五河琴里|夜刀神十香
  ```

```python
# 字符串重复	*
print('1'*5)  # '11111'
```



#### 转义符

```python
# \n	表示换行，
print('方法\n')
# 鸢一    
# 折纸-

# \t	表示制表符
print('鸢一\t折纸')
# 鸢一    折纸

# \r	截断之后,替换开头
print('5鸢一\r折纸')
# 折纸一         (5鸢一h)

# \b	表示退格符(前删一个字符)
print('abcd\bef')
# abcef 

# \\	表示\

# 前加r不转义
print(r'鸢一\t折纸')
# 鸢一\t折纸
```



#### 占位符

| 占位符 | 替换内容     |
| :----- | :----------- |
| %d     | 整数         |
| %f     | 浮点数       |
| %s     | 字符串       |
| %c     | 字符(ASCII)  |
| %x     | 十六进制整数 |

```python
c='You'
print('I love %s'%a)

print('%m.nf'%3.14)
# 域宽为m,n位小数
# -代表左对齐
```

#### 前置符

```python
# b
# 字符串为byte类型
a=666
print(type(b'{a}==666')) 	# <class 'bytes'>

# r
# 忽略转义符
print('鸢一\t折纸')		# 鸢一    折纸
print(r'鸢一\t折纸')	# 鸢一\t折纸



# u
# 字符串用Unicode编码

# f
# 支持{}内表达式
d=666
print('{d}==666')		# {a}==666
print(f'{d}==666')		# 666==666
```



#### 格式化

- 占位符

  ```python
  a=8888
  b='192.168.1.100'
  c='Web Server Info :'
  print("%s%s:%d"%(c,b,a))
  #Web Server Info :192.168.1.100:8888
  ```

- format()

  ```python
  a=8888
  b='192.168.1.100'
  c='Web Server Info :'
  print("{server}{1}:{0}".format(a,b,server=c))
  #Web Server Info :192.168.1.100:8888　
  ```

- 前置符f

  ```python
  a=8888
  b='192.168.1.100'
  c='Web Server Info :'
  print(f"{c}{b}:{a}")
  #Web Server Info :192.168.1.100:8888　
  ```

  



#### 填充对齐

```python
{:填充符(默认空格) 对齐符 字符宽度}
```

- `^`	 居中
- `<`     左对齐
- `>`     右对齐

![](https://images2018.cnblogs.com/blog/1300369/201804/1300369-20180416230047090-1417876788.png)

```python
print("{0}*{1}={2:0>2}".format(3,2,2*3))  
#3*2=06
 
print("{:*^30}".format('centered'))
#***********centered***********　
```





#### 方法:大小写

  ```python
str.upper()
# 全部变大写

a='abC'
print(a.upper()) # ABC
  ```

```python
str.lower()
# 全部变小写

A='ABc'
print(A.lower()) # abc
```

```python
str.capitalize()
# 首字母大写

b='home'
print(b.capitalize()) 	# Home
```

```python
str.title()
# 返回原字符串的标题版本，其中每个单词第一个字母为大写，其余字母为小写

>>> 'Hello world'.title()
'Hello World'
```

```python
str.swapcase()
# 返回原字符串的副本，其中大写字符转换为小写，反之亦然。 
# 请注意 s.swapcase().swapcase() == s 并不一定为真值。
```



#### 方法:操作

```python
str.split(sep=None, maxsplit=-1)
# 返回一个由字符串内单词组成的列表，使用 sep 作为分隔字符串
# 如果给出了 maxsplit，则最多进行 maxsplit 次拆分（因此，列表最多会有 maxsplit+1 个元素）
# 如果 maxsplit 未指定或为 -1，则不限制拆分次数（进行所有可能的拆分）。
# 如果给出了 sep，则连续的分隔符不会被组合在一起而是被视为分隔空字符串
# sep 参数可能由多个字符组成 
# 使用指定的分隔符拆分空字符串将返回 ['']。

a='鸢一折纸 五河琴里 夜刀神十香'
print(a.split()) #['鸢一折纸', '五河琴里', '夜刀神十香']

a='鸢一折纸*五河琴里*夜刀神十香'
print(a.split('*'))#['鸢一折纸', '五河琴里', '夜刀神十香']

a='root:123456'
print(a.split(':')[1])  # 123456
```

```python
str.rsplit(sep=None, maxsplit=-1)
# 返回一个由字符串内单词组成的列表，使用 sep 作为分隔字符串
# 如果给出了 maxsplit，则最多进行 maxsplit 次拆分，从 最右边 开始
# 如果 sep 未指定或为 None，任何空白字符串都会被作为分隔符
# 除了从右边开始拆分，rsplit() 的其他行为都类似于 split()。
```



```python
str.join(iterable)
# 返回一个由 iterable 中的字符串拼接而成的字符串
# 如果 iterable 中存在任何非字符串值包括 bytes 对象则会引发 TypeError
# 调用该方法的字符串将作为元素之间的分隔

print(':'.join(['鸢一折纸','五河琴里','夜刀神十香']))	# 鸢一折纸:五河琴里:夜刀神十香

```



```python
str.strip([chars])
# 返回原字符串的副本，移除其中的前导和末尾字符
# chars 参数为指定要移除字符的字符串。 如果省略或为 None，则 chars 参数默认移除空白符
# 实际上 chars 参数并非指定单个前缀或后缀；而是会移除参数值的所有组合:

>>> '   spacious   '.strip()
'spacious'
>>> 'www.example.com'.strip('cmowz.')
'example'
```

```python
str.rstrip([chars])
# 返回原字符串的副本，移除其中的末尾字符
# chars 参数为指定要移除字符的字符串
# 如果省略或为 None，则 chars 参数默认移除空白符
# 实际上 chars 参数并非指定单个后缀；而是会移除参数值的所有组合:

>>> '   spacious   '.rstrip()
'   spacious'

>>> 'mississippi'.rstrip('ipz')
'mississ'
```

```python
str.lstrip([chars])
# 返回原字符串的副本，移除其中的前导字符
# chars 参数为指定要移除字符的字符串
# 如果省略或为 None，则 chars 参数默认移除空白符
# 实际上 chars 参数并非指定单个前缀；而是会移除参数值的所有组合

>>> '   spacious   '.lstrip()
'spacious   '
>>> 'www.example.com'.lstrip('cmowz.')
'example.com'
```



```python
# str.replace(old, new[, count])
# 返回字符串的副本，其中出现的所有子字符串 old 都将被替换为 new
# 如果给出了可选参数 count，则只替换前 count 次出现。
```



```python
# str.center(width[, fillchar])
# 返回长度为 width 的字符串，原字符串在其正中
# 使用指定的 fillchar 填充两边的空位（默认使用 ASCII 空格符）
# 如果 width 小于等于 len(s) 则返回原字符串的副本。
```

```python
# str.ljust(width[, fillchar])
# 返回长度为 width 的字符串，原字符串在其中靠左对齐
# 使用指定的 fillchar 填充空位 (默认使用 ASCII 空格符)
# 如果 width 小于等于 len(s) 则返回原字符串的副本。
```

```python
str.rjust(width[, fillchar])
# 返回长度为 width 的字符串，原字符串在其中靠右对齐
# 使用指定的 fillchar 填充空位 (默认使用 ASCII 空格符)
# 如果 width 小于等于 len(s) 则返回原字符串的副本。
```



#### 方法:查找

```python
str.find(sub[, start[, end]])
# 返回子字符串 sub 在 s[start:end] 切片内被找到的最小索引
# 可选参数 start 与 end 会被解读为切片表示法
# 如果 sub 未被找到则返回 -1。

a='hello world'
print(a.find('or')) 	#7
print(a.find('o')) 		#4
print(a.find('o',5,8))	#7   (在[5:8]的切片中寻找)
```

```python
str.rfind(sub[, start[, end]])
# 返回子字符串 sub 在字符串内被找到的最大（最右）索引，这样 sub 将包含在 s[start:end] 当中
# 可选参数 start 与 end 会被解读为切片表示法
# 如果未找到则返回 -1。
```



```python
str.index(sub[, start[, end]])
# 与find()类似 找不到报错ValueError

a='hello world'
print(a.index('or')) #7
```

```python
str.rindex(sub[, start[, end]])
# 类似于 rfind()，但在子字符串 sub 未找到时会引发 ValueError。
```



```python
str.count(sub[, start[, end]])
# 返回子字符串 sub 在 [start, end] 范围内非重叠出现的次数
# 可选参数 start 与 end 会被解读为切片表示法

a='hello world'
print(a.count("o")) #2
```



#### 方法:转换

```python
str.maketrans(x[, y[, z]])
# 此静态方法返回一个可供 str.translate() 使用的转换对照表

```

```python
str.translate(table)
# 返回原字符串的副本，其中每个字符按给定的转换表进行映射
# 转换表必须是一个使用 __getitem__() 来实现索引操作的对象，通常为 mapping 或 sequence
# 当以 Unicode 码位序号（整数）为索引时，转换表对象可以做以下任何一种操作：返回 Unicode 序号或字符串，将字符映射为一个或多个字符；返回 None，将字符从结果字符串中删除；或引发 LookupError 异常，将字符映射为其自身。
```



#### 方法:内容检测

```python
str.isdigit()
# 判断是否为数字

a='hello world'
print(a.isdigit()) #False
b='666'
print(b.isdigit()) #True
```

```python
# str.isalpha()
# 如果字符串中的所有字符都是字母，并且至少有一个字符，返回 True ，否则返回 False 。


print('hello world'.isalpha()) # False
print('abc'.isalpha()) #True
print('鸢一折纸'.isalpha())		# True
```

```python
str.isalnum()
# 如果字符串中的所有字符都是字母或数字且至少有一个字符，则返回 True ， 否则返回 False 。 
# 如果 c.isalpha() ， c.isdecimal() ， c.isdigit() ，或 c.isnumeric() 之中有一个返回 True ，则字符``c``是字母或数字。
```

```python
str.isspace()
# 如果字符串中只有空白字符且至少有一个字符则返回 True ，否则返回 False 。
```



```python
str.endswith(suffix[, start[, end]])
# 如果字符串以指定的 suffix 结束返回 True，否则返回 False
# suffix 也可以为由多个供查找的后缀构成的元组
# 如果有可选项 start，将从所指定位置开始检查
# 如果有可选项 end，将在所指定位置停止比较。

a='hello world'
print(a.endswith("rld")) #True
```

```python
str.startswith(prefix[, start[, end]])
# 如果字符串以指定的 prefix 开始则返回 True，否则返回 False 
# prefix 也可以为由多个供查找的前缀构成的元组
# 如果有可选项 start，将从所指定位置开始检查
# 如果有可选项 end，将在所指定位置停止比较

a='hello world'
print(a.startswith('hel')) #True
```



```python
str.islower()
# 判断字符串是否都是小写

a='abc'
print(a.islower()) # True
```

```python
str.isupper()
# 判断字符串是否都是大写
a='ABC'
print(a.isupper())  #True
```

```python
str.istitle()
# 如果字符串中至少有一个字符且为标题字符串则返回 True ，例如大写字符之后只能带非大写字符而小写字符必须有大写字符打头。 否则返回 False 。
```



#### 类型转换

```python
# list()
# 字符串转为列表

DATE = '鸢一折纸'
a=list(DATE)	
print(a)		# ['鸢', '一', '折', '纸']
print(type(a))  # <class 'list'>
```

```python
# tuple()
# 字符串生成对应元组(拆开)

DATE = '鸢一折纸'
a=tuple(DATE)
print(a)		# ('鸢', '一', '折', '纸')
print(type(a)) 	# <class 'tuple'>
```

```python
# set()
# 字符串生成对应集合(拆开)(无序)

DATE = '鸢一折纸'
a=set(DATE)
print(a)		# {'鸢', '纸', '折', '一'}
print(type(a)) 	# <class 'set'>
```







### 列表(list)

  ```python
# 创建	用[]  或 list()

list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5 ]
list3 = ["a", "b", "c", "d"]

print(type(list1)) 	# <class 'list'>

print(len(list1)) 	#4
  ```

```python
# 删除

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
del DATE  		#
del DATE[0:1] 	#指定删除
DATE.remove('鸢一折纸')
```

```python
# 索引
# 可修改

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
print(DATE[1]) # 五河琴里
DATE[1]='555' 
```

```python
# 切片
# 终止值对应元素不取 

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
print(DATE[0:2]) 	# ['鸢一折纸', '五河琴里']
print(DATE[0:2:2])	#['鸢一折纸']

# 可赋值
a=['a','b','c','d','e','f','g']
a[2:4]=[1]
print(a)	# ['a', 'b', 1, 'e', 'f', 'g']

# 设置步长赋值时要一一对应
b=['a','b','c','d','e','f','g']
b[2:6:2]=[1,2]
print(b)	# ['a', 'b', 1, 'd', 2, 'f', 'g']

```
```python
# 成员运算 in    not in

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
print('鸢一折纸' in DATE) #True
```
```python
# 列表拼接

print(['a','b','c']+[1,2,3])		# ['a', 'b', 'c', 1, 2, 3]
```

```python
# 列表重复

print(['a','b','c']*3)				# ['a', 'b', 'c', 'a', 'b', 'c', 'a', 'b', 'c']
```



#### 方法:插入

```python
append()
# 向列表末尾添加元素

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
DATE.append('七罪')
print(DATE) #['鸢一折纸', '五河琴里', '夜刀神十香', '七罪']
```

```python
#insert()
# 向列表指定位置添加元素 
# s.insert(i,x)  等价于 s[i:i]=[x]

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
DATE.insert(1,'七罪')
print(DATE) #['鸢一折纸', '七罪', '五河琴里', '夜刀神十香']
```

```python
# extend()
# 向列表插入多个元素(以列表形式)
# s.entend(l) 等价于 s+=l       (l为列表)

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
DATE.extend(['八舞耶俱矢','八舞夕弦'])
print(DATE) # ['鸢一折纸', '五河琴里', '夜刀神十香', '八舞耶俱矢', '八舞夕弦']
```



#### 方法:删除

```python
# remove()
# 删除指定元素

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
DATE.remove('鸢一折纸')			# 相当于  del DATE[0:1]
print(DATE) # ['五河琴里', '夜刀神十香']
```

```python
# pop()
# 删除一个元素并返回该元素(按索引)(默认最后一个)

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
print(DATE.pop()) 	# 夜刀神十香
print(DATE)			# ['鸢一折纸', '五河琴里']
```

```python
# clear()
# 清空列表

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
DATE.clear()
print(DATE) # []
```

#### 方法:查找

```python
# count()
# 统计元素个数

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
print(DATE.count('鸢一折纸')) #1
```
```python
# index()
# 查找指定元素
# 可设置寻找访问(切片)

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
print(DATE.index('鸢一折纸')) #0
```


#### 方法:排序

```python
reverse()
# 反序排列列表

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
DATE.reverse()
print(DATE) # ['夜刀神十香', '五河琴里', '鸢一折纸']
```
```python
sort(*, key=None, reverse=False)
# 对列表进行原地排序(内置函数sort()返回新列表)，只使用 < 来进行各项间比较
#异常不会被屏蔽 —— 如果有任何比较操作失败，整个排序操作将失败（而列表可能会处于被部分修改的状态）
# sort() 接受两个仅限以关键字形式传入的参数 (仅限关键字参数):
# key 指定带有一个参数的函数，用于从每个列表元素中提取比较键 (例如 key=str.lower)。 对应于列表中每一项的键会被计算一次，然后在整个排序过程中使用。 默认值 None 表示直接对列表项排序而不计算一个单独的键值。
# reverse 为一个布尔值。 如果设为 True，则每个列表元素将按反向顺序比较进行排序。


DATE = [5,6,0,-8,99]
DATE.sort()  				# 正向(默认reverse=False)
print(DATE) # [-8, 0, 5, 6, 99]
DATE.sort(reverse=True)		# 反向
print(DATE) # [99, 6, 5, 0, -8]
```

#### 方法:拷贝

```python
copy()
# 创建浅拷贝(多维元素id不变)
# l=s.copy()	等价于	   l=s[:]
```

```python
import copy
b=['a','b','c','d','e','f','g']
a=copy.deepcopy(b)
```

#### 列表推导式

```python
# 创建列表的方式更简洁
# 对序列或可迭代对象中的每个元素应用某种操作，用生成的结果创建新的列表；或用满足特定条件的元素创建子序列
# 列表推导式的方括号内包含以下内容：
#	一个表达式，后面为一个 for 子句，然后，是零个或多个 for 或 if 子句。
#	结果是由表达式依据 for 和 if 子句求值计算而得出一个新列表


>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]


# 列表推导式中的初始表达式可以是任何表达式，甚至可以是另一个列表推导式

>>> matrix = [
...     [1, 2, 3, 4],
...     [5, 6, 7, 8],
...     [9, 10, 11, 12],
... ]

>>> [[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```



#### 类型转换

```python
# tuple()
# 列表生成对应元组

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
a=tuple(DATE)
print(a)		# ('鸢一折纸', '五河琴里', '夜刀神十香')
print(type(a)) 	# <class 'tuple'>
```

```python
# set()
# 列表生成对应集合

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
a=set(DATE)
print(a)		# {'鸢一折纸', '夜刀神十香', '五河琴里'}
print(type(a)) 	# <class 'set'>
```

```python
# dict()
# 列表生成对应字典(列表需内为二元列表或元组)

DATE =[['name','鸢一折纸'],['id','angel']]
a=dict(DATE)
print(a)		# {'name': '鸢一折纸', 'id': 'angel'}
print(type(a)) 	# <class 'dict'>
```



### 元组(tuple)

```python
# 创建	用()	多个时可省

DATE = ('鸢一折纸','五河琴里','夜刀神十香')
DATE1 = '鸢一折纸','五河琴里','夜刀神十香'


print(type(DATE)) 	# <class 'tuple'>

print(len(DATE))	# 3
```
```python
# 索引
# 元组元素不能修改(元组中列表元素可修改)

DATE = ('鸢一折纸','五河琴里','夜刀神十香',[5,9])
print(DATE[0]) # 鸢一折纸
DATE[3][0]=666
print(DATE) # ('鸢一折纸', '五河琴里', '夜刀神十香', [666, 9])
```
```python
# 元组相加(生成新元组)
print((1,2,3)+('a','b'))	# (1, 2, 3, 'a', 'b')
```

```python
# 元组重复(生成新元组)
print((1,2,3)*3)			# (1, 2, 3, 1, 2, 3, 1, 2, 3)
```

#### 方法:查找

```python
# count()
# 统计元素个数

DATE = ('鸢一折纸','五河琴里','夜刀神十香')
print(DATE.count('鸢一折纸')) #1
```

```python
# index()
# 查找指定元素
# 可设置寻找访问(切片)

DATE = ('鸢一折纸','五河琴里','夜刀神十香')
print(DATE.index('鸢一折纸')) #0
```



#### 序列解包

```python
test=('apple','big','cat')
x,y,z=test
print(x)	# apple
print(y)	# big
print(z)	# cat
```



#### 生成器推导式

```python
# 语法与列表推导式类似,用()包裹
# 返回的是生成器对象,需转为元组
# 可用__next__()遍历
a = (x for x in range(1,10))
print(tuple(a))
```



#### 类型转化

```python
# list()
# 元组生成对应列表

DATE = ('鸢一折纸','五河琴里','夜刀神十香')
a=list(DATE)
print(a)		# ['鸢一折纸', '五河琴里', '夜刀神十香']
print(type(a))  # <class 'list'>
```
```python
# set()
# 元组生成对应集合

DATE =('鸢一折纸','五河琴里','夜刀神十香')
a=set(DATE)
print(a)		# {'鸢一折纸', '夜刀神十香', '五河琴里'}
print(type(a)) 	# <class 'set'>
```

```python
# dict()
# 元组生成对应字典(元组需内为二元列表或元组)

DATE =(['name','鸢一折纸'],['id','angel'])
a=dict(DATE)
print(a)		# {'name': '鸢一折纸', 'id': 'angel'}
print(type(a)) 	# <class 'dict'>
```



### 字典(dict)

- 

```python
# 创建	用{}	对键值对的存储(键为字符串或数字,值任意)

angel1 = {'id':'angel','name':'鸢一折纸'}
angel2=dict(id='angel',name='鸢一折纸')
angel3=dict([['id','angel'],['name','鸢一折纸']])
angel4=dict(zip(['id','name'],['angel','鸢一折纸']))

print(type(angel1)) # <class 'dict'>

print(len(angel1))  # 2
```

```python
# 删除

angel = {'id':'angel','name':'鸢一折纸'}
del angel['id']
del angel
```

```python
# 索引

angel = {'id':'angel','name':'鸢一折纸'}

angel['id']="devil"		# 修改

angel['age']=16     	# 添加

print(angel) # {'id': 'devil', 'name': '鸢一折纸', 'age': 16}
```

```python
# 成员运算  in    not in
# 对key

angel = {'id':'angel','name':'鸢一折纸'}
print('id' in angel)  # True
```



#### 方法:获取

```python
get(key[, default])
# 如果 key 存在于字典中则返回 key 的值，否则返回 default
# 如果 default 未给出则默认为 None，因而此方法绝不会引发 KeyError(用索引找不到报错)
```

```python
keys()
# 返回由字典键组成的一个新视图
```

```python
values()
# 返回由字典值组成的一个新视图。
```

```python
items()
# 返回键值对列表
```



#### 方法:删除

```python
clear()
# 清空字典

angel = {'id':'angel','name':'鸢一折纸'}
angel.clear()
print( angel)   # {}
```

```python
pop(key[, default])
# 如果 key 存在于字典中则将其移除并返回其值，否则返回 default
# 如果 default 未给出且 key 不存在于字典中，则会引发 KeyError

angel = {'id':'angel','name':'鸢一折纸'}
print(angel.pop('id'))  	# angel
print(angel)				# {'name': '鸢一折纸'}
```

```python
popitem()
# 从字典中移除并返回一个 (键, 值) 对。
# 键值对会按 LIFO(Last In First Out)(后进先出)(返回最后一个)(栈) 的顺序被返回。

angel = {'id':'angel','name':'鸢一折纸'}
print(angel.popitem()) 	# ('name', '鸢一折纸')
print(angel) 			# {'id': 'angel'}
```
#### 方法:更新

```python
update([other])
# 使用来自 other 的键/值对更新字典，覆盖原有的键。 返回 None。 
# update() 接受另一个字典对象，或者一个包含键/值对（以长度为二的元组或其他可迭代对象表示）的可迭代对象。

angel = {'id':'angel','name':'鸢一折纸'}
angel.update({'id':'devil','age':'16'})
print(angel)     # {'id': 'devil', 'name': '鸢一折纸', 'age': '16'}
```

```python
# setdefault(key[, default])
# 如果字典存在键 key ，返回它的值。如果不存在，插入值为 default 的键 key ，并返回 default 
# default 默认为 None。
```

#### 字典推导式

```python
# 字典推导式与列表和集合推导式有所不同，它需要以冒号分隔的两个表达式，后面带上标准的 "for"和"if" 子句 
# 当推导式被执行时，作为结果的键和值元素会按它们的产生顺序被加入新的字典。

>>>{x: x ** 2 for x in range(10)}
{0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}
```



#### 类型转换

```python
# list()
# 字典生成对应列表(只保留键)

DATE = {'name':'鸢一折纸','id':'angel'}
a=list(DATE)
print(a)        # ['name', 'id']
print(type(a))  # <class 'list'>
```

```python
# tuple()
# 字典生成对应元组(只保留键)

DATE = {'name':'鸢一折纸','id':'angel'}
a=tuple(DATE)
print(a)		# ('name', 'id')
print(type(a)) 	# <class 'tuple'>
```

```python
# set()
# 字典生成对应集合(只保留键)

DATE = {'name':'鸢一折纸','id':'angel'}
a=set(DATE)
print(a)		# {'id', 'name'}
print(type(a)) 	# <class 'set'>
```




### 集合(set)

- 集合（set）是一个`无序`的不重复元素序列。

- 可以使用大括号 **{ }** 或者 **set()** 函数创建集合，注意：创建一个空集合必须用 **set()** 而不是 **{ }**，因为 **{ }** 是用来创建一个空字典。
- 集合中False和0相同,不能同时存在

```python
# 创建	用{}

angel={'鸢一折纸','五河琴里'}
print(type(angel))	# <class 'set'>
print(len(angel)) 	# 2

angel1=set('鸢一折纸')
print(angel1)		# {'鸢', '一', '纸', '折'}
```

```python
# 成员运算 in 		not in

angel={'鸢一折纸','五河琴里'}
print('鸢一折纸' in angel) 	# Ture
```

#### 字典推导式

```

```



#### 方法:添加

```python
# add(elem)
# 将元素 elem 添加到集合中。

angel={'鸢一折纸'}
angel.add('五河琴里')
print(angel) 			# {'鸢一折纸', '五河琴里'}
```

```python
# update(*others)
# set |= other | ...
# 更新集合，添加来自 others 中的所有元素。
 
angel={'鸢一折纸'}
angel.update('五河琴里')
print(angel) 		# {'五', '琴', '河', '鸢一折纸', '里'}
```

#### 方法:删除

```python
# remove(elem)
# 从集合中移除元素 elem
# 如果 elem 不存在于集合中则会引发 KeyError。

angel={'鸢一折纸','五河琴里'}
angel.remove('五河琴里')
print(angel)		# {'鸢一折纸'}
```

```python
# discard(elem)
# 如果元素 elem 存在于集合中则将其移除。
# (元素不存在不报错)

angel={'鸢一折纸','五河琴里'}
angel.discard('五河琴里')
print(angel)		# {'鸢一折纸'}
```

```python
# pop()
# 从集合中移除并返回任意一个元素
# 如果集合为空则会引发 KeyError。
```

```python
# clear()
# 从集合中移除所有元素。
```

#### 方法:检测

```python
# issuperset(other)
# set >= other
# 检测是否 other 中的每个元素都在集合之中

a,b={1,2,3,4},{1,3}
print(a.issuperset(b))		# True
print(b.issuperset(a))		# False
print(a.issuperset(a))		# True
```

```python
# issubset(other)
# set <= other
# 检测是否集合中的每个元素都在 other 之中
```

```python
# isdisjoint(other)
# 如果集合中没有与 other 共有的元素则返回 True
# 当且仅当两个集合的交集为空集合时，两者为不相交集合
```



#### 集合运算

```python
# 交集

a,b={1,2,3,4},{2,4,6,8}

# &
# 交集运算符号
print(a&b)					# {2, 4}	

# intersection(*others)
# set & other & ...
# 返回一个新集合，其中包含原集合以及 others 指定的所有集合中共有的元素
print(a.intersection(b))	# {2, 4}

# intersection_update(*others)
# set &= other & ...
# 更新集合，只保留其中在所有 others 中也存在的元素
a.intersection_update(b)	# 更新a,而非返回新集合
print(a)					# {2, 4}
```

```python
# 并集

a,b={1,2,3,4},{2,4,6,8}

# |
# 并集运算符号
print(a|b)					# {1, 2, 3, 4, 6, 8}	

# union(*others)
# set | other | ...
# 返回一个新集合，其中包含来自原集合以及 others 指定的所有集合中的元素
print(a.union(b))			# {1, 2, 3, 4, 6, 8}	

# update(*others)
# set |= other | ...
# 更新集合，添加来自 others 中的所有元素
a.update(b)					# 更新a,而非返回新集合
print(a)					# {1, 2, 3, 4, 6, 8}
```

```python
# 差集

a,b={1,2,3,4},{2,4,6,8}

# -
# 差集运算符号
print(a-b)					# {1, 3}	

# difference(*others)
# set - other - ...
# 返回一个新集合，其中包含原集合中在 others 指定的其他集合中不存在的元素
print(a.difference(b))		# {1, 3}	

# difference_update(*others)
# set -= other | ...
# 更新集合，移除其中也存在于 others 中的元素
a.difference_update(b)
print(a)					# {1, 3}
```

```python
# 对称差集(并去交)

a,b={1,2,3,4},{2,4,6,8}

# ^
# 对称差集运算符号
print(a^b)					#	{1, 3, 6, 8}		

# symmetric_difference(other)
# set ^ other
# 返回一个新集合，其中的元素或属于原集合或属于 other 指定的其他集合，但不能同时属于两者
print(a.symmetric_difference(b))	#	{1, 3, 6, 8}

# symmetric_difference_update(other)
# set ^= other
# 更新集合，只保留存在于集合的一方而非共同存在的元素
a.symmetric_difference_update(b)
print(a)						#	{1, 3, 6, 8}			
```



#### 类型转换

```python
# list()
# 集合生成对应列表

DATE = {1,2,3,4}
a=list(DATE)
print(a)        # [1, 2, 3, 4]
print(type(a))  # <class 'list'>
```

```python
# tuple()
# 集合生成对应元组

DATE = {1,2,3,4}
a=tuple(DATE)
print(a)		# (1, 2, 3, 4)
print(type(a)) 	# <class 'tuple'>
```



#### 冰冻集合

```python
#  frozenset 类型是不可变并且为 hashable --- 其内容在被创建后不能再改变；因此它可以被用作字典的键或其他集合的元素

```



## 运算符

### 算术运算符

| 运算符 | 描述                                         | 例         |
| ------ | -------------------------------------------- | ---------- |
| `+`    | 加                                           | 6+3`=`9    |
| `-`    | 减                                           | 6-3`=`3    |
| `*`    | 乘                                           | 6*3`=`18   |
| `/`    | 除                                           | 6/3`=`2.0  |
| `%`    | 取模(返回除法余数)                           | 6%3`=`0    |
| `**`   | 幂                                           | 6**3`=`216 |
| `//`   | 取整除(向下取接近除数整数)(去除除数小数部分) | 6//3`=`2   |

### 逻辑运算符

```python
# 逻辑运算符 and or not

# and 与(&) 全真为真
print(1<3 and 2<4) #True   

# or 或(|) 全假为假
print(1<3 or 5<4)  #True

# not 非(!) 取反
print(not 1<3)     #False
```



### 位运算符

| 运算符 | 描述          |
| ------ | ------------- |
| `&`    | 与(同1则1)    |
| `|`    | 或(有1则1)    |
| `^`    | 异或(相异为1) |
| `~`    | 非            |
| `<<`   | 左移          |
| `>>`   | 右移          |



### 成员运算符

| 运算符   | 描述                                        |
| -------- | ------------------------------------------- |
| `in`     | 检测在序列是否能找到,**找到**返回**True**   |
| `not in` | 检测在序列是否能找到,**找不到**返回**True** |



### 身份运算符

| 运算符   | 描述                                  | 例子                         |
| -------- | ------------------------------------- | ---------------------------- |
| `is`     | 是否引自同一对象,**是**返回**True**   | x is y等价于id(x)==id(y)     |
| `is not` | 是否引自同一对象,**不是**返回**True** | x is not y等价于id(x)!=id(y) |





### 优先级

从高到低

| 运算符                                   | 描述                   |
| ---------------------------------------- | ---------------------- |
| `**`                                     | 指数(最高)             |
| `~ ` `+` ` -`                            | 位翻转  一元加  一元减 |
| `*` `/` `%` `//`                         | 乘  除  取模  取整除   |
| `+` `-`                                  | 加  减                 |
| `<<` `>>`                                | 左移  右移             |
| `&`                                      | 位与                   |
| `^ ` `|`                                 | 异或  或               |
| `<=` `<` `>` `>=`                        | 比较运算符             |
| `==` `!=`                                | 等于运算符             |
| `=` `+=` `-=` `/=` `*=` `%=` `//=` `**=` | 赋值运算符             |
| `is` `is not`                            | 身份运算符             |
| `in` `not in`                            | 成员运算符             |
| `not` `and` `or`                         | 逻辑运算符             |













## 条件/循环


### if else

```python
# if elif else

a=1

if a==1:
    print("鸢一折纸")
elif a==5:
    print("五河琴里")
elif a==9:
    print("夜刀神十香")
else:
    print("其他")   
```



### while

```python
# while
# 	break 结束循环
# 	continue 结束本次循环

a=0
while a<5:
    a=a+1
    print(a) 
```

### for

```python
# for 遍历列表

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
for p in DATE:
    print(p)
    
# 鸢一折纸
# 五河琴里
# 夜刀神十香
```

```python
# for 遍历字典
angel = {'id':'angel','name':'鸢一折纸'}

# 默认为key
for c in angel:
    print(c)	
# id 
# name

for c in angel:
    print(angel[c]) 
# angel 
# 鸢一折纸

for c in angel.keys():
    print(c) 
# id 
# name
    
for c in angel.values():
    print(c) 
# angel 
# 鸢一折纸

for c in angel.items():
    print(c)
#('id', 'angel')
#('name', '鸢一折纸')

for k,y in angel.items():
    print(k,y)  # k相当于 .keys()			v相当于.values()
```

```python
# for 嵌套
#九九乘法表
for i in range(1,10):
    for j in range(1,10):
        if(i<j):
            break
        print('%s*%s=%s'%(i,j,i*j),end=' ')
    print(end='\n')
```

### 三目

```python
# 三目

a=5

print("鸢一折纸") if a==5 else print("五河琴里")
```

 



## 函数

```python
# 创建
def hello() :
    print("Hello World!")

hello() # 调用
```



#### 参数

```python
# 默认参数
# 要在最后
def fu(a,b=7):
    return a+b

print(fu(5))		# 12 5+7
print(fu(5,8))		# 13 5+8
```

```python
# 收集参数
# *  元组

def date1(*args):
	print(args)

date1('angel','devil','鸢一折纸') #('angel', 'devil', '鸢一折纸')
```

```python
# 关键字参数

def date(id,name):
    print(id,name)
date(name='鸢一折纸',id='angel')	# angel 鸢一折纸

def date1(*args,name):
	print(args,name)
date1('angel','devil',name='鸢一折纸') # ('angel', 'devil') 鸢一折纸
```

```python
# 关键字收集参数
# ** 字典
def fun(*args,**kwargs):
    print(args)         # (1, 2, 3)
    print(kwargs)		# {'x': 6, 'y': 7}
fun(1,2,3,x=6,y=7)
fun(*(1,2,3),**{'x':6,'y':7})
```



#### 返回值

```python
# 返回值 return
# 用于退出函数
# 不带参数值的return语句返回None

def fun1(a,b):
    return a+b
    print('aaa') # 不执行(会虚化)
print(fun1(5,8))	# 13

# 可返回多个值	用','分割	返回值是元组
def fun2():
    return '55','66'
print(fun2())		# ('55', '66')
print(type(fun2()))	# <class 'tuple'>

```



#### lambda函数

```python
# lambda
# :前参数
# :后返回值

a = lambda x:x+1 # 加1

b = lambda x:True if x%2==0 else False # 偶数返回True
```





## 装饰器

- 在不改变原有函数代码,并保持原函数调用方法不变,给原函数增加功能(或给类增加属性和功能)
- **核心思想**:用一个函数(或类)去装饰另一个函数(或类),造出一个新的函数(或类)
- **应用场景**:引入日志,函数执行时间统计,执行函数前准备工作,权限校验,缓存等场景
- **语法规则**:给原有函数加@,装饰器会将原函数当作参数传入装饰器中
- 嵌套时,先执行***离函数近的***

```python
# 原型(闭包)

def outer(f):
    def inner():
        print("我是外函数中内函数1")
        f()
        print("我是外函数中内函数2")
    return inner

def old():
    print('我是普通函数')
    
old=outer(old)
old()
# outputs:  我是外函数中内函数1
#			我是普通函数
#			我是外函数中内函数2
```

```python
# 可用@进行简写

def outer(f):
    def inner():
        print("我是外函数中内函数1")
        f()
        print("我是外函数中内函数2")
    return inner

@outer
def old():
    print('我是普通函数')

old()
# outputs:  我是外函数中内函数1
#			我是普通函数
#			我是外函数中内函数2
```

#### 装饰参数函数

```python
def old():
    print('我是普通函数')

def outer(f):
    def inner(a):
        print("我是外函数中内函数1")
        f(a)
        print("我是外函数中内函数2")
        print(a)
    return inner

@outer
def old(a):
    print('我是普通函数',a)


old(99)   # old() ->inner()			old(a) -> inner(a)
```



#### 带参数装饰器

```python
# 在装饰器外面再套一层
def old():
    print('我是普通函数')

def extend(b):
    def outer(f):
        def inner(a):
            print("我是外函数中内函数1")
            f(a)
            print("我是外函数中内函数2")
        def b(a):
            print('bbbbbbbbbb')
            f(a)
            print('bbbbbbbbbb')
        if b==1:
            return inner
        else:
            return b
    return outer 

@extend(656)
def old(a):
    print('我是普通函数',a)

old(99)
# outputs:  bbbbbbbbbb
#			我是普通函数 99
#			bbbbbbbbbb
```



#### 类装饰函数

```python
def old():
    print('我是普通函数')

class outer:
    def __call__(self,f) :
        self.f=f
        return self.inner
    def inner(self,a):
        print('bbbbbbbbbb')
        self.f(a)
        print('bbbbbbbbbb')

@outer()
def old(a):
    print('我是普通函数',a)

old(99)
# outputs:  bbbbbbbbbb
#			我是普通函数 99
#			bbbbbbbbbb
```

#### 类方法装饰函数

```python
class outer:
    def a(f):
        outer.f=f
        return outer.inner   
    def inner():
        print("我是外函数中内函数1")
        outer.f()
        print("我是外函数中内函数2")
@outer.a
def old():
    print('我是普通函数')
    

old()
```



#### 函数装饰类

```python
def outer(cls):
    cls.name='5'
    return cls

@outer
class old():
    def a(self):
        print('a')
        
q=old()
print(q.name)
print(old.name)
```



#### 类装饰类

```python
class outer:
    def __call__(self, cls) :
        self.cls=cls
        return self.a
    def a(self):
        self.cls.name='鸢一折纸'
        return self.cls()


@outer()
class old():
    def a(self):
        print('a')
        
q=old()
print(q.name)
```



## 命名空间和作用域

### 命名空间

一般有三种命名空间：

- **内置名称（built-in names**）， Python 语言内置的名称，比如函数名 abs、char 和异常名称 BaseException、Exception 等等。
- **全局名称（global names）**，模块中定义的名称，记录了模块的变量，包括函数、类、其它导入的模块、模块级的变量和常量。
- **局部名称（local names）**，函数中定义的名称，记录了函数的变量，包括函数的参数和局部定义的变量。（类中定义的也是）



要使用变量 runoob，则 Python 的查找顺序为：**局部命名空间 -> 全局命名空间 -> 内置命名空间**。

### 作用域

有四种作用域：

- **L（Local）**：最内层，包含局部变量，比如一个函数/方法内部。
- **E（Enclosing）**：包含了非局部(non-local)也非全局(non-global)的变量。比如两个嵌套函数，一个函数（或类） A 里面又包含了一个函数 B ，那么对于 B 中的名称来说 A 中的作用域就为 nonlocal。
- **G（Global）**：当前脚本的最外层，比如当前模块的全局变量。
- **B（Built-in）**： 包含了内建的变量/关键字等，最后被搜索。

#### 局部变量

- 函数内定义变量
- 在函数外不能使用
- 用`locals()`函数获取局部变量(在函数外等同于`globals()`)(以字典形式)
- 

#### 全局变量

- 函数外定义变量是全局变量(函数可直接访问,但不能修改)
- 函数内用*global*关键词定义的保留是全局变量
- 函数内用global关键字引用外部变量
- 用`globals()`函数获取全局变量(以字典形式)

#### global 关键字

- 函数内用*global*关键词定义的变量是全局变量
- 函数内用global关键字引用外部变量

####  nonlocal 关键字

要修改嵌套作用域（enclosing 作用域，外层非全局作用域）中的变量则需要 *nonlocal* 关键字

- 嵌套函数内用 *nonlocal* 关键字引用上一层函数的变量(依旧表示全局变量)





## 迭代器与生成器

### 迭代器

- 是访问**集合**元素一种方式
- 是一个可记住**访问位置**对象
- 才集合第一个元素开始,到最后一个结束
- **只能前进**

##### 创建

```python
a=['鸢一折纸','五河琴里','夜刀神十香']
b=iter(a)
print(b)        # <list_iterator object at 0x00000163B8CA03A0>
print(type(b))  # <class 'list_iterator'>

```

##### 使用

```python
# 通过next()

a=['鸢一折纸','五河琴里','夜刀神十香']
b=iter(a)
print(next(b))	# 鸢一折纸
print(next(b))	# 五河琴里
print(next(b))	# 夜刀神十香
```
```python
# 通过list()	(容器类转换方法)(转换为容器类型)	

a=['鸢一折纸','五河琴里','夜刀神十香']
b=iter(a)
c=list(b)
print(c)	# ['鸢一折纸','五河琴里','夜刀神十香']
```
```python
# 通过for
a=['鸢一折纸','五河琴里','夜刀神十香']
b=iter(a)
for i in b:
    print(i)

# 鸢一折纸
# 五河琴里
# 夜刀神十香
```



### 生成器

```python
# 生成器 是一个用于创建迭代器的简单而强大的工具
# 写法类似于标准的函数，但当它们要返回数据时会使用 yield 语句
# 每次在生成器上调用 next() 时，它会从上次离开的位置恢复执行（它会记住上次执行语句时的所有数据值）

def Fibonacci():
    a,b=0,1
    while True:
        yield b
        a,b=b,a+b

a=Fibonacci()
for i in range(8):
    print(next(a),end=",")

# 生成器表达式
# 某些简单的生成器可以写成简洁的表达式代码，所用语法类似列表推导式，但外层为圆括号而非方括号
# 这种表达式被设计用于生成器将立即被外层函数所使用的情况。
# 生成器表达式相比完整的生成器更紧凑但较不灵活，相比等效的列表推导式则更为节省内存。
>>> sum(i*i for i in range(10))                 # sum of squares
285

>>> xvec = [10, 20, 30]
>>> yvec = [7, 5, 3]
>>> sum(x*y for x,y in zip(xvec, yvec))         # dot product
260

>>> unique_words = set(word for line in page  for word in line.split())

>>> valedictorian = max((student.gpa, student.name) for student in graduates)

>>> data = 'golf'
>>> list(data[i] for i in range(len(data)-1, -1, -1))
['f', 'l', 'o', 'g']
```







## 面对对象

### 类的创建

```python
class MyClass:
    """A simple example class"""
    i = 12345

    def f(self):
        return 'hello world'
    
# 实例对象会作为函数的第一个参数被传入(self是对象)
# 有self能被对象调用,不能被类调用
# 无self不能被对象调用,能被类调用   
```





### 内置成员

| 属性              | 意义                                                         |      |
| :---------------- | :----------------------------------------------------------- | :--- |
| `__doc__`         | 该函数的文档字符串，没有则为 `None`；不会被子类继承。        | 可写 |
| `__name__`        | 该函数的名称。                                               | 可写 |
| `__qualname__`    | 该函数的 qualified name。*3.3 新版功能.*                     | 可写 |
| `__module__`      | 该函数所属模块的名称，没有则为 `None`。                      | 可写 |
| `__defaults__`    | 由具有默认值的参数的默认参数值组成的元组，如无任何参数具有默认值则为 `None`。 | 可写 |
| `__code__`        | 表示编译后的函数体的代码对象。                               | 可写 |
| `__globals__`     | 对存放该函数中全局变量的字典的引用 --- 函数所属模块的全局命名空间。 | 只读 |
| `__dict__`        | 命名空间支持的函数属性。                                     | 可写 |
| `__closure__`     | `None` 或包含该函数可用变量的绑定的单元的元组。有关 `cell_contents` 属性的详情见下。 | 只读 |
| `__annotations__` | 包含参数标注的字典。字典的键是参数名，如存在返回标注则为 `'return'`。 | 可写 |
| `__kwdefaults__`  | 仅包含关键字参数默认值的字典。                               | 可写 |

```python
__dict__
所属成员

__doc__
文档

__name__
类名称(对象不可用)

__module__
类所在文件名称(是当前文件,则为__main__)

__base__
第一个父类

__bases__
父类列表

__mro__
l
```





### 方法分类

#### 成员方法

- 含`self`形参
- 只能通过对象调用

```python
class A:
    def f(self)
    	pass
```



#### 类方法

- 使用`@classmethod`定义
- 含`cls`形参
- 可通过类调用

```python
class A:
    @classmethod
    def f(cls)
    	pass
```



#### 绑定类方法

- 只能通过类调用

```python
class A:
    def f()
    	pass
```



#### 静态方法

- 使用`@staticmethod`定义

```python
class A:
    @staticmethod
    def f()
    	pass
```







### 魔术方法

#### 基本定制

#####`__new__`

- 创建方法
- 在构造对象期间被发起调用

```python
# 调用以创建一个 cls 类的新实例。__new__() 是一个静态方法 (因为是特例所以你不需要显式地声明)，它会将所请求实例所属的类作为第一个参数。其余的参数会被传递给对象构造器表达式 (对类的调用)。

# __new__() 的返回值应为新对象实例 (通常是 cls 的实例)。如果 __new__() 未返回一个 cls 的实例，则新实例的 __init__() 方法就不会被执行


class MyClass:
	def __new__(cls,*args):
        return object.__new__(cls)
```



##### `__init__`

- 初始化方法
- 类实例化对象后,自动触发

```python
class MyClass:
	def __init__(self,a='1'):
        self.a=a
```



##### `__del__`

- 析构方法
- 对象销毁时触发

```python
class MyClass:
	def __del__(self):
        pass
```



##### `__repr__`

```python
# object.__repr__(self)
# 由 repr() 内置函数调用以输出一个对象的“官方”字符串表示。如果可能，这应类似一个有效的 Python 表达式，能被用来重建具有相同取值的对象（只要有适当的环境）。如果这不可能，则应返回形式如 <...some useful description...> 的字符串。返回值必须是一个字符串对象。如果一个类定义了 __repr__() 但未定义 __str__()，则在需要该类的实例的“非正式”字符串表示时也会使用 __repr__()。

用%r进行字符串拼接时
用repr(x)转换对象x时
则会调用这个对象的__repr__()方法；若没有，则不再看其是否有__str__()方法，而是显示其内存地址

class A:
    a='666'
    def __str__(self) -> str:
        return '鸢一折纸'

    def __repr__(self) -> str:
        return '五河琴里'    

obj=A()
print(repr(obj))	# 五河琴里

```



##### `__str__`

```python
# object.__str__(self)
# 通过 str(object) 以及内置函数 format() 和 print() 调用以生成一个对象的“非正式”或格式良好的字符串表示。返回值必须为一个 字符串 对象。

使用print()时
使用%s和f'{}'拼接对象时
使用str(x)转换对象x时
会优先调用对象的__str__()方法；若没有，就调用__repr__()方法；若再没有，则显示其内存地址。

class A:
    a='666'
    def __str__(self) -> str:
        return '鸢一折纸'
    def __repr__(self) -> str:
        return '五河琴里' 
obj=A()
print(str(obj))   # 鸢一折纸
print(obj)		  # 鸢一折纸
```



`__bool__`

```python
# object.__bool__(self)
# 调用此方法以实现真值检测以及内置的 bool() 操作；应该返回 False 或 True
# 如果未定义此方法，则会查找并调用 __len__() 并在其返回非零值时视对象的逻辑值为真
如果一个类既未定义 __len__() 也未定义 __bool__() 则视其所有实例的逻辑值为真
```





#### 自定义属性访问

##### `__getattribute__`

- 访问成员时触发
- 优先级比`__getattr__`高

```python
# object.__getattribute__(self, name)
# 此方法会无条件地被调用以实现对类实例属性的访问。如果类还定义了 __getattr__()，则后者不会被调用，除非 __getattribute__() 显式地调用它或是引发了 AttributeError
# 此方法应当返回（找到的）属性值或是引发一个 AttributeError 异常
# 为了避免此方法中的无限递归，其实现应该总是调用具有相同名称的基类方法来访问它所需要的任何属性，例如 object.__getattribute__(self, name)。

class A:
    a='666'
    def __getattribute__(self, name: str):
        print('__getattribute__')
        return object.__getattribute__(self,name)

obj=A()
print(obj.a)
# __getattribute__
# 666
```



##### `__getattr__`

- 访问不存在成员时触发

```python
# object.__getattr__(self, name)
# 当默认属性访问因引发 AttributeError 而失败时被调用 (可能是调用 __getattribute__() 时由于 name 不是一个实例属性或 self 的类关系树中的属性而引发了 AttributeError；或者是对 name 特性属性调用 __get__() 时引发了 AttributeError)。
# 此方法应当返回（找到的）属性值或是引发一个 AttributeError 异常。

class A:
    a='666'
    def __getattribute__(self, name: str):
        print('__getattribute__')
        return object.__getattribute__(self,name)

    def __getattr__(self,name:str):
        print('__getattr__')
        return f'{name}不存在'

obj=A()
print(obj.b)
# __getattribute__         引发了 AttributeError,调用__getattr__
# __getattr__
# b不存在
```



##### `__setattr__`

- 为成员变量赋值时触发

```python
# object.__setattr__(self, name, value)
# 此方法在一个属性被尝试赋值时被调用。这个调用会取代正常机制（即将值保存到实例字典）。 name 为属性名称， value 为要赋给属性的值。
# 如果 __setattr__() 想要赋值给一个实例属性，它应该调用同名的基类方法，例如 object.__setattr__(self, name, value)。

class A:
    def __setattr__(self, name: str, value) -> None:
        print('__setattr__')
        object.__setattr__(self,name,value)

obj=A()
obj.f=666
print(obj.f)
# __setattr__
# 666
```



##### `__delattr__`

- 删除成员变量时触发

```python
# object.__delattr__(self, name)
# 类似于 __setattr__() 但其作用为删除而非赋值
# 此方法应该仅在 del obj.name 对于该对象有意义时才被实现。
# 引发一个 审计事件 object.__delattr__，附带参数 obj, name。
class A:
    def __delattr__(self, name: str) -> None:
        return object.__delattr__(self,str)

```



#### 实现描述器

描述符是一个类，定义了**另一个类**中属性的访问方式。换句话说，一个类可以将属性管理全权委托给描述符类

##### `__get__`

```python
object.__get__(self, instance, owner=None)
# 调用此方法以获取所有者类的属性（类属性访问）或该类的实例的属性（实例属性访问）

# 可选的 owner 参数是所有者类
# 而 instance 是被用来访问属性的实例，如果通过 owner 来访问属性则返回 None。

# 此方法应当返回计算得到的属性值或是引发 AttributeError 异常。
PEP 252 指明 __get__() 为带有一至二个参数的可调用对象。 Python 自身内置的描述器支持此规格定义；但是，某些第三方工具可能要求必须带两个参数。 Python 自身的 __getattribute__() 实现总是会传入两个参数，无论它们是否被要求提供。
```

##### `__set__`

```python
object.__set__(self, instance, value)
调用此方法以设置 instance 指定的所有者类的实例的属性为新值 value。
请注意，添加 __set__() 或 __delete__() 会将描述器变成“数据描述器”。 
```

##### `__delete__`

```python
object.__delete__(self, instance)
# 调用此方法以删除 instance 指定的所有者类的实例的属性。
```





```python
# 描述符是一个类，定义了另一个类中属性的访问方式。换句话说，一个类可以将属性管理全权委托给描述符类
# 描述符是 Python 中复杂属性访问的基础，它在内部被用于实现property、方法、类方法、静态方法和super类型
class revealAccess:
    def __init__(self, initval = None, name = 'var'):
        self.val = initval
        self.name = name
    def __get__(self, obj, objtype):
        print("__get__",self.name)
        return self.val
    def __set__(self, obj, val):
        print("__set__",self.name)
        self.val = val
        
class myClass:
    x = revealAccess(10,'var "x"')
    y = 5
    
m = myClass()
print(m.x)
# __get__ var "x"
# 10
m.x = 20
# __set__ var "x"
print(m.x)
# __get__ var "x"
# 20
print(m.y)
# 5
```



#### 模拟可调用对象

#####`__call__`

```python
object.__call__(self[, args...])
# 此方法会在实例作为一个函数被“调用”时被调用
# 如果定义了此方法，则 x(arg1, arg2, ...) 就大致可以被改写为 type(x).__call__(x, arg1, ...)。
```



#### 模拟容器类型

##### `__len__`

```python
object.__len__(self)
# 调用此方法以实现内置函数 len()。应该返回对象的长度，以一个 >= 0 的整数表示。此外，如果一个对象未定义 __bool__() 方法而其 __len__() 方法返回值为零，则在布尔运算中会被视为假值。

class A:
    a='666'
    def __len__(self):
        return len(self.a)

obj=A()
print(len(obj))  # 3          a的长度
```





### 类的封装

- **public**
  - 公有属性的类变量和类函数，在类的外部、类内部以及子类中，都可以正常访问
- **private**
  - **私有属性**的类变量和类函数，只有在*本类内部*使用，类的外部以及子类都无法使用
  - 以双下划线“`__`”开头

以单下划线“`_`”开头的类属性和类方法约定俗成的被视为私有属性和私有方法，虽然它们也能通过类对象正常访问，但是建议不要这样



### 类的继承

```python
class parent:
    pass

class child(parent):
    pass

```

- 子类可通过`super()`调用父类方法(多继承时调用前一个)
- 多继承时,从左至右搜索

#### 菱形继承

```python
# MRO(Method Resolution Order)也叫方法解析顺序，主要用于在多重继承时判断调的属性来自于哪个类，其使用了一种叫做C3的算法，其基本思想时在避免同一类被调用多次的前提下，使用`广度优先`和`从左到右`的原则去寻找需要的属性和方法。
# 为避免顶层父类中的某个方法被多次调用呢，使用super()
# super本质上是一个类，内部记录着MRO信息，由于C3算法确保同一个类只会被搜寻一次，就避免了顶层父类中的方法被多次执行了

class A():
    def __init__(self):
        print('init A...')
        print(self)
        print('end A...')

class B(A):
    def __init__(self):
        print('init B...')
        super(B, self).__init__()
        print('end B...')

class C(A):
    def __init__(self):
        print('init C...')
        super(C, self).__init__()
        print('end C...')

class D(B, C):
    def __init__(self):
        print('init D...')
        super(D, self).__init__()
        print('end D...')

if __name__ == '__main__':
    D()
#                                                             3
# init D...                                                   A
# init B...												    /	\	
# init C...       B调用C                             1      B    C       2
# init A...		  C再调用A                                   \   /
# <__main__.D object at 0x0000023B5E3E7DC0>                   D
# end A...                  super()将D的self向上传递                                 
# end C...                          
# end B...                                                D->B->c->A
# end D...


print(D.mro())
[<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
```



### 描述符

```python
# 定义描述符类
class A:
    def __get__(self, instance, owner=None):
        pass
    def __set__(self, instance, value):
        pass
    def __delete__(self, instance):
        pass

class demo:
    a=A()
```

```python
# property 函数
class demo:
    def getA(self):
        pass
    def setA(self,value):
        pass
    def delA(self):
        pass
    a=property(getA,setA,delA)
```

```python
# @property 装饰器 
class demo:
    __a=None
    @property
    def A(self):
        print('a')
    @A.setter
    def A(self,value):
        print('b')
    @A.deleter
    def A(self):
        print('c')
        
```



## 异常处理

- `try` 语句可为一组语句指定异常处理器和/或清理代码
- `except` 子句指定一个或多个异常处理程序
  -  当 try 子句中没有发生异常时，没有任何异常处理程序会被执行
  -  当 try 子句中发生异常时，将启动对异常处理程序的搜索。 此搜索会逐一检查 except 子句直至找到与该异常相匹配的子句。 
  - 如果存在无表达式的 except 子句，它必须是最后一个,它将匹配任何异常

```python
try:
    pass
except:
    pass
finally:
    pass
```

```python
class MyException():
    '''自定义异常日志处理类'''
    def __init__(self) -> None:
        import traceback,logging
        logging.basicConfig(
            filename='./error.log',# 日志存储的文件及目录
            format='%(asctime)s %(levelname)s \n %(message)s',# 格式化日志存储格式
            datefmt='%Y-%m-%d %H:%M:%S'
            )
        logging.error(traceback.format_exc())


try:
    int('yy')
except:
    MyException()
print(6666)
```



## `内置函数`

### 数据类型

#### int()

```python
# int()
# 将一个字符串或数字转换为整型

print(int('9565'))			 # 9565
print(int(66.66))  			 # 66
print(int('0xa',base=16))	 # 10
print(int('10',8)) 			 
```



#### float()

```python
# float()
# 返回从数字或字符串生成的浮点数。

>>> float('+1.23')
1.23
>>> float('   -12345\n')
-12345.0
>>> float('1e-003')
0.001
>>> float('+1E6')
1000000.0
>>> float('-Infinity')
-inf
```



#### bool()

```python
# bool()
# 返回一个布尔值，True 或者 False

>>>bool()
False
>>> bool(0)
False
>>> bool(1)
True
>>> bool(2)
True
>>> issubclass(bool, int)  # bool 是 int 子类
True
```



#### complex()

```python
# complex()
# class complex([real[, imag]])
# 返回值为 real + imag*1j 的复数，或将字符串或数字转换为复数
 
>>>complex(1, 2)
(1 + 2j)
 
>>> complex(1)    # 数字
(1 + 0j)
 
>>> complex("1")  # 当做字符串处理
(1 + 0j)
 
# 注意：这个地方在"+"号两边不能有空格，也就是不能写成"1 + 2j"，应该是"1+2j"，否则会报错
>>> complex("1+2j")
(1 + 2j)
```



#### str()

```python
# str()
# 返回一个 str 版本的 object 
```



#### list()

```python
# list()
# 生成空列表  或  转换为对应序列
# 虽然被称为函数，list 实际上是一种可变序列类型

DATE = ('鸢一折纸','五河琴里','夜刀神十香')
a=list(DATE)	# 元组转化为列表
print(a)		# ['鸢一折纸', '五河琴里', '夜刀神十香']
print(type(a))  # <class 'list'>


DATE = '鸢一折纸'
a=list(DATE)	# 字符串转为列表(拆开)
print(a)		# ['鸢', '一', '折', '纸']
print(type(a))  # <class 'list'>

DATE = {1,2,3,4}
a=list(DATE)	# 集合转化为列表
print(a)        # [1, 2, 3, 4]
print(type(a))  # <class 'list'>

DATE = {'name':'鸢一折纸','id':'angel'}
a=list(DATE)	# 字典生成对应列表(只保留键)
print(a)        # ['name', 'id']
print(type(a))  # <class 'list'>
```

#### tuple()

```python
# tuple()
# 生成空元组  或  转换为对应元组

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
a=tuple(DATE)	# 列表转化为元组
print(a)		# ('鸢一折纸', '五河琴里', '夜刀神十香')
print(type(a))	# <class 'tuple'>

DATE = '鸢一折纸'
a=tuple(DATE)	# 字符串生成对应元组(拆开)
print(a)		# ('鸢', '一', '折', '纸')
print(type(a)) 	# <class 'tuple'>

DATE = {1,2,3,4}
a=tuple(DATE)	# 集合生成对应元组
print(a)		# (1, 2, 3, 4)
print(type(a)) 	# <class 'tuple'>

DATE = {'name':'鸢一折纸','id':'angel'}
a=tuple(DATE)	# 字典生成对应元组
print(a)		# ('name', 'id')
print(type(a)) 	# <class 'tuple'>
```



#### dict()

```python
# dict()
# 创建空字典  或  生成对应字典

DATE =[['name','鸢一折纸'],['id','angel']]
a=dict(DATE)	# 列表生成对应字典(列表需内为二元列表或元组)
print(a)		# {'name': '鸢一折纸', 'id': 'angel'}
print(type(a)) 	# <class 'dict'>

DATE =(['name','鸢一折纸'],['id','angel'])
a=dict(DATE)	# 元组生成对应字典(元组需内为二元列表或元组)
print(a)		# {'name': '鸢一折纸', 'id': 'angel'}
print(type(a)) 	# <class 'dict'>
```



#### set()

```python
# set()
# 生成空字典	 或	准换为对应集合

DATE = {'name':'鸢一折纸','id':'angel'}
a=set(DATE)		# 字典生成对应集合(只保留键)
print(a)		# {'id', 'name'}
print(type(a)) 	# <class 'set'>

DATE = ['鸢一折纸','五河琴里','夜刀神十香']
a=set(DATE)		# 列表生成对应集合
print(a)		# {'鸢一折纸', '夜刀神十香', '五河琴里'}
print(type(a)) 	# <class 'set'>

DATE =('鸢一折纸','五河琴里','夜刀神十香')
a=set(DATE)		# 元组生成对应集合
print(a)		# {'鸢一折纸', '夜刀神十香', '五河琴里'}
print(type(a)) 	# <class 'set'>

DATE = '鸢一折纸'
a=set(DATE)		# 字符串生成对应集合(拆开)(无序)
print(a)		# {'鸢', '纸', '折', '一'}
print(type(a)) 	# <class 'set'>
```



### 变量

#### id()

```python
# id()
# 返回对象的“标识值”(内存地址)
# 该值是一个整数，在此对象的生命周期中保证是唯一且恒定的
# 两个生命期不重叠的对象可能具有相同的 id() 值
```



#### type()

```python
# type()
# 传入一个参数时，返回 object 的类型。

print(type(1)) # <class 'int'>
```



#### len()

```python
# len()
# 返回对象的长度（元素个数）
# 实参可以是序列（如 string、bytes、tuple、list 或 range 等）
# 集合（如 dictionary、set 或 frozen set 等）

print(len(['鸢一折纸','五河琴里','夜刀神十香']))  # 3
```





#### locals()

```python
# locals()
# 返回局部变量(以字典形式)(在函数外等同于globals())

print(locals())
```



#### globals()

```python
# globals()
# 返回全局变量(以字典形式)

print(globals())
```



### I/O

#### input()

```python
# input()
# 接受一个标准输入数据，返回为 string 类型

a=input('请输入:')			  # 接收参数为提示信息
print(a)					#
print(type(a))				# <class 'str'>
```



#### print()

```python
# print()
# 打印到 file 指定的文本流
# 末尾加上 end

print('鸢一折纸')
print('鸢一折纸',end='') # 为什么结束 默认为'\n'即换行
```



### 数学

#### abs()

```python
# abs()
# 返回一个数的绝对值。 参数可以是整数、浮点数或任何实现了 __abs__() 的对象
# 如果参数是一个复数，则返回它的模
```



#### sum()

```python
# sum()
# sum(iterable, /, start=0)
# 从 start 开始自左向右对 iterable 的项求和并返回总计值。 
# iterable 的项通常为数字，而 start 值则不允许为字符串。

a=[1,2,3,4]
print(sum(a)) # 10
```



#### max()

```python
# max()
# max(iterable, *[, key, default])
# max(arg1, arg2, *args[, key])
# 返回可迭代对象中最大的元素，或者返回两个及以上实参中最大的。

print(max(666,98,1))	# 666
print(max([666,98,1]))	# 666
```



#### min()

```python
# min()
# min(iterable, *[, key, default])
# min(arg1, arg2, *args[, key])
# 返回可迭代对象中最小的元素，或者返回两个及以上实参中最小的。

print(min(666,98,1))	# 1
print(min([666,98,1]))	# 1
```



#### pow()

```python
# pow()
# pow(base, exp[, mod])
# 返回 base 的 exp 次幂
# 如果 mod 存在，则返回 base 的 exp 次幂对 mod 取余（比 pow(base, exp) % mod 更高效）
# 两参数形式 pow(base, exp) 等价于乘方运算符: base**exp


```



#### round()

```python
# round()
# round(number[, ndigits])
# 返回 number 舍入到小数点后 ndigits 位精度的值。 
# 如果 ndigits 被省略或为 None，则返回最接近输入值的整数。
# 如果与两个倍数的距离相等，则选择偶数 (因此，round(0.5)和round(-0.5)均为0 而 round(1.5) 为 2)。
# 奇进偶y
```



### 进制

#### bin()

```python
# bin()
# 将一个整数转变为一个前缀为“0b”的二进制字符串
# int()可将二进制字符串转为整数

print(bin(3))		# '0b11'
print(bin(-10))		# '-0b1010'

print(type(bin(3)))	# <class 'str'>
```



#### oct()

```python
# oct()
# 将一个整数转变为一个前缀为“0o”的八进制字符串

>>>oct(8)
'0o10'
>>>oct(-56)
'-0o70'
```



#### hex()

```python
# hex()
# 将整数转换为以“0x”为前缀的小写十六进制字符串

>>>hex(255)
'0xff'
>>>hex(-42)
'-0x2a'
```



### 编码

#### chr()

```python
# chr()
# 返回 Unicode 码位为整数 i 的字符的字符串格式
# 是 ord() 的逆函数。

>>>chr(97)
'a'
>>>chr(8364) 
'€'
```



#### ord()

```python
# ord()
# 对表示单个 Unicode 字符的字符串，返回代表它 Unicode 码点的整数
# 是 chr() 的逆函数
>>>ord('a')	
97
>>>ord('€')# 欧元符号
8364
```



### 迭代



#### iter()

```python
# iter()
# 将可迭代对象转换为迭代器

a=['鸢一折纸','五河琴里','夜刀神十香']
b=iter(a)
print(b)        # <list_iterator object at 0x00000163B8CA03A0>
print(type(b))  # <class 'list_iterator'>
```



#### next()

```python
next(iterator[, default])
# 返回迭代器下一个元素 如果迭代器耗尽，则返回给定的 default，如果没有默认值则触发 StopIteration。

a=['鸢一折纸','五河琴里','夜刀神十香']
b=iter(a)
print(next(b))	# 鸢一折纸
print(next(b))	# 五河琴里
print(next(b))	# 夜刀神十香
```



#### zip()

```python
zip(*iterables, strict=False)
# 创建一个聚合了来自每个可迭代对象中的元素的迭代器
# 返回一个元组的迭代器，其中的第 i 个元组包含来自每个参数序列或可迭代对象的第 i 个元素
# 当所输入可迭代对象中最短的一个被耗尽时，迭代器将停止迭代
# 只有一个可迭代对象参数时，它将返回一个单元组的迭代器。 不带参数时，它将返回一个空迭代器

# zip('ABCD', 'xy') --> Ax By

a=[1,2,3,4]
b=['a','b','c','d']
e=zip(a,b)
# print(next(e)[1]) # a
print(list(e))	# [(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd')]


# zip()和* 连用可进行拆解
x,y=zip(*zip(a,b))
print(list(x))	# [1,2,3,4]
print(list(y)) 	# ['a','b','c','d']
o=zip(*zip(a,b))
print(list(o))	# [(1, 2, 3, 4), ('a', 'b', 'c', 'd')]
```



#### range()

```python
class range(stop)
class range(start, stop[, step])
# 返回一个对象，该对象按步生成从start(包括)到stop(排除)的整数序列	[左闭右开)	

# Range (i, j)得到i, i+1, i+2，… j - 1 
for i in range(1,4): # 1包含  4排除
    print(i) # 1 2 3
    
# Start默认为0,stop省略 Range(4)产生0,1,2,3
for i in range(4):
    print(i)# 0 1 2 3
    
# 当给定step时，它指定增量(或减量)(默认为1)  

print(list(range(-5,5)))	# [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4]
print(list(range(5,-5,-1)))	# [5, 4, 3, 2, 1, 0, -1, -2, -3, -4]
```



#### filter()

```python
filter(function, iterable)
# 用 iterable 中函数 function 返回真的那些元素，构建一个新的迭代器
# iterable 可以是一个序列，一个支持迭代的容器，或一个迭代器
# 如果 function 是 None ，则会假设它是一个身份函数，即 iterable 中所有返回假的元素会被移除

>>>print(list(filter(lambda x:True if x%2==0 else False,[1,2,3,4,5,6,7,8,9]))) 
[2, 4, 6, 8]
```



#### enumerate()

```python
enumerate(iterable, start=0)
# 返回一个枚举对象。iterable 必须是一个序列，或 iterator，或其他支持迭代的对象
# enumerate() 返回的迭代器的 __next__() 方法返回一个元组，里面包含一个计数值（从 start 开始，默认为 0）和通过迭代 iterable 获得的值。

>>>seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>>list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>>list(enumerate(seasons, start=1))
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

 

#### map()

```python
map(function, iterable, ...)
# 返回一个将 function 应用于 iterable 中每一项并输出其结果的迭代器
# 如果传入了额外的 iterable 参数，function 必须接受相同个数的实参并被应用于从所有可迭代对象中并行获取的项
#当有多个可迭代对象时，最短的可迭代对象耗尽则整个迭代就将结束。

>>>list(map(str,[1,2,3,4,5,6]))
['1', '2', '3', '4', '5', '6']
```



### 类与对象

#### super()

```python
super([type[, object-or-type]])
# 返回一个代理对象，它会将方法调用委托给 type 的父类或兄弟类
# 这对于访问已在类中被重载的继承方法很有用。
# 调用mro上一级

class C(B):
    def method(self, arg):
        super().method(arg)    # This does the same thing as:
                               # super(C, self).method(arg)
```



#### issubclass()

```python
# issubclass(class, classinfo)
# 如果class是classinfo的子类（直接、间接或虚拟），则返回True
```



#### isinstance()

```python
# isinstance()
# 确定是否为给定类型
# isinstance(object, classinfo)
# 如参数 object 是参数 classinfo 的实例或者是其 (直接、间接或 虚拟) 子类则返回 True
# 如 object 不是给定类型的对象，函数将总是返回 False。 
# 如classinfo是类型对象元组（或由其他此类元组递归组成元组）,那么如object是其中任一类型的实例返回 True。 
# 如 classinfo 既不是类型，也不是类型元组或类型元组的元组，则将引发 TypeError 异常

print(isinstance(1,int))  	# True
print(isinstance('1',str))	# True

class A:
    pass
a=A()
print(isinstance(a,A))		# True
```



#### hasattr()

```python
# hasattr()
# hasattr(object, name)
# 该实参是一个对象和一个字符串。如果字符串是对象的属性之一的名称，则返回 True，否则返回 False。（此功能是通过调用 getattr(object, name) 看是否有 AttributeError 异常来实现的。）

```



#### getattr()

```python
# getattr(object, name[, default])
# 返回对象命名属性的值。name 必须是字符串。如果该字符串是对象的属性之一，则返回该属性的值
# 如果指定的属性不存在，且提供了 default 值，则返回它，否则触发 AttributeError。

getattr(x, 'foobar')  # 等同于 x.foobar。
```



#### setattr()

```python
# setattr(object, name, value)
#此函数与 getattr() 两相对应。 其参数为一个对象、一个字符串和一个任意值。 字符串指定一个现有属性或者新增属性。 函数会将值赋给该属性，只要对象允许这种操作。 

setattr(x, 'foobar', 123) # 等价于 x.foobar = 123。
```



#### delattr()

```python
# delattr(object, name)
# setattr() 相关的函数。实参是一个对象和一个字符串。该字符串必须是对象的某个属性。如果对象允许，该函数将删除指定的属性。

delattr(x, 'foobar') # 等价于 del x.foobar 。
```



#### dir()

```python
# dir([object])
# 如果没有实参，则返回当前本地作用域中的名称列表。如果有实参，它会尝试返回该对象的有效属性列表。
```



#### repr()

```python
repr(object)
# 返回包含一个对象的可打印表示形式的字符串
# 对于许多类型来说，该函数会尝试返回的字符串将会与该对象被传递给 eval() 时所生成的对象具有相同的值，在其他情况下表示形式会是一个括在尖括号中的字符串，其中包含对象类型的名称与通常包括对象名称和地址的附加信息
# 类可以通过定义 __repr__() 方法来控制此函数为它的实例所返回的内容。
```



### 排序

#### sorted()

```python
# sorted()
# sorted(iterable, *, key=None, reverse=False)
# 根据 iterable 中的项返回一个新的已排序列表。
# 具有两个可选参数，它们都必须指定为关键字参数。
# key 指定带有单个参数的函数，用于从 iterable 的每个元素中提取用于比较的键 (例如 key=str.lower)。 默认值为 None (直接比较元素)。
# reverse 为一个布尔值。 如果设为 True，则每个列表元素将按反向顺序比较进行排序。

>>>sorted([5, 2, 3, 1, 4])
[1, 2, 3, 4, 5]                      # 默认为升序

>>> print(sorted([5, 0, 6, 1, 2, 7, 3, 4], key=lambda x: x*-1))
[7, 6, 5, 4, 3, 2, 1, 0]

>>> sorted([5, 0, 6, 1, 2, 7, 3, 4], reverse=True)
[7, 6, 5, 4, 3, 2, 1, 0]
```



### 文件

#### open()

```python
# open()
# 打开 file 并返回对应的 file object。 如果该文件不能被打开，则引发 OSError
open(file, 			# 将要打开的文件的路径		
     mode='r', 		# 指定打开文件的模式
     buffering=-1, 	# 可选的整数，用于设置缓冲策略
     encoding=None, # 用于解码或编码文件的编码的名称
     errors=None, 	# 可选的字符串参数，用于指定如何处理编码和解码错误 
     newline=None,	# 控制 universal newlines 模式如何生效
     closefd=True, 	#
     opener=None  	#
    )
```

```markdown
#	mode
	-	r	读取（默认）
	-	w	写入，并先截断文件
	-	x	排它性创建，如果文件已存在则失败
	-	a	写入，如果文件存在则在末尾追加
	-	b	二进制模式
	-	t	文本模式（默认）
	-	+	打开用于更新（读取与写入）

```

```python
with open('train01.txt','r',encoding='utf8') as fr,open('train02.txt','w') as fw:
    for line in fr.readlines():
        if(len(line)!=1):
            fw.write('\t'+line.lstrip()+'\n')
```







### -----



###### all()

```python
# all()
```



###### any()

```python
# any()
```



###### ascii()

```python
# ascii()
# 与 repr() 类似，返回一个包含对象的可打印表示形式的字符串，但是使用 \x、\u 和 \U 对 repr() 返回的字符串中非 ASCII 编码的字符进行转义
```





###### breakpoint()

```python
# breakpoint()
```



###### bytearray()

```python
# bytearray()
```



###### bytes()

```python
# bytes()
```



###### callable()

```python
# 
```





###### classmethod()

```python
# classmethod()
```



###### compile()

```python
# compile()
```









###### divmod()

```python
# divmod()
```



###### eval()

```python
eval(expression[, globals[, locals]])
# 实参是一个字符串，以及可选的 globals 和 locals。globals 实参必须是一个字典。locals 可以是任何映射对象
# 表达式解析参数 expression 并作为 Python 表达式进行求值（从技术上说是一个条件列表），采用 globals 和 locals 字典作为全局和局部命名空间

>>>x = 1
>eval('x+1')
2
```



###### exec()

```python
# exec()
```





#### format()

```python
# format()
# 格式化字符串

# 普通方式
print('{}, {}, {}'.format('a', 'b', 'c'))# a, b, c

# s
print('{2} and {1}'.format('a','b','c','d'))  # c and b

# 关键字传参
print('{a}, {b}, {c}'.format(a='2',c='8',b='9'))# 2,9,8
```



###### frozenset()

```python
# frozenset()
```



###### hash()

```python
# 
```



###### help()

```python
# 
```













###### memoryview()

```python
# 
```







###### object()

```python
# 
```











###### property()

```python
# 
```



###### reversed()

```python
# 
```





###### slice()

```python
# 
```





###### staticmethod()

```python
# 
```













###### vars()

```python
# vars()
```





## 文件操作

#### 打开

```python
# 使用内置函数open()
f=open('demo.txt','w',encoding='utf8')

# 常用with关键字配合打开
with open('demo.txt','w',encoding='utf8') as f:
    f.write()
# 如果没有使用 with 关键字，则应调用 f.close() 关闭文件，即可释放文件占用的系统资源
```



#### 读写

```python
# f.read(size)
# 用于读取文件内容，它会读取一些数据，并返回字符串（文本模式），或字节串对象（在二进制模式下）
# size是可选的数值参数。省略size或size为负数时，读取并返回整个文件内容；文件大小是内存两倍时，会出现问题
# size 取其他值时，读取并返回最多 size 个字符（文本模式）或 size 个字节（二进制模式）
# 如已到达文件末尾，f.read() 返回空字符串（''）

>>> f.read()
'This is the entire file.\n'
>>> f.read()
''
```

```python
# f.readline() 
# 从文件中读取单行数据；字符串末尾保留换行符（\n），只有在文件不以换行符结尾时，文件的最后一行才会省略换行符。这种方式让返回值清晰明确；只要 f.readline() 返回空字符串，就表示已经到达了文件末尾，空行使用 '\n' 表示，该字符串只包含一个换行符。

# 从文件中读取多行时，可以用循环遍历整个文件对象
>>> for line in f:
...     print(line, end='')
...
This is the first line of the file.
Second line of the file
```

```python
# f.readlines()
# 以列表形式读取文件中的所有行
# 相当于 list(f)
```





```python
# f.write(string) 
# 把 string 的内容写入文件，并返回写入的字符数

>>> f.write('This is a test\n')
15

# 写入其他类型的对象前，要先把它们转化为字符串（文本模式）或字节对象（二进制模式）
>>> value = ('the answer', 42)
>>> s = str(value)  # convert the tuple to string
>>> f.write(s)
18
```

```python

```

```python

```



```python
# f.seek(offset, whence) 
# 可以改变文件对象的位置。通过向参考点添加 offset 计算位置；参考点由 whence 参数指定
# whence 值为 0 时，表示从文件开头计算，1 表示使用当前文件位置，2 表示使用文件末尾作为参考点
# 省略 whence 时，其默认值为 0，即使用文件开头作为参考点


```



## 模块

### 安装

```

```

```
python -m ensurepip
```



### 导入

```python
# 绝对导入
import <模块>
import <包>
import <包.模块>
from <模块> import <内容> 
from <包> import <模块>
from <包.模块> import <内容>

# 相对导入
# 只能在非主程序的模块中使用,不需要直接运行的模块
from <.包名/模块名> import <模块/内容>
from <..包名/模块名> import <模块/内容>
```

```

```



### 包

包是一个分层次的文件目录结构，它定义了一个由模块及子包，和子包下的子包等组成的 Python 的应用环境。

简单来说，包就是文件夹，但该文件夹下必须存在 `__init__.py` 文件, 该文件的内容可以为空。`_init__.py` 用于标识当前文件夹是一个包。







# 内置模块

## 文本处理服务

### re

- 正则表达式操作



```python
re.compile(pattern, flags=0)
# 将正则表达式的样式编译为一个 正则表达式对象 （正则对象），可以用于匹配，通过这个对象的方法 match(), search() 以及其他如下描述。
```

```python
re.search(pattern, string, flags=0)
# 扫描整个 字符串 找到匹配样式的第一个位置，并返回一个相应的 匹配对象
# 如果没有匹配，就返回一个 None ； 注意这和找到一个零长度匹配是不同的。

import re
print(re.search('\d',"B2 is the suite number."))
# <re.Match object; span=(1, 2), match='2'>
```

```python
re.match(pattern, string, flags=0)
# 如果 string 开始的0或者多个字符匹配到了正则表达式样式，就返回一个相应的 匹配对象 
# 如果没有匹配，就返回 None ；注意它跟零长度匹配是不同的。

import re
print(re.match('\d',"B2 is the suite number."))
# None
print(re.match('\d',"2 is the suite number."))
# <re.Match object; span=(0, 1), match='2'>
```

```python
re.findall(pattern, string, flags=0)
# 返回字符串中模式的所有非重叠匹配项，作为字符串或元组
# 从左到右扫描字符串，并按找到的顺序返回匹配项。结果中包含空匹配项
# 结果取决于模式中捕获组的数量。如果没有组，则返回与整个模式匹配的字符串列表。如果只有一个组，则返回与该组匹配的字符串列表。如果存在多个组，则返回与这些组匹配的字符串元组列表。非捕获组不会影响结果的形式。

import re
print(re.findall('.y',"yes make my day"))
# ['my', 'ay']
```

```python
re.split(pattern, string, maxsplit=0, flags=0)
# 用 pattern 分开 string 
# 如果在 pattern 中捕获到括号，那么所有的组里的文字也会包含在列表里
# 如果 maxsplit 非零， 最多进行 maxsplit 次分隔， 剩下的字符全部返回到列表的最后一个元素
```

```python
re.sub(pattern, repl, string, count=0, flags=0)
```

```python
re.escape(pattern)
```

| 方法 / 属性 | 目的                                 |
| :---------- | :----------------------------------- |
| `group()`   | 返回正则匹配的字符串                 |
| `start()`   | 返回匹配的开始位置                   |
| `end()`     | 返回匹配的结束位置                   |
| `span()`    | 返回包含匹配 (start, end) 位置的元组 |







```python
Match.group([group1, ...])
# 返回一个或者多个匹配的子组
# 如果只有一个参数，结果就是一个字符串
# 如果有多个参数，结果就是一个元组（每个参数对应一个项）
# 如果没有参数，组1默认到0（整个匹配都被返回）
# 如果一个组N 参数值为 0，相应的返回值就是整个匹配字符串
# 如果它是一个范围 [1..99]，结果就是相应的括号组字符串。
# 如果一个组号是负数，或者大于样式中定义的组数，就引发一个 IndexError 异常
# 如果一个组包含在样式的一部分，并被匹配多次，就返回最后一个匹配

>>> m = re.match(r"(\w+) (\w+)", "Isaac Newton, physicist")
>>> m.group(0)       # The entire match
'Isaac Newton'
>>> m.group(1)       # The first parenthesized subgroup.
'Isaac'
>>> m.group(2)       # The second parenthesized subgroup.
'Newton'
>>> m.group(1, 2)    # Multiple arguments give us a tuple.
('Isaac', 'Newton')
```

```python
Match.groups(default=None)
# 返回一个元组，包含所有匹配的子组，在样式中出现的从1到任意多的组合
# default 参数用于不参与匹配的情况，默认为 None

>>> m = re.match(r"(\d+)\.(\d+)", "24.1632")
>>> m.groups()
('24', '1632')
```

```python
Match.groupdict(default=None)
# 返回一个字典，包含了所有的 命名 子组。key就是组名。 
# default 参数用于不参与匹配的组合；默认为 None
```



## 数据类型

### array

- 定义了一种对象类型，可以紧凑地表示基本类型值的数组：字符、整数、浮点数等
-  数组属于序列类型，其行为与列表非常相似，不同之处在于其中存储的对象类型是受限的
-  类型在对象创建时使用单个字符的 *类型码* 来指定。

| 类型码 | C 类型             | Python 类型  | 以字节表示的最小尺寸 |
| :----- | :----------------- | :----------- | :------------------- |
| `'b'`  | signed char        | int          | 1                    |
| `'B'`  | unsigned char      | int          | 1                    |
| `'u'`  | wchar_t            | Unicode 字符 | 2                    |
| `'h'`  | signed short       | int          | 2                    |
| `'H'`  | unsigned short     | int          | 2                    |
| `'i'`  | signed int         | int          | 2                    |
| `'I'`  | unsigned int       | int          | 2                    |
| `'l'`  | signed long        | int          | 4                    |
| `'L'`  | unsigned long      | int          | 4                    |
| `'q'`  | signed long long   | int          | 8                    |
| `'Q'`  | unsigned long long | int          | 8                    |
| `'f'`  | float              | float        | 4                    |
| `'d'`  | double             | float        | 8                    |

```python
class array.array(typecode[, initializer])
# 一个包含由 typecode 限制类型的条目的新数组，并由可选的 initializer 值进行初始化，该值必须为一个列表、bytes-like object 或包含正确类型元素的可迭代对象。

# 如果给定一个列表或字符串，该 initializer 会被传给新数组的 fromlist(), frombytes() 或 fromunicode() 方法（见下文）以将初始条目添加到数组中。 否则会将可迭代对象作为 initializer 传给 extend() 方法。
```



### datetime

- 基本日期和时间类型。

```python
from datetime import datetime
print(datetime.now())  # 现在时间
```





### calendar 

- 日历相关函数

```python
# calendar.monthrange(year, month)
# 返回指定 年份 的指定 月份 的第一天是星期几和这个月的天数

import calendar
print(calendar.monthrange(2000,2))	# (1, 29)
```







### copy

- 浅层 (shallow) 和深层 (deep) 复制操作

```python
import copy
b=['a','b','c','d','e','f','g']
a=copy.deepcopy(b)
```





## 数字和数学模块

### math

- 数学函数

```python
# math.ceil(x)
# 返回 x 的上限，即大于或者等于 x 的最小整数

import math
print(math.ceil(2.25))	# 3
print(round(2.25))	# 2	  
# round()为四舍五入
```

```python
# math.floor(x)
# 返回 x 的向下取整，小于或等于 x 的最大整数

import math
print(math.floor(2.25))	# 2
```



```python
# math.pow(x, y)
# 将返回 x 的 y 次幂。
# 与内置的 ** 运算符不同， math.pow() 将其参数转换为 float 类型
# 使用 ** 或内置的 pow() 函数来计算精确的整数幂。

import math
print(math.pow(2,3))	# 8.0
print(2**3)				# 8
print(pow(2,3))			# 8
```

```python
# math.sqrt(x)
# 返回 x 的平方根

import math
print(math.sqrt(5))		# 2.23606797749979
```



```python
# math.fabs(x)
# 返回 x 的绝对值(float 浮点型)

import math
print(math.fabs(-3))	# 3.0
print(abs(-3))			# 3
```

```python
# math.fsum(iterable)
# 返回迭代中的精确浮点值。通过跟踪多个中间部分和来避免精度损失

>>> sum([.1, .1, .1, .1, .1, .1, .1, .1, .1, .1])
0.9999999999999999
>>> fsum([.1, .1, .1, .1, .1, .1, .1, .1, .1, .1])
1.0
```



```python
# math.modf(x)
# 返回 x 的小数和整数部分  两个结果都带有 x 的符号并且是浮点数

import math
print(math.modf(3))		# (0.0, 3.0)
print(math.modf(3.5))	# (0.5, 3.0)
```



```python
# math.copysign(x, y)
# 返回一个基于 x 的绝对值和 y 的符号的浮点数

import math
print(math.copysign(1.0, -0.0))		# -1.0
```



```python
# math.factorial(x)
# 以一个整数返回 x 的阶乘。 如果 x 不是整数或为负数时则将引发 ValueError。

import math
print(math.factorial(4))		# 24      1*2*3*4
print(math.factorial(5))		# 120	  1*2**3*4*5
```



### random 

- 生成伪随机数

```python
# random.randrange(stop)
# random.randrange(start, stop[, step])
# 从 range(start, stop, step) 返回一个随机选择的元素
# 这相当于 choice(range(start, stop, step)) ，但实际上并没有构建一个 range 对象。
```

```python
# random.randint(a, b)
# 返回随机整数 N 满足 a <= N <= b
# 相当于 randrange(a, b+1)。
```



```python
# random.uniform(a, b)
# 返回一个随机浮点数 N ，当 a <= b 时 a <= N <= b ，当 b < a 时 b <= N <= a 
# 取决于等式 a + (b-a) * random() 中的浮点舍入，终点 b 可以包括或不包括在该范围内
```



```python
# random.choice(seq)
# 从非空序列 seq 返回一个随机元素。 如果 seq 为空，则引发 IndexError。
```

```python
# random.shuffle(x[, random])
# 将序列 x 随机打乱位置。
```



## 函数式编程模块 

### functools

- 高阶函数和可调用对象上的操作

```python
# reduce()
from functools import reduce

# functools.reduce(function, iterable[, initializer])
# 将两个参数的 function 从左至右积累地应用到 iterable 的条目，以便将该可迭代对象缩减为单一的值。

>>>reduce(lambda x, y: x+y, [1, 2, 3, 4, 5])
15	# ((((1+2)+3)+4)+5)
```

## 文件和目录访问

### os.path

- 常用路径操作

```python
# os.path.abspath(path)
# 返回路径 path 的绝对路径（标准化的）
# 在大多数平台上，这等同于用 normpath(join(os.getcwd(), path)) 的方式调用 normpath() 函数。
```



```python
# os.path.basename(path)
# 返回路径 path 的基本名称
# 这是将 path 传入函数 split() 之后，返回的一对值中的第二个元素。请注意，此函数的结果与Unix basename 程序不同, basename 在 '/foo/bar/' 上返回 'bar'，而 basename() 函数返回一个空字符串 ('')。
```

```python
# os.path.dirname(path)
# 返回路径 path 的目录名称
# 这是将 path 传入函数 split() 之后，返回的一对值中的第一个元素。
```



```python
# os.path.join(path, *paths)
# 智能地拼接一个或多个路径部分
# 返回值是 path 和 *paths 的所有成员的拼接，其中每个非空部分后面都紧跟一个目录分隔符，最后一个部分除外，这意味着如果最后一个部分为空，则结果将以分隔符结尾
# 如果某个部分为绝对路径，则之前的所有部分会被丢弃并从绝对路径部分开始继续拼接。
```



```python
# os.path.splitext(path)
# 将路径名称 path 拆分为 (root, ext) 对使得 root + ext == path，并且扩展名 ext 为空或以句点打头并最多只包含一个句点。
# 如果路径 path 不包含扩展名，则 ext 将为 '':
```



```python
# os.path.getsize(path)
# 返回 path 的大小，以字节为单位
# 如果该文件不存在或不可访问，则抛出 OSError 异常。
```

```python
# os.path.getatime(path)
# 返回 path 的最后访问时间
# 返回值是一个浮点数，为纪元秒数（参见 time 模块）
# 如果该文件不存在或不可访问，则抛出 OSError 异常。

```

```python
# os.path.getmtime(path)
# 返回 path 的最后修改时间
# 返回值是一个浮点数，为纪元秒数（参见 time 模块）
# 如果该文件不存在或不可访问，则抛出 OSError 异常。
```

```python
# os.path.getctime(path)
# 返回 path 在系统中的 ctime，在有些系统（比如 Unix）上，它是元数据的最后修改时间，其他系统（比如 Windows）上，它是 path 的创建时间
# 返回值是一个数，为纪元秒数（参见 time 模块）
# 如果该文件不存在或不可访问，则抛出 OSError 异常。
```



```python
# os.path.isfile(path)
# 如果 path 是 现有的 常规文件，则返回 True
# 本方法会跟踪符号链接，因此，对于同一路径，islink() 和 isfile() 都可能为 True。
```

```python
# os.path.isdir(path)
# 如果 path 是 现有的 目录，则返回 True
# 本方法会跟踪符号链接，因此，对于同一路径，islink() 和 isdir() 都可能为 True。
```



```python
# os.path.exists(path)
# 如果 path 指向一个已存在的路径或已打开的文件描述符，返回 True。对于失效的符号链接，返回 False
# 在某些平台上，如果使用 os.stat() 查询到目标文件没有执行权限，即使 path 确实存在，本函数也可能返回 False。
```



```python
# os.path.samefile(path1, path2)
# 如果两个路径都指向相同的文件或目录，则返回 True。
```



### shutil 

- 高阶文件操作

```python
# shutil.copy(src, dst, *, follow_symlinks=True)
# 将文件 src 拷贝到文件或目录 dst。 src 和 dst 应为 路径类对象 或字符串
# 如果 dst 指定了一个目录，文件将使用 src 中的基准文件名拷贝到 dst 中
# 将返回新创建文件所对应的路径。
```

```python
# shutil.copy2(src, dst, *, follow_symlinks=True)
# 类似于 copy()，区别在于 copy2() 还会尝试保留文件的元数据(操作时间,权限)
```



```python
# shutil.move(src, dst, copy_function=copy2)
# 递归地将一个文件或目录 (src) 移至另一位置 (dst) 并返回目标位置
```



```python
# shutil.copytree(src, dst, symlinks=False, ignore=None, copy_function=copy2, ignore_dangling_symlinks=False, dirs_exist_ok=False)
# 将以 src 为根起点的整个目录树拷贝到名为 dst 的目录并返回目标目录(dst不存在)
```

```python
# shutil.rmtree(path, ignore_errors=False, onerror=None)
# 删除一个完整的目录树；path 必须指向一个目录（但不能是一个目录的符号链接）
```



```python
# shutil.make_archive(base_name, format[, root_dir[, base_dir[, verbose[, dry_run[, owner[, group[, logger]]]]]]])
# 创建一个归档文件（例如 zip 或 tar）并返回其名称。

# base_name 是要创建的文件名称，包括路径，去除任何特定格式的扩展名
# format 是归档格式：为 "zip" (如果 zlib 模块可用), "tar", "gztar" (如果 zlib 模块可用), "bztar" (如果 bz2 模块可用) 或 "xztar" (如果 lzma 模块可用) 中的一个。
# root_dir 是一个目录，它将作为归档文件的根目录，归档中的所有路径都将是它的相对路径；例如，我们通常会在创建归档之前用 chdir 命令切换到 root_dir。
# base_dir 是我们要执行归档的起始目录；也就是说 base_dir 将成为归档中所有文件和目录共有的路径前缀。 base_dir 必须相对于 root_dir 给出。 

# root_dir 和 base_dir 默认均为当前目录。


import shutil
shutil.make_archive('a','zip','./')
```





## 数据持久化

### pickle 

- Python 对象序列化

```python
# pickle.dump(obj, file, protocol=None, *, fix_imports=True, buffer_callback=None)
# 将对象 obj 封存以后的对象写入已打开的 file object file
# 它等同于 Pickler(file, protocol).dump(obj)

import pickle
a=['鸢一折纸','五河琴里','夜刀神十香']
b=pickle.dump(a,open('01.txt','wb'))
```

```python
# pickle.dumps(obj, protocol=None, *, fix_imports=True, buffer_callback=None)
# 将 obj 封存以后的对象作为 bytes 类型直接返回，而不是将其写入到文件
import pickle
a=['鸢一折纸','五河琴里','夜刀神十香']
b=pickle.dumps(a)
print(pickle.loads(b))
```



```python
# pickle.load(file, *, fix_imports=True, encoding="ASCII", errors="strict", buffers=None)
# 从已打开的 file object 文件 中读取封存后的对象，重建其中特定对象的层次结构并返回
# 它相当于 Unpickler(file).load()。

import pickle
# a=['鸢一折纸','五河琴里','夜刀神十香']
# b=pickle.dump(a,open('01.txt','wb'))
c=pickle.load(open('01.txt','rb'))
print(c,type(c))		# ['鸢一折纸', '五河琴里', '夜刀神十香'] <class 'list'>
```

```python
# pickle.loads(data, /, *, fix_imports=True, encoding="ASCII", errors="strict", buffers=None)
# 重建并返回一个对象的封存表示形式 data 的对象层级结构。 data 必须为 bytes-like object。
import pickle
a=['鸢一折纸','五河琴里','夜刀神十香']
b=pickle.dumps(a)
print(pickle.loads(b))
```



## 数据压缩和存档

### zipfile

- 使用ZIP存档

```python
class zipfile.ZipFile(file, mode='r', compression=ZIP_STORED, allowZip64=True, compresslevel=None, *, strict_timestamps=True)
# 打开一个 ZIP 文件，file 为一个指向文件的路径（字符串），一个类文件对象或者一个 path-like object。
# 形参 mode 应当为 'r' 来读取一个存在的文件，'w' 来截断并写入新的文件， 'a' 来添加到一个存在的文件，或者 'x' 来仅新建并写入新的文件
# 如果 mode 为 'x' 并且 file 指向已经存在的文件，则抛出 FileExistsError
# 如果 mode 为 'a' 且 file 为已存在的文件，则格外的文件将被加入。如果 file 不指向 ZIP 文件，之后一个新的 ZIP 归档将被追加为此文件。这是为了将 ZIP 归档添加到另一个文件（例如 python.exe）
# 如果 mode 为 'a' 并且文件不存在， 则会新建
# 如果 mode 为 'r' 或 'a'， 则文件应当可定位。
```

```python
# 压缩文件
import zipfile

with zipfile.ZipFile('spam.zip', 'w') as myzip:
    myzip.write('eggs.txt')
```

```python
import zipfile,os

with zipfile.ZipFile('spam.zip', 'w',zipfile.ZIP_DEFLATED) as mz:
    arr=os.listdir('./')
    for i in arr:
        mz.write(i)
```



```python
ZipFile.extract(member, path=None, pwd=None)
# 从归档中提取出一个成员放入当前工作目录；member 必须为成员的完整名称或 ZipInfo 对象。 成员的文件信息会尽可能精确地被提取。 path 指定一个要提取到的不同目录。 member 可以是一个文件名或 ZipInfo 对象。 pwd 是用于解密文件的密码。
# 返回所创建的经正规化的路径（对应于目录或新文件）。

ZipFile.extractall(path=None, members=None, pwd=None)
# 从归档中提取出所有成员放入当前工作目录。 path 指定一个要提取到的不同目录。 members 为可选项且必须为 namelist() 所返回列表的一个子集。 pwd 是用于解密文件的密码。
```

```python
# 解压文件
import zipfile

with zipfile.ZipFile('spam.zip', 'r') as mz:
    mz.extractall('./')
```



## 互联网数据处理 

### JSON

- JSON 编码和解码器

```python
# json.dump(obj, fp, *, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, default=None, sort_keys=False, **kw)
# 使用这个 转换表 将 obj 序列化为 JSON 格式化流形式的 fp (支持 .write() 的 file-like object)。
```

```python
# json.dumps(obj, *, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, default=None, sort_keys=False, **kw)
# 使用这个 转换表 将 obj 序列化为 JSON 格式的 str。 其参数的含义与 dump() 中的相同。
```



```python
# json.load(fp, *, cls=None, object_hook=None, parse_float=None, parse_int=None, parse_constant=None, object_pairs_hook=None, **kw)
# 使用这个 转换表 将 fp (一个支持 .read() 并包含一个 JSON 文档的 text file 或者 binary file) 反序列化为一个 Python 对象
```

```python
# json.loads(s, *, cls=None, object_hook=None, parse_float=None, parse_int=None, parse_constant=None, object_pairs_hook=None, **kw)
# 将 s (一个包含 JSON 文档的 str, bytes 或 bytearray 实例) 反序列化为 Python 对象
```



## 通用操作系统服务

### os

- 多种操作系统接口

```python
# os.getcwd()
# 返回表示当前工作目录的字符串。
```



```python
# os.chdir(path)
# 将当前工作目录更改为 path

import os
os.chdir('E:\\')
print(os.getcwd())	# E:\
```



```python
# os.listdir(path='.')
# 返回一个包含由 path 指定目录中条目名称组成的列表。
# 该列表按任意顺序排列，并且不包括特殊条目 '.' 和 '..'，即使它们存在于目录中
# 如果有文件在调用此函数期间在被移除或添加到目录中，是否要包括该文件的名称并没有规定。
```



```python
# os.mkdir(path, mode=0o777, *, dir_fd=None)
# 创建一个名为 path 的目录，应用以数字表示的权限模式 mode。
# 如果目录已存在，则抛出 FileExistsError 异常。
```

```python
# os.makedirs(name, mode=0o777, exist_ok=False)
# 递归目录创建函数。与 mkdir() 类似，但会自动创建到达最后一级目录所需要的中间目录。
```



```python
# os.rmdir(path, *, dir_fd=None)
# 移除（删除）目录 path
# 如果目录不存在或不为空，则会分别抛出 FileNotFoundError 或 OSError 异常
# 要删除整个目录树，可以使用 shutil.rmtree()。
```

```python
# os.removedirs(name)
# 递归删除目录。工作方式类似于 rmdir()，不同之处在于，如果成功删除了末尾一级目录，removedirs() 会尝试依次删除 path 中提到的每个父目录，直到抛出错误为止（但该错误会被忽略，因为这通常表示父目录不是空目录）
# 例如，os.removedirs('foo/bar/baz') 将首先删除目录 'foo/bar/baz'，然后如果 'foo/bar' 和 'foo' 为空，则继续删除它们。如果无法成功删除末尾一级目录，则抛出 OSError 异常。
```



```python
# os.remove(path, *, dir_fd=None)
# 移除（删除）文件 path。 
# 如果 path 是目录，则会引发 IsADirectoryError。 使用 rmdir() 来删除目录。 
# 如果文件不存在，则会引发 FileNotFoundError。
```



```python
# os.rename(src, dst, *, src_dir_fd=None, dst_dir_fd=None)
# 将文件或目录 src 重命名为 dst。如果 dst 已存在，则下列情况下将会操作失败，并抛出 OSError 的子类：
# 在 Windows 上，如果 dst 已存在，则抛出 FileExistsError 异常。
```



```python
# os.system(command)
# 在子外壳程序中执行此命令（一个字符串）
# 这是通过调用标准 C 函数 system() 来实现的，并受到同样的限制
```





### time

- 时间的访问和转换

```python
# time.time() → float
# 返回以浮点数表示的从 epoch 开始的秒数的时间值。 
# epoch 的具体日期和 leap seconds 的处理取决于平台。 在 Windows 和大多数 Unix 系统中， epoch 是 1970 年 1 月 1 日 00:00:00 (UTC)，并且闰秒将不计入从 epoch 开始的秒数。 这通常被称为 Unix 时间。 要了解给定平台上 epoch 的具体定义，请查看 gmtime(0)。
```

```python
# time.ctime([secs])
# 转换以距离初始纪元的秒数表示的时间为以下形式的字符串
# 例: 'Sun Jun 20 23:21:05 1993' 代表本地时间
# 日期字段的长度为两个字符，如果日期只有一个数字则会以零填充，例如: 'Wed Jun  9 04:26:40 1993'。
```

```python
# time.localtime([secs])
# 返回时间元组
# 与 gmtime() 相似但转换为当地时间。如果未提供 secs 或为 None ，则使用由 time() 返回的当前时间。当 DST 适用于给定时间时，dst标志设置为 1 。

import time
res=time.localtime()
print(f'{res.tm_year}年{res.tm_mon}月{res.tm_mday}日 {res.tm_hour}时{res.tm_min}分{res.tm_sec}秒 星期{res.tm_wday+1}')
```

```python
# time.strftime(format[, t])
# 转换一个元组或 struct_time 表示的由 gmtime() 或 localtime() 返回的时间到由 format 参数指定的字符串
# 如果未提供 t ，则使用由 localtime() 返回的当前时间。 format 必须是一个字符串。如果 t 中的任何字段超出允许范围，则引发 ValueError 

import time
res=time.strftime('%Y-%m-%d %H:%M:%S')
print(res)

```



```python
# time.sleep(secs)
# 调用该方法的线程将被暂停执行 secs 秒。参数可以是浮点数，以表示更为精确的睡眠时长。由于任何捕获到的信号都会终止 sleep() 引发的该睡眠过程并开始执行信号的处理例程，因此实际的暂停时长可能小于请求的时长；此外，由于系统需要调度其他活动，实际暂停时长也可能比请求的时间长。
```



```python
# time.perf_counter() → float
# （以小数表示的秒为单位）返回一个性能计数器的值，即用于测量较短持续时间的具有最高有效精度的时钟。 它会包括睡眠状态所消耗的时间并且作用于全系统范围。 返回值的参考点未被定义，因此只有两次调用之间的差值才是有效的。

import time
start=time.perf_counter()
pass
end=start=time.perf_counter()
print(start-end)
```



## 软件打包和分发

### venv

- 创建虚拟环境

```shell
# 创建虚拟环境
python -m venv env
```

```shell
# 使用虚拟环境
.\env\Scripts\activate
```

```shell
# 退出虚拟环境
deactivate
```









## Python运行时服务

### sys 

- 系统相关的参数和函数

```python
# sys.path
# 一个由字符串组成的列表，用于指定模块的搜索路径
# 初始化自环境变量 PYTHONPATH，再加上一条与安装有关的默认路径
# 程序启动时将初始化本列表，列表的第一项 path[0] 目录含有调用 Python 解释器的脚本。如果脚本目录不可用（比如以交互方式调用了解释器，或脚本是从标准输入中读取的），则 path[0] 为空字符串，这将导致 Python 优先搜索当前目录中的模块。注意，脚本目录将插入在 PYTHONPATH 的条目*之前*。
# 程序可以随意修改本列表用于自己的目的。只能向 sys.path 中添加 string 和 bytes 类型，其他数据类型将在导入期间被忽略。
```



### abc

- 抽象基类

```python

```



### traceback

- 打印或检索堆栈回溯

```python

```




# 常用模块





## 数据库

### mysql-connector

```shell
pip install mysql-connector
```

```python
import mysql.connector

def model(sql):
    mydb = mysql.connector.connect(
      host="localhost",        
      user="root",             
      passwd="123456"         
      database="students_db"
    )
    mycursor = mydb.cursor()
    mycursor.execute(sql)
    myresult = mycursor.fetchall()
    mydb.commit()
    if myresult:
        return myresult
    else
        return mycursor.rowcount
```





### pymysql

```shell
pip install pymysql
```

```python
import pymysql,pymysql.cursors

def model(sql):
    connection = pymysql.connect(host='localhost',
                                user='root',
                                password='123456',
                                database='demo')
    with connection:
        cursor=connection.cursor() 
        row=cursor.execute(sql)
        data=cursor.fetchall()
        connection.commit()
        if data:
            return data 
        else:
            return row
```



## ----



```
%%timeit
执行多次,算平均时间

%%time
执行一次,显示时间
```



### pandas

- 数据预处理的数据分析库

### numpy

- 数值计算库

```python
pip install numpy
```



```python
# numpy.array()
# array(object, dtype=None, *, copy=True, order='K', subok=False, ndmin=0,like=None)
# 可通过dtype设置元素类型

import numpy
a=numpy.array([1,2,3],dtype=int)
```

```python
# 数组维度
a.ndim

```

```python
# 数组外形
a.shape
# 
```

### matplotlib

- 绘图库,数据可视化



### scikit-learn

- 机器学习库



# 数据科学

## 爬虫





- 主要通过`requests`

  ```python
  import requests
  url=''
  headers={'User-Agent':''}
  res=requests.get(url=url,headers=headers)		
  print(res)					# <Response [200]>
  print(res.url)				# 请求的url地址
  print(res.status_code)		# 请求状态码 200
  print(res.headers)			# 响应头信息 
  print(res.request.headers)	# 请求头信息
  print(res.content)			# 二进制文本流 b'...'
  print(res.text)				# 响应内容
  ```

#### headers配置

##### `User-Agent`

```python
import requests
url=''
headers={'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36 Edg/92.0.902.84'}

res=requests.get(url=url,headers=headers)	
```

#### post

```python
import requests

url='https://fanyi.baidu.com/sug'
headers={'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36 Edg/92.0.902.84'}
data={'kw':'你好'}
res=requests.post(url=url,headers=headers,data=data)
if res.status_code==200:
    print('请求成功')
    result=res.json()
    if result['errno']==0:
        print('响应成功')
        print(result)
```







## 数据分析





## 数据展示



# 网络编程

## Flask

```shell
# 1.安装Flask
pip install flask
```





## Django

### 基本

```shell
# 1.安装Django
pip install django==<版本号>

# 2.创建项目
django-admin startproject <项目名>

# 3.启动项目(进入manage.py同级目录)(默认8000)
python manage.py runserver [<端口号>]
```

```shell
[auth]
    changepassword
    createsuperuser

[contenttypes]
    remove_stale_contenttypes

[django]
    check
    compilemessages
    createcachetable
    dbshell
    diffsettings
    dumpdata
    flush
    inspectdb
    loaddata
    makemessages
    makemigrations
    migrate
    sendtestemail
    shell
    showmigrations
    sqlflush
    sqlmigrate
    sqlsequencereset
    squashmigrations
    startapp
    startproject
    test
    testserver

[sessions]
    clearsessions

[staticfiles]
    collectstatic
    findstatic
    runserver
```

```python
# 初始目录
mysite/
    manage.py					# 管理 Django 项目的命令行工具
    mysite/
        __init__.py
        settings.py				# Django 项目的配置文件
        urls.py					# Django 项目的 URL 声明
        asgi.py					# 项目的运行在 ASGI 兼容的 Web 服务器上的入口
        wsgi.py					# 项目的运行在 WSGI 兼容的 Web 服务器上的入口
        
# 创建
	templates/
    static/
```



```python
LANGUAGE_CODE = 'zh-Hans'

TIME_ZONE = 'Asia/Shanghai'
```





### 应用

```shell
# 1.创建应用
python manage.py startapp <应用名>

# 2.在setting.py的INSTALLED_APPS中加入'<应用名>'
```

```python
# 初始目录
<应用名>/
	migrations/					# 迁移文件
        __init__.py
    __init__.py
    admin.py					# 后台
    apps.py						# 应用配置
    models.py					# 模型(数据库配置)
    tests.py					# 测试用
    views.py					# 视图函数
     
# 创建
	templates/					# 模板文件夹(html)
	urls.py						# 子路由
    
```





### 模板层(T)

#### 模板语法

##### 变量

```django
{{ my_dict.key }}
{{ my_object.attribute }}
{{ my_list.0 }}
```



##### 标签

###### `for`

```django
<ul>
{% for athlete in athlete_list %}
    <li>{{ athlete.name }}</li>
{% empty %}
    <h1>可迭代对象为空是显示</h1>
{% endfor %}
</ul>
```

for 循环设置了一组可以在循环体内直接使用的变量：

| 变量名                | 描述                                             |
| --------------------- | ------------------------------------------------ |
| `forloop.counter`     | 循环计数器，表示当前循环的索引（从 `1` 开始）    |
| `forloop.counter0`    | 循环计数器，表示当前循环的索引（从 `0` 开始）    |
| `forloop.revcounter`  | 反向循环计数器（以最后一次循环为 `1`，反向计数） |
| `forloop.revcounter0` | 反向循环计数器（以最后一次循环为 `0`，反向计数） |
| `forloop.first`       | 当前循环为首个循环时，该变量为 True              |
| `forloop.last`        | 当前循环为最后一个循环时，该变量为 True          |
| `forloop.parentloop`  | 在嵌套循环中，指向当前循环的上级循环             |



###### `if`

```django
{% if athlete_list %}
    Number of athletes: {{ athlete_list|length }}
{% elif athlete_in_locker_room_list %}
    Athletes should be out of the locker room soon!
{% else %}
    No athletes.
{% endif %}
```



###### `url`

- url反向解析

```django
{% url 'some-url-name' v1 v2 %}
<!--v1 v2 填充到path转换器 -->

{% url 'some-url-name' arg1=v1 arg2=v2 %}
```





###### `csrf_token`

- 用于 CSRF 保护

```django
<form method="post">
    {% csrf_token %}
</form>
```



###### `static`

- 要链接到保存在 `STATIC_ROOT` 中的静态文件，Django 有一个 `static` 模板标签。如果安装了 `django.contrib.staticfiles`应用程序，该标签将使用 `STATICFILES_STORAGE`指定的存储空间的 `url()` 方法来提供文件

```django
{% load static %}
<img src="{% static 'images/hi.jpg' %}" alt="Hi!">xxxxxxxxxx static{% load static %}<img src="{% static 'images/hi.jpg' %}" alt="Hi!">
```



##### 过滤器

###### `lower`

- 将一个字符串转换为全小写

```django
{{ value|lower }}
<!--Totally LOVING this Album!	-> totally loving this album! -->
```



###### `upper`

- 将一个字符串转换为全大写

```django
{{ value|upper }}
<!--Joel is a slug	-> JOEL IS A SLUG -->
```



###### `safe`

- 标记一个字符串在输出前不需要进一步的 HTML 转义
- 当自动转义关闭时，该过滤器没有效果
- 使用链式过滤器，在 safe 之后应用的过滤器会使内容再次不安全

```django
<script>alert(111);</script>   
	--safe ->	执行			   
	--转义 ->	   &lt;script&gt;alert(111);&lt;/script&gt;
```



###### `add`

- 将参数添加到值中

```django
<!--  -->

{{ value|add:"2" }}
<!-- 4	->  6 -->

{{ first|add:second }}
<!-- first 是 [1, 2, 3] 并且 second 是 [4, 5, 6]，则输出为 [1, 2, 3, 4, 5, 6] -->
```



###### `truncatechars`

- 如果一个字符串的长度超过指定的字符数，则截断它
- 截断后的字符串将以一个可翻译的省略号（“...”）结束
- **参数**： 要截断的字符数

```django
{{ value|truncatechars:7 }}
<!-- 如果 value 是 "Joel is a slug"，则输出将是 "Joel i…" -->
```





###### `date`

- 根据给定的格式设置日期。

```django
{{ value|date:"D d M Y" }}
<!-- 如果 value 是一个 datetime 对象（例如，datetime.datetime.datetime.now() 的结果），输出将是字符串 'Wed 09 Jan 2008' 
```



##### 继承

###### `extends`

- 表示该模板扩展了一个父模板

```django
{% extends "base.html" %}
<!--（带引号）使用字面值 "base.html" 作为要扩展的父模板的名称-->

{% extends variable %}
<!--如果变量的值是一个字符串，Django 将使用这个字符串作为父模板的名称。如果变量的值是一个 Template 对象，Django 将使用该对象作为父模板-->
```



###### `block`

- 定义一个可以被子模板覆盖的块

```django
<!--父-->
	<div class="ex">
        {% block info %}
            <h2>123sd456</h2>
        {% endblock %}
    </div>
```

```django
<!--子-->
{% extends 'home/base.html' %} 

{% block info %}
45454
{% endblock  %}
```



#### templates配置

- 存放模板(html)

```python
# 1.在manage.py同级目录创建templates目录

# 2.配置setting.py
TEMPLATES = [{'DIRS': [os.path.join(BASE_DIR,"templates")],},]
```

```python
# 在应用中创建templates目录
# 'APP_DIRS': True且应用加入INSTALLED_APPS
# 优先级不如项目的(优先查找项目的,找不到再找应用的)
```



#### static配置

- 存放静态文件

```python
# 1.在manage.py同级目录创建static目录

# 2.配置setting.py
STATIC_URL = '/static/'
STATICFILES_DIRS=[os.path.join(BASE_DIR,"static")]

# 3.导入
# <link rel="stylesheet" href="/static/a.css">
```





### 视图层(V)

#### 创建视图

- 通过视图函数载入模板,创建视图
- 在`views.py`中配置

```python
"""
Function views
"""
from django.shortcuts import render

def index(request):
    return render(request, 'home/index.html')
```

```python
""""
Class-based views
""""


```



#### 路由调度

- 为视图配置url
- 在`urls.py`中配置

```python
"""
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
"""
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

```python
""""
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
""""
models.Administrators.objects.create(username='chen',password='e10adc3949ba59abbe56e057f20f883e')
```

```python
"""
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path,include

urlpatterns = [
    path('',include('home.urls'))
]
```



##### `django.urls` 函数

###### `path()`

```python
# path(route, view, kwargs=None, name=None)
# 返回一个元素，以便包含在 urlpatterns 中

from django.urls import include, path

urlpatterns = [
    path('index/', views.index, name='main-view'),
    path('bio/<username>/', views.bio, name='bio'),
    path('articles/<slug:title>/', views.article, name='article-detail'),
    path('articles/<slug:title>/<int:section>/', views.section, name='article-section'),
    path('weblog/', include('blog.urls')),
    ...
]

#route 参数应该是一个字符串或 gettext_lazy() ，它包含一个 URL 模式

# 这个字符串可以包含角括号（就像上面的 <username>）来捕获 URL 的一部分，并将其作为关键字参数发送给视图(接收时以username形式接收)
# 角括号可以包含一个转换器规格（像 <int:section> 的 int 部分），它限制了匹配的字符，也可以改变传递给视图的变量的类型
# 例如，<int:section> 匹配一串十进制数字，并将值转换为 int

# str - 匹配除了 '/' 之外的非空字符串。如果表达式内不包含转换器，则会默认匹配字符串。
# int - 匹配 0 或任何正整数。返回一个 int 。
# slug - 匹配任意由 ASCII 字母或数字以及连字符和下划线组成的短标签。比如，building-your-1st-django-site 。
# uuid - 匹配一个格式化的 UUID 。为了防止多个 URL 映射到同一个页面，必须包含破折号并且字符都为小写。比如，075194d3-6885-417e-a8a8-6c931e272f00。返回一个 UUID 实例。
# path - 匹配非空字段，包括路径分隔符 '/' 。它允许你匹配完整的 URL 路径而不是像 str 那样匹配 URL 的一部分

#view 参数是一个视图函数或 as_view() 的结果，用于基于类的视图。它也可以是一个 django.urls.include()。

# kwargs 参数允许你向视图函数或方法传递附加参数。参见 传递额外选项给视图函数 的例子

# 模板中可通过name跳转
```



###### `re_path()`

```python
# re_path(route, view, kwargs=None, name=None)
# 返回一个元素，以便包含在 urlpatterns 中

# (?P<name>p)

from django.urls import include, re_path

urlpatterns = [
    re_path(r'^index/$', views.index, name='index'),
    re_path(r'^bio/(?P<username>\w+)/$', views.bio, name='bio'),
    re_path(r'^weblog/', include('blog.urls')),
    ...
]

# route 参数应该是一个字符串或 gettext_lazy() ，它包含一个与 Python 的 re 模块兼容的正则表达式
# 字符串通常使用原始字符串语法（r''），因此它们可以包含像 /d 这样的序列，而不需要用另一个反斜杠来转义
# 当进行匹配时，从正则表达式中捕获的组会被传递到视图中 —— 如果组是命名的，则作为命名的参数，否则作为位置参数。值以字符串的形式传递，不进行任何类型转换。

# view、kwargs 和 name 参数与 path() 相同。
```



###### `include()`

```python
# include(module, namespace=None)
# include(pattern_list)
# include((pattern_list, app_namespace), namespace=None)

# 一个函数它接收一个完整的 Python 导入路径到另一个应该被 “包含” 在这里的 URLconf 模块
# 可以选择指定 application namespace 和 instance namespace，在这两个空间中，条目将被包含进去
```



###### `reverse()`

```python
# reverse(viewname, urlconf=None, args=None, kwargs=None, current_app=None)
# viewname 可以是一个 URL 模式名称 或者是可调用的视图对象。

from news import views
path('archive/', views.archive, name='news-archive')
你可以使用以下任何一种方式来反查 URL：

# using the named URL
reverse('news-archive')

# passing a callable object
# (This is discouraged because you can't reverse namespaced views this way.)
from news import views
reverse(views.archive)
```





##### `django.conf.urls` 函数

```

```







#### `HttpRequest` 

- 当一个页面被请求时，Django 会创建一个 `HttpRequest` 对象，这个对象包含了请求的元数据。然后，Django 加载相应的视图，将 `HttpRequest `作为视图函数的第一个参数。每个视图负责返回一个 `HttpResponse` 对象。
- 

###### `path_info`

```python
request.path_info
#URL字符串
```



###### `method`

```python
HttpRequest.method
# 代表请求中使用的 HTTP 方法的字符串。保证是大写字母

if request.method == 'GET':
    do_something()
elif request.method == 'POST':
    do_something_else()
```



###### `GET`

```python
HttpRequest.GET
# 一个类似字典的对象，包含所有给定的 HTTP GET 参数

id=request.GET['id']			# 如果键不存在,报错 

id=request.GET.get('id') 
id=request.GET.get('id','666')	# 如果键不存在，则用钩子返回一个默认值

a=request.GET.getlist('a')	# 复选框
# ?a=1&a=2   ->  ['1','2']
```



###### `POST`

```python
HttpRequest.POST
# 一个类似字典的对象，包含所有给定的 HTTP POST 参数，前提是请求包含表单数据

data=request.POST.dict()
id=data.pop('id')
```



###### `FILES`

```python
HttpRequest.FILES
# 一个类似字典的对象，包含所有上传的文件
# FILES 中的每个键是 <input type="file" name=""> 中的 name
# FILES 中的每个值是一个 UploadedFile

file=request.FILES.get("img_url",None)
```







#### `HttpResponse`



###### `render()`

```python
render(request, template_name, context=None, content_type=None, status=None, using=None)
# 便捷函数
# 将给定的模板与给定的上下文字典组合在一起，并以渲染的文本返回一个 HttpResponse 对象

def index(request):
    '''主页'''
    return render(request, 'home/index.html',{'data':99})
```



###### `JsonResponse`

```python
class JsonResponse(data, encoder=DjangoJSONEncoder, safe=True, json_dumps_params=None, **kwargs)
# 一个 HttpResponse 子类，帮助创建一个 JSON 编码的响应
# 它继承了它的超类的大部分行为，但有一些不同：
# 其默认的 Content-Type 头设置为 application/json
# 第一个参数 data 应该是 dict 实例
# 如果 safe 参数设置为 False ，它可以是任何 JSON 可序列化的对象

def test(request):
    return JsonResponse({"a":"65"})
```



### 模型层(M)

#### 数据库配置

- 在`setting.py`中

##### mysql

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '<连接的库>',
        'USER':'root',
        'PASSWORD':'123456',
        'HOST':'localhost',
        'PORT':'3306'
    }
}
```



#### 定义模型

```python
from django.db import models

# Create your models here.
class Stu(models.Model):
    name=models.CharField(max_length=20)
    age=models.IntegerField(default=24)
    sex=models.CharField(max_length=1,default="0")
    address=models.CharField(max_length=50,null=True)

```

##### 字段类型

###### CharField

- 字符串字段

```python
class CharField(max_length=None, **options)
# 一个字符串字段，适用于小到大的字符串。
# 对于大量的文本，使用 TextField。
# 该字段的默认表单部件是一个 TextInput

# CharField 有两个额外的参数：

# CharField.max_length
# 必须的。该字段的最大长度（以字符为单位）。max_length 在数据库层面强制执行，在 Django 的验证中使用 MaxLengthValidator。

# CharField.db_collation(New in Django 3.2.)
# 可选的。该字段的数据库字符序名称。
```



###### TextField

- 大的文本字段

```python
class TextField(**options)
# 一个大的文本字段。该字段的默认表单部件是一个 Textarea。

# 如果指定了 max_length 属性，它将反映在自动生成的表单字段的 Textarea 部件中。但是，它并没有在模型或数据库层面被强制执行。使用一个 CharField 来实现。
```





###### AutoField

- 自增Id

```python
class AutoField(**options)
# 一个 IntegerField，根据可用的 ID 自动递增
#通常不需要直接使用它；如果没有指定，主键字段会自动添加到模型中
```



###### IntegerField

- 整数

```python
class IntegerField(**options)
# 一个整数
# 从 -2147483648 到 2147483647 的值在 Django 支持的所有数据库中都是安全的。

# 使用 MinValueValidator 和 MaxValueValidator 根据默认数据库支持的值来验证输入。
# 当 localize 为 False 时是 NumberInput 否则，该字段的默认表单部件是 TextInput。
```



###### FloatField

- 浮点数

```python
class FloatField(**options)
# 在 Python 中用一个 float 实例表示的浮点数。

# 当 localize 为 False 时是 NumberInput 否则，该字段的默认表单部件是 TextInput。
```



###### DecimalField

- 固定精度的十进制数

```python
class DecimalField(max_digits=None, decimal_places=None, **options)
#一个固定精度的十进制数，在 Python 中用一个 Decimal 实例来表示。它使用 DecimalValidator 验证输入。

# 有两个 必要的 参数：
# DecimalField.max_digits
# 数字中允许的最大位数。请注意，这个数字必须大于或等于 decimal_places。

# DecimalField.decimal_places
# 与数字一起存储的小数位数。

#例如，如果要存储精度为小数点后两位的 999 的数字，你可以使用：
models.DecimalField(..., max_digits=5, decimal_places=2)
```



###### BooleanField

- true／false

```python
class BooleanField(**options)
# 一个 true／false 字段。

# 该字段的默认表单部件是 CheckboxInput，或者如果 null=True 则是 NullBooleanSelect。

# 当 Field.default 没有定义时，BooleanField 的默认值是 None。
```



###### DateField

- 日期

```python
class DateField(auto_now=False, auto_now_add=False, **options)
# 一个日期，在 Python 中用一个 datetime.date 实例表示。有一些额外的、可选的参数。

# DateField.auto_now
# 每次保存对象时，自动将该字段设置为现在。对于“最后修改”的时间戳很有用。请注意，当前日期 总是 被使用，而不仅仅是一个你可以覆盖的默认值。
# 只有在调用 Model.save() 时，该字段才会自动更新。当以其他方式对其他字段进行更新时，如 QuerySet.update()，该字段不会被更新，尽管你可以在这样的更新中为该字段指定一个自定义值。

# DateField.auto_now_add
# 当第一次创建对象时，自动将该字段设置为现在。对创建时间戳很有用。请注意，当前日期是 始终 使用的；它不是一个你可以覆盖的默认值。因此，即使你在创建对象时为该字段设置了一个值，它也会被忽略。如果你想修改这个字段，可以设置以下内容来代替 auto_now_add=True ：

# 对于 DateField: default=date.today ——来自 datetime.date.today()
# 对于 DateTimeField: default=timezone.now ——来自 django.utils.timezone.now()

# 该字段的默认表单部件是一个 DateInput。管理中增加了一个 JavaScript 日历，以及“今天”的快捷方式。包含一个额外的 invalid_date 错误信息键。

#auto_now_add、auto_now 和 default 选项是相互排斥的。这些选项的任何组合都会导致错误。
```



###### DateTimeField

- 时间

```python
class DateTimeField(auto_now=False, auto_now_add=False, **options)¶
# 一个日期和时间，在 Python 中用一个 datetime.datetime 实例表示。与 DateField 一样，使用相同的额外参数。

# 该字段的默认表单部件是一个单独的 DateTimeInput。管理中使用两个单独的 TextInput 部件，并使用 JavaScript 快捷方式。
```



###### EmailField

- 邮箱

```python
class EmailField(max_length=254, **options)¶
#一个 CharField，使用 EmailValidator 来检查该值是否为有效的电子邮件地址。
```



###### ImageField

- 图片

```python
class ImageField(upload_to=None, height_field=None, width_field=None, max_length=100, **options)
# 继承 FileField 的所有属性和方法，但也验证上传的对象是有效的图像。

# 除了 FileField 的特殊属性外， ImageField 也有 height 和 width 属性。

# 为了方便查询这些属性，ImageField 有两个额外的可选参数。

# ImageField.height_field¶
# 模型字段的名称，每次保存模型实例时将自动填充图像的高度。

# ImageField.width_field¶
# 模型字段的名称，每次保存模型实例时将自动填充图像的宽度。

# 需要 Pillow 库。

# ImageField 实例在数据库中创建为 varchar 列，默认最大长度为 100 个字符。与其他字段一样，你可以使用 max_length 参数改变最大长度。

# 该字段的默认表单部件是一个 ClearableFileInput。
```









##### 字段选项

###### default

```python
Field.default
# 该字段的默认值。可以是一个值或者是个可调用的对象，如果是个可调用对象，每次实例化模型时都会调用该对象。

# 默认值不能是一个可更改的对象（模型实例、list、set 等），因为对该对象同一实例的引用将被用作所有新模型实例的缺省值。相反，将所需的默认值包裹在一个可调用对象中。例如，如果你想为 JSONField 指定一个默认的 dict，使用一个函数：
```



###### primary_key

```python
Field.primary_key
# 如果设置为 True ，将该字段设置为该模型的主键。

# 如果没有为模型中的任何字段指定 primary_key=True，Django 会自动添加一个字段来保存主键，所以不需要在任何字段上设置 primary_key=True，除非你想覆盖默认主键行为

# 自动创建的主键字段的类型可以在 AppConfig.default_auto_field 中为每个应用程序指定，或者在 DEFAULT_AUTO_FIELD 配置中全局指定

# primary_key=True 意味着 null=False 和 unique=True。一个对象只允许有一个主键。

# 主键字段是只读的。如果改变了现有对象的主键值，然后将其保存，则会在旧对象旁边创建一个新对象。
```



###### choices

```python
TYPE_CHOICE=[
        (SINGLE_CHOICE,'single choice'),
        (MULTIPLE_CHOICES,'multiple choice'),
        (JUDGMENT_QUESTION,'judgement'),
        (ESSAY_QUESTION,'essay')
    ]

class Question(models.Model):
    '''题目'''
    type=models.CharField(choices=TYPE_CHOICE,max_length=2,default=SINGLE_CHOICE)
```



###### blank

```python
Field.blank
# 如果是 True ，该字段允许为空。默认为 False 

# 注意，这与 null 不同。 null 纯属数据库相关，而 blank 则与验证相关
# 如果一个字段有 blank=True，表单验证将允许输入一个空值。如果一个字段有 blank=False，则该字段为必填字段
```



###### null

```python
Field.null
# 如果是 True， Django 将在数据库中存储空值为 NULL。默认为 False

# 避免在基于字符串的字段上使用 null，如 CharField 和 TextField
# 如果一个基于字符串的字段有 null=True，这意味着它有两种可能的“无数据”值
# NULL，和空字符串。在大多数情况下，“无数据”有两种可能的值是多余的，Django 的惯例是使用空字符串，而不是 NULL。一个例外是当一个 CharField 同时设置了 unique=True 和 blank=True。在这种情况下，null=True 是需要的，以避免在保存具有空白值的多个对象时违反唯一约束。

#无论是基于字符串的字段还是非字符串的字段，如果希望在表单中允许空值，还需要设置 blank=True，因为 null 参数只影响数据库的存储（参见 blank ）
```



###### unique

```python
Field.unique
#如果设置为 True，这个字段必须在整个表中保持值唯一。

# 这是在数据库级别和模型验证中强制执行的。如果试图保存一个在 unique 字段中存在重复值的模型，模型的 save() 方法将引发 django.db.IntegrityError。

# 除了 ManyToManyField 和 OneToOneField 之外，该选项对所有字段类型有效。

# 请注意，当 unique 为 True 时，你不需要指定 db_index，因为 unique 意味着创建一个索引。
```



###### db_index

```python
Field.db_index
# 如果是 True，将为该字段创建数据库索引
```



###### db_column

```python
Field.db_column

# 这个字段要使用的数据库列名。如果没有给出列名，Django 将使用字段名。

# 如果数据库列名是 SQL 的保留字，或者包含了 Python 变量名中不允许的字符——特别是连字符——那也没关系。Django 会在幕后引用列名和表名。
```



###### verbose_name

- 别名

```python
Field.verbose_name
# 字段的一个人类可读名称，如果没有给定详细名称，Django 会使用字段的属性名自动创建，并将下划线转换为空格
```





##### 关系字段

###### OneToOneField

- 一对一

```python
class OneToOneField(to, on_delete, parent_link=False, **options)
# 一对一的关系。概念上，这类似于 ForeignKey 与 unique=True，但关系的“反向”将直接返回一个单一对象
# 最有用的是作为某种方式“扩展”另一个模型的主键；多表继承 是通过添加一个从子模型到父模型的隐式一对一关系来实现的
# 需要一个位置参数：模型将与之相关的类。这与 ForeignKey 的工作原理完全相同，包括关于 递归 和 惰性 关系的所有选项。
# 如果没有为 OneToOneField 指定 related_name 参数，Django 将使用当前模型的小写名作为默认值
# 当访问反向关系时，如果相关表中的条目不存在，就会引发一个 RelatedObjectDoesNotExist 异常。这是目标模型的 Model.DoesNotExist 异常的一个子类

from django.db import models
class Author(models.Model):
    name=models.CharField(verbose_name='姓名',max_length=11)
class Wife(models.Model):
    name=models.CharField(verbose_name='姓名',max_length=11)
    author=models.OneToOneField(Author,on_delete=models.CASCADE)
    
a=Author.objects.create(name='王先生') 
wife1=Wife.objects.create(name='王夫人',auhtor=a)		# 关联王先生obj
wife1=Wife.objects.create(name='王夫人',auhtor_id=1)	# 关联王先生对应主键值

# 正向查询(通过wife查author)
wife1.author.name

# 反向查询(通过author查wife)
a.wife.name
```



###### ForeignKey

- 一对多

- 参数

  - `ForeignKey.on_delete`

    当一个由 `ForeignKey`引用的对象被删除时，Django 将模拟 `on_delete` 参数所指定的 SQL 约束的行为

    - **CASCADE**

      级联删除。Django 模拟了 SQL 约束 ON DELETE CASCADE 的行为，也删除了包含 ForeignKey 的对象。

      `Model.delete()`在相关的模型上没有被调用，但是 `pre_delete` 和 `post_delete` 信号是为所有被删除的对象发送的。

    - **PROTECT**

      通过引发 `ProtectedError`，即 `django.db.IntegrityError`的子类，防止删除被引用对象

    - **SET_NULL**

      设置 `ForeignKey` 为空；只有当 `null`为 `True` 时，才有可能

```python
class ForeignKey(to, on_delete, **options)
# 一个多对一的关系。需要两个位置参数：模型相关的类和 on_delete 选项


class Publisher(models.Model):
    name=models.CharField(verbose_name='名称',max_length=50,)
class Book(models.Model):
    title=models.CharField(verbose_name='名称',max_length=11)
    publisher=models.ForeignKey(Publisher,on_delete=models.CASCADE)

pub1=Publisher.objects.create(name='清华大学出版社')
book1=Book.objects.create(title='Python',publisher=pub1)
book2=Book.objects.create(title='c',publisher_id=1)

# 正向查询(通过book查publisher)
book1.publisher.name

# 反向查询(通过publisher查book)
pub1.book_set.all()
```



###### ManyToManyField

- 多对多

```python 
class ManyToManyField(to, **options)
# 一个多对多的关系。需要一个位置参数：模型相关的类，它的工作原理与 ForeignKey 完全相同，包括 递归 和 惰性 关系。

# 可以通过字段的 RelatedManager 来添加、删除或创建相关对象

class Author(models.Model):
    name=models.CharField(verbose_name='姓名',max_length=11)
class Book(models.Model):
    title=models.CharField(verbose_name='书名',max_length=50)
    authors=models.ManyToManyField(Author)
    
author1=Author.objects.create(name='张三')
author2=Author.objects.create(name='李四')
book1=author1.book_set.create(title='Python')
author2.book_set.add(book1)

book2=Book.objects.create(title='Java')
author3=book2.authors.create(name='王五')
book2.authors.add(author1)

# 正向查询(y)
book1.authors.all()
book1.authors.filter()

# 反向查询
author1.book_set.all()
author1.book_set.filter()
```





##### Meta选项

模型的内部 `class Meta` 中为模型提供这些选项

```python
Options.db_table
# 用于模型的数据库表的名称
```

```python
Options.verbose_name
# 对象的可读名称，单数
```

```python
Options.verbose_name_plural
# 对象的复数名称
# 如果没有给定，Django 将使用 verbose_name + "s"

verbose_name_plural = "stories"
```



```python

```



```python

```











#### 数据迁移

- 迁移是 Django 将你对模型的修改（例如增加一个字段，删除一个模型）应用至数据库架构中的方式

```shell
# 基于模型的修改创建迁移()
python manage.py makemigrations
```

```shell
# 负责应用和撤销迁移()
python manage.py migrate
```







#### 模型使用

##### 增加

```python
# 插入数据
>>>from home.models import Stu
>>>data={'name':'李四','age':22,'sex':0,address:'江苏'}
>>>obj=Stu(**data)
>>>obj.save()	# 调用 save() 后才操作数据库
```



##### 删除

```python
# 删除数据(一个)(对模型实例操作)
>>>from home.models import Stu
>>>obj=Stu.objects.get(id=1)
>>>obj.delete()
```

```python
# 删除数据(批量)(对QuerySet操作)

delete()
# 对 QuerySet 中的所有行执行 SQL 删除查询，并返回删除的对象数量和每个对象类型的删除数量的字典

>>> Entry.objects.filter(blog=b).delete()
```



##### 修改

```python
# 修改数据(一个)(查-改-存)
>>>from home.models import Stu
>>>obj=Stu.objects.get(id=1)
>>>obj.name='耶梦加得'
>>>obj.save()
```

```python
update(**kwargs)
# 修改数据(批量)(对QuerySet操作)
# 对指定的字段执行 SQL 更新查询，并返回匹配的行数（如果有些行已经有了新的值，则可能不等于更新的行数）

>>> Entry.objects.filter(pub_date__year=2010).update(comments_on=False)
```



##### 查询

```python
all()
# 查询数据(全部)(返回模型实例组成的QuerySet)
# 返回当前 QuerySet （或 QuerySet 子类）的 副本

>>>from home.models import Books
>>>Books.objects.all()
<QuerySet [<Books: Books object (1)>, <Books: Books object (2)>]>
```

```python
values(*fields, **expressions)
# 查询数据(全部)(返回字典组成的QuerySet)
# 返回一个 QuerySet，当用作可迭代对象时，返回字典，而不是模型实例

>>>from home.models import Books
>>>Books.objects.values()
<QuerySet [{'id': 1, name:'python'}, {'id': 2,name:'django' }]>
>>>Books.objects.values('id')
<QuerySet [{'id': 1}, {'id': 2}]>
```

```python
values_list(*fields, flat=False, named=False)
# 查询数据(全部)(返回元组组成的QuerySet)
# 与 values() 类似，只是在迭代时不返回字典，而是返回元组

>>>from home.models import Books
>>>Books.objects.values_list()
<QuerySet [(1, 'python'), (20, 'django')]>
>>>Books.objects.values_list('id')
<QuerySet [(1,), (2,)]>
```



```python
get(*args, **kwargs)
# 查询数据(一个)(返回模型实例)
# 返回与给定的查找参数相匹配的对象，没有报错

>>>from home.models import Books
>>>Books.objects.get(id='1')
<Books: Books object (1)>
```



```python
filter(*args, **kwargs)
# 查询数据(部分)(返回模型实例组成的QuerySet)
# 返回一个新的 QuerySet，其中包含与给定查找参数相匹配的对象。

>>>from home.models import Books
>>>Books.objects.filter(id='1')
<QuerySet [<Books: Books object (1)>]>
```

```python
exclude(*args, **kwargs)
# 查询数据(部分)(返回模型实例组成的QuerySet)
# 返回一个新的 QuerySet，其中包含与给定查找参数不匹配的对象

>>>from home.models import Books
>>>Books.objects.exclude(id='1')
<QuerySet [<Books: Books object (2)>]>
```





###### `Field` 查找

- 字段查找是指定 SQL `WHERE` 子句的方法。它们被指定为 `QuerySet` 方法 `filter()`、`exclude()`和 `get()` 的关键字参数
- 当没有提供查找类型时（如 `Entry.objects.get(id=14)`），查找类型被假定为 `exact`
- 双下划线(`__`)

```python
exact
# 完全匹配
# 如果提供的比较值是 None，它将被解释为 SQL NULL （详见 isnull）

Entry.objects.get(id__exact=14) 	# SELECT ... WHERE id = 14;
Entry.objects.get(id__exact=None)	# SELECT ... WHERE id IS NULL;
```

```python
iexact
# 不区分大小写的完全匹配
# 如果提供的比较值是 None，它将被解释为 SQL NULL （详见 isnull）

Blog.objects.get(name__iexact='beatles')	# SELECT ... WHERE name ILIKE 'beatles';
Blog.objects.get(name__iexact=None)			# SELECT ... WHERE name IS NULL;
```



```python
contains
# 区分大小写的包含测试

Entry.objects.get(headline__contains='Lennon')
# SELECT ... WHERE headline LIKE '%Lennon%';
```

```python
icontains
# 不区分大小写的包含测试。

Entry.objects.get(headline__icontains='Lennon')
# SELECT ... WHERE headline ILIKE '%Lennon%';
```



```python
startswith
# 区分大小写的开头为。

Entry.objects.filter(headline__startswith='Lennon')
# SELECT ... WHERE headline LIKE 'Lennon%';
# SQLite 不支持区分大小写的 LIKE 语句；startswith 的作用就像 SQLite 的 istartswith
```

```python
istartswith
# 不区分大小写的开头

Entry.objects.filter(headline__istartswith='Lennon')
# SELECT ... WHERE headline ILIKE 'Lennon%';
```



```python
endswith
# 区分大小写的结尾

Entry.objects.filter(headline__endswith='Lennon')
# SELECT ... WHERE headline LIKE '%Lennon';
```
```python
iendswith
# 不区分大小写的结尾为。

Entry.objects.filter(headline__iendswith='Lennon')
# SELECT ... WHERE headline ILIKE '%Lennon'
```



```python
gt
# 大于

Entry.objects.filter(id__gt=4)
# SELECT ... WHERE id > 4;
```
```python
gte
# 大于等于
```

```python
lt
# 小于
```
```python
lte
# 小于等于
```



```python

```
```python

```



```python

```
```python

```



```python

```
```python

```





##### 排序

```python
order_by(*fields)
# 排序(默认升序,降序前-)(返回模型实例组成的QuerySet)

>>>from home.models import Books
>>>Books.objects.order_by('id')
 <QuerySet [<Books: Books object (1)>, <Books: Books object (2)>]>
>>>Books.objects.order_by('-id')
 <QuerySet [<Books: Books object (2)>, <Books: Books object (1)>]>
```





##### F与Q

###### `F()` 

```python
class F()
# F（）对象表示模型字段的值、模型字段的转换值或带注释的列
# 它使得引用模型字段值并使用它们执行数据库操作成为可能，而实际上不必将它们从数据库中拉到Python内存中
# Django 使用 F() 对象来生成一个 SQL 表达式，在数据库层面描述所需的操作

reporter = Reporters.objects.get(name='Tintin')
reporter.stories_filed += 1
reporter.save()
	
from django.db.models import F
reporter = Reporters.objects.get(name='Tintin')
reporter.stories_filed = F('stories_filed') + 1
reporter.save()

reporter = Reporters.objects.filter(name='Tintin')
reporter.update(stories_filed=F('stories_filed') + 1)
```





###### `Q()` 

```python
class Q()
# Q() 对象表示一个 SQL 条件，它可以用于数据库相关的操作
# 它类似于 F() 对象如何表示一个模型字段或注解的值。它们使得定义和重用条件成为可能，并使用诸如 | （OR）和 & （AND）等运算符将它们组合起来。见 通过 Q 对象完成复杂查询。

Poll.objects.get(
    Q(question__startswith='Who'),
    Q(pub_date=date(2005, 5, 2)) | Q(pub_date=date(2005, 5, 6))
)

# SELECT * from polls WHERE question LIKE 'Who%'
#    AND (pub_date = '2005-05-02' OR pub_date = '2005-05-06')
```



##### 聚合查询

```python
aggregate(*args, **kwargs)
# 返回对 QuerySet 计算的聚合值（平均值、总和等）的字典
# aggregate() 的每个参数都指定了一个将被包含在返回的字典中的值

>>> from django.db.models import Count
>>> q = Blog.objects.aggregate(Count('entry'))
{'entry__count': 16}
>>> q = Blog.objects.aggregate(a=Count('entry'))
{'a': 16}
```

```python
annotate(*args, **kwargs)
# 用所提供的 查询表达式 列表对 QuerySet 中的每个对象进行注解
# 表达式可以是一个简单的值，也可以是对模型（或任何相关模型）字段的引用，或者是对与 QuerySet 中的对象相关的对象进行计算的聚合表达式（平均数、总和等）
# annotate() 的每个参数都是一个注解，将被添加到返回的 QuerySet 中的每个对象

>>> from django.db.models import Count
>>> q = Blog.objects.annotate(Count('entry'))
# The name of the first blog
>>> q[0].name
'Blogasaurus'
# The number of entries on the first blog
>>> q[0].entry__count
42
```





#### 原生SQL

##### raw()

```python
Person.objects.raw('SELECT id, first_name, last_name, birth_date FROM myapp_person')
```



##### cursor()

```python
from django.db import connection

def my_custom_sql(self):
    with connection.cursor() as cursor:
        cursor.execute("UPDATE bar SET foo = 1 WHERE baz = %s", [self.baz])
        cursor.execute("SELECT foo FROM bar WHERE baz = %s", [self.baz])
        row = cursor.fetchone()

    return row
```







### cookie&session

#### cookie

- `max_age`

  如果cookie的持续时间与客户端浏览器会话的持续时间相同，则应为整数秒，或`None`（默认值）。如果未指定expires，则将计算它。

- `expires` 

  应是格式为 `"Wdy, DD-Mon-YY HH:MM:SS GMT"` 的字符串，或者是 UTC 的 `datetime.datetime` 对象。如果 `expires` 是一个 `datetime` 对象，将计算 `max_age`

- `domain`

  如果想设置一个跨域的 cookie，使用 `domain`。例如，`domain="example.com"` 将设置一个可被 `www.example.com`、`blog.example.com` 等域读取的 cookie。否则，一个 cookie 将只能被设置它的域读取

- `secure`

  如果你想让 cookie 只在使用 `https` 方案进行请求时才发送给服务器，请使用 `secure=True`

- `httponly`

  如果你想防止客户端的 JavaScript 访问 cookie，请使用 `httponly=True`

- `samesite`

  使用 `samesite='Strict'` 或 `samesite='Lax'` 来告诉浏览器在执行跨源请求时不要发送这个 cookie。SameSite 并不是所有浏览器都支持，所以它并不能替代 Django 的 CSRF 保护，而是一种深度防御措施。

  使用 `samesite=''None'` （字符串）来明确说明这个 cookie 会随着所有的同站和跨站请求而发送

```python
HttpResponse.set_cookie(key, value='', max_age=None, expires=None, path='/', domain=None, secure=False, httponly=False, samesite=None)
# 设置一个 cookie。参数与 Python 标准库中的 Morsel cookie 对象相同
```

```python
HttpResponse.set_signed_cookie(key, value, salt='', max_age=None, expires=None, path='/', domain=None, secure=False, httponly=False, samesite=None)
# 像 set_cookie() 一样，但是 在设置 cookie 之前对它进行加密签名
# 与 HttpRequest.get_signed_cookie() 一起使用
# 可以使用可选的 salt 参数来增加密钥强度，但你需要记得把它传递给相应HttpRequest.get_signed_cookie() 调用
```



```python
HttpResponse.delete_cookie(key, path='/', domain=None, samesite=None)¶
# 删除给定键的 cookie。如果键不存在，则静默失败。
# 由于 cookie 的工作方式，path 和 domain 应该与在 set_cookie() 中使用的值相同，否则 cookie 可能不会被删除
```



```python
HttpRequest.COOKIES
# 一个包含所有 cookies 的字典。键和值是字符串
```

```python
HttpRequest.get_signed_cookie(key, default=RAISE_ERROR, salt='', max_age=None)
# 返回已签名 cookie 的 cookie 值，如果签名不再有效，则会引发 django.core.signing.BadSignature 异常。如果你提供了 default 参数，异常将被抑制，并返回默认值
# 可选的 salt 参数可以用来提供额外的保护，以防止对你秘钥的暴力攻击。如果提供了这个参数，max_age 参数将根据附加在 cookie 值上的签名时间戳进行检查，以确保 cookie 不超过 max_age 秒

>>> request.get_signed_cookie('name')
'Tony'
>>> request.get_signed_cookie('name', salt='name-salt')
'Tony' # assuming cookie was set using the same salt
```

 





#### session

- `python manage.py cleansessions`删除过去session

```python
HttpRequest.session
# 来自 SessionMiddleware。一个可读可写的，类似字典的对象，代表当前会话
```




### admin

```shell
# 创建超级用户
python manage.py createsuperuser
```



#### 自定义模型类

##### 注册

- 应用中的`admin.py`

```python
from django.contrib import admin

# 导入模型
from .models import Books

# 注册
admin.site.register(Books)
```



##### 管理

- 创建模型管理器类
- 绑定

```python
from django.contrib import admin
from .models import Book

# 创建模型管理器类 
class BookAdmin(admin.ModelAdmin):
    pass

# 绑定
admin.site.register(Books,BookAdmin)
```



###### `ModelAdmin` 选项

```python
ModelAdmin.list_display
# 设置 list_display 来控制哪些字段显示在管理的变更列表页面
# 如果不设置 list_display，管理网站将显示一个单列，显示每个对象的 __str__() 表示
	list_display = ('first_name', 'last_name')
```

```python
ModelAdmin.list_display_links
# 使用 list_display_links 来控制 list_display 中的字段是否以及哪些字段应该被链接到对象的 “更改” 页面
# 默认情况下，更改列表页将把第一列 —— list_display 中指定的第一个字段 —— 链接到每个项目的更改页面。但是 list_display_links 改变这一点
# 将其设置为 None，则完全没有链接
# 将它设置为一个列表或元组字段（格式与 list_display 相同），你希望将其列转换为链接
```
```python
ModelAdmin.list_editable
# 将 list_editable 设置为模型上允许在更改列表页上编辑的字段名称列表。也就是说，在 list_editable 中列出的字段将作为表单部件显示在变更列表页上，允许用户一次编辑和保存多行
```
```python
ModelAdmin.list_filter¶
# 设置 list_filter 来激活管理更改列表页面右侧侧栏的过滤器
```
```python
ModelAdmin.search_fields
# 设置 search_fields，在管理更改列表页面上启用搜索框。这应该被设置为字段名的列表，每当有人在该文本框中提交搜索查询时，就会被搜索到
```
```python

```
```python

```
```python

```



### 文件

- 存储在 `request.FILES`
- 这个字典中的每一个条目都是一个 `UploadedFile` 对象（或一个子类）
- 提交时`enctype="multipart/form-data"`

```python
UploadedFile.read()
# 从文件中读取整个上传的数据。
# 小心使用：如果上传的文件很大，如果你试图把它读到内存中，它可能会让你的系统不堪重负
# 可用 chunks() 来代替
```

```python
UploadedFile.multiple_chunks(chunk_size=None)
# 如果上传的文件足够大，需要分块读取，返回 True
```

```python
UploadedFile.chunks(chunk_size=None)¶
# 一个生成器，返回文件的块
# 如果 multiple_chunks() 是 True，你应该在循环中使用这个方法而不是 read()。

# 在实践中，通常最简单的做法是一直使用 chunks()。循环使用 chunks() 而不是使用 read() 可以确保大文件不会过度占用系统的内存。
```



```python
UploadedFile.name
# 上传的文件名称（如 my_file.txt）
```

```python
UploadedFile.size
# 上传文件的大小，以字节为单位
```



### 跨域

#### CORS

- 跨域资源共享(Cross-origin resource sharing)

##### 简单请求

- 请求方法是以下三种方法之一：

  - `HEAD`
  - `GET`
  - `POST`

- HTTP的头信息不超出以下几种字段：

  - `Accept`

  - `Accept-Language`
  - `Content-Language`
  - `Last-Event-ID`
  - `Content-Type`：只限于三个值`application/x-www-form-urlencoded`、`multipart/form-data`、`text/plain`

```
服务器设置响应头：
Access-Control-Allow-Origin = '域名' 或 '*'
```



##### 复杂请求

- 非简单请求
- 在发送数据之前会先发一次请求用于做“预检”，只有“预检”通过后才再发送一次请求用于数据传输

```markdown
“预检”请求时，允许请求方式则需服务器设置响应头：`Access-Control-Request-Method`
“预检”请求时，允许请求头则需服务器设置响应头：`Access-Control-Allow-Headers`
```



##### Cookies

```markdown
如果在发送请求的时候，给xhr 设置了`withCredentials:true`，从而向服务器发送 Cookies，如果服务端需要想客户端也发送cookie的情况，需要服务器端也返回`Access-Control-Allow-Credentials: true`响应头信息。
```



##### 配置

```python
from django.utils.deprecation import MiddlewareMixin

class SolveCrossDomainMiddleware(MiddlewareMixin):
    def process_response(self, request, response):
        response['Access-Control-Allow-Origin'] = "*"
        return response
```



#### Proxy







### 部署

#### uwsgi

- 



#### nginx



# 机器学习

```python

```

