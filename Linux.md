# SSH登录

- `/root/.ssh/authorized_keys`





# 基本命令

## 文件目录

### cd

- 改变当前工作目录

```shell
cd [路径]

# cd - 	回到之前目录
# cd ~  回到家目录(或直接cd)
```



### ls

- 列出目录和文件的信息

```shell
ls [选项] [文件] 

# 选项
#	-a 显示所有文件及目录 (. 开头的隐藏文件也会列出)
#	-l 除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出
#	-h 显示文件大小
```



### pwd

- 显示当前目录

```shell
pwd
```



### mkdir

- 创建目录

```shell
mkdir [选项] 路径

# 选项:
#	-m：对新建目录设置存取权限，也可以用chmod命令设置
#	-p：可以是一个路径名称(此时若此路径中的某些目录尚不存在，在加上此选项后，系统将自动建立好那些尚不存在的目录，即一次可以建立多个目录)
```

wget https://github.com/nvm-sh/nvm/archive/refs/tags/v0.39.1.tar.gz

### cp

- 将给出的文件或目录复制到另一文件或目录中

```shell
cp [选项] 源文件或目录 目标文件或目录 

# 选项:
#	-r：若给出源文件是个目录文件，此时cp将递归复制该目录下所有的子目录和文件。此时目标文件必需为一个目录名
#	-v: 显示复制过程
#	-i：在覆盖目标文件之前将给出提示要求用户确认
```



### rmdir

- 删除空目录

```shell
rmdir 路径
```



### rm

- 删除文件或目录

```shell
rm [选项] 文件或目录

# 选项:
#	-r 将目录及以下之档案亦逐一删除
#	-f 忽略不存在的文件，但从不给出提示
#	-i 删除前逐一询问确认。
```









## 打包压缩

### gzip

- 对文件进行压缩和解压缩

```shell
gzip [选项] 压缩（解压缩）的文件名
# 选项
#	-c：将输出信息写到标准输出上，并保留原有文件
#-d：将压缩文件解压
-1：对每个压缩文件显示下列字段：压缩文件的大小、未压缩时文件的大小、压缩比、未压缩时文件的名字
-r：查找指定目录并压缩或解压缩其中的所有文件
-t：测试，检查压缩文件是否完整
-v：对每一个压缩和解压的文件，显示文件名和压缩比
```



## 用户

### su

- 变更使用者身份 主要用于普通用户转超级用户

```shell
su [选项] [使用者]	
```



### useradd

- 添加用户账号

```shell
useradd [选项] 用户名

# 选项
#	-g：指定用户所属的群组
#	-m：自动建立用户的登入目录
#	-n：取消建立以用户名称为名的群组
```

### passwd

- 设置账号密码

```shell
passwd [对应账号]
```





## 其他

### clear

- 清除屏幕上的信息

```shell
clear
```



### history

- 显示命令历史

```shell
history [参数] [目录]

# 之前执行命令前有序号,!序号  可再次执行
```



### man

- 显示命令手册

```shell
man [命令]
```

















# 文件

### 文件类型

`-`	普通文件 
`d`	目录文件 
`l`	链接文件 
`c`	字符设备文件
`b`	块设备文件
`p`	管道
`f`	堆栈
`s`	套接字



### 文件权限

权限由九个字符组成-可分成三个字符组

- 第一个三位字符组表示文件所有者(u)对该文件的权限 
- 第二个三位字符组表示文件用户组(g)对该文件的权限
- 第三个三位字符组表示系统其他用户(o)对该文件的权限
- 可读（`r`） 可写（`w`） 可执行（`x`）
- 若用户组对此没有权限，一般显示`-`







# 环境配置



## nvm

```shell
# 1.获取
wget -c https://github.com/nvm-sh/nvm/archive/refs/tags/v0.39.1.tar.gz

# 2.解压
tar -zxvf v0.39.1.tar.gz -C /root/.nvm

# 3.修改.bashrc(尾行插入)
export NVM_DIR="$HOME/.nvm/nvm-0.39.1"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# 4.应用
source ~/.bashrc
```



## python



## docker





## nginx

```shell
# 准备()
yum -y install make gcc gcc-c++ libtool zlib zlib-devel openssl  openssl-devel

```

```shell
# 安装

# 1.获取
wget -c https://nginx.org/download/nginx-1.21.6.tar.gz

# 2.解压
tar -xvf nginx-1.21.6.tar.gz

./configure

make && make install
```



## mysql





## redis





## MongoDB
