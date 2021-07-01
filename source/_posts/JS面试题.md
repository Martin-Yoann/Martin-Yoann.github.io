---
title: JavaScript面试汇总
date: 2021-5-1 12:00:00
categories: 
    - web前端开发
    - Html,
    - Css
    - JavaScript
tags: 
    - Html 
    - Css
    - JavaScript
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=509728140.mp3
cover: https://img0.baidu.com/it/u=2192262292,218971922&fm=26&fmt=auto&gp=0.jpg


---


##### js的基本数据类型有哪些，基本数据类型和复杂数据类型的区别
    String、Number、Boolean、Null、undefined
    
    Object为复杂数据类型
    
    基本数据类型把数据名和值直接存储在栈当中
    
    复杂数据类型在栈中存储数据名和一个堆的地址，在堆中存储属性和值，访问时先从栈中获取地址再到堆中取相应的值

##### == 和 === 有什么区别
    ==用于一般比较 比较时可以转换数据类型 
    
    ===用于严格比较 比较时只要类型不匹配就返回false

##### 例举3种强制类型转换和2种隐式类型转换?
    强制：通过String（），Number（），Boolean（）函数强制转换
    隐式：（乘，除，大于，小于，减，==）

##### split() 和 join() 的区别
    split() 字符串转数组 如：var str = "hello?word?welcome"  console.log(str.split(“？”)) 返回值为 ["hello", "word", "welcome"]
    
    join() 数组转字符串 如：var arr = new Array() arr[0] = "hello" arr[1] = "world" arr[3] = "welcome" arr.join("、")  返回值为 "hello、world、welcome"

##### ajax请求的时候get 和post方式的区别

    一个在url后面 ，一个放在虚拟载体里面
    get有大小限制(只能提交少量参数)
    安全问题
    应用不同 ，请求数据和提交数据

##### 解释jsonp的原理，以及为什么不是真正的ajax

    jsonp的核心原理就是目标页面回调本地页面的方法,并带入参数
    动态创建script标签，使用回调函数
    Ajax是页面无刷新请求数据操作

##### call()、bind()、apply()区别
    三者都是可以改变this的指向
    
    bind() 返回对应函数便于稍后调用；call()、apply()则是立即调用
    
    call() call(thisArg, case1, case2, case3,...) 第一个参数是对象 后面是字符串
    
    apply() apply(thisArg, [case1, case2, case3,...]) 第一个参数是对象  后面是数组

##### 数组有哪些操作方法
    unshift()  把参数添加到数组开头
    shift() 把数组的第一个元素删除
    push() 向数组末尾添加一个或多个元素
    pop() 把数组的最后一个元素删除 
    concat() 连接两个或多个数组
    join() 数组转成字符串
    reverse() 数组倒叙
    slice() 截取后返回新数组 ['H','el','lo','wo','rld!'].slice(1,3) 返回 ["el", "lo"]
    splice() 添加或删除数组中的元素，这种方法会改变原始数组
    sort() 数组元素排序
    forEach() 遍历数组
    filter() 返回符合条件的新数组，arr.filter((item,index,arr)=>{return 测试语句})
    Map()  

##### 对象有哪些操作方法
    assign() 合并对像
    is() 对象比较是否严格相等
    keys() 遍历键名，返回所有键名数组
    values() 遍历键值，返回键值数组

##### 什么是闭包,有什么特性，对页面有什么影响
    可以调用其它函数内部变量的函数
    
    闭包就是能够读取其他函数内部变量的函数,避免变量污染、加强了封装性，逻辑性比较强代码的可读性高；加载到内存中执行效率高,使得函数不被GC回收，如果过多使用闭包，容易导致内存泄露,在内存中，造成了内存浪费，如果滥用闭包是灾难性的；

#### 闭包的好处

    (1)希望一个变量长期驻扎在内存当中(不被垃圾回收机制回收)
    
    (2)避免全局变量的污染
    
    (3)私有成员的存在
    
    (4)安全性提高

##### 怎么创建闭包
    在函数内部嵌套使用函数
```
    function fn() {
            for (var i = 0; i < 2; i++) {
                (function () {
                    var variate = i;
                    setTimeout(function () {
                        console.log("setTimeout执行后:"+variate);
                    }, 1000);
                })();//闭包,立即执行函数,匿名函数

            }
            console.log(i);//2
            console.log(variate);//variate is not defined
        }
        fn();
```

##### 如何阻止事件冒泡
    e.stopPropagation()（IE:window.event.cancelBubble=true）

