---
title: 函数的length
date: 2020-10-10 12:00:00
categories: 
    - web前端开发
    - JavaScript
tags: 
    - JavaScript
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=1824025894.mp3
cover: https://img2.baidu.com/it/u=3429416796,2324999190&fm=26&fmt=auto&gp=0.jpg
---
## ES6中的函数length属性
ES6中函数的length属性，将返回没有指定默认值的参数个数。也就是说指定了默认值后，length属性将失真。
```
在es6之前函数的length就是指函数声明形参的个数
function fn1(){} //length为0
function fn2(a,b){} //length为1
function fn3(a,b,c) //length为3
```
但是在ES6之后，就发生了变化，因为ES6更新了一个新特性，让函数可以给形参设置默认值
```
function fn1(a,b=10){}
//这种写法在ES6之前是不允许的
```
有了这一新特性之后，length的解释就要修改成这样：length的值是指函数的第一个具有默认值得形参之前的形参的个数！！！
写点代码更好理解
```
function fn1(a,b){} //因为a,b 没有默认值，length的值为2！
function fn2(a=1,b){} //因为a 为‘第一个具有默认值得形参’，而a的前面没有其他形参了，所以length为1
function fn3(a,b=1,c){} //b为‘第一个具有默认值的形参’，前面还有一个a，length为1 。
function fn4(a,b,c=1){} //所以length为2 因为‘c为第一个具有默认值的形参’
function fn5(a,b=1,c,d=2){} //length为1。因为‘b为第一个具有默认值的形参’，它前面只有一个a,并且只算
//具有默认值形参前面的形参的个数，后面的不算所以是1个。
```
```
注意，当函数拥有剩余参数时，比如
function fn1(a,...args){} //length为1，剩余参数也有默认值，默认为空数组。前面有只有一个a，所以length为1
function fn1(...args){} //如果函数形参只有一个默认参数，那么length为0！
```