# DexLego:Reassembleable Bytecode Extraction For Aiding Static Analysis

## Abstart
代码隐藏技术会困扰着静态分析工具。因此，我们提出了DexLego系统，这个系统能够提取字节码，帮助静态分析工具揭示Android应用的恶意行为。在运行时，DexLego利用及时收集来提取应用中的数据和字节码。在离线时，DexLego将这些东西重组成一个新的Dex文件。实验显示DexLego能够重组出正确的Dex文件，显著的提升了现有静态分析系统的分析结果。

## Introduction
