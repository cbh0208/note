```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

# 基础

## 基本语法

### 语言成分

#### 标识符与关键字

##### 标识符

Java 所有的组成部分都需要名字。类名、变量名以及方法名都被称为标识符。

关于 Java 标识符，有以下几点需要注意：

- 所有的标识符都应该以字母（A-Z 或者 a-z）,美元符（$）、或者下划线（_）开始
- 首字符之后可以是字母（A-Z 或者 a-z）,美元符（$）、下划线（_）或数字的任何字符组合
- 关键字不能用作标识符
- 标识符是大小写敏感的
- 合法标识符举例：age、$salary、_value、__1_value
- 非法标识符举例：123abc、-salary

##### 关键字

<table>
    <tr>
        <th>类别</th> 
        <th>关键字</th> 
        <th>说明</th> 
    </tr>
    <tr>
        <td rowspan="4">访问控制</td> 
        <td >private</td>
        <td >私有的</td>   
    </tr>
    <tr>
        <td>protected</td>
        <td>受保护的</td>
    </tr>
    <tr>
    	<td>public</td>
        <td>公共的</td>
    </tr>
    <tr>
        <td>default</td>
        <td>默认的</td>
    </tr>
    <tr></tr>
	<tr>
  		<td rowspan="13">类、方法和变量修饰符</td> 
   		<td>abstract</td>
   		<td>声明抽象</td>
	</tr>
    <tr>
		<td>class</td>
    	<td>类</td>
	</tr>
    <tr>
        <td>extends</td>
        <td>扩充,继承</td>
    </tr>
    <tr>
        <td>final</td>
        <td>最终值,不可改变的</td>
    </tr>
    <tr>
        <td>implements</td>
        <td>实现（接口）</td>
    </tr>
    <tr>
        <td>interface</td>
        <td>接口</td>
    </tr>
    <tr>
        <td>native</td>
        <td>本地，原生方法（非 Java 实现）</td>
    </tr>
    <tr>
        <td>new</td>
        <td>新,创建</td>
    </tr>
    <tr>
        <td>static</td>
        <td>静态</td>
    </tr>
    <tr>
        <td>strictfp</td>
        <td>严格,精准</td>
    </tr>
    <tr>
        <td>synchronized</td>
        <td>线程,同步</td>
    </tr>
    <tr>
        <td>transient</td>
        <td>短暂</td>
    </tr>
    <tr>
        <td>volatile</td>
        <td>易失</td>
    </tr>
    <tr>
        <td rowspan="12">程序控制语句</td>
        <td>break</td>
        <td>跳出循环</td>
    </tr>
    <tr>
        <td>case</td>
        <td>定义一个值以供 switch 选择</td>
    </tr>
    <tr>
        <td>continue</td>
        <td>继续</td>
    </tr>
    <tr>
        <td>default</td>
        <td>默认</td>
    </tr>
    <tr>
        <td>do</td>
        <td>运行</td>
    </tr>
    <tr>
        <td>else</td>
        <td>否则</td>
    </tr>
    <tr>
        <td>for</td>
        <td>循环</td>
    </tr>
    <tr>
        <td>if</td>
        <td>如果</td>
    </tr>
    <tr>
        <td>instanceof</td>
        <td>实例</td>
    </tr>
    <tr>
    	<td>return</td>
        <td>返回</td>
    </tr>
    <tr>
        <td>switch</td>
        <td>根据值选择执行</td>
    </tr>
    <tr>
        <td>while</td>
        <td>循环</td>
    </tr>
    <tr></tr>
    <tr>
        <td rowspan="6">错误处理</td>
        <td>assert</td>
        <td>断言表达式是否为真</td>
    </tr>
    <tr>
        <td>catch</td>
        <td>捕捉异常</td>
    </tr>
    <tr>
        <td>finally</td>
        <td>有没有异常都执行</td>
    </tr>
    <tr>
        <td>throw</td>
        <td>抛出一个异常对象</td>
    </tr>
    <tr>
        <td>throws</td>
        <td>声明一个异常可能被抛出</td>
    </tr>
    <tr>
        <td>try</td>
        <td>捕获异常</td>
    </tr>
    <tr></tr>
    <tr>
        <td rowspan="2">包相关</td>
        <td>import</td>
        <td>引入</td>
    </tr>
    <tr>
        <td>package</td>
        <td>包</td>
    </tr>
    <tr></tr>
    <tr>
        <td rowspan="8">基本类型</td>
        <td>boolean</td>
        <td>布尔型</td>
    </tr>
    <tr>
        <td>byte</td>
        <td>字节型</td>
    </tr>
    <tr>
        <td>char</td>
        <td>字符型</td>
    </tr>
    <tr>
        <td>double</td>
        <td>双精度浮点</td>
    </tr>
    <tr>
        <td>float</td>
        <td>单精度浮点</td>
    </tr>
    <tr>
        <td>int</td>
        <td>整型</td>
    </tr>
    <tr>
        <td>long</td>
        <td>长整型</td>
    </tr>
    <tr>
        <td>short</td>
        <td>短整型</td>
    </tr>
    <tr></tr>
    <tr>
        <td rowspan="3">变量引用</td>
        <td>super</td>
        <td>父类,超类</td>
    </tr>
    <tr>
        <td>this</td>
        <td>本类</td>
    </tr>
    <tr>
        <td>void</td>
        <td>无返回值</td>
    </tr>
    <tr>
        <td rowspan="3">保留关键字</td>
        <td>goto</td>
        <td>是关键字，但不能使用</td>
    </tr>
    <tr>
        <td>const</td>
        <td>是关键字，但不能使用</td>
    </tr>
    <tr>
        <td>null</td>
        <td>空</td>
    </tr>


#### 基本数据类型

##### 整数数据类型

- 整数数据类型：byte、short、int、long

| 数据类型 | 字节数 | 可表示范围(拆分表示) | 可表示数值范围                           |
| -------- | ------ | -------------------- | ---------------------------------------- |
| byte     | 1      | -2^7 ~ 2*7-1         | -128~127                                 |
| short    | 2      | -2^15 ~ 2^15-1       | -32768~32766                             |
| int      | 4      | -2^31 ~ 2^31-1       | -2147483648~2147483647                   |
| long     | 8      | -2^63 ~ 2^63-1       | -9223372036854775808~9223372036854775807 |

- 整数类型扩展

- - 当数值超过long类型的最大范围时，可使用java官方提供的java.math.BigInteger类型

  - 该类的使用需要初始化构造器 new BigIngeter("")

  - - 方法有：add(),subtract(),multiply(),divide()

##### 小数数据类型

| 数据类型 | 字节数 | 可表示范围(拆分表示)                                | 可表示数值范围         |
| -------- | ------ | --------------------------------------------------- | ---------------------- |
| float    | 4      | -3.403*(10^38) ~ 3.403*(10^38) -3.403E38 ~ 3.403E38 | -3.403E38 ~ 3.403E38   |
| double   | 8      | -1.798*(10^308) ~ 1.798*(10^308)                    | -1.798E308 ~ 1.798E308 |


#### 运算符

##### 算术运算符

表格中的实例假设整数变量A的值为10，变量B的值为20：

| 操作符 | 描述                              | 例子               |
| :----- | :-------------------------------- | :----------------- |
| +      | 加法 - 相加运算符两侧的值         | A + B 等于 30      |
| -      | 减法 - 左操作数减去右操作数       | A – B 等于 -10     |
| *      | 乘法 - 相乘操作符两侧的值         | A * B等于200       |
| /      | 除法 - 左操作数除以右操作数       | B / A等于2         |
| ％     | 取余 - 左操作数除以右操作数的余数 | B%A等于0           |
| ++     | 自增: 操作数的值增加1             | B++ 或 ++B 等于 21 |
| --     | 自减: 操作数的值减少1             | B-- 或 --B 等于 19 |

##### 关系运算符

表格中的实例整数变量A的值为10，变量B的值为20：

| 运算符 | 描述                                                         | 例子             |
| :----- | :----------------------------------------------------------- | :--------------- |
| ==     | 检查如果两个操作数的值是否相等，如果相等则条件为真。         | （A == B）为假。 |
| !=     | 检查如果两个操作数的值是否相等，如果值不相等则条件为真。     | (A != B) 为真。  |
| >      | 检查左操作数的值是否大于右操作数的值，如果是那么条件为真。   | （A> B）为假。   |
| <      | 检查左操作数的值是否小于右操作数的值，如果是那么条件为真。   | （A <B）为真。   |
| >=     | 检查左操作数的值是否大于或等于右操作数的值，如果是那么条件为真。 | （A> = B）为假。 |
| <=     | 检查左操作数的值是否小于或等于右操作数的值，如果是那么条件为真。 | （A <= B）为真。 |

##### 位运算符

假设整数变量 A 的值为 60 和变量 B 的值为 13：

| 操作符 | 描述                                                         | 例子                           |
| :----- | :----------------------------------------------------------- | :----------------------------- |
| ＆     | 如果相对应位都是1，则结果为1，否则为0                        | （A＆B），得到12，即0000 1100  |
| \|     | 如果相对应位都是 0，则结果为 0，否则为 1                     | （A \| B）得到61，即 0011 1101 |
| ^      | 如果相对应位值相同，则结果为0，否则为1                       | （A ^ B）得到49，即 0011 0001  |
| 〜     | 按位取反运算符翻转操作数的每一位，即0变成1，1变成0。         | （〜A）得到-61，即1100 0011    |
| <<     | 按位左移运算符。左操作数按位左移右操作数指定的位数。         | A << 2得到240，即 1111 0000    |
| >>     | 按位右移运算符。左操作数按位右移右操作数指定的位数。         | A >> 2得到15即 1111            |
| >>>    | 按位右移补零操作符。左操作数的值按右操作数指定的位数右移，移动得到的空位以零填充。 | A>>>2得到15即0000 1111         |

##### 逻辑运算符

假设布尔变量A为真，变量B为假

| 操作符 | 描述                                                         | 例子                |
| :----- | :----------------------------------------------------------- | :------------------ |
| &&     | 称为逻辑与运算符。当且仅当两个操作数都为真，条件才为真。     | （A && B）为假。    |
| \| \|  | 称为逻辑或操作符。如果任何两个操作数任何一个为真，条件为真。 | （A \| \| B）为真。 |
| ！     | 称为逻辑非运算符。用来反转操作数的逻辑状态。如果条件为true，则逻辑非运算符将得到false。 | ！（A && B）为真。  |

### 流程控制语句

### 数组

#### 一维数组

### 静态方法

### 字符串

## 异常处理





## 多线程

## 流和文件



## 注解与反射

### 注解



### 反射



















# 数据结构


​    





















# JavaWeb

## Maven

### 配置

https://maven.apache.org/download.cgi#

>**配置文件：**`.\conf\settings.xml`
>
>>**仓库**
>
>>```xml
>><localRepository>D:\Repository\maven_repository</localRepository>
>>```
>
>---
>
>>**vs code**
>>Java.Configuration.Maven.User settings   `.\conf\settings.xml`
>
>---
>
>>**镜像**
>
>>```xml
>>//阿里云
>><mirror>
>><id>nexus-aliyun</id>
>><name>Nexus aliyun</name>
>><url>http://maven.aliyun.com/nexus/content/groups/public/</url>
>><mirrorOf>central</mirrorOf>
>></mirror>
>>```
>
>---
>
>>**环境：**
>>
>>- M2_HOME            `./bin`                                            *new*
>>- MAVEN_HOME     `./`                                                 *new*
>>- path                       `%MAVEN_HOME%/bin`                    *add*
>



### 使用



#### `pom.xml`

##### 打war包

```xml
<project>
    .......
	<packaging>war</packaging>
    .......
    <build>
        <pluginManagement>
            <plugins>
                .......
                <plugin>
                  <artifactId>maven-war-plugin</artifactId>
                  <version>3.2.2</version>
                </plugin>
                .......
            </plugins>
        </pluginManagement>
    </build>
    .......
