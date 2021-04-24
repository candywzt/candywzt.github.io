

## 1.Java的八大基本类型

#### 1.八种基本类型

**byte**：8位，最大存储数据量是255，存放的数据范围是-128~127之间。

**short**：16位，最大数据存储量是65536，数据范围是-32768~32767之间。

**int**：32位，最大数据存储容量是2的32次方减1，数据范围是负的2的31次方到正的2的31次方减1。

**long**：64位，最大数据存储容量是2的64次方减1，数据范围为负的2的63次方到正的2的63次方减1。

**float**：32位，数据范围在3.4e-45~1.4e38，直接赋值时必须在数字后加上f或F。

**double**：64位，数据范围在*4.9e*-324~1.8e308，赋值时可以加d或D也可以不加。

**boolean**：只有true和false两个取值。

**char**：16位，存储Unicode码，用单引号赋值。

*<u><font color=red>取值范围不用记，已经被封装在对应的包装类里了</font></u>*

#### 2.八种基本类型的封装器类

| 简单类型   | byte | short |   int   | long | float | double | Boolean |   char    | void |
| ---------- | :--: | :---: | :-----: | :--: | :---: | :----: | :-----: | :-------: | :--: |
| 二进制位数 |  8   |  16   |   32    |  64  |  32   |   64   |    1    |    16     |  --  |
| 封装器类   | Byte | Short | Integer | Long | Float | Double | Boolean | Character | Void |

<font color=red> int  和 char 的首字母不要大写，不要大写，不要大写！别的能大写是因为他们的封装器类和类型名一致，非要大写就写成 Integer </font>

有关包装类与基本数据类型的区别看[这里](Java/Java基础知识/Trap)

## 2.Java中的常量

0x16：十六进制整型常量，以十六进制表示时，必须以0x或0X开头，如0xFF、0XA9.

08：八进制整型常量，必须以0开头，如012、034.

32L：长整型常量，必须以L结尾，如9L、123L.

3.14F：浮点型常量，带有小数点的常量，必须加F(f)，如1.0F、9.09f.

3.14D：双精度浮点型常量，比单精度范围更大，后面的d(D)可加可不加.

‘A’：字符常量，使用两个**<font color=red>单引号</font>**包起来的**<font color=red>单个</font>**字符，

<font color=#808080>"Hello"：字符串常量，使用双引号包起来，</font><font color=red>String并不是java基本类型，他属于String类.</font>

\r：回车符号，相当于键盘上按下的回车键.

\n：换行符，在字符串中遇到该符号字符串剩下的部分会另起一行显示.

\t：制表符，在字符串中显示为大概4个空格宽度的空位，相当于按下了Tab键.

\b：退格键，相当于BackSpace键，那个通常用来删除的按键.

\‘：单引号，所有特殊字符都必须用反斜杠来转义，如下双引号\"，反斜杠\\，正斜杠\/.

## 3.基本数据类型间的转换

<font color=red>boolean不参与类型转换</font>

#### 1.数据类型的*"大小"*

​	这里的大小，其实指的是数据类型涵盖范围的大小，也叫作类型的高低级，比如int只能存储2的32次方减一，而long可存储2的64次方减一，都是存储整数，但是long比int范围更大。

整型：long >int >short

浮点型：double >float

浮点型>整型

​	byte和short以及char处于同一级。

​	(byte , short , char)

#### 2.自动转换

当一个较低级(小)的数据类型和一个较高级(大)的数据类型一起运算时，系统会自动将低级数据转换为高级类型在进行运算，在此期间，数据精度不会丢失。<font color=red>同一级之间不会自动转换</font>

```java
int a = 12;
long b = 100L;
long c = a + b;
System.out.println(c);
```

编译成功，运行结果：

```java
112
```

再运行如下代码

```java
int a = 12;
long b = 100L;
int c = a + b;
System.out.println(c);
```

编译报错，a+b的值不能赋值给类型为int的变量c。

#### 3.强制转换

当需要把高级的数据类型转换为低级数据类型，(如上面把long类型的结果赋值给int类型的变量从)就必须要用到类型强制转换。

转换方法：<font color=red>在被转换变量前面用括号添加要转的类型名，</font>如下所示

```java
int a = 12;
double b =3.59;
int c = (int)(a + b);
System.out.println(c);
```

编译成功，输出结果，但是<font color=red>精度丢失！！！(并不是四舍五入，而是直接舍去小数位)</font>

```
15
```

#### 4.包装类过渡类型转换

如下将folat类型转换为double

使用了Float类提供的`.doubleValue()`方法

```java
float a = 3.14f;
Float b = new Float(a);
double c = aa.doubleValue();
```

如下将float类型转换为int

使用了Float类提供的`.intValue()`方法

```java
float a = 3.14f;
Float b = new Float(a);
int c = b.intValue(b);
```

简单类型转换为对应包装类可以使用类似`Integer(int value)`的包装类自带方法，

包装类转换对应(或可用来转换数据类型)基本类型可以使用类似`.intValue()`的包装类自带方法。

#### 5.字符串与其他类型转换

##### 其他类型转换为字符串

1.调用类的转换方法：`.toString()`方法

2.使用字符串拼接符号：`a + ""`

3.使用String类的方法：`String.volueOf(a)`

##### 字符串转换为其他类型

1.先转换为对应包装类对象，在调用对应方法转换成其他类型(<font color=red>已在jdk14中被弃用,jdk14后推荐使用下一种方法</font>)

```java
String a = "3.14";
Folat b = new Folat(a).doubleValue();
```

2.使用包装类提供的静态方法parse

```java
String a = "3.14";
Float b = Float.parseFloat(a);
```

## 4.引用变量

java有5种引用类型(对象类型)：

类、接口、数组、枚举、标注

引用类型：底层结构和基本类型差距较大

JVM的内存空间：

​		Heap 堆空间：分配对象 new Student（）

​		Stack 栈空间：临时变量 Student stu

​		Code 代码区 ：类的定义，静态资源 Student.class

```java
Student stu = new Student（）； //new 在内存的堆空间创建对象
stu.study(); //把对象的地址赋给stu引用变量
```

上例实现步骤：

​	JVM加载Student.class 到Code区

​	new Student()在堆空间分配空间并创建一个Student实例

​	将此实例的地址赋值给引用stu， 栈空间