##### 如何阻止默认事件、阻止标签自带功能
    e.preventDefault()（IE:window.event.returnValue=false）

##### 0级事件和2级事件

    0级：dom.on事件名称=function(){}
    2级：dom.addEvenListener('事件类型',function(){},布尔值(为true表在捕du获阶段调用处理函数.false在冒泡阶段调用.为了兼zhi,一般都用false))

##### 添加 删除 替换 插入到某个接点的方法

    1）创建新节点
    createElement() //创建一个具体的元素
    createTextNode() //创建一个文本节点
    
    2）添加、移除、替换、插入
    appendChild() //添加
    removeChild() //移除
    replaceChild() //替换
    insertBefore() //插入
    
    3）查找
    getElementsByTagName() //通过标签名称
    getElementsByName() //通过元素的Name属性的值
    getElementById() //通过元素Id，唯一性

##### null 和 undefined 的区别
    null表示没有对象，该处不该有值，转为数值时为0
    
    undefined表示缺少值，该处应该有值，但是未定义，转为数值时为NaN

##### 什么是变量提升
    变量提升是js的默认行为，变量提升会将所有变量声明移动到当前作用域的顶部，并可以在声明之前使用该变量，初始化不会被提升，提升的仅作用于变量的声明

##### 什么是事件委托
    利用事件冒泡的原理，把原本需要绑定的事件委托给父元素，让父元素负责事件监听

##### 深拷贝和浅拷贝 
    浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。
    
    深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象

##### async与defer区别
    异步(async) 脚本将在其加载完成后立即执行，而 延迟(defer) 脚本将等待 HTML 解析完成后，并按加载顺序执行。

##### cookies，sessionStorage和localStorage 有什么区别？
    cookies可以和服务端交互，数据大小不会超过4k，设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭，使用方法需要自己封装不够友好;
    
    sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存，虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大，有封装好的方法，可以直接存取值
    
    localStorage 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；sessionStorage 数据在当前浏览器窗口关闭后自动删除。

##### 数组去重有哪些方法
```
    new Set()  如：var arr = [1,2,3,9,6,3,1,2,6] new set(arr)
```
利用冒泡for循环嵌套，然后splice()去重 如：
```
    function unique(arr){            
            for(var i=0; i<arr.length; i++){
                for(var j=i+1; j<arr.length; j++){
                    if(arr[i]==arr[j]){         //第一个等同于第二个，splice方法删除第二个
                        arr.splice(j,1);
                        j--;
                    }
                }
            }
    return arr;
    }
    var arr = [1,2,3,9,6,3,1,2,6]
    console.log(unique(arr))
```

##### indexOf()去重 如：
```
    function unique(arr) {
        if (!Array.isArray(arr)) {
            console.log('type error!')
            return
        }
        var array = [];
        for (var i = 0; i < arr.length; i++) {
            if (array .indexOf(arr[i]) === -1) {
                array .push(arr[i])
            }
        }
        return array;
    }
    var arr = [1,2,3,9,6,3,1,2,6]
        console.log(unique(arr))
```
##### sort()去重 如：
```
    function unique(arr) { 
        if (!Array.isArray(arr)) { 
            console.log('type error!') return;
        } 
        arr = arr.sort() 
        var arrry= [arr[0]]; 
        for (var i = 1; i < arr.length; i++) { 
            if (arr[i] !== arr[i-1]) { 
                arrry.push(arr[i]);
            } 
        } 
        return arrry; 
        }

    var arr = [1,2,3,9,6,3,1,2,6]

    console.log(unique(arr))
```
##### filter()去重 如:
```
    function unique(arr) { 
        return arr.filter(function(item, index, arr) { 
            return arr.indexOf(item, 0) === index;
        });
    }

    var arr = [1,2,3,9,6,3,1,2,6]

    console.log(unique(arr))
```

##### 行代码实现数组去重？
```
    [...new Set([1,2,3,1,'a',1,'a'])]
```

##### 冒泡排序
```
    var array = [5, 4, 3, 2, 1];
    var temp = 0;
    for (var i = 0; i <array.length; i++){
        for (var j = 0; j <array.length - i; j++){
            if (array[j] > array[j + 1]){
                temp = array[j + 1];
                array[j + 1] = array[j];
                array[j] = temp;
            }
        }
    }
```

