# 创建



```
dotnet new wpf -o W
```

```
dotnet new webapp -o Web --no-https -f net6.0
```



# 基础

## 关键字

ffmpeg ‐i lucene.mp4 ‐hls_time 10 ‐hls_list_size 0 ‐hls_segment_filename ./hls/lucene_%05d.ts ./hls/lucene.m3u8

- | 声明的可访问性       | 含义                                                         |
  | :------------------- | :----------------------------------------------------------- |
  | `public`             | 访问不受限制。                                               |
  | `protected`          | 访问限于包含类或派生自包含类的类型。                         |
  | `internal`           | 访问限于当前程序集。                                         |
  | `protected internal` | 访问限于当前程序集或派生自包含类的类型。                     |
  | `private`            | 访问限于包含类。                                             |
  | `private protecte`   | 访问限于包含类或当前程序集中派生自包含类的类型。 自 C# 7.2 之后可用。 |









## 数据类型

### 数字

#### `int`

- 32 位有符号整数类型



#### `long`

- 64 位有符号整数类型



#### `short`

- 16 位有符号整数类型



#### `float`

-  32 位单精度浮点型



#### `double`

- 64 位双精度浮点型



#### `decimal`

- 128 位精确的十进制值，28-29 有效位数





### `string`

- 引用类型  
- 不可变

- `@`:原义标识符
- `$`:字符串内插



### `Array`

- 固定长度



### `List<T>`

- 


### `Dictionary<K，V>`

- 哈希表



### `HashSet<T>`

- 集合



### `Queue<T>`

- 队列



### `Stack<T>`

- 栈



### 类型转换



## 函数







## 结构体

- 类是引用类型，结构是值类型。
- 结构不支持继承。
- 结构不能声明默认的构造函数。

## 枚举



## 记录

- 值相等性
- 不可变性

## 运算符和表达式

### =>运算符

- 



### with表达式

- 修改的特定属性和字段生成其操作数的副本



### 运算符重载

```c#
public readonly struct Fraction
{
    private readonly int num;
    private readonly int den;

    public Fraction(int numerator, int denominator)
    {
        if (denominator == 0)
        {
            throw new ArgumentException("Denominator cannot be zero.", nameof(denominator));
        }
        num = numerator;
        den = denominator;
    }

    public static Fraction operator +(Fraction a) => a;
    public static Fraction operator -(Fraction a) => new Fraction(-a.num, a.den);

    public static Fraction operator +(Fraction a, Fraction b)
        => new Fraction(a.num * b.den + b.num * a.den, a.den * b.den);

    public static Fraction operator -(Fraction a, Fraction b)
        => a + (-b);

    public static Fraction operator *(Fraction a, Fraction b)
        => new Fraction(a.num * b.num, a.den * b.den);

    public static Fraction operator /(Fraction a, Fraction b)
    {
        if (b.num == 0)
        {
            throw new DivideByZeroException();
        }
        return new Fraction(a.num * b.den, a.den * b.num);
    }

    public override string ToString() => $"{num} / {den}";
}

public static class OperatorOverloading
{
    public static void Main()
    {
        var a = new Fraction(5, 4);
        var b = new Fraction(1, 2);
        Console.WriteLine(-a);   // output: -5 / 4
        Console.WriteLine(a + b);  // output: 14 / 8
        Console.WriteLine(a - b);  // output: 6 / 8
        Console.WriteLine(a * b);  // output: 5 / 8
        Console.WriteLine(a / b);  // output: 10 / 4
    }
}
```



## 委托

- 通过`delegate`关键字来声明
- 委托对象必须使用 `new`关键字来创建
- 委托对象初始为null，可用`+`向委托对象添加同参数类型的方法或委托

```c#
int Meth(int a)
{
    Console.WriteLine("Meth");
    Console.WriteLine(a);
    return 1111;
}

// 2.初始化
Del d;

// 3.添加方法
d=Meth;

// 4.调用
d(666);
// 1.声明
delegate int Del(int q);
```

### Action<>

- 用于需要使用委托参数执行操作的情况。 它所封装的方法不返回值。

```c#

```



### Func<>

- 通常用于现有转换的情况，也就是说需要将委托参数转换为其他结果时。 投影是一个很好的示例。 它所封装的方法返回指定值。

## 事件

- 事件是一种特殊的多播委托



## 特性

- 所有特性名称均以“Attribute”一词结尾，但在代码中使用特性时，无需指定特性后缀

### 预定义

#### AttributeUsage



#### Conditional



#### Obsolete

- 标记了不应被使用的程序实体



### 自定义

- 一个新的自定义特性应派生自 `System.Attribute` 类
- 







## 异步

### lock语句

- `lock` 语句获取给定对象的互斥 lock，执行语句块，然后释放 lock

- ```c#
  lock (x)
  {
      // Your code...
  }
  ```

  