</project>
```



##### 静态资源导出

```xml
<project>
    .......
    <build>
    	.......
        <resources>
          <resource>
            <directory>src/main/resources</directory>
            <includes>
                <include>**/*.properties</include>
                <include>**/*.xml</include>
            </includes>
            <filtering>true</filtering>
          </resource>
          <resource>
            <directory>src/main/java</directory>
            <includes>
                <include>**/*.properties</include>
                <include>**/*.xml</include>
            </includes>
            <filtering>true</filtering>
          </resource>
        </resources>
        ......
    </build>
    .......
</project>
```



## Tomcat

### 配置

https://tomcat.apache.org/index.html

>**配置文件**：`./conf/server.xml`
>
>>修改端口号(port)
>>
>>```xml
>><Connector port="8081" protocol="HTTP/1.1"
>>connectionTimeout="20000"
>>redirectPort="8443" />
>>```



### 使用

#### `web.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
  version="4.0"
  metadata-complete="true">

    <request-character-encoding>UTF-8</request-character-encoding>

    
</web-app>

```

##### 首页

```xml
<web-app>
    .......
    <welcome-file-list>
        <welcome-file>index1.jsp</welcome-file>
        <welcome-file>index2.jsp</welcome-file>
        <welcome-file>index3.jsp</welcome-file>
        <welcome-file>index4.jsp</welcome-file>
        <welcome-file>/target/redirectAndFoward.jsp</welcome-file>
    </welcome-file-list>
    .......
