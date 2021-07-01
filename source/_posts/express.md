---
title: Express
date: 2021-4-15 12:00:00
categories: 
    - web前端开发
    - JavaScript
tags: 
    - JavaScript
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=1456270729.mp3
cover: https://img1.baidu.com/it/u=2799030891,3348642794&fm=26&fmt=auto&gp=0.jpg
---
# 简单使用express
首先安装 npm i express 、body-parser (post请求需要用到)

1.分别引用：import express from 'express';(如果没有引用bable,可以用require()引用)

import baodyParser from 'body-parser';

import fs from 'fs'

import path from 'path'

2. const app=express() //创建一个express应用

3. const post=3000 端口号

4. 用一下body-parser :app.use(bodyParser.json())

app.use(bodyParser.urlencoded({extended:false}))

下面就可以使用 get post 进行请求了

app.post('/post',(req,res)=>{

　　

})

app.get('/gett',(req,res)=>{

　　

})

app.listen(post,()=>{//监听端口号

 　　console.log(post)

})

 题外：1.关于express中间件的简单概述：在use(),get(),post()等方法里面是都可以使用中间件的。写法：app.user((req,res,next)=>{

　　console.log('继续往下走')

　　next()//如果不写next它是不会继续执行下面代码的

　　由此可简单说一个例子：就是有了这个中间件我们可以把一些公共逻辑放在use()方法中来执行，如果可行就next()继续往下走，否则停止本次请求。因为use()方法不管什么请求都会走进来！我们可以在这里进行账号密码的校验，因为不论登录还是注册都是要校验的，所以不可能登录和注册的接口都要写一遍校验。这个时候我们可以把校验这段逻辑放在use()方法中，如果校验通过就可以继续请求，否则直接停止。所以有了它就可以减少代码冗余问题。

})

　　2. express 重定向：使用 express.get('*',(req,res)=>{//就是当所有的请求都找不到时，给它重定向到一个专门的404页面。第一个参数是 *（通配符 所有），后面依然是回调函数

　　express.redirect('404.网页')//用redirect方法做重定向

})

　　3. 请求对象req的方法：

　　　　req.body :获取post请求体的数据

　　　　req.query获取get请求的数据

　　　　req.originnalUrl 获取原始url地址、当需要处理路径的时候可以还可以用req.baseUrl，req.path  这三个方法是可以操作url的。

　　　　req.get('Content-type')用来获取请求头

　　4. 响应对象res的方法：

　　　　res.set('key',value)设置响应头  key:响应头的字段名称  。 value:值。

　　　　res.send()发送数据

　　　　res.senfFile()发送文件

　　　　res.redirect()重新定向 参数是文件的地址

　　　　res.download()下载

　　　　res.jsonp()以jsonp的方式返回数据