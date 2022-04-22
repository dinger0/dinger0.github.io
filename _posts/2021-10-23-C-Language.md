---
title: C语言的注意事项
author: dinger0
date: 2021-10-23 15:10:00 +0800
categories: [技术, 总结]
tags: [C语言, C++]
render_with_liquid: false
math: false
#image:
#  src: /pics/0.jpg
#  width: 1024   # in pixels
#  height: 768   # in pixels
#  alt: image alternative text
---

**记录一些自己写代码遇到的小问题，不定期更新。**

## 1. C/C++语言区别

### 1.1 malloc()函数

在C++语言中，`malloc()` 返回的类型是 `void*` 指针，需要做类型转换，但是C语言不需要。

### 1.2 const

 - 在C语言中，`const`修饰的变量不能用作申请数组的长度，编译器认为其只读，而不是常量，但是在C++中可以。

 - `const`修饰的全局变量不能通过指针进行修改，但是局部变量可以。

 - `const`右侧修饰的是什么，就是什么不能被**直接**修改。

## 2. C语言

### 2.1 结构体和结构体指针的访问

在C语言中，访问结构体的成员，使用 `struct_name.member` ，结构体指针的话，使用 `struct_name->member`。

### 2.2 typedef与#define的区别

```c
#include <stdio.h>
typedef int * PTRINT;
#define pint int *
int main()
{
    int a = 10;
    int b = 11;
    const int * p1 = &a; //指针常量，即p1指向的地址的内容不能通过指针的形式进行修改，但p1指向的地址可变。
    //*p1 = 11; //error:ssignment of read-only location ‘*p1’
    //p1 = &b; //无问题
    int * const p2 =&b; //常量指针，即p2指向地址不可变，但p2指向的地址的内容可变。
    //*p2 = 11; //无问题
    //p2 = &a; //error: assignment of read-only variable ‘p2’

    pint c, d; //等价于 int *a, b;
    //c = &a; //无问题
    //d = &a; //warning: assignment to ‘int’ from ‘int *’ makes integer from pointer without a cast
    PTRINT e, f; //PTRINT是一种类型，类似于 int a, b;
    //e = &a; //无问题
    //f = &a; //无问题

    const pint g; //声明了一个指针常量
    const PTRINT h; //声明了一个常量指针
    //*g = 11; //error: assignment of read-only location ‘*g’
    //g = &b; //无问题
    //*h = 11; //无问题
    h = &a; //error: assignment of read-only variable ‘h’
    
    printf("1\n");
}
```
`define`只是字符的替换，`typedef`作为一个新的类型。

### 2.3 数组、形参和sizeof()函数

```c
#include <stdio.h>
void fun(int *arr)
{
    printf("fun:%d\n", (int)(sizeof(arr) / sizeof(arr[0])));
}
int main()
{
    int arr[4] = {0};
    printf("main():%d\n", (int)(sizeof(arr) / sizeof(arr[0]))); //main():4
    fun(arr); //fun:2
}
```
数组名做形参，传入的是数组首元素指针，另外，C语言不能实现函数默认参数。

### 2.4 main()函数参数

```c
#include <stdio.h>
int main(int argc, char** argv) //等价 int main(int argc, char* argv[])
{
    // argc表示参数个数，argv表示指向参数的指针数组。
    // argv[0]:程序运行路径，argv[1]:运行路径后第1个字符串
    // 运行命令：./a.out 0000      输出：2 0000
    printf("%d\n", argc);
    printf("%s\n", argv[1]);
}
```

### 2.5 可变数组

C99及以后版本支持不定长数组的声明,再也不要用malloc和free了。