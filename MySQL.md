

# MySQL

## 基础命令

```mysql
/* 连接mysql */
mysql -u root -p 

/* 
	-h 服务器地址
	-u 登录账号
	-p 回车后输入密码
	-P 端口号
*/
```

```markdown
快捷键
	-	\G	格式化输出
	-	\s	查看服务器端信息
	-	\c	结束命令输出操作
	-	\q	退出当前sql命令行模式
	-	\h	帮助
```



## 默认库

- ###information_schema

  >提供了访问数据库元数据的方式
  >
  >

- ### mysql

  >主要负责存储数据库的用户、权限设置、关键字等mysql自己需要使用的控制和管理信息
  >
  >不可以删除
  >
  >

- ### performance_schema

  >
  >
  >



## 转义符

` 是 MySQL 的转义符，这个符号是对数据库名、表明、字段的特殊处理。避免和 mysql 的本身的关键字冲突。





## 数据类型

### 字符串

#### char

- 1~255字符的**定长**字符串
- 长度创建时需指定,否则默认`char(1)`

#### varchar

- **变长**字符串,最多不超过255
- 设置`varchar(n)`,可存储0~n个字符的变长串(n<=255)
- 查询速度不然char快

#### text

- 变长文本类型存储
- 最大64K

#### enum

- 接受最多64k个串组成的一个预定义集合的某个串




### 数值

#### int

- **整数值**,支持`-2147483648~2147486847`(*UNSIGNED*为`0~4294967295`)
- 占**4**字节

#### tinyint

- **整数值**,支持`-128~127`(*UNSIGNED*为`0~255`)
- 占**1**字节

#### float

- **单精度浮点值**

#### double

- **双精度浮点数**

#### decimal

- 精度**可变**浮点值
- `decimal(m,n)` 
  - **m**表示有效数字数的精度(1~65)
  - **n**表示小数点后的位数(1~30)
  - m>=n

### 时间

#### date

- 格式:`YYYY-MM-DD`
- 支持的范围:`1000-01-01到`9999-12-31`

#### time

- 格式:`HH:MM:SS`
- 支持的范围:`00:00:00`到`23:59:59`

#### datetime

- 格式:`YYYY-MM-DD HH:MM:SS`

- 支持范围:`1000-01-01 00:00:00`到`9999-12-31 23:59:59`






## 表的约束条件

- `unsigned` 无符号 给数值类使用 
- 字段类型后加*(n)*限制宽度
  - char(n)	varchar(n) 可选择字符串宽度
  - int(n)无意义    有符号默认10位,无符号默认11位
  - int(n)在设置无符号前导0(fillzero)时有意义
- `not null` 不能为空,如果输入该字段的值为null,会报错
- `default ` 设置默认值
- `primary key ` 主键 不能为空且唯一
- `auto_increment`  定义列为自增属性(一般主键),数值会自动加1
- `unique`  唯一索引(数据不能重复),增加查询速度,但会降低插入和更新速度



## 表引擎

### `InnoDB`

**具备外键支持功能的事务存储引擎**

- 存储结构

  ```markdown
  	-.frm	存储表结构
  	-.ibd	存储数据与索引(可能是多个.ibd文件,或者独立表空间文件)
  ```

- **支持事务和行级锁**(`InnoDB`最大特点)

- 不保持表的总行数

- 支持外键

  









### `MyISAM`

**主要的非事务处理存储引擎**

- 存储结构

  ```markdown
  	-.frm	存储表结构
  	-.MYD	存储数据
  	-.MYI	存储索引
  ```

- **只支持表级锁**

- 保持表的总行数

- 不支持外键



### `MEMORY`

**置于内存的表**





# SQL



## 库

### 创建库

```mysql
/* 创建库(如果不存在)(默认字符集utf8) */

create database if not exists <数据库名> default charset=utf8;
```



### 删除库

```mysql
DROP DATABASE IF EXISTS <数据库名>;
```



### 查看库

