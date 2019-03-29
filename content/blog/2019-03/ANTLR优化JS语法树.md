---
title: "ANTLR优化JS语法树"
date: 2019-03-29T12:48:45+08:00
draft: false
summary: "ANTLR优化JS语法树"
img: /images/The_Elder_Scrolls_V_Skyrim_forest.jpg
toc: true
id: 2019032901
author: magic

typora-copy-images-to: ..\..\..\static\images
typora-root-url: ..\..\..\static
---



# ANTLR优化JS语法树

## 1.背景

在最近项目中，对老的风控项目进行重构，风控决策包含很多的规则项和表达式，老项目使用的是apache jexl 这个脚本引擎来解析和执行表达式的计算，对于重构后的新项目打算将脚本引擎换成java8 里面的 javascript 引擎，通过程序的清洗转换，老的表达式都转换成新的 js 函数。转换过来的表达式如下图所示：

![img](/images/15538363338245.png)

转换过来的函数包含很多重复调用，如何解决重复调用呢？ 第一想法可能就是人工修改，有没有办法通过程序来实现这个功能呢？ 答案是有的，antlr 就可以做到。项目的 github 地址： https://github.com/magicdogs/antlr-parser



## 2.语法生成树

antlr 的功能可以说是非常的强大，各式各样的语法规则都能在 https://github.com/antlr/grammars-v4 这个仓库里找得到，antlr  github 地址是 https://github.com/antlr/antlr4 ，环境搭建不在本文的讨论范围之内,搭建环境也很简单，根据官方的getting start 来就可以了。开发的同学可以直接安装对应的IDE插件就可以了，方便快捷生成解析工具类和访问器。

对应的语法文件和测试代码我都会放到我的仓库，首先来展示一下antlr 强大的语法解析生成树

![img](/images/15538370263839.png)



## 3.执行优化后的结果



![img](/images/15538372615675.png)



虽然不是很完美，但是可以减少很多手工的工作量哦。