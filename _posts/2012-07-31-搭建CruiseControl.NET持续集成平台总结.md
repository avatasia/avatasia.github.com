---
layout: post
title: "搭建CruiseControl.NET持续集成平台总结"
description: ""
category: 
tags: [.net,持续集成,CC.NET]
---
{% include JB/setup %}

# 搭建CruiseControl.NET持续集成平台总结

参照博客园L.Qiu的文章[CruiseControl.Net持续集成平台搭建总结](http://www.cnblogs.com/qiuliang/archive/2011/05/04/2036557.html),下载地址要去[sf.net](http://sf.net)找，我下的是最新的1.8.0版。

## CC.Net的安装中出现的问题
1. 系统服务中无法启动CC.Net

这是因为CC.Net安装目录下ccnet.conf没有配置，可参照L.Qiu的文章里的配置，如果XML格式错误，也会启动失败。

2. SVN认证错误

我使用的是VisualSVN Server，默认开启了Https,由于证书的原因，CC.Net自动运行的时候会出错，在控制台下运行svn时，要手动选择继续操作。 这里试了很多办法都不行，只好把SVN改成http。

3. MSBuild编译过程中出错

在vs的项目里，如果有unload的工程，那么自动编译时就会报错，这个要可以通过合理配置Configuration Manager,设置Build选项来解决。