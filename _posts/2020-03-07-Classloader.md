---
layout:     post
title:      Android ClassLoader
subtitle:   android
date:       2020-03-07
author:     101142ts
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - android
---


# 什么是ClassLoader

ClassLoader是负责加载类的，在给定类的名字以后，ClassLoader应该尝试去定位或者生成该类的定义。ClassLoader是一个抽象类，所以应用可以自定义ClassLoader以使用自己想要的方式加载类。

## 委托模型

ClassLoader使用委托模型来搜索类和资源。每一个ClassLoader的实例都有一个父类ClassLoader，当对一个ClassLoader请求类或资源时，该ClassLoader会首先向它的父类ClassLoader请求。父类ClassLoader同理。"bootstrap class loader"是虚拟机内置的ClassLoader，其没有父类ClassLoader，但**可能**会成为其他ClassLoader的父类。

比较两个类是否相等只有在相同的ClassLoader下比较才有意义。哪怕是同一个类，分别使用系统的ClassLoader加载和使用应用自定义的ClassLoader加载，其也会被认为是不同的。

有些公共类我们希望它们哪怕被不同的ClassLoader加载，也被视为相等。这是通过委托模型实现的，因为公共类可以被ClassLoader的某个爷爷ClassLoader加载，所以一个公共类如果想要被不同的ClassLoader加载，还能被视为相等。只要这些不同的ClassLoader是通过相同的爷爷ClassLoader加载就行。
## 并行ClassLoader

如果委托模型不够严格，类加载可能引发死锁，因为类加载过程中保持了类加载器锁。


## 类的来源

不是所有的类都来源于对文件的加载，有些类可能来源于网络，也可能来源于应用的制造。defineClass方法将字节的数组转换成类。每一个ClassLoader都应该有名为loadClass的方法用以加载类

## 使用ClassLoader加固应用

不太懂，见[这里](https://www.jianshu.com/p/ce20fa304e1e)

自定义类加载器加密Dex文件的[例子](https://juejin.im/post/5cd57c216fb9a031ec6d426b)