##### 降维数组
```
    var arr=[[1,2],[3,4]];
    function Jw(obj){
        return Array.prototype.concat.apply([],obj);
    }
    Jw(arr);
```
##### GET 和 POST 有什么区别
    GET请求在浏览器回退和刷新时是无害的，而POST请求会告知用户数据会被重新提交；
    
    GET请求可以收藏为书签，POST请求不可以收藏为书签；
    
    GET请求可以被缓存，POST请求不可以被缓存，除非在响应头中包含合适的Cache-Control/Expires字段，但是不建议缓存POST请求，其不满足幂等性，每次调用都会对服务器资源造成影响；
    
    GET请求一般不具有请求体，因此只能进行url编码，而POST请求支持多种编码方式。
    
    GET请求的参数可以被保留在浏览器的历史中，POST请求不会被保留；
    
    GET请求因为是向URL添加数据，不同的浏览器厂商，代理服务器，web服务器都可能会有自己的长度限制，而POST请求无长度限制；
    
    GET请求只允许ASCII字符，POST请求无限制，支持二进制数据；
    
    GET请求的安全性较差，数据被暴露在浏览器的URL中，所以不能用来传递敏感信息，POST请求的安全性较好，数据不会暴露在URL中；
    
    GET请求具有幂等性(多次请求不会对资源造成影响)，POST请求不幂等；
    
    GET请求一般不具有请求体，请求中一般不包含100-continue 协议，所以只会发一次请求，而POST请求在发送数据到服务端之前允许双方"握手"，客户端先发送Expect:100-continue消息，询问服务端是否愿意接收数据，接收到服务端正确的100-continue应答后才会将请求体发送给服务端，服务端再响应200返回数据。

##### 跨域有几种解决方案
    jsonp 适用于get请求
    document.domain + iframe 适用于主域相同 子域不同  两个页面都通过js强制设置document.domain为基础主域，就实现了同域
    location.hash + iframe 
    window.name + iframe 
    postMessage (data,origin)方法接受两个参数
    data：需要传递的数据，html5规范支持任意基本类型或可复制的对象，但部分浏览器只支持字符串，所以传参时最好用JSON.stringify()序列化。
    
    origin：协议+主机+端口号，也可以设置为"*"，表示可以传递给任意窗口，如果要指定和当前窗口同源的话设置为"/"。
    
    跨域资源共享（CORS）

##### typeof和instanceof有什么区别
    typeof 判断一个数据是什么数据类型；一般只能返回如下几个结果："number"、"string"、"boolean"、"object"、"function" 和 "undefined"。
    instanceof 判断一个对象是否在另一个对象的原型链上

##### 函数声明与函数表达式的区别？

    在Javscript中，解析器在向执行环境中加载数据时，对函数声明和函数表达式并非是一视同仁的，解析器会率先读取函数声明，并使其在执行任何代码之前可用（可以访问），至于函数表达式，则必须等到解析器执行到它所在的代码行，才会真正被解析执行。

##### Javascript的事件流模型都有什么?

    “事件冒泡”：事件开始由最具体的元素接受，然后逐级向上传播
    
    “事件捕捉”：事件由最不具体的节点先接收，然后逐级向下，一直到最具体的
    
    “DOM事件流”：三个阶段：事件捕捉，目标阶段，事件冒泡

##### 希望获取到页面中所有的checkbox怎么做？(不使用第三方框架)
```
    var inputs = document.getElementsByTagName("input");//获取所有的input标签对象
    var checkboxArray = [];//初始化空数组，用来存放checkbox对象。
    for(var i=0;i<inputs.length;i++){
        var obj = inputs[i];
        if(obj.type=='checkbox'){
            checkboxArray.push(obj);
        }
    }
```
##### 如何获取javascript三个数中的最大值和最小值？

    Math.max(a,b,c);//最大值
    
    Math.min(a,b,c)//最小值

##### javascript是面向对象的，怎么体现javascript的继承关系？

    使用prototype原型来实现。

##### 列举javaScript的3种主要数据类型，2种复合数据类型和2种特殊数据类型。

    主要数据类型：string, boolean, number
    
    复合数据类型：function, object
    
    特殊类型：undefined，null
##### 解释什么是Json:
    (1)JSON 是一种轻量级的数据交换格式。
    
    (2)JSON 独立于语言和平台，JSON 解析器和 JSON 库支持许多不同的编程语言。
    
    (3)JSON的语法表示三种类型值，简单值(字符串，数值，布尔值，null),数组，对象

#####  js中的3种弹出式消息提醒（警告窗口，确认窗口，信息输入窗口）的命令式什么？

    alert
    confirm
    prompt

#### 浏览器的滚动距离：

    可视区域距离页面顶部的距离
    
    scrollTop=document.documentElement.scrollTop||document.body.scrollTop

