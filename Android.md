# 安装

### Android Studio

https://developer.android.google.cn/studio

>>**AVD路径**
>>默认路径：C:\Users\sukura\.android\avd
>>默认路径下有存放模拟器的文件夹，及其同名的`.ini`文件。将文件夹移动到其他目录，再修改.ini文件，配置路径
>
>---
>
>>**SDK路径**
>>默认路径：C:\Users\sukura\AppData\Local\Android\Sdk
>>将Sdk文件夹移动到D:\Environment\Android下
>>Android Studio： File>Project Structure>SDK Location 配置



# 界面 (UI)

Android 应用的界面 (UI) 以布局和微件的层次结构形式构建而成。布局是 `ViewGroup` 对象，即控制其子视图在屏幕上的放置方式的容器。微件是 `View` 对象，即按钮和文本框等界面组件。

所有的布局和微件的类都是View子类，由一些共有属性



## 微件(view)

### TextView

#### 基础

```xml
    <TextView
        android:layout_width="133dp"
        android:layout_height="139dp"
        android:id="@+id/demo"
        android:text="@string/Angel"
        android:textColor="@color/purple_200"
        android:textStyle="italic"
        android:textSize="10sp"
        android:background="@color/black"
        android:gravity="center_vertical"
              
		android:shadowRadius="0.3"
        android:shadowColor="@color/black"
        android:shadowDx="10.0"
        android:shadowDy="10.0">
	</TextView>
```

- **layout_width** 宽度
  - `match_parent` 与父组件同宽
  - wrap_content` 由组件内容填充
  - 设置成特定的大小()

  
  
- **layout_height** 高度
  
  - `match_parent` 与父组件同高
  - `wrap_content` 由组件内容填充
  - 设置成特定的大小()
  
  
  
- **id**  编号(java通过findViewById调用)

  ```
   android:id="@+id/sd"
  ```

  ```java
  //调用
  TextView sd= findViewById(R.id.sd);
  ```

  

- **background**  背景颜色(可为图片)



- **text**  文本

  - 直接插入文本

  - 调用在`string.xml`中的配置(src/main/res/value)

    ```
    android:text="@string/Angel"
    ```

    ```xml
    <resources>
        <string name="app_name">My Application</string>
        <string name="Angel">鸢一折纸</string>
    </resources>
    ```

  

- **textcolor**  文本颜色

  - 直接配置

    ```
    //8位(前2位为透明度，后6位为rgb)(前2位可省略)
    android:textColor="#F8F8FF00"
    ```

  - 调用在`color.xml`中配置(src/main/res/value)

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <resources>
        <color name="purple_200">#FFBB86FC</color>
        <color name="purple_500">#FF6200EE</color>
        <color name="purple_700">#FF3700B3</color>
        <color name="teal_200">#FF03DAC5</color>
        <color name="teal_700">#FF018786</color>
        <color name="black">#FF000000</color>
        <color name="white">#FFFFFFFF</color>
    </resources>
    ```

  

- **textStyle**  设置字体风格

  - `normal`  无效果

  - `bold `加粗

  - `italic` 斜体



- **textSize**  字体大小(单位一般是用sp)

  

- **foreground**  前景颜色(可为图片)

  

- **gravity**  内容对齐方式

  - `center_vertical`  水平居中
  - `center_horizontal  `  垂直居中



#### 带阴影

```xml
    <TextView
        android:layout_width="133dp"
        android:layout_height="139dp"
        android:id="@+id/demo"
        android:text="@string/Angel"
              
		android:shadowRadius="0.3"
        android:shadowColor="@color/black"
        android:shadowDx="10.0"
        android:shadowDy="10.0">
	</TextView>
```

- **shadowRadius**  设置阴影的模糊程度,设为0.1就变成字体颜色了,建议使用3.0

- **shadowColor**  设置阴影颜色,需要与shadowRadius一起使用哦!

- **shadowDx**  设置阴影在水平方向的偏移,就是水平方向阴影开始的横坐标位置

- **shadowDy**  设置阴影在竖直方向的偏移,就是竖直方向阴影开始的纵坐标位置

#### 走马灯

```xml
    <TextView
        android:layout_width="133dp"
        android:layout_height="139dp"
        android:id="@+id/demo"
        android:text="@string/Angel"
              
        android:singleLine="true"
        android:focusable="true"
        android:ellipsize="marquee"
        android:marqueeRepeatLimit="marquee_forever">
	</TextView>
```

- **singleLine**  是否单行显示
  - `false`  **默认**
  - `true`  单行显示

- **focusable**  是否可获得焦点
  - `auto`
  - `true` 允许成为焦点
  - `false  `  不会成为焦点

- **focusableInTouchMode**  是否通过触摸获得焦点

