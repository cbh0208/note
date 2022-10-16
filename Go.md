```go
package main
import "fmt"
func main() {
	fmt.Println("hello world!啊`")
}
```

```shell
# 编译
go build demo.go     
> demo.exe
demo.exe

# 运行
go run demo.go		
```

# 基础

## 基础语法

### 行分隔符

- 在 Go 程序中，一行代表一个语句结束。每个语句不需要像 C 家族中的其它语言一样以分号 ; 结尾，因为这些工作都将由 Go 编译器自动完成。
- 如果将多个语句写在同一行，它们则必须使用 ; 人为区分

```go
fmt.Println("Hello, World!")
fmt.Println("Hello, World!")
```

### 注释

- 注释不会被编译，每一个包应该有相关注释。
- 单行注释是最常见的注释形式，可以在任何地方使用以 // 开头的单行注释。
- 多行注释也叫块注释，均已以 /* 开头，并以 */ 结尾。如：

```go
// 单行注释
/*
 我是多行注释
 */
```

### 标识符

标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或是多个字母(A~Z和a~z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。

以下是有效的标识符：

```
mahesh   kumar   abc   move_name   a_123
myname50   _temp   j   a23b9   retVal
```

以下是无效的标识符：

- 1ab（以数字开头）
- case（Go 语言的关键字）
- a+b（运算符是不允许的）



### 字符串连接

- Go 语言的字符串可以通过 **+** 实现：

```go
package main
import "fmt"
func main() {
  fmt.Println("hello" + "world")
}

// hello world
```



### 关键字

- 25 个关键字或保留字

```go
break		default		func	interface	select
case		defer		go		map			struct
chan		else		goto	package		switch
const		fallthrough	if		range		type
continue	for			import	return		var
```

- 36 个预定义标识符

```go
append	bool	byte	cap		close	complex		complex64	complex128	uint16
copy	false	float32	float64	imag	int			int8		int16		uint32
int32	int64	iota	len		make	new			nil			panic		uint64
print	println	real	recover	string	true		uint		uint8		uintptr
```



### 格式化字符串

- Go 语言中使用 `fmt.Sprintf` 格式化字符串并赋值给新串：

- `%d` 表示整型数字，`%s` 表示字符串

```go
package main

import (
  "fmt"
)

func main() {
  // 
  var stockcode=123
  var enddate="2020-12-31"
  var url="Code=%d&endDate=%s"
  var target_url=fmt.Sprintf(url,stockcode,enddate)
  fmt.Println(target_url)
}
// xxxxxxxxxx Code=123&endDate=2020-12-31
```



### 转义符

```go
// \t	指标符
fmt.Println("鸢一\t折纸")
//  鸢一    折纸

// \n	换行符
fmt.Println("鸢一\n折纸")
// 鸢一
// 折纸


// \\	\
fmt.Println("鸢一\\折纸")
// 鸢一\折纸

// \"	"
fmt.Println("鸢一\"折纸")
// 鸢一"折纸

// \r	截断之后,替换开头
fmt.Println("5鸢一\r折纸")
// 折纸一     (5鸢一换成折纸)
```



### 变量

- 声明变量的一般形式	`var identifier type`

  ```go
  var int i=9
  ```

- 变量为赋值使用默认值

  ```go
  var int i
  fmt.Println(i) // 0
  ```

- 可进行类型推导(省略类型)

  ```go
  var i=666
  ```

- 可使用`:=`声明变量(不可用于赋值)

  ```
  i:=666
  ```

- 可进行多变量声明

  ```go
  var a,b int= 1,2
  
  var a,b = 1,2 
  
  a, b:= 1,2 
  
  // 这种因式分解关键字的写法一般用于声明全局变量
  var (
      a 1
      b 2
  )
  ```










## 基本数据类型

### 数字类型

#### 整型

##### `int`

- 大小随CPU变换
- 32位系统4字节,64位系统8字节
- 默认声明为`int`



##### `int8`

- 有符号 8 位整型 (-128 到 127)
- 1字节



##### `int16`

- 有符号 16 位整型 (-32768 到 32767)
- 2字节



##### `int32`

- 有符号 32 位整型 (-2147483648 到 2147483647)
- 4字节



##### `int64`

- 有符号 64 位整型 (-9223372036854775808 到 9223372036854775807)
- 8字节



##### `uint`

- 大小随CPU变换
- 32位系统4字节,64位系统8字节



##### `uint8`

- 无符号 8 位整型 (0 到 255)
- 1字节



##### `uint16`

- 无符号 16 位整型 (0 到 65535)
- 2字节



##### `uint32`

- 无符号 32 位整型 (0 到 4294967295)
- 4字节



##### `uint64`

- 无符号 64 位整型 (0 到 18446744073709551615)
- 8字节



##### `uintptr`

- 



##### `byte`

- `uint8`别名



##### `rune`

- `int32`别名



#### 浮点型

- 可用科学计数法

##### `float32`

- IEEE-754 32位浮点型数



##### `float64`

- IEEE-754 64位浮点型数
- 默认声明为`float64`



##### `complex64`

- 32 位实数和虚数



##### `complex128`

- 64 位实数和虚数



### 布尔型(bool)



### 字符串(string)

#### 格式化

- 使用`fmt.Printf()`

```go
// %T 类型

fmt.Printf("%T", 1) // int
```





## 派生数据类型

### 指针类型(Pointer)

### 数组类型

### 结构化类型(struct))

### 管道类型(Channel)

### 函数类型

### 切片类型(slice)

### 接口类型(interface)

#### Map 类型

## 面对对象





# 标准库

## fmt

- 

```go
func fmt.Print(a ...interface{}) (n int, err error)
// 使用其操作数的默认格式打印格式，并写入标准输出
// 当两个操作数都不是字符串时，将在操作数之间添加空格
// 它返回写入的字节数和遇到的任何写入错误

fmt.Print(666, 666, 666)
fmt.Print(666, 666, 666)
// 666 666 666666 666 666
```

```go
func fmt.Println(a ...interface{}) (n int, err error)
// Println格式使用其操作数的默认格式，并写入标准输出。始终在操作数之间添加空格，并追加换行符
// 它返回写入的字节数和遇到的任何写入错误

fmt.Println(666, 666, 666)
fmt.Println(666, 666, 666)
// 666 666 666
// 666 666 666
```

```go
func fmt.Printf(format string, a ...interface{}) (n int, err error)
// Printf根据格式说明符格式化并写入标准输出
// 它返回写入的字节数和遇到的任何写入错误

fmt.Printf("%T", 1) // int
```





## unsafe

- 

```go
//unsafe.Sizeof()
// 变量占用字节数大小

fmt.Printf("%d", unsafe.Sizeof(1)) // 8
```

