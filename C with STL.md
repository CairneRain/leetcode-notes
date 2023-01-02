# Leetcode Notes

> Rui Chen

----

## C++ with STL 基础知识

### Basic

Hello World

```c++
#include <iostream>
using namespace std;
int main(){
    cout<<"Hello, World"<<endl;
    return 0;
}
```

数组

```c++
//声明
double test[10];
//初始化
double test[]={1,2,3};
double test[3]={1,2,3};
//赋值
test[1]=10;

//指针
double * fp=test;

cout<<*fp<<*(fp+1);
cout<<*test<<*(test+1);
cout<<fp[0]<<fp[1]

//函数
int* foo(int* param);
int* foo(int param[]);
int* foo(int param[]10);
```

字符串

- C风格

```c++
//C风格
char site[3]={'C','R','\0'}
char site[]="CR";

//方法
#include<cstring>
strcpy(s1,s2);//复制s1到s2
strcat(s1,s2);//s2添加到s1后面
strlen(s1);//s1的长度
strcmp(s1,s2);//相同返回0，小于返回负数，大于返回正数
strchr(s1,ch);//s1中ch出现的位置
strstr(s1,s2);//s1中s2出现的位置
```

- C++

```c++
#include<string>

string str1="cr";
string str2="zds";
string str3;

str3=str1+str2;
int len=str3.size();
```

Scope

- 定义在最外面的是全局变量，被本文件和所有其他的文件公用，其他文件调用此变量，需要声明extern，不同文件不可重名，生命周期和程序运行周期一样。

- 在函数里的是局部变量

- static全局变量：作用范围限制在定义的文件中，不同文件可以重名，生命周期和程序运行周期一样，同时只初始化一次

- static局部变量：在定义的函数范围内有效，但是生命周期和程序运行周期一样，并且只会执行第一次初始化，可以复制多次。如未赋值，则系统自动赋值

- extern 声明全局变量，注意是声明不是定义

- 全局函数和静态函数，默认都是全局的，用static声明后规定此函数只能在定义的文件中使用，其他文件中声明了也没用

### Standard Template Library

```c++
//数组
//链表
//栈
//队列

```



## Algorithms
