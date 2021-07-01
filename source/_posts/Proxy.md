---
title: Proxy
date: 2020-9-1 12:00:00
categories: 
    - web前端开发
    - JavaScript
tags: 
    - JavaScript
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=1476449831.mp3
cover: https://img2.baidu.com/it/u=3429416796,2324999190&fm=26&fmt=auto&gp=0.jpg
---
## async函数默认返回一个Promise对象
### proxy 对对象操作进行拦截
#### new Proxy()接受两个参数，第一个是目标对象，另一个是拦截方法
```
let obj = {
        name:'hello',
        age:'18'
    }
    //相当于proxy1代理了obj,需要通过proxy1 去操作代理的obj
    let proxy1 = new Proxy(obj,{
        get(target,key,proxy){//get 方法只要是对对象进行获取操作就会触发get方法
            console.log(arguments)//得到target:目标对象和key:name属性名，以及proxy实例
            //这里return什么，就会返回什么，如果没有return，就是undefined
            console.log('触发了')
            return target[key]//返回属性name的值
    }})
    console.log(proxy1.name)//'触发了'
```
```
Proxy 用于修改某些操作默认行为，等同于在语言层面做出修改，所以属于一种‘元编程’(meta progrmming),即对编程语言进行编程。
Proxy 可以理解成，在目标对象之前架设一层‘拦截’，外界对该对象的访问，都必须先通过这层拦截，因此提供一种机制，可以对外界的访问进行过滤和改写。Proxy 这个词的原意是代理，用在这里表示由他来‘代理’某些操作，可以译为‘代理器’。
```
### 为什么需要 Proxy
1.被代理的对象不想直接被访问
2.控制和修改被代理对象的行为（调用属性、属性赋值、方法调用等等），使之可以进行访问控制和增加功能。

API 概览如下：

