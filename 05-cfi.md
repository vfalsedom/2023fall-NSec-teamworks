# Group-5 CFI

#### 相关链接

[此项目的 GitHub repository](https://github.com/Group-5-for-Compiler-H/Group5-CFI)

[实验报告链接]()  



## 成员

| 姓名   | 学号       | GitHub用户名                                                 |
| ------ | ---------- | ------------------------------------------------------------ |
| 赵梓涓 | PB20061369 | [zzzzzzzzjj](https://github.com/orgs/Group-5-for-Compiler-H/people/zzzzzzzzjj) |
| 王芊予 | PB20061363 | [07lengmo](https://github.com/orgs/Group-5-for-Compiler-H/people/07lengmo) |



## 简介

控制流劫持是一种危害性极大的攻击方式，攻击者能够通过它来获取目标机器的控制权，甚至进行提权操作，对目标机器进行全面控制。代码注入(shellcode)的方式、代码重用(ROP)攻击方式、DOP(Data Oriented Programming)攻击方式等都属于控制流劫持。

为了应对新型的控制流劫持攻击，控制流完整性（Control Flow Integrity, CFI）的防御机制应运而生。其核心思想是限制程序运行中的控制转移，使之始终处于原有的控制流图所限定的范围内。具体做法是通过分析程序的控制流图，获取间接转移指令（包括间接跳转、间接调用、和函数返回指令）目标的白名单，并在运行过程中，核对间接转移指令的目标是否在白名单中。控制流劫持攻击往往会违背原有的控制流图，CFI使得这种攻击行为难以实现，从而保障软件系统的安全。这一技术被应用于LLVM/Clang、Microsoft、Intel Control-flow Enforcement Technology、Android等安全防护场景。

LLVM/Clang提供了CFI保护选项，这一CFI保护机制依靠链接时优化（LTO），主要使用了前向边沿的防护（forward-edge protection）、后向边沿防护（backward-edge protection，使用影子调用堆栈SCS）两种方式。

本实验主要任务：研究控制流劫持原理和不同CFI防护方法，比较各种方法优劣；通过比较CFI优化前后IR和汇编码的不同、对程序进行攻击，验证CFI的原理；尝试编写一个pass实现CFI保护。



## 研究任务以及分工

#### 赵梓涓：

查阅文献了解CFI原理与应用

- 查阅资料

- 结合论文和代码介绍说明CFI要解决的问题和实现原理

  不同CFI的优劣分析

  CFI的应用场景介绍

- 比较CFI优化前后的程序汇编代码，说明保护控制流完整性的具体方法

#### 王芊予：

编写实例

- 控制流劫持攻击实现

  编写程序实现注入攻击

- 调用llvm链接时优化CFI对上一步被攻击程序进行保护

  尝试再次攻击，验证效果

  验证CFI对控制流劫持的保护效果保护效果

  

## 进展记录

12. 25查阅资料确定研究课题

1.11	确定研究思路

1.12	阅读文献学习控制流攻击原理、

## 讨论记录

1.12	青年之家讨论选题和任务分工，3h

1.13	

## 问题记录

Return-to-libc、ROP(Return Oriented Programming)攻击原理是什么？

有哪些保证控制流完整性的方法？原理是什么？效果如何？

如何在使用clang/LLVM进行优化时调用CFI？

## 待办清单

- [x] 研究控制流劫持原理和不同CFI防护方法，比较各种方法优劣；

- [ ] 通过比较CFI优化前后汇编码的不同，验证CFI的原理；

- [ ] 对经过CFI优化后的程序进行攻击，检验保护效果；

- [ ] 尝试编写一个pass实现CFI保护；

  


## 引用

[Control-Flow Integrity Principles, Implementations, and Applications](https://www.cs.columbia.edu/~suman/secure_sw_devel/p340-abadi.pdf)

[Control-Flow Integrity: Precision, Security, and Performance](https://arxiv.org/pdf/1602.04056v1.pdf)

[Analyzing Control Flow Integrity with LLVM-CFI](https://arxiv.org/pdf/1910.01485.pdf)

