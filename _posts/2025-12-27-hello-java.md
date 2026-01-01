---
layout: post
title: "Java 变量与数据类型学习总结"
date: 2025-12-27 12:00:00 +0800
categories: [Java基础]
tags: [变量, 数据类型]
---

# 一、变量的定义
> - 变量有三要素：变量名，变量类型，作用域
> - 变量分为基本类型和引用类型变量
> - 不写初始值，就相当于给它指定了默认值。默认值总是0。
> - 变量最后都以分号(;)结束。

## (一).变量是存储数据的容器，变量必须先定义后使用,定义格式:
```java
// 数据类型 变量名 = 赋值;   （可以使用逗号隔开来声明多个同类型变量）
int age = 18;
double score = 92.5;
```
## (二).变量的作用域
1. 类变量
2. 实列变量
3. 局部变量


# 二、 基本数据类型
Java定义了以下几种基本数据类型：
- 整数类型：byte，short，int，long
- 浮点数类型：float，double
- 字符类型：char
- 布尔类型：boolean

Java基本数据类型占用的字节数：
- byte: 1
- short: 2
- int: 4
- long: 8
- float: 4
- double: 8
- char: 2


## (一).整数
各种整型能表示的最大范围如下：
- byte：-128 ~ 127
- short: -32768 ~ 32767
- int: -21_4748_3648 ~ 21_4748_3647
- long: -922_3372_0368_5477_5808 ~ 922_3372_0368_5477_5807,long型的结尾需要加L
```java
// 定义整型的例子:
public class Main {
    public static void main(String[] args) {
        int i = 2147483647;
        int i2 = -2147483648;
        int i3 = 2_000_000_000; // 加下划线更容易识别
        int i4 = 0xff0000; // 十六进制表示的16711680
        int i5 = 0b1000000000; // 二进制表示的512

        long n1 = 9000000000000000000L; // long型的结尾需要加L
        long n2 = 900; // 没有加L，此处900为int，但int类型可以赋值给long
        int i6 = 900L; // 错误：不能把long型赋值给int
    }
}
```
#### 1.整数拓展:
进制   二进制0b   十进制    八进制0    十六进制0x
```java
public class NumberSystemDemo {
    public static void main(String[] args) {
        // 1. 二进制：Java中以0b（数字0+字母b）为前缀，逢2进1，数字范围0-1
        int binaryNum = 0b1010; // 二进制的1010
        // 二进制转十进制计算：1×2³ + 0×2² + 1×2¹ + 0×2⁰ = 8+0+2+0=10
        System.out.println("二进制 0b1010 转十进制：" + binaryNum);

        // 2. 八进制：以0（数字0）为前缀，逢8进1，数字范围0-7
        int octalNum = 012; // 八进制的12
        // 八进制转十进制计算：1×8¹ + 2×8⁰ = 8+2=10
        System.out.println("八进制 012 转十进制：" + octalNum);

        // 3. 十进制：无前缀，逢10进1，数字范围0-9
        int decimalNum = 10; // 普通十进制10
        System.out.println("十进制 10 本身：" + decimalNum);

        // 4. 十六进制：以0x（数字0+字母x）为前缀，逢16进1，数字范围0-9/A-F（A=10，F=15）
        int hexNum = 0xA; // 十六进制的A（对应十进制10）
        // 十六进制转十进制计算：10（A）×16⁰ = 10
        System.out.println("十六进制 0xA 转十进制：" + hexNum);

        // 额外举一个复杂点的十六进制例子（巩固理解）
        int hexNum2 = 0x1F; // 十六进制的1F
        // 计算：1×16¹ + 15（F）×16⁰ = 16+15=31
        System.out.println("\n拓展：十六进制 0x1F 转十进制：" + hexNum2);
    }
}
```

## (二).浮点型
>double类型
> float类型，需要加上 **f** 后缀
下面是定义浮点数的例子:
```java
//下面是定义浮点数的例子：
float f1 = 3.14f;
float f2 = 3.14e38f; // 科学计数法表示的3.14x10^38
float f3 = 1.0; // 错误：不带f结尾的是double类型，不能赋值给float

double d = 1.79e308;
double d2 = -1.79e308;
double d3 = 4.9e-324; // 科学计数法表示的4.9x10^-324
```

#### 1.浮点数拓展：
- （1）浮点数不建议直接用==做相等比较，核心原因是浮点数的二进制存储存在精度误差，很容易出现逻辑错误。
- （2）浮点数（float/double）是基于二进制浮点表示法存储的，但很多十进制小数（比如0.1）转成二进制是无限循环的小数，计算机只能存储其 “近似值”（会截断或舍入），这就导致了精度丢失。
1. 例子 1：f == d输出false
float f = 0.1f：float是单精度浮点数，只能存约 7 位有效数字，它存储的0.1是 “近似值 A”；
double d = 1.0/10：double是双精度浮点数，存约 15-17 位有效数字，它存储的0.1是 “近似值 B”；
虽然数学上0.1=0.1，但 “近似值 A≠近似值 B”，所以f == d结果是false。

2. 例子 2：d1 == d2输出true
float d1 = 23131312312312313f：float的精度有限（只能精确表示约 7 位有效数字），这个数已经远超float的精度范围，存储时会被 “舍入” 成一个近似的大整数；
d2 = d1 + 1：因为d1本身是被舍入后的近似值，+1后超出了float的精度分辨能力，计算机无法区分d1和d1+1，所以两者存储的近似值完全一样，d1 == d2结果是true。