##### innerHTML、innerText和outerHTML的区别

    innerHTML(元素内包含的内容）
    
    innerText(元素的文本内容）
    
    outerHTML(自己以及元素内的内容）

##### offsetWidth offsetHeight和clientWidth clientHeight的区别

    (1)offsetWidth （content宽度+padding宽度+border宽度）
    
    (2)offsetHeight（content高度+padding高度+border高度）
    
    (3)clientWidth（content宽度+padding宽度）
    
    (4)clientHeight（content高度+padding高度）

##### 请解释一下什么是语义化的HTML。

    内容使用特定标签，通过标签就能大概了解整体页面的布局分布

##### 请说出三种减低页面加载时间的方法
    1、压缩css、js文件
    2、合并js、css文件，减少http请求
    3、外部js、css文件放在最底下
    4、减少dom操作，尽可能用变量替代不必要的dom操作

##### 请解释什么是Javascript的模块模式，并举出实用实例。

    js模块化mvc（数据层、表现层、控制层）
    seajs
    命名空间

##### 你如何组织自己的代码？是使用模块模式，还是使用经典继承的方法？

    对内：模块模式
    对外：继承

##### 你如何优化自己的代码？

    代码重用
    避免全局变量（命名空间，封闭空间，模块化mvc..）
    拆分函数避免函数过于臃肿
    注释

#### 你能解释一下JavaScript中的继承是如何工作的吗？

    子构造函数中执行父构造函数，并用call\apply改变this
    克隆父构造函数原型上的方法

##### 最简单的一道题
```
    var a = 2, b = 3;
    var c = a++ + b; 
    // c = 5
```

##### dom事件委托什么原理，有什么优缺点
    事件委托原理:事件冒泡机制
    
    优点
    1.可以大量节省内存占用，减少事件注册。比如ul上代理所有li的click事件就很不错。
    2.可以实现当新增子对象时，无需再对其进行事件绑定，对于动态内容部分尤为合适
    
    缺点
    事件代理的常用应用应该仅限于上述需求，如果把所有事件都用事件代理，可能会出现事件误判。即本不该被触发的事件被绑定上了事件。

##### js基础数据类型和引用类型分别是什么？这个前提条件下写一个getType，返回相应的类型

    1.基本数据类型（自身不可拆分的）：Undefined、Null、Boolean、Number、String
    2.引用数据类型（对象）：Object （Array，Date，RegExp，Function）
    ES6基本数据类型多了个symbol 据说这道题刷了百分之二十的人 感谢Abbyshen提出
```
    function gettype(nm){
        return Object.prototype.toString.call(nm);
    }
```

##### js垃圾回收机制知道哪些，垃圾回收机制的好处和坏处

    1 标记清除（mark and sweep）
    2 引用计数（reference counting）
    
    好处：大幅简化程序的内存管理代码，减轻程序猿负担，并且减少因为长时间运转而带来的内存泄露问题。
    
    坏处：自动回收意味着程序猿无法掌控内存。ECMAScript中没有暴露垃圾回收的借口，我们无法强迫其进行垃圾回收，更加无法干预内存管理。

##### setTimeout 和 setInterval 细谈

    常问的点，前者是在一定时间过后将函数添加至执行队列，执行时间=延迟时间+之前函数代码执行时间+执行函数时间。
    后者是不管前一次是否执行完毕，每隔一定时间重复执行，用于精准执行互相没有影响的重复操作。
    如果需要控制前后执行顺序，最好使用setTimeout模拟setInterval
```
    var time = 400, times = 0, max = 10;
    function func(){
    times++;
    if(times < max){
        //code here
        setTimeout(func, time);
    } else {
        console.log("finished");
    }
    }
    setTimeout(func, time);
```

##### 判断数组
```
    function isArray(arr){
        return Object.prototype.toString.call(arr) === '[Object Array]';
    }
```

##### window.name

    即使在页面打开多层iframe后，每个iframe中window.name 属性值都是相同的，以此用作数据传输的工具。
    但由于跨域的限制，是无法获取另一个frame中的window.name数据，所以要使用一个同域的代理(proxy.html)：

##### forEach和map的区别

###### 相同点

    都是循环遍历数组中的每一项
    forEach和map方法里每次执行匿名函数都支持3个参数，参数分别是item（当前每一项）、index（索引值）、arr（原数组）
    匿名函数中的this都是指向window
    只能遍历数组
    都有兼容问题

###### 不同点

    map速度比foreach快
    map会返回一个新数组，不对原数组产生影响,foreach不会产生新数组，
    map因为返回数组所以可以链式操作，foreach不能