```mysql
/* 展示所有数据库 */
show databases;
```



### 打开库

```sql
USE 数据库名;
```



## 表

### 创建表

```sql
CREATE table<表名>
( <列名> <数据类型> [列级完整性约束条件]
[,<列名> <数据类型> [列级完整性约束条件]]
......
[,表级完整性约束条件])engine=innodb default charser=utf8	;


/* 列:
	-Field	列名
	-Type	列数据类型
	-Null	是否可为空
	-Key	是否为主键
	-Default
	-Extra
*/
```





### 删除表

```sql
drop table<表名>[restrict|cascade];
```





### 查看表

```mysql
/* 查看所有表 */
show tables;
```

```mysql
/* 查看表结构 */
desc <表名>;
```

```mysql
/* 查看建表语句 */
show create table <表名>;
```



### 修改表

```mysql
/* 向表中插入新字段或加入约束条件 */
alter table <表名>
[add [column] <新列名> <数据类型> [完整性约束条件]
[first|after <列名>] 	# 确定插入字段位置 
```

```mysql
/* 删除表中字段或约束条件 */
alter table <表名>
[drop [column] <列名> [cascade|restrict]]
```

```mysql
/* 修改表中字段 */
alter table <表名>
change <列名> <数据类型> [完整性约束条件]       	 # 不修改字段名
modify <列名> <新列名> <数据类型> [完整性约束条件] # 修改字段名
```

```mysql
/* 修改表名 */
alter table <表名> rename as <新表名>
```



```
[add <表级完整性约束条件>]

[drop constraint<完整性约束条件>[restrict|cascade]]
```



## 数据

### 查询数据

```mysql
Select [all|distinct]<目标列表达式>[,<目标列表达式>]...
From <表名或视图名>[,<表名或视图名>...]|(<select语句>[as]<别名>)
[where <条件表达式>]
[group by <列名> [having<条件表达式>]]
[order by <列名> [ASC|DESC]]
[limit m,n]
```

```markdown
# like 模糊查询子句
	- %	任意个字符
	- _ 任意字符

# 聚合函数
	- max()
	- min()
	- count()
	- sum()
	- avg()

# group by 分组子句 
	- having 子句 在分组后进行过滤

# order by 排序子句
	-asc   从小到大(默认)
	-desc  从大到小

# limit 数据分页
	-limit n		提取n条数据
	-limit m,n		跳过m条数据,z提取n条数据
```





### 插入数据

```mysql
insert
into <表名> [(<属性列1>[,<属性列2>]......)]
Values(<常量>[,<常量>]......)

```

```mysql
insert
into <表名> [(<属性列1>[,<属性列2>]......)]
子查询
```



### 修改数据

```mysql
update <表名>
Set  <列名>=<表达式>[, <列名>=<表达式>]......
[where  <条件>]
```



### 删除数据

```mysql
delete
From <表名>
[where <条件>]
```







## 索引

### 创建索引

```mysql
create [unique][cluster]index<索引名>
On<表名>(<列名>[<次序>][,<列名>[<次序>]]......)
```





### 修改索引

```mysql
alter index<旧索引名>rename to<新索引名>
```





### 删除索引

```mysql
drop index<索引名>
```







## 视图

### 创建视图

```mysql
create view <视图名> [(<列名>[,(<列名>]......)]
As <子查询>
[with check option]
```





### 删除视图

```mysql
drop view<视图名>[cascade]
```





## 权限

### 授权

```mysql
grant <权限>[,<权限>]...
On <对象类型><对象名>[,<对象类型><对象名>]...
To <用户>[,<用户>]...
[with grant option](传播)
```

```
# 权限
	-select
	-insert
	-
```



### 回收

```mysql
revoke <权限>[,<权限>]...
On <对象类型><对象名>[,<对象类型><对象名>]...
from <用户>[,<用户>]...[cascade|restrict]
```

```markdown

```



### 删除

```mysql
drop user <用户>
```