## (三).字符类型
> 字符类型char表示一个字符,只能写一个字不能写词组。Java的char类型除了可表示标准的ASCII外，还可以表示一个Unicode字符.

```java
// 字符类型
public class Main {
    public static void main(String[] args) {
        char a = 'A';
        char zh = '中';
        System.out.println(a);
        System.out.println(zh);
    }
}
```
**注意char类型使用单引号'，且仅有一个字符，要和双引号"的字符串类型区分开。**

## (四).字符串类型
> String 不是关键字，它是一个类。
> String 就可以写词组或句子了。

```java
String name = "一个椰子";

```

## (五).布尔类型
> 布尔类型boolean **只有true和false** 两个值
-布尔类型总是关系运算的计算结果

```java
boolean b1 = true;
boolean b2 = false;
boolean isGreater = 5 > 3; // 计算结果为true
int age = 12;
boolean isAdult = age >= 18; // 计算结果为false
```

## (六).引用类型
> 除了上述基本类型的变量，剩下的都是引用类型！

```java
//例如，引用类型最常用的就是String字符串:
String s = "hello";

// 变量之间的赋值
public class Main {
    public static void main(String[] args) {
        int n = 100; // 定义变量n，同时赋值为100
        System.out.println("n = " + n); // 打印n的值

        n = 200; // 变量n赋值为200
        System.out.println("n = " + n); // 打印n的值

        int x = n; // 变量x赋值为n（n的值为200，因此赋值后x的值也是200）
        System.out.println("x = " + x); // 打印x的值

        x = x + 100; // 变量x赋值为x+100（x的值为200，因此赋值后x的值是200+100=300）
        System.out.println("x = " + x); // 打印x的值
        System.out.println("n = " + n); // 再次打印n的值，n应该是200还是300？
   }
}
```
## (七).类型转换
> - 1.不能对boolean值进行转换。
> - 2.转换的时候可能存在内存溢出，或精度问题！

#### (1).强制转换：**表示的最大范围由高---低时需要强制转换！！**
强制转换格式：（类型）变量名   

```java
public class Dome1 {
    public static void main(String[] args) {
        int i = 128;
        byte b = (byte) i;//内存溢出

        //强制转换格式：  （类型）变量名

        System.out.println(i);
        System.out.println(b);
    }
}
```
输出结果：
<img width="620" height="217" alt="image" src="https://github.com/user-attachments/assets/15d1fbf6-0a7f-4add-b355-94d9dbf39dd4" />
byte的最大范围是-128 ~ 127，128超出范围造成溢出结果错误，如图中System.out.println(b);输出为-128是错误的

#### (2).自动转换：**表示的最大范围由低---高时会自动转换**
```java
public class Dome1 {
    public static void main(String[] args) {
        int i = 128;
        double b = i;//由低到高自动转换

        System.out.println(i);
        System.out.println(b);
    }
}
```

<img width="487" height="213" alt="image" src="https://github.com/user-attachments/assets/1774a6c1-7e58-4dc4-8a74-02abb33fbd9f" />
如图中结果输出b System.out.println(b);结果为128.0正确

```java
public class Dome2 {
    public static void main(String[] args) {
        //操作比较大的数字时，注意溢出问题
        //用下划线分割数字
        int money = 10_0000_0000 ; // 十亿
        int years = 20 ;
        //int total1 = money * years;//错误，出现溢出
        //long total2 = money * years;//错误，还是出现溢出。因为money * years在转换成long类型前就已经发生溢出，错误了。
        long total3 = money * ((long)years);//正确，先将money或years中的一个先转化成long类型，然后money*((long)years)的过程中自动转换成了long类型。
        System.out.println(total3);
    }
}
```

#### (3).jdk的特性，数字之间可以用下划线分割。
当数字很大难以区分时可以使用下划线分割，方便识别。
```java
public class Dome2 {
    public static void main(String[] args) {
        //操作比较大的数字时，注意溢出问题
        //用下划线分割数字
        int money = 10_0000_0000 ; // 十亿
        int years = 20 ;
        //int total1 = money * years;//错误，出现溢出
        //long total2 = money * years;//错误，还是出现溢出。因为money * years在转换成long类型前就已经发生溢出，错误了。
        long total3 = money * ((long)years);//正确，先将money或years中的一个先转化成long类型，然后money*((long)years)的过程中自动转换成了long类型。
        System.out.println(total3);
    }
}
```



## (八).常量
> - 定义变量的时候，如果加上final修饰符，这个变量就变成了常量
> - 核心特点是 “一旦完成初始化赋值，后续就无法再修改其值”
> - 为了和变量区分开来，常量名通常全部大写 + 下划线分隔的格式

```java
// 例子
final double PI = 3.14; // PI是一个常量
double r = 5.0;
double area = PI * r * r;
PI = 300; // compile error!
```

![现在就出发](https://www.naifeitv.xyz/upload/vod/20251018-1/13902da461173debdceccceae6bbfbdc.jpg)
[点击跳转到现在就出发](https://v.qq.com/x/cover/mzc00200znyfa5u/g4101cwlymi.html)

姓名|年龄|性别|
--|--|--|
tyy|18|y|










