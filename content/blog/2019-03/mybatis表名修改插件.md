---
title: "Mybatis表名修改插件"
date: 2019-03-05T22:12:53+08:00
draft: false
summary: "  有时候我们需要通过同一套 mybatis mapper 来操作相同的表结构但是却拥有不同的表名的时候，这个插件可以帮助我们在执行mapper的时候动态更改操作的表名字。..."
img: /images/The_Elder_Scrolls_V_Skyrim_forest.jpg
toc: true
id: 2019031001
author: magic

typora-copy-images-to: ..\..\..\static\images
typora-root-url: ..\..\..\static
---

&#160;&#160;&#160;&#160;&#160;&#160;有时候我们需要通过同一套 mybatis mapper 来操作相同的表结构但是却拥有不同的表名的时候，这个插件可以帮助我们在执行mapper的时候动态更改操作的表名字。目前只提供在做增删改查的时候，动态的追加表名后缀到mybatis的mapper sql 中。

#### 

#### 特性

基于springboot2开发，实现了自动装配。完美兼容 pagehelper 插件，只捕获处理 select,insert,delete,update 语句。项目地址:  <a href="https://github.com/magicdogs/tablehelper">tablehelper</a>



#### MAVEN使用姿势

```java
<dependency>
   <groupId>com.magicdogs.tablehelper</groupId>
   <artifactId>springboot2-tablehelper</artifactId>
   <version>1.0.0-SNAPSHOT</version>
</dependency>
```



#### 项目中使用方式

```java
PageHelper.startPage(1,10);
TableNameHelper.suffix("_default");
int id = 587;
RiskRuleProperty riskRuleProperty = riskRulePropertyMapper.selectByPrimaryKey(id);
TableNameHelper.suffix("_default");
riskRulePropertyMapper.updateByPrimaryKeySelective(riskRuleProperty);
TableNameHelper.suffix("_default");
riskRulePropertyMapper.deleteByPrimaryKey(id);
TableNameHelper.suffix("_default");
riskRulePropertyMapper.insertSelective(riskRuleProperty);
```



#### 执行效果

![效果](/images/Capturer_gif_20190307_114746_053.gif)