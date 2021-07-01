---
title: History
date: 2021-1-1 12:00:00
categories: 
    - web前端开发
    - JavaScript
tags: 
    - JavaScript
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=1456270729.mp3
cover: https://img2.baidu.com/it/u=3429416796,2324999190&fm=26&fmt=auto&gp=0.jpg
---
#### history:接口允许操作浏览器的曾经在标签页或者框架里访问的绘画历史记录。
history不继承任何接口。就是它不需要别的接口来调用它，想使用它直接使用就行。
### 属性
1. history.length :它返回一个整数，该整数表示会话历史中元素的数目，包括当前加载的页。
2. history.scrollRestorration:允许Web应用程序在历史导航上显式地设置默认滚动恢复行为。此属性可以是自动的或者手动的
3. history.state:返回一个表示历史堆栈顶部的状态的值，这是一种可以不必等待popstate事件而查看状态的事件
### 方法
1. history.back() 在浏览器历史记录里前往上一页，用户可点击浏览器左上角的返回 等同于 history.go(-1)
2. history.forward() 在浏览器历史记录里前往下一页，用户可点击浏览器左上角的前进 等同于history.go(1)
3. history.pushState() 按指定的名称和URL（如果提供该参数）将数据push进会话历史栈，数据被DOM进行不透明处理；你可以指定任何可以被序列化的javascript对象。注意到Firefox现在忽略了这个title参数
4. history.replaceState() 按指定的数据，名称和URL(如果提供该参数)，更新历史栈上最新的入口。这个数据被DOM 进行了不透明处理。你可以指定任何可以被序列化的javascript对象。注意到Firefox现在忽略了这个title参数