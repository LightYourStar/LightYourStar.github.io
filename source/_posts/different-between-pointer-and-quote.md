---
title: 指针和解引用，引用和取地址的区别
date: 2021-03-30 10:35:18
tags: c++ pointer reference
---
### 指针*：指向对象的地址  取地址&：获取变量在内存中的地址
{% codeblock lang:Cpp %}
    int i = 10;
    int *p = &i;
{% endcodeblock %}
&i是i在内存中的地址
p是指针，p存放变量i的地址

### 引用&：别名，只能指向一个对象不可更改
{% codeblock lang:Cpp %}
    int j = 20;
    int &ref_j = j;
{% endcodeblock %}
ref_j 是j的引用，ref_j的值为等于j即20
修改j的值ref_j随之改变，修改ref_j的值 j的值也随之改变，引用必须初始化

### 解引用*：取指针指向的地址的存储内容
{% codeblock lang:Cpp %}
    int j = 20;
    int *p = &j; //p为指针
    cout << *p << endl; //输出20
{% endcodeblock %}
*p中的*为解引用标识符，*p为取p指向的地址&j中存储的值20；

###小技巧
    跟随类型名（int\double...) 后面出现的*则是指针，出现在表达式中的*为解引用
    跟随类型名（int\double...) 后面出现的&则是引用，出现在表达式中的&为取地址
    可以把指针、接引用， 引用、取地址理解为不同的标识符