get(target, propKey, receiver)：拦截对象属性的读取，比如 proxy.foo 和 proxy['foo'] 。
set(target, propKey, value, receiver)：拦截对象属性的设置，比如 proxy.foo = v 或 proxy['foo'] = v ，返回一个布尔值。
has(target, propKey)：拦截 propKey in proxy 的操作，返回一个布尔值。
deleteProperty(target, propKey)：拦截 delete proxy[propKey]的操作，返回一个布尔值。
ownKeys(target)：拦截 Object.getOwnPropertyNames(proxy) 、 Object.getOwnPropertySymbols(proxy) 、 Object.keys(proxy) 、 for...in 循环，返回一个数组。该方法返回目标对象所有自身的属性的属性名，而 Object.keys() 的返回结果仅包括目标对象自身的可遍历属性。
getOwnPropertyDescriptor(target, propKey)：拦截 Object.getOwnPropertyDescriptor(proxy, propKey) ，返回属性的描述对象。
defineProperty(target, propKey, propDesc)：拦截 Object.defineProperty(proxy, propKey, propDesc） 、
Object.defineProperties(proxy, propDescs)，返回一个布尔值。
preventExtensions(target)：拦截 Object.preventExtensions(proxy) ，返回一个布尔值。
getPrototypeOf(target)：拦截 Object.getPrototypeOf(proxy)，返回一个对象 。
isExtensible(target)：拦截 Object.isExtensible(proxy) ，返回一个布尔值。
setPrototypeOf(target, proto)：拦截 Object.setPrototypeOf(proxy, proto) ，返回一个布尔值。如果目标对象是函数，那么还有两种额外操作可以拦截。
apply(target, object, args)：拦截 Proxy 实例作为函数调用的操作，比如 proxy(...args)、proxy.call(object, ...args)、proxy.apply(...)`。
construct(target, args)：拦截 Proxy 实例作为构造函数调用的操作，比如 new proxy(...args) 。
#### 最常用的一般就是 get()和set()
### get()
get方法用于拦截某个属性的读取操作，可以接受三个参数，依次为目标对象、属性名和 proxy 实例本身（严格地说，是操作行为所针对的对象），其中最后一个参数可选。

get方法的用法，上文已经有一个例子，下面是另一个拦截读取操作的例子。
```
var person = {
  name: "张三"
};

var proxy = new Proxy(person, {
  get: function(target, propKey) {
    if (propKey in target) {
      return target[propKey];
    } else {
      throw new ReferenceError("Prop name \"" + propKey + "\" does not exist.");
    }
  }
});

proxy.name // "张三"
proxy.age // 抛出一个错误
上面代码表示，如果访问目标对象不存在的属性，会抛出一个错误。如果没有这个拦截函数，访问不存在的属性，只会返回undefined。
```
```
get方法可以继承。
let proto = new Proxy({}, {
  get(target, propertyKey, receiver) {
    console.log('GET ' + propertyKey);
    return target[propertyKey];
  }
});

let obj = Object.create(proto);
obj.foo // "GET foo"
上面代码中，拦截操作定义在Prototype对象上面，所以如果读取obj对象继承的属性时，拦截会生效。
```
```
下面的例子使用get拦截，实现数组读取负数的索引。
function createArray(...elements) {
  let handler = {
    get(target, propKey, receiver) {
      let index = Number(propKey);
      if (index < 0) {
        propKey = String(target.length + index);
      }
      return Reflect.get(target, propKey, receiver);
    }
  };

  let target = [];
  target.push(...elements);
  return new Proxy(target, handler);
}

let arr = createArray('a', 'b', 'c');
arr[-1] // c
上面代码中，数组的位置参数是-1，就会输出数组的倒数第一个成员。
```
```
利用 Proxy，可以将读取属性的操作（get），转变为执行某个函数，从而实现属性的链式操作。
var pipe = function (value) {
  var funcStack = [];
  var oproxy = new Proxy({} , {
    get : function (pipeObject, fnName) {
      if (fnName === 'get') {
        return funcStack.reduce(function (val, fn) {
          return fn(val);
        },value);
      }
      funcStack.push(window[fnName]);
      return oproxy;
    }
  });

  return oproxy;
}

var double = n => n * 2;
var pow    = n => n * n;
var reverseInt = n => n.toString().split("").reverse().join("") | 0;

pipe(3).double.pow.reverseInt.get; // 63
上面代码设置 Proxy 以后，达到了将函数名链式使用的效果。
```
```
下面的例子则是利用get拦截，实现一个生成各种 DOM 节点的通用函数dom。
const dom = new Proxy({}, {
  get(target, property) {
    return function(attrs = {}, ...children) {
      const el = document.createElement(property);
      for (let prop of Object.keys(attrs)) {
        el.setAttribute(prop, attrs[prop]);
      }
      for (let child of children) {
        if (typeof child === 'string') {
          child = document.createTextNode(child);
        }
        el.appendChild(child);
      }
      return el;
    }
  }
});

const el = dom.div({},
  'Hello, my name is ',
  dom.a({href: '//example.com'}, 'Mark'),
  '. I like:',
  dom.ul({},
    dom.li({}, 'The web'),
    dom.li({}, 'Food'),
    dom.li({}, '…actually that\'s it')
  )
);

document.body.appendChild(el);
```
```
下面是一个get方法的第三个参数的例子，它总是指向原始的读操作所在的那个对象，一般情况下就是 Proxy 实例。
const proxy = new Proxy({}, {
  get: function(target, key, receiver) {
    return receiver;
  }
});
proxy.getReceiver === proxy // true
上面代码中，proxy对象的getReceiver属性是由proxy对象提供的，所以receiver指向proxy对象。
```
```
const proxy = new Proxy({}, {
  get: function(target, key, receiver) {
    return receiver;
  }
});

const d = Object.create(proxy);
d.a === d // true
上面代码中，d对象本身没有a属性，所以读取d.a的时候，会去d的原型proxy对象找。这时，receiver就指向d，代表原始的读操作所在的那个对象。
```
```
如果一个属性不可配置（configurable）且不可写（writable），则 Proxy 不能修改该属性，否则通过 Proxy 对象访问该属性会报错。
const target = Object.defineProperties({}, {
  foo: {
    value: 123,
    writable: false,
    configurable: false
  },
});

const handler = {
  get(target, propKey) {
    return 'abc';
  }
};

const proxy = new Proxy(target, handler);
proxy.foo
// TypeError: Invariant check failed
```
### set()
```
let obj={
        name:'hello world',
    }
    let proxy2 = new Proxy(obj,{
        get(target,key,receiver){
            return target[key]//获取想要得到的属性
        },
        set(target,key,value,receiver){
            console.log('要设置')
            console.log(arguments)
            //key这里就是要设置的那个age属性
            target[key]=value
            return true //最后返回一个布尔值
        },
        has(target,key){//拦截in这个操作。接收两个参数，目标对象和判断的那个属性名
            if(key.startsWith('_')){//判断下是否是带__的属性比如'__proto__'
                return false
            }else{
                return key in target
            }
        },
    })
    proxy2.age=10//这里我们想要给obj设置一个age为10的属性
    console.log(obj)
    console.log('name' in proxy2)
```
### apply()//拦截实例作为函数调用的时候：proxy3()
```
function query(){
        console.log(this)
        return {name:'hello world'}
    }
    let obj = {name:'北京'}
    let proxy3 = new Proxy(query,{
        apply(target,object,args){
            //函数直接执行()、通过call执行、apply执行，都会触发此处。
            //object 给函数修改this
            // args 函数执行的参数
            console.log('执行')
            console.log(target,object,args)
            if(object){
                object.fn=target
                object.fn(...args)
                delete object.fn
            }else{
                target(...args)
            }
        }
    })
    proxy3()
    console.log(proxy3.call(obj,1,2,3))
```

