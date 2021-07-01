---
title: JavaScript ES5和Es6的区别
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
#### 什么是ES5

    ECMAScript第五个版本

##### 1. strict模式

    严格模式，限制一些用法，'use strict';

##### 2. Array增加方法

    增加了every、some 、forEach、filter 、indexOf、lastIndexOf、isArray、map、reduce、reduceRight方法
    
    还有其他方法 Function.prototype.bind、String.prototype.trim、Date.now

##### 3. Object方法

    Object.getPrototypeOf
    Object.create
    Object.getOwnPropertyNames
    Object.defineProperty
    Object.getOwnPropertyDescriptor
    Object.defineProperties
    Object.keys
    Object.preventExtensions / Object.isExtensible
    Object.seal / Object.isSealed
    Object.freeze / Object.isFrozen

#### 什么是ES6

    ECMAScript6版本 
    
    ES6特性如下：
    
    1.块级作用域 关键字let, 常量const
    
    2.对象字面量的属性赋值简写

```
    let width = "100px";
    let height = "200px";
    let background = "red";
    let style = {
        width,
        height,
        background,
        method(){
            console.log("hello");
        }
    }
    style.method();   //"hello"
```

    3.赋值解构

```let singer = { first: "Bob", last: "Dylan" };
let { first: f, last: l } = singer; // 相当于 f = "Bob", l = "Dylan"
let [all, year, month, day] =  /^(\d\d\d\d)-(\d\d)-(\d\d)$/.exec("2015-10-25");
let [x, y] = [1, 2, 3]; // x = 1, y = 2```

    4.函数参数 - 默认值、参数打包、 数组展开（Default 、Rest 、Spread）

```

    //Default
    function findArtist(name='lu', age='26') {
        ...
    }
    
    //Rest
    function f(x, ...y) {
    // y is an Array
    return x * y.length;
    }
    f(3, "hello", true) == 6
    
    //Spread
    function f(x, y, z) {
    return x + y + z;
    }
    // Pass each elem of array as argument
    f(...[1,2,3]) == 6

```
    5.箭头函数 Arrow functions

    (1).简化了代码形式，默认return表达式结果。

    (2).自动绑定语义this，即定义函数时的this。如上面例子中，forEach的匿名函数参数中用到的this。

    6.字符串模板 Template strings
```

    var name = "Bob", time = "today";
    `Hello ${name}, how are you ${time}?`
    // return "Hello Bob, how are you today?"

```
    7. Iterators（迭代器）+ for..of

    迭代器有个next方法，调用会返回：

    (1).返回迭代对象的一个元素：{ done: false, value: elem }

    (2).如果已到迭代对象的末端：{ done: true, value: retVal }
```

    for (var n of ['a','b','c']) {
    console.log(n);
    }
    // 打印a、b、c```
    
    8.Class

Class，有constructor、extends、super，但本质上是语法糖（对语言的功能并没有影响，但是更方便程序员使用）。

```
class Artist {
    constructor(name) {
        this.name = name;
    }

    perform() {
        return this.name + " performs ";
    }
}

class Singer extends Artist {

    constructor(name, song) {
        super.constructor(name);
        this.song = song;
    }

    perform() {
        return super.perform() + "[" + this.song + "]";
    }
}```

    9.Symbols

    Symbol是一种基本类型。Symbol 通过调用symbol函数产生，它接收一个可选的名字参数，该函数返回的symbol是唯一的。
```

    var key = Symbol("key");
    var key2 = Symbol("key");
    key == key2  //false

```
    10.Promises

    Promises是处理异步操作的对象，使用了 Promise 对象之后可以用一种链式调用的方式来组织代码，让代码更加直观（类似jQuery的deferred 对象）。
```

    function fakeAjax(url) {
    return new Promise(function (resolve, reject) {
        // setTimeouts are for effect, typically we would handle XHR
        if (!url) {
        return setTimeout(reject, 1000);
        }
        return setTimeout(resolve, 1000);
    });
    }
    
    // no url, promise rejected
    fakeAjax().then(function () {
        console.log('success');
        },function () {
        console.log('fail');
    });

```

```
