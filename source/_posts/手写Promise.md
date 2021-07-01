---
title: 手写Promise
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
<font> 手写Promise  主要是解决回调地狱的问题，在ES6中出现了promise来解决这个问题，但是同样也带来了多个.then()的问题
    //随着es7 async和await到来可以说彻底解决回调地狱。
    new Promise() //是谁执行了？直接new一个Promise是内置构造Promise执行了，但是它会报错。因为这里缺一个回调函数，平常大家也都是这么用的
    new Promise(()=>{
       console.log('你大爷')//‘你大爷’会执行吗？：这里new了一个Promose,Promise执行一次，那里面的回调函数也会执行，所以‘你大爷’成功被打印
    })
    function fn(callBack){

    }
    new fn(()=>{

    })//fn执行，但是里面的回调并没有，Promise的回调会执行。


    //new Promise 是内置构造函数Promise执行一次
    //Promise的回调函数也会执行一次，这个回调函数会给我们提供两个形参（函数）：成功、失败
    //Promise的回调函数，又有两个参数分别是：resolve、reject两个函数
    //Promise类的实例没有then方法，应该是原型对象的方法
    var obj = new Promise((resolve,rejecct)=>{
         console.log(resolve,reject)//两个函数
    })//obj是Promise的一个实例

    // 手写
    function myPromise(callBack){//接受传进来的回调函数
        //状态属性
        this.status='pending'
        //回调函数
        callBack(resolve.bind(this),reject.bing(this))
        //定义一个成功的函数
        function resolve(hello,           params){
            //那么console.log(hello)肯定是执行的（很早演示时写）


            //修改状态（后写）
            if(this.status==='pending'){//如果出事状态为pengding,
                this.status='success'//那就把它改成success成功
                //这里还有一个上下文的问题。成功时resolve是怎么调用的？是函数名+小括号，也就是window.
                //但这里就不该用window，因为将来获取服务器的数据实在.then()里的来获取。所以我们在初始化时就要给
                //resolve和reject绑死这个类的实例：resolve.bind(this)  reject.bing(this) 走起上面绑死↑
                //否则你在调用resolve和reject时他们就会指向window
                //为什么绑死上下文为这个类的实例？因为我们要借用这个类的实例的成功和失败的方法74行里面成功与失败的回调
                //所以↓
                this.successCallBack(params)//这个是谁？它就是then的第一个参数也就是成功的回调，所以把参数直接注进来就行了
                //失败同样
            }
        }
        //定义一个失败的函数
        function reject(err){
            if(this.status==='pending'){
                this.status='faile'
                this.faileCallBack(err)
            }
        }
    }
    //调用
    new myPromise(()=>{//并且传进去一个回调函数。但是我们在实际运用中肯定要传2个参数进去。resolve,reject,并且37行回调也要接受这个2个函数
        //console.log('我是Promise')//这里肯定会执行。打印。
        //假如这里调用并传参resolve('hello')
        //处理异步,一般promise就是处理异步的
        setTimeout(()=>{
            resolve('我是promise')
        })
    })//假如我们是在处理异步请求那么肯定要在这.then()。但是能直接.then()吗？要注意.then()是在原型上面的。虽然链式语法可以这么写，但是这里并没有这个方法。.then()应该是原型上面类的原型的方法
    .then((data)=>{
        console.log(data)
    },()=>{})//一般我们在调用then()的时候肯定要传2个参数进去，下面接收，就是相当于将then方法里面成功与失败的回调函数当做当前类的实例即可，当前类是谁？promise

    //所以原型上定义一个then的方法，应该是
    myPromise.prototype.then=function(success,faile){//接收上面调用then时传进来的来个函数。就是将then方法里面成功与失败的回到函数作为当前类的实例即可
        this.successCallBack=success//相当于then传进一个成功的函数给了success,就是给myPromise的实例动态添加了属性就是success这个成功的箭头函数。还有一个失败的同样 
        this.faileCallBack=faile
        //then()的两个函数相当于作为这个实例的两个方法
    }
    //53行异步成功后执行，就是相当于调用了41行那个方法。失败同样
    //因为promise有3中状态，pending、成功、失败。所以此时我去上面给类定义个状态的属性，走起↑
    //如果说异步解决成功就调用resolve方法 。resolve就是41行函数执行。但是我们都是在then()来获取成功或失败的数据，(其实就是调用this.successCallBack，this.faileCallBack)。所以走起去上面↑，就是修改promise的状态
    

    ``` //上面的看着乱，可以看这个
    (()=>{
        window.myPromise=function(callBack){
            //状态属性
            this.status='pending'
            //回调函数
            callBack(resolve.bind(this),reject.bind(this))
            // 成功
            function resolve(params){
                if(this.status==='pending'){
                    this.status='success'
                    this.successCallBack(params)
                }
            }
            // 失败
            function reject(err){
                if(this.status==='pending'){
                    this.status='faile'
                    this.successCallBack(err)
                }
            }
        }
        //原型上定义一个then的方法
        myPromise.prototype.then=function(success,faile){
            this.successCallBack=success
            this.faileCallBack=faile
        }
    })()
    var obj = new myPromise((resolve,reject)=>{
        setTimeout(()=>{
            resolve('你真好')
        },1000)
    }).then((data)=>{
        console.log(data)//成功执行
    })
    ```