---
title:  "基础知识面试题"
modified: 2020-08-03T20:03:49
categories: 
  - java基础知识
tags:
  - java基础知识
  - 面试题
---
{% include toc title="目录" %}

## 1.Java 基本类型与引用类型的区别？
基本类型保存原始值，引用类型保存的是引用值（引用值就是指对象在堆中所 处的位置/地址）

## 2.Java 8种基本类型及其字节长度

| 类型名称 | 字节空间 |    取值范围     |
| :------: | :------: | :-------------: |
|   byte   |    1     |  -2^7----2^7-1  |
|  short   |    2     | -2^15----2^15-1 |
|   int    |    4     | -2^31----2^31-1 |
|  float   |    4     | -2^31----2^31-1 |
|   long   |    8     |  -2^63----2^63  |
|  double  |    8     |  -2^63----2^63  |
|   char   |    2     | -2^15----2^15-1 |
| boolean  |    1     |                 |




## 3.自动装箱和拆箱？
自动装箱是Java 编译器在基本数据类型和对应的对象包装类型之间做的一个转化。
比如：把int转化成 Integer，double转化成 Double，等等。反之就是自动拆箱。
原始类型: boolean，char，byte，short，int，long，float，double 
封装类型：Boolean，Character，Byte，Short，Integer，Long，Float，Double
装箱：将基本类型用它们对应的引用类型包装起来；
拆箱：将包装类型转换为基本数据类型；

## 4.short s1 = 1; s1 = s1 + 1;有什么错? short s1 = 1; s1 +=1;有什么错?
1) 对于 shorts1=1;s1=s1+1 来说，在s1+1 运算时会自动提升表达式的类型为 int， 那么将int赋予给 short类型的变量 s1会出现类型转换错误。
2) 对于 short s1=1;s1+=1 来说 +=是java 语言规定的运算符，java 编译器会对它 进行特殊处理，因此可以正确编译。

## 5.两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？

不对

1.若重写了equals(Object obj)方法，则有必要重写hashCode()方法。

2.若两个对象equals(Object obj)返回true，则hashCode（）有必要也返回相同的int数。

3.若两个对象equals(Object obj)返回false，则hashCode（）不一定返回不同的int数。

4.若两个对象hashCode（）返回相同int数，则equals（Object obj）不一定返回true。

5.若两个对象hashCode（）返回不同int数，则equals（Object obj）一定返回false。



关于hashCode和equal是方法是有一些 常规协定 ：   

1. 在 Java 应用程序执行期间，在同一对象上多次调用 hashCode 方法时，必须一致地返回相同的整数，前提是对象上 equals 比较中所用的信息没有被修改。从某一应用程序的一次执行到同一应用程序的另一次执行，该整数无需保持一致。   
2. 如果根据 equals(Object) 方法，两个对象是相等的，那么在两个对象中的每个对象上调用 hashCode 方法都必须生成相同的整数结果。   
3. 以下情况不 是必需的：如果根据 equals(java.lang.Object) 方法，两个对象不相等，那么在两个对象中的任一对象上调用 hashCode 方法必定会生成不同的整数结果。但是，程序员应该知道，为不相等的对象生成不同整数结果可以提高哈希表的性能。   
4. 实际上，由 Object 类定义的 hashCode 方法确实会针对不同的对象返回不同的整数。（这一般是通过将该对象的内部地址转换成一个整数来实现的，但是 JavaTM 编程语言不需要这种实现技巧。）   
5. 当equals方法被重写时，通常有必要重写 hashCode 方法，以维护 hashCode 方法的常规协定，该协定声明相等对象必须具有相等的哈希码。