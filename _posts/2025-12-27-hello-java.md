---
layout: post
title: "Java 变量与数据类型学习总结"
date: 2025-12-27 12:00:00 +0800
categories: [Java基础]
tags: [变量, 数据类型]
---

# 一、变量的定义
## 1.变量是存储数据的容器，变量必须先定义后使用,(基本变量)定义格式：
```java
// 数据类型 变量名 = 赋值;
int age = 18;
double score = 92.5;
```
### (1).不写初始值，就相当于给它指定了默认值。默认值总是0。
## 2.引用类型的变量
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






