---
title: Java 13 - 判断对象是否存活
date: 2018-07-28 05:14:50
categories: Java
---
# 判断对象是否存活

<!--more-->

程序计数器, 虚拟机栈, 本地方法栈属于线程私有, 只存在于线程的生存周期内, 线程结束也就跟着消失了, 因此不需要对上述空间进行垃圾回收. 只需要考虑方法区和堆.

那么我们判断一个对象是否存活就有下列两种方法:

1. 引用计数法

    通过给对象添加一个引用计数器, 判断被引用次数是否为0来确定是否存活. 但是弊端在于循环引用导致环状死亡对象不能被回收.

1. 可达性分析算法

    通过GC Roots作为起始点来进行搜索, 能够到达的对象都是存活的, 不可达的对象可被回收.

    Java中的GC Roots包含以下内容:

    1. 虚拟机栈中引用的对象.

    2. 本地方法栈中引用的对象.

    3. 方法区中类静态属性引用的对象.

    4. 方法区中常量引用的对象