- **ellipsize**  设置省略号位置
  - `none`  没有
  - `start   `  开头
  - `end`  最后
  - `middle `  中间
  - `marquee`  以横向滚动方式显示(需获得当前焦点时)

- **marqueeRepeatLimit**  滚动次数
  - `marquee_forever` 永远

##### 获取焦点方法

1. 在<TextView></TextView>加入<requestFocus/>标签

2. 允许点击(点击获得焦点)

   ```
           android:clickable="true"
   ```

3. java设置焦点(将TextView换为com.example.myapplication.MyTextView)

   ```java
   package com.example.myapplication;
   
   import androidx.annotation.Nullable;
   import androidx.appcompat.app.AppCompatActivity;
   
   import android.content.Context;
   import android.os.Bundle;
   import android.os.PersistableBundle;
   import android.util.AttributeSet;
   import android.widget.TextView;
   
   public class MainActivity extends AppCompatActivity {
   
       @Override
       public void onCreate(Bundle savedInstanceState) {
           super.onCreate(savedInstanceState);
           setContentView(R.layout.activity_main);
       }
   }
   ```







### Button

`Button`为`TextView`子类

#### 基础

- **layout_width** 
- **layout_height**  
- **id**  
- **text**
- **textcolor**
- **textStyle**
- **textSize**
- **background**

#### 效果

通过`StateListDrawable`实现

StateListDrawable是Drawable资源的一种，可以根据不同的状态，设置不同的图片效果

关键节点 < selector >，我们只需要将Button的background属性设置为该drawable资源即可实现，按下按钮时不同的按钮颜色或背景

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- btn_selector.xml -->
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@drawable/ic_baseline_airplanemode_active_24" android:state_pressed="true"></item>
    <item android:drawable="@drawable/ic_baseline_airplanemode_inactive_24" ></item>


</selector>
```

```
        android:background="@drawable/btn_selector"
```

**selector对顺序极其敏感，如果第一行匹配，则不会进行后面的匹配。**

- **drawable**:引用的Drawable位图,我们可以把他放到最前面,就表示组件的正常状态~
- **state_focused**:是否获得焦点
- **state_window_focused**:是否获得窗口焦点
- **state_enabled**:控件是否可用
- **state_checkable**:控件可否被勾选,eg:checkbox
- **state_checked**:控件是否被勾选
- **state_selected**:控件是否被选择,针对有滚轮的情况
- **state_pressed**:控件是否被按下
- **state_active**:控件是否处于活动状态,eg:slidingTab
- **state_single**:控件包含多个子控件时,确定是否只显示一个子控件
- **state_first**:控件包含多个子控件时,确定第一个子控件是否处于显示状态
- **state_middle**:控件包含多个子控件时,确定中间一个子控件是否处于显示状态
- **state_last**:控件包含多个子控件时,确定最后一个子控件是否处于显示状态

#### 事件

```java
package com.example.myapplication;
import androidx.annotation.Nullable;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Context;
import android.os.Bundle;
import android.os.PersistableBundle;
import android.util.AttributeSet;
import android.util.Log;
import android.view.MotionEvent;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    private static final String TAG = "cbh";

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btn = findViewById(R.id.btn);

        //点击
        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.e(TAG, "onClick: ");
            }
        });

        //长按
        btn.setOnLongClickListener(new View.OnLongClickListener() {
            @Override
            public boolean onLongClick(View v) {
                Log.e(TAG, "onLongClick: ");
                return false;
            }
        });

        //触摸事件
        btn.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View v, MotionEvent event) {
                Log.e(TAG, "onTouch: "+event.getAction());
                return false;
            }
        });
    }
}

```

```java
//or
//android:onClick="myclick"
public void myclick(View view) {
    }
```

### EditText

`Button`为`TextView`子类，继承许多属性

#### 基础

- **layout_width** 
- **layout_height**  
- **id**  
- **text**
- **textcolor**
- **textStyle**
- **textSize**
- **background**

#### 输入框

```xml
    <EditText
        android:layout_width="match_parent"
        android:layout_height="100dp"
        android:id="@+id/et"
        android:hint="@string/Angel"
        android:textColorHint="#95a1a1"
        android:inputType="textPassword"
        android:drawableLeft="@drawable/ic_baseline_person_24"
        android:layout_margin="50dp"
        android:drawablePadding="10dp"
        android:paddingLeft="5dp">
```

- **hint**  提示词



- **textColorHint**  提示词颜色
  - `phone`  拨号键盘
  - `textPassword`  输入密码



- **inputType**  输入类型限制



- **drawableLeft**  文本左侧插入的drawable(图片)



- **drawablePadding**  设置text与drawable(图片)的间隔

  与drawableLeft、drawableRight、drawableTop、drawableBottom一起使用，可设置为负数，单独使用没有效果。



- **margin**  margin相关属性控制组件相对其他控件的距离



- **padding**  padding控制组件内文字和组件边框的距离

#### 文本获取

```java
package com.example.myapplication;

