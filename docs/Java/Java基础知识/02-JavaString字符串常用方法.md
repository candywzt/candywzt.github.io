## 1.String类

#### 1.取字符串长度

`.length()`方法

```
String a = "一二三四五六七";
int b = a.length();
System.out.println(b);
```

运行结果

```
7
```

#### 2.字符串转换数组

`.toCharArray()`方法

```
String a = "一二三四五六七";
char [] b = a.toCharArray();
for (int i = 0; i < b.length; i++) {
   System.out.println(i + ":" + b[i]);
}
```

运行结果

```
0:一
1:二
2:三
3:四
4:五
5:六
6:七
```

#### 3.从字符串指定位置取出字符

`.charAt()`方法

```
 String a = "一二三四五六七";
for (int i = 0; i < a.length(); i++) {
   System.out.println(i + ":" + a.charAt(i));
}
```

运行结果

```
0:一
1:二
2:三
3:四
4:五
5:六
6:七
```

#### 4.字符串转换byte数组

`getBytes()`方法

```
String a = "一二三四五六七";
byte b[] = a.getBytes();
System.out.println(new String (b));
```

运行结果

```
一二三四五六七
```

#### 5.过滤字符串中存在的字符

`.indexOf()`方法

```
String a = "一二三四五六七";
int b = a.indexOf("三");
System.out.println(b);
```

运行结果

```
2
```

#### 6.去掉字符串前后的空格

`.trim()`方法

```
String a = "   一二三四五六七   ";
String b = a.trim();
System.out.println(b);
```

运行结果

```
一二三四五六七
```

#### 7.从字符串中取出子字符串

`.substring()`方法

```
String a = "一二三四五六七";
String b = a.substring(2,5);
System.out.println(b);
```

运行结果

```
三四五
```

#### 8.大小写转换

`.toLowerCase()`和`.toUpperCase()`方法

```
String a = "aAbBcCdD";
String b = a.toLowerCase();
System.out.println(b);
```

运行结果

```
aabbccdd
```

#### 9.判断字符串开头结尾字符

`.endsWith()`和`.startWith()`方法

#### 10.替换String字符串中的一个字符

`.replace()`方法

## 2.StringBuffer类

#### 1.追加字符串

`.addend()`方法

```
StringBuffer a = new StringBuffer();
a.append("一二三四五六七");
System.out.println();
```

运行结果

```
一二三四五六七
```

#### 2.插入

`.insert()`方法

```
StringBuffer a = new StringBuffer();
a.append("一二三四五六七");
a.insert(1,"aa");
System.out.println(a);
```

运行结果

```
一aa二三四五六七
```

#### 3.替换

`.replace()`方法

```
StringBuffer a = new StringBuffer();
a.append("一二三四五六七");
a.replace(1,5,"aa");
System.out.println(a);
```

运行结果

```
一aa六七
```

## 3.StringBuilder类

跟StringBuffer一样，但不是[<font color=red>线程安全</font>](http)的