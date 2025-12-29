---
layout: post
title: "Java 变量与数据类型学习总结"
date: 2025-12-27 12:00:00 +0800
categories: [Java基础]
tags: [变量, 数据类型]
---

# 一、变量的定义
## (一).变量是存储数据的容器，变量必须先定义后使用,(基本变量)定义格式：
```java
// 数据类型 变量名 = 赋值;
int age = 18;
double score = 92.5;
```
> 不写初始值，就相当于给它指定了默认值。默认值总是0。
## (二).引用类型的变量
```java
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
# 二、 基本数据类型
Java定义了以下几种基本数据类型：
- **整数类型：byte，short，int，long**
- **浮点数类型：float，double**
- **字符类型：char**
- **布尔类型：boolean**

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
- int: -2147483648 ~ 2147483647
- long: -9223372036854775808 ~ 9223372036854775807
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
## (浮点型)
![现在就出发](https://www.naifeitv.xyz/upload/vod/20251018-1/13902da461173debdceccceae6bbfbdc.jpg)
[点击跳转到现在就出发](https://v.qq.com/x/cover/mzc00200znyfa5u/g4101cwlymi.html)