import androidx.annotation.Nullable;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Context;
import android.os.Bundle;
import android.os.PersistableBundle;
import android.util.AttributeSet;
import android.util.Log;
import android.view.MotionEvent;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    private EditText et;
    private static final String TAG = "cbh";

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et=findViewById(R.id.et);
        Button btn=findViewById(R.id.btn);
        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String text=et.getText().toString();
                Log.e(TAG, "input: "+text);
            }
        });
    }
}
```



### ImageView

`ImageView`为`View`子类，继承许多属性





## 布局(ViewGroup)

### LinearLayout

#### 基础

- **layout_width**  

- **layout_height**   

- **id**  

- **background** 

  

- **orientation** 组件排列方式

  - `vertical`   竖直
  - `horizontal`  水平(**默认**)



- **gravity** 控制子组件的对齐方式(可多项组合如 ：center_vertical|bottom)



- **layout_gravity**  控制该组件在父组件中对齐方式



#### 分割线

##### 添加view

这个view的作用仅仅是显示出一条线

```xml
<!--水平黑线-->
<View  
    android:layout_width="match_parent"  
    android:layout_height="1px"  
    android:background="#000000" />  
```

##### 使用divider

需要准备一张线的图片

- **divider**  导入分割线图片

  

- **showDividers ** 设置分割线位置

  - `none`  无

  - `beginning`   开始

  - `end  `  结束

  - `middle`  中间

    

- **dividerPadding**  设置padding

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:divider="@drawable/ktv_line_div"   
    android:showDividers="middle"  
    android:dividerPadding="10dp">
</LinearLayout>
```



#### 权重

对**剩余空间**进行分配

如果父容器**水平**对齐，对**子**容器高进行分配







### RelativeLayout

内部组件可重叠

#### 基础

- **layout_width**  

- **layout_height**   

- **id**  

- **background** 



#### 根据父容器定位

```
        android:layout_centerVertical="true"
        <!--通过true和flase设置-->
```

- **layout_alignParentLeft**  左对齐
- **layout_alignParentRight** 右对齐
- **layout_alignParentTop  ** 顶部对齐
- **layout_alignParentBottom**  底部对齐
- **layout_centerInParent**  中间位置
- **layout_centerHorizontal ** 水平居中
- **layout_centerVertical ** 垂直居中



#### 根据兄弟组件定位

```
        android:layout_toRightOf="@+id/sd"
        <!--通过兄弟组件id设置-->
```

- **layout_toRightOf**  参考组件右边
- **layout_toLeftOf ** 参考组件左边
- **layout_above ** 参考组件上方
- **layout_below** 参考组件下方
- **layout_alignLeft ** 参考组件右边界
- **layout_alignTop ** 参考组件上边界
- **layout_alignRight**  参考组件左边界
- **layout_alignBottom ** 参考组件下边界



#### margin

设置组件与父容器边距

- **layout_margin**
- **layout_marginLeft**

#### padding

设置组件内部元素边距

- **padding**
- **paddingRight**





### TableLayout

- 如果我们直接往TableLayout中添加组件的话,那么这个组件将占满一行

- 如果我们想一行上有多个组件的话,就要添加一个<TableRow>的容器,把组件都丢到里面

- <TableRow>中的组件个数就决定了该行有多少列,而列的宽度由该列中最宽的单元格决定

- <TableRow>的layout_width默认是match_parent的,设置成其他的值也不会生效 

- <TableRow>的layout_height默认是wrap_content的,可以自己设置大小

  

#### 常用属性

- **android:collapseColumns ** 设置需要**被隐藏**的列的序号
- **android:shrinkColumns ** 设置允许**被收缩**的列的列序号
- **android:stretchColumns**  设置运行**被拉伸**的列的列序号

以上这三个属性的列号都是**从0开始算**的,比如shrinkColunmns = "2",对应的是第三列

可以**设置多个**,用**逗号隔开**比如"0,2"     如果是所有列**都生效**,则**用"\*"号**即可*



#### 子组件属性

- **android:layout_column**

  表**跳过**n个单元格,直接显示到第n+1个格子处,从1开始算

- **android:layout_span**

  表**合并**n个单元格,也就说这个组件占n个单元格





### FrameLayout

- **foreground   ** 前景
- **foregroundGravity** 前景位置 





### GridLayout

#### 常用属性

- **orientation** 组件排列方式
  - `vertical`   竖直
  - `horizontal`  水平(**默认**)

- **columnCount** 列数设置

- **rowCount**  行数设置

  

#### 子组件属性

- **layout_columnSpan** 所占列数
- **layout_rowSpan**  所占行数



- **layout_row**  设置所在行数
- **layout_column**  设置所在列数

# 应用组件

## Activity



## Service



## BroadcastReceiver



## ContentProvider