</web-app>
```

##### 错误页

```xml
<web-app>
    .......
    <error-page>
        <error-code>400</error-code>
        <location>/filter/error.jsp</location>
    </error-page>
    <error-page>
        <error-code>404</error-code>
        <location>/filter/error.jsp</location>
    </error-page>
    <error-page>
        <error-code>500</error-code>
        <location>/filter/error.jsp</location>
    </error-page>
    .......
</web-app>
```



## Servlet

Java Servlet 是运行在 Web 服务器或应用服务器上的程序，它是作为来自 Web 浏览器或其他 HTTP 客户端的请求和 HTTP 服务器上的数据库或应用程序之间的中间层。

### demo

1. `pom.xml`配置（Maven导入）

   ```xml
   <project>
       .......
       <dependencies>
           .......
           <dependency>
               <groupId>javax.servlet</groupId>
               <artifactId>javax.servlet-api</artifactId>
               <version>4.0.1</version>
               <scope>provided</scope>
           </dependency>
           .......
       <dependencies>
       .......
   </project>
   ```

2. 编写一个Java类，继承HttpServlet类

   重写HttpServlet类的doGet和doPost方法

   ```java
   package com.cbh.servlet;
   
   import java.io.IOException;
   
   import javax.servlet.ServletContext;
   import javax.servlet.ServletException;
   import javax.servlet.http.HttpServlet;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;
   
   public class hello extends HttpServlet{
   
       @Override
       protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           System.out.println("use doGet");
           PrintWriter writer=resp.getWriter();//响应流
           writer.print("hello servlet!");
       }
   
       @Override
       protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           super.doPost(req, resp);
       }        
   }
   ```

   

3. 配置`web.xml`，对servlet进行配置

```xml
<web-app>  
    .......
    <!-- 注册servlet -->
    <servlet>        
        <servlet-name>HelloWorld</servlet-name>
        <servlet-class>HelloWorld</servlet-class>
    </servlet>
    
	<!-- servlet的请求路径 -->
    <servlet-mapping>
        <servlet-name>HelloWorld</servlet-name>
        <url-pattern>/HelloWorld</url-pattern>
    </servlet-mapping>
    .......
