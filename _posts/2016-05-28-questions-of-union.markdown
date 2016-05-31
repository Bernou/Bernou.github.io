---
layout: post  
title:  "think in union!"  
categories: jekyll update  
---

# 什么是union #

* union 是c++一种类型,翻译成汉语就是"共用体",从名字我们大概就可以了解到它的大致特点，共用。
* union 在实际的项目中应用的蛮多的，比如最近我们的一个通用排行榜系统就是使用union。
* union 的样子是这个样子   
```
union Test{   
  int a;    
   double b;   
};   
```
     

# 使用union的优点和注意事项#

* union 和 struct 进行比较的话,能够比较明显的展现union的特点
    * 内存布局   
    ```
    struct Test          
    {  
        int    a;      //4 byte          
        double b;      //8 byte       
    };     
    ```     
    sizeof(struct Test) 占用12字节,两个变量的内存是单独分配，因此整个结构体的是各个成员的内存之和
    当然要考虑内存内存对齐的情况  ^-^

    而对于:   
    ```
    union Test     
    {    
        int    a;         
        double b;       
    };   
    ```     

    sizeof(union Test) 占用8字节，union成员之前共用同一个内存地址，内存的使用是相互覆盖，这就充分体现了共用的特点，
    所以呢，union的内存大小是要满足内存占用最大的成员变量(大的满足了，小的肯定够用啦 ^~^ ),当然也要注意内存对齐的
    情况。
    * 其他的一些点
        *struct 可以定义static 成员变量，而union不可以( 问我为什么，union说: 我是属于大家的，任何人都不能吃独食,不然宝宝不开心* ~ * )



# 一些实例


