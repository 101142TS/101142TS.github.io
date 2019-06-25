---
layout:     post
title:      DexLego
subtitle:   Reassembleable Bytecode Extraction For Aiding Static Analysis
date:       2019-06-25
author:     101142ts
header-img: img/post-bg-hacker.jpg
catalog: true
tags: Android 
---
论文阅读

来源：2018 48th Annual IEEE/IFIP International Conference on Dependable Systems and Networks

## Abstart
代码隐藏技术会困扰着静态分析工具。因此，我们提出了DexLego系统，这个系统能够提取字节码，帮助静态分析工具揭示Android应用的恶意行为。在运行时，DexLego利用及时收集来提取应用中的数据和字节码。在离线时，DexLego将这些东西重组成一个新的Dex文件。实验显示DexLego能够重组出正确的Dex文件，显著的提升了现有静态分析系统的分析结果。

## Introduction
理解恶意软件的行为很有必要，静态工具通常用来分析恶意软件。但是，恶意软件编写者可以隐藏恶意行为，通过使用一系列的混淆技术。报告显示加壳应用已经增长了9倍，其中三分之一是恶意软件。静态分析工具通常使用直接分析Dex文件中的字节码来分析一个应用中的恶意行为。加壳服务会将原始的Dex文件替换成一个壳Dex文件，在运行时动态的释放出原始的Dex文件。此外，原来的Dex文件会被加密，直到运行时才会解密。由于免费加壳服务的存在，因此静态的分析工具在分析时只能够获取壳Dex文件，而没办法获取原始的Dex文件。