</web-app>  
```

#### Mapping配置

- 一个servlet可指定一个映射路径

  ```xml
  <servlet-mapping>
          <servlet-name>HelloWorld</servlet-name>
          <url-pattern>/HelloWorld</url-pattern>
  </servlet-mapping>
  ```

  

- 一个servlet可指定多个映射路径

  ```xml
  <servlet-mapping>
          <servlet-name>HelloWorld</servlet-name>
          <url-pattern>/helloworld1</url-pattern>
  </servlet-mapping>
  
  <servlet-mapping>
          <servlet-name>HelloWorld</servlet-name>
          <url-pattern>/helloworld2</url-pattern>
  </servlet-mapping>
  ```



- 一个servlet可指定通用映射路径

  ```xml
  <servlet-mapping>
          <servlet-name>HelloWorld</servlet-name>
          <url-pattern>/HelloWorld/*</url-pattern>
  </servlet-mapping>
  ```

- 默认请求路径

  ```xml
  <servlet-mapping>
          <servlet-name>HelloWorld</servlet-name>
          <url-pattern>/*</url-pattern>
  </servlet-mapping>
  ```

- 指定前缀和后缀

  ```xml
  <!-- *前不能加项目映射路径 -->
  <!-- 常用.do -->
  <servlet-mapping>
          <servlet-name>HelloWorld</servlet-name>
          <url-pattern>*.do</url-pattern>
  </servlet-mapping>
  ```

  

- 优先级问题

  指定了固有的映射路径优先级最高，如果找不到就走默认路径

  



### 生命周期

##### init () 

- 只执行一次

- 创建配置：<servlet>

  - 第一次访问时，创建（**默认**）

    <load-on-startup>值为负数

    ```xml
    <load-on-startup>-1</load-on-startup>
    ```

  - 服务器前端时，创建

    <load-on-startup>值为0或正数

    ```xml
    <load-on-startup>1</load-on-startup>
    ```

  

##### service()

-  



##### destroy()

-  







### `ServletContext`

web应用启动时，会为每个web程序创建一个对于ServletContext对象，它代表了当前的web应用

##### 共享数据

```java
	   @Override
       protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           ServletContext context=this.getServletContext();
           String username="sdasdasd";
           context.setAttribute("username", username); // 设置
       }
```

```java
       @Override
       protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           ServletContext context=this.getServletContext();
           String test=(String)context.getAttribute("username"); // 读取
           resp.setContentType("text/html");
           resp.setCharacterEncoding("utf-8");
           resp.getWriter().print("cbh名字:"+test);
       }
```



##### 获取初始化参数

```xml
<web-app>
    .......
    <context-param>
        <param-name>url</param-url>
        <param-value>jdbc:mssql://localhost:3306/mybatis</param-value>
    </context-param>
    .......
</web-app>
```

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        ServletContext context=this.getServletContext();
        String url=context.getInitParameter("url"); // 获取(通过param-name)
        resp.getWriter().print(url);
    }
```



##### 请求转发

- 地址栏不会发生改变

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        ServletContext context=this.getServletContext();
		context.getRequestDispatcher("/hello").forward(req, resp);// 转发给/hello
    }
```



##### 读取资源文件

```properties
username=root
password=wm710326
```
- 资源文件在`./WEB-INF/classes`中


```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        InputStream is=this.getServletContext().getResourceAsStream("./WEB-INF/classes/db.properties");
        Properties prop=new Properties();
        prop.load(is);
        String user=prop.getProperty("username");
        String password=prop.getProperty("password");
        resp.getWriter().print(user+":"+password);
    }
```





### `HttpServletRequest`

web服务器接收到客户端的http请求，针对这个请求，分别创建一个代表请求`HttpServletRequest`对象，一个代表响应的`HttpServletResponse`

- 如要获取客户端**请求**过来的参数：找`HttpServletRequest`

##### 获取参数

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String userName=req.getParameter("userName");
        String password=req.getParameter("Password");
        String[] hobby=req.getParameterValues("hobby");
    }
```



##### 请求转发

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.getRequestDispatcher("/a").forward(req, resp);
    }
```







### `HttpServletResponse`

web服务器接收到客户端的http请求，针对这个请求，分别创建一个代表请求`HttpServletRequest`对象，一个代表响应的`HttpServletResponse`

- 如要给客户端**响应**一些信息：找`HttpServletResponse`

##### 下载文件

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 1. 要获取下载文件的路径
        String realPath="D:\\WorkSpace\\java\\javaweb\\servlet\\servlet-01\\target\\servlet-01\\WEB-INF\\classes\\1.png";
        System.out.println("下载文件的路径："+realPath);
        
        // 2. 下载的文件名是什么
        String fileName=realPath.substring(realPath.lastIndexOf('\\')+1);
        
        // 3. 设置让浏览器能支持(Content-Disposition)下载我们需要的东西
        resp.setHeader("Content-Disposition", "attachment;filename"+URLEncoder.encode(fileName, "utf-8"));
        
        // 4. 获取下载文件的输入流
        FileInputStream in=new FileInputStream(realPath);
        
        // 5. 创建缓冲区
        int len=0;
        byte[] buffer=new byte[1024];
        
        // 6. 获取OutputStream对象
        ServletOutputStream out=resp.getOutputStream();
        
        // 7. 将FileOutputStream流写入到buffer缓冲区,使用OutputStream将缓冲区数据输出到客户端
        while((len=in.read(buffer))>0){
            out.write(buffer,0,len);
        }
        in.close();
        out.close();
    }
```



##### 验证码

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //让浏览器5秒刷新一次
        resp.setHeader("refresh", "5");

        //在内存中创建一个图片
        BufferedImage image=new BufferedImage(80,20,BufferedImage.TYPE_INT_RGB);
        
        //得到图片
        Graphics2D g=(Graphics2D)image.getGraphics();//笔
        
        //设置图片的背景颜色
        g.setColor(Color.white);
        g.fillRect(0, 0, 80, 20);
        
        //给图片写数据 
        g.setColor(Color.blue); 
        g.setFont(new Font(null,Font.BOLD,20));
        g.drawString(makeNum(), 0, 20);

        //告诉浏览器，这个请求用图片方式打开
        resp.setContentType("image/jpeg");
        //设置不让缓存
        resp.setDateHeader("expires", -1);
        resp.setHeader("Cache-Control", "no-cache");
        resp.setHeader("Pragma", "no-cache");

        //把图片写给浏览器
        ImageIO.write(image, "jpg", resp.getOutputStream());
    }

	// 生成随机数
    private String makeNum(){
        Random random=new Random();
        StringBuffer sb=new StringBuffer();
        String num =random.nextInt(9999999)+"";
        for(int i=0;i<7-num.length();i++){
            sb.append("0");
        }
        num=sb.toString()+num;
        return num;


    }
```



##### 重定向

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        resp.setHeader("Location", "/a");
        resp.setStatus(302);
    }
```

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        resp.sendRedirect("/a");
    }
```





### `Cookie`

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        Cookie[] cookies=req.getCookies(); // 获取Cookie
        
        if(cookies!=null){
        	for(int i=0;i<cookies.length;i++){
            Cookie cookie=cookies[i];
            String name=cookie.getName(); // 获取Cookie的key
            String value=cookie.getValue(); // 获取Cookie的value
        	}    
        }

        Cookie cookie=new Cookie("name", "value"); // 新建Cookie
        cookie.setMaxAge(24*60*60);	// 设置时限
        resp.addCookie(cookie); // 加入        
    }
```





### `Session`

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        HttpSession session=req.getSession();// 获取session
        
        session.setAttribute("name", new Person("张三",14)); // 设置
        
        String sessionId=session.getId();//获取id(用户唯一)
        
        Person parson=(Person)session.getAttribute("name");//
        
        if(session.isNew()){
           
        }
        
        session.removeAttribute("name");
        session.invalidate();
    }
```

```xml
<web-app>
	<session-config>
        <!-- 15min后注销 -->
        <session-timeout>15</session-timeout>
    </session-config>
</web-app>
```

```

```



## JSP

```xml
<project>
    .......
    <dependencies>
        .......
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>javax.servlet.jsp-api</artifactId>
            <version>2.3.3</version>
            <scope>provided</scope>
        </dependency>
        .......
    <dependencies>
    .......
</project>
```



### 基本语法

#### 表达式

```jsp
<%=request.getContextPath()%>
```



#### EL表达式

```jsp
${pageContext.request.contextPath}
```



#### 代码片段

- 在_jspService()中

```jsp
<% 代码片段 %>
```





#### 声明

- 被编译到jsp生成的java类中

```jsp
<%!  %>
```



#### 注释

```jsp
<%-- 该部分注释在网页中不会被显示 --%>
```



### 指令

| **指令**           | **描述**                                                  |
| :----------------- | :-------------------------------------------------------- |
| <%@ page ... %>    | 定义页面的依赖属性，比如脚本语言、error页面、缓存需求等等 |
| <%@ include ... %> | 包含其他文件                                              |
| <%@ taglib ... %>  | 引入标签库的定义，可以是自定义标签                        |



#### `<%@ page %>`







#### `<%@ include %>`

```jsp
<%@ include file="1.jsp"%>
主体
<%@ include file="2.jsp"%>
```





#### `<%@ taglib %>`



### 隐式对象

| **对象**    | **描述**                                                     |
| :---------- | :----------------------------------------------------------- |
| request     | **HttpServletRequest** 接口的实例                            |
| response    | **HttpServletResponse** 接口的实例                           |
| out         | **JspWriter**类的实例，用于把结果输出至网页上                |
| session     | **HttpSession**类的实例                                      |
| application | **ServletContext**类的实例，与应用上下文有关                 |
| config      | **ServletConfig**类的实例                                    |
| pageContext | **PageContext**类的实例，提供对JSP页面所有对象以及命名空间的访问 |
| page        | 类似于Java类中的this关键字                                   |
| Exception   | **Exception**类的对象，代表发生错误的JSP页面中对应的异常对象 |







```jsp
<%
	// pageContext->request->session->application->null
	String name=(String)pageContext.findAttribute("name");
%>
```





### JSTL

```

```

###### 核心标签

###### 格式化标签

###### SQL 标签

###### XML 标签

###### JSTL 函数

# SSM框架

## MyBatis

### demo

#### 环境

- maven导入（`pom.xml`）

```xml
<dependency>
  <groupId>org.mybatis</groupId>
  <artifactId>mybatis</artifactId>
  <version>3.5.2</version>
</dependency>
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <version>8.0.25</version>
</dependency>
```



#### 创建模块

- 编写mybatis核心配置文件(`mybatis-config.xml`) 

  ```xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE configuration
    PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-config.dtd">
  <configuration>
    <environments default="development">
      <environment id="development">
        <transactionManager type="JDBC"/>
        <dataSource type="POOLED">
          <property name="driver" value="${driver}"/>
          <property name="url" value="${url}"/>
          <property name="username" value="${username}"/>
          <property name="password" value="${password}"/>
        </dataSource>
      </environment>
    </environments>
    <mappers>
      <mapper resource=""/>
    </mappers>
  </configuration>
  ```

- 编写mybatis工具类

  ```java
  package com.example.utils;
  import java.io.InputStream;
  import java.io.IOException;
  import org.apache.ibatis.io.Resources;
  import org.apache.ibatis.session.SqlSession;
  import org.apache.ibatis.session.SqlSessionFactory;
  import org.apache.ibatis.session.SqlSessionFactoryBuilder;
  //SqlSessionFactory-->SqlSession
  public class MybatisUtils {
      private static SqlSessionFactory sqlSessionFactory;
      static{
          try {
              //使用mybatis第一步：获取SqlSessionFactory对象
              String resource = "mybatis-config.xml";
              InputStream inputStream = Resources.getResourceAsStream(resource);
              sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
          } catch (IOException e) {
              e.printStackTrace();
          }
      }
      public static SqlSession getSqlSession(){
          return sqlSessionFactory.openSession();
      }
  }
  ```

  



#### 编写代码

- 实体类

  ```java
  package com.example.pojo;
  //source action :
  //Generate Constructors
  //Generate getters and setters   
  //Generate toStrings()  
  public class User {
      private int id;
      private String name;
      private String pwd;
      public User(int id, String name, String pwd) {
          this.id = id;
          this.name = name;
          this.pwd = pwd;
      }
      public int getId() {
          return id;
      }
      public void setId(int id) {
          this.id = id;
      }
      public String getName() {
          return name;
      }
      public void setName(String name) {
          this.name = name;
      }
      public String getPwd() {
          return pwd;
      }
      public void setPwd(String pwd) {
          this.pwd = pwd;
      }
      @Override
      public String toString() {
          return "User [id=" + id + ", name=" + name + ", pwd=" + pwd + "]";
      }
  } 
  
  ```

- Dao接口

  ```java
  package com.example.dao;
  import com.example.pojo.User;
  import java.util.List;
  public interface UserDao {
      List<User> getUserList();
  }
  ```

- 接口实现类由原来的UserDaoImpl变为一个Mapper配置文件

  ```xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
      PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
      "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  
  <!-- namespace——绑定一个对应的Dao/Mapper接口 -->
  <mapper namespace="com.example.dao.userDao">
  
      <select id="getUserList" resultType="com.example.pojo.User">
          select * from mybatis.user
      </select>
      <select id="getUserById" parameterType="int" resultType="com.example.pojo.User">
          select * from mybatis.user where id=#{id}
      </select>
  </mapper>
  ```

  

- 注册Mapping(`mybatis-config.xml`) 

  ```xml
    <mappers>
      <mapper resource="com/example/dao/UserMapper.xml"/>
    </mappers>
  ```

  

#### 测试

```java
package com.example.dao;
import java.util.List;

import com.example.pojo.User;
import com.example.utils.MybatisUtils;

import org.apache.ibatis.session.SqlSession;
import org.junit.Test;

public class ts {
    @Test
    public void test(){
        //获得SqlSession对象
        SqlSession sqlSession=MybatisUtils.getSqlSession();

        try {
            //getMapper()
            UserDao userDao=sqlSession.getMapper(UserDao.class);
            List<User> userList = userDao.getUserList();
        
            for(User user :userList){
                System.out.println(user);
        }
            
        } catch (Exception e) {
            e.printStackTrace();
        }
        finally{
            //关闭SqlSession
            sqlSession.close();
        }             
    }
     @Test
    public void test1(){
        SqlSession sqlSession=MybatisUtils.getSqlSession();
        UserMapper mapper =sqlSession.getMapper(UserMapper.class);

        User u1=mapper.getUserById(1);
        System.out.println(u1);
        sqlSession.close();

    }
}
```



### CRUD

- namespace

  namespace中包名与Dao/Mappe接口的包名一致

  

#### select

```java
	//根据id查询用户
	User getUserById(int id);
```

```xml
    <select id="getUserById" parameterType="int" resultType="com.example.pojo.User">
        select * from mybatis.user where id=#{id};
    </select>
```

```java
	//获得SqlSession对象
	SqlSession sqlSession=MybatisUtils.getSqlSession();
	//getMapper()
	UserMapper mapper =sqlSession.getMapper(UserMapper.class);

	User u1=mapper.getUserById(1);

	System.out.println(u1);
	//关闭SqlSession
	sqlSession.close();
```

- **id**:对应namesp中方法名
- **parameterType**:参数类型
- **resultType**:sql语句执行的返回值

#### insert

```java
    //insert一个用户
	int addUser(User user);
```

```xml
    <insert id="addUser" parameterType="com.example.pojo.User">
        insert into mybatis.user (id,name,pwd) values(#{id},#{name},#{pwd});
    </insert>
```

```java
	//获得SqlSession对象
	SqlSession sqlSession=MybatisUtils.getSqlSession();
	//getMapper()
	UserMapper mapper =sqlSession.getMapper(UserMapper.class);

    int res=mapper.addUser(new User(4, "饺子", "416"));
    if(res>0)
        System.out.println("ok");

	//提交事务
    sqlSession.commit();
	//关闭SqlSession
    sqlSession.close();
```





#### update

```java
    //修改用户
    int updateUser(User user);
```

```xml
    <update id="updateUser" parameterType="com.example.pojo.User">
        update mybatis.user set name=#{name},pwd=#{pwd} where id=#{id};
    </update>
```

```java
	//获得SqlSession对象
	SqlSession sqlSession=MybatisUtils.getSqlSession();
	//getMapper()
	UserMapper mapper =sqlSession.getMapper(UserMapper.class);

    mapper.updateUser(new User(04,"jiaozi", "123123"));

	//提交事务
    sqlSession.commit();
	//关闭SqlSession
    sqlSession.close();
```



#### delete

```java
    //删除用户
    int deleteUser(int id);
```

```xml
    <delete id="deleteUser" parameterType="int">
        delete from mybatis.user where id=#{id};
    </delete>
```

```java
	//获得SqlSession对象
	SqlSession sqlSession=MybatisUtils.getSqlSession();
	//getMapper()
	UserMapper mapper =sqlSession.getMapper(UserMapper.class);

    mapper.deleteUser(4);

	//提交事务
    sqlSession.commit();
	//关闭SqlSession
    sqlSession.close();
```



### 动态SQL

### 缓存

## Spring

applicationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">
 

 

</beans>


```



## SpringMVC











# 微服务

## SpringBoot

```html
<img preview="imgPreview" 
     src="https://upload-bbs.mihoyo.com/upload/2021/12/31/75276539/f9dc87d7db78ef76fcf7ac03b33563c2_5985978696238311983.jpg?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,jpg" 
     large="https://upload-bbs.mihoyo.com/upload/2021/12/31/75276539/f9dc87d7db78ef76fcf7ac03b33563c2_5985978696238311983.jpg?x-oss-process=image/auto-orient,0/interlace,1/format,jpg" data-pswp-uid="3">
```



## SpringCloud



























# HarmonyOS







