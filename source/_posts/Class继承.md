---
title: 数组去重方式
date: 2019-5-1 12:00:00
categories: 
    - web前端开发
    - JavaScript
tags: 
    - JavaScript
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=1456270729.mp3
cover: https://img2.baidu.com/it/u=3429416796,2324999190&fm=26&fmt=auto&gp=0.jpg
---
class的基本语法:
一.类的由来 
JS中生成实例对象的传统方法是通过构造函数，下面请看一个例子

```
function Point(x,y){
    this.x=x
    this.y=y
}
Point.prototype.toString=function (){
    return '('+this.x+','+this.y+')'
}
var p = new Point(1,2)
console.log(p)
```
上面这种写法跟传统的面向对象语言（比如 C++ 和 Java）差异很大，很容易让新学习这门语言的程序员感到困惑。

ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对象的模板。通过class关键字，可以定义类。

基本上，ES6 的class可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。上面的代码用 ES6 的class改写，就是下面这样。
```
class Point{
    constructor(x,y){
        this.x=x
        this.y=y
    }
    toString(){
            return '('+this.x+','+this.y+')'
    }
}
let p =new Point(1,2)
console.log(p)
```
这个是定义了一个类，有一个constructor()方法，就是构造方法而this关键字就是实力的对象。这种新的Class写法，最开始ES5的构造函数Point是一样的。

Point类除了构造方法，还定义了一个toString方法。注意，这里定义toString()方法，是不用加上function关键字的。直接定义就可以，并且不用逗号隔开，加了会报错。

ES6的类，完全可以看做构造函数的另一种写法。
```
class Point{

}
console.log(typeof Point)//function 说明类的数据类型是函数，类本身就指向构造函数
console.log(Point===Point.prototype.constructor)//true
使用的时候也是直接对类使用new 命令，跟构造函数的用法完全一致。

```
```
class Bar{
    todo(){
        console.log('类')
    }
}
const b = new Bar()
b.todo()//'类'
构造函数的prototype属性，在ES6的 类上面继续存在。事实上，类的所有方法都定义在类的 prototype属性上面
```
```
class Point {
        constructor() {
            // ...
        }

        toString() {
            // ...
        }

        toValue() {
            // ...
        }
    }

        // 等同于

        Point.prototype = {
        constructor() {},
        toString() {},
        toValue() {},
        };
        上面代码中，所有的方法，其实都是定义在Point.prototype上面
        因此，在类的实例上面调用方法，其实就是调用原型上的方法
```
    ```
    class B{}
    const b = new B()
    console.log(b.constructor === B.prototype.constructor)//true
    b是B类的实例，b的constructor()方法就是B类原型的constructor()方法
    ```
    ```
    由于类的方法都定义在prototype对象上面，所以类的新方法可以添加在prototype对象上面。
    Object.assign()方法可以很方便地一次向类天机多个方法。比如：
    class Point{
        constructor(){
    
        }
    }
    Object.assign(Point.prototype,{
        toString(){},
        toValue(){}
    })
    ```
    ```
    prototype对象的constructor()属性，直接指向'类'的本身，这与ES5的行为是一致的。
    Point.prototype.constructor===Point //true
    ```
    另外，类的内部所有定义的方法，都是不可枚举的(non-enumerabal)
    ```
        class Point{
            constructor(x,y){
    
            }
            toString(){
    
            }
        }
        console.log(Object.keys(Point.prototype))//[]
        console.log(Object.getOwnPropertyNames(Point.prototype))//['constructor','toString']
        这里，toString()方法是Point类 内部定义的方法，它是不可枚举的。这一点与ES5是不一样的
    ```
```
    var Point = function (x,y){

}
Point.prototype.toString = function (){

}
console.log(Object.keys(Point.prototype))//['toString']
console.log(Object.getOwnPropertyNames(Point.prototype))//['constructor','toString']
这是ES5 的写法，toString()方法就是可枚举的。
```
Constructor()方法
    constructor()方法是类的默认方法，是通过new 命令生成对象实例时，自动调用该方法。一个类必须有constructor()
    方法，如果没有显示定义，一个空德constructor()方法也会被默认添加

```
class Ponit{

    }
    //等同于
    class Point{
        constructor(){

        }
    }
这里，定义了一个空的类Point,JS引擎会自动给他添加一个空的constructor()方法。
constructor()方法默认返回实例对象(即this),完全可以指定返回另一个对象
```
```
class Foo{
    constructor(){
        return Object.create(null)
    }
}
console.log(new Foo() instanceof Foo)//false
这里，constructor()函数返回一个全新的对象，结果导致实例对象不是Foo类的实例。
类必须使用new调用，否则会报错，这是它跟普通构造函数的一个主要区别，后者不用new也可以执行
```
```
class Foo{
    constructor(){
        return Object.create(null)
    }
}
Foo()//Class constructor Foo cannot be invoked without 'new'
```

类的实例！
    生成类的实例的写法，与ES5 完全一样，也是使用 new命令。如果没有用 new，像函数那样调用class,将会报错
```
   class Point{

    }
    var point = Point(2,3)//报错
    var point = new Point(2,3)//正确
```
与ES5 一样，实例的属性除非显示定义在其本身(即定义在this上)，否则都是定义在原型上(即定义在class上)
```
class Point{
    constructor(x,y){
        this.x=x
        this.y=y
    }
    toString(){
        return '('+this.x+','+this.y+')'
    }
}
var point = new Point(2,3)
console.log(point.toString(2,3))//(2,3)
console.log(point.hasOwnProperty('x'))//true
console.log(point.hasOwnProperty('y'))//true
console.log(point.hasOwnProperty('toString'))//false
console.log(point.__proto__.hasOwnProperty('toString'))//true
上面代码中，x和y都是实例对象point自身属性(因为定义在this变量上)，所以hasOwnProperty()方法返回true，而toString()
是原型对象的属性(因为定义在Point类上)，所以hasOwnProperty()方法返回false,这些都与ES5的行为保持一致
```
与ES5一样，类的所有实例共享一个原型对象！！！！
```
var p1 = new Point(2,3)
var p2 = new Point(1,3)
p1.__proto===p2.__proto__//true
上面代码中。p1和p2都是Point的实例，他们的原型都是Point.prototype,所以__proto__属性是相等的。
这也意味着，可以通过实例的__proto__属性为'类'添加方法
```
__proto__ 并不是语言本身的特性，这是各大厂商具体实现时添加的私有属性，虽然目前很多现代浏览器的 JS 引擎中都提供了这个私有属性，但依旧不建议在生产中使用该属性，避免对环境产生依赖。生产环境中，我们可以使用 Object.getPrototypeOf 方法来获取实例对象的原型，然后再来为原型添加方法/属性。
```
var p1 = new Point(2,3);
var p2 = new Point(3,2);

p1.__proto__.printName = function () { return 'Oops' };

p1.printName() // "Oops"
p2.printName() // "Oops"

var p3 = new Point(4,2);
p3.printName() // "Oops"
上面代码在p1的原型上添加了一个printName()方法，由于p1的原型就是p2的原型，因此p2也可以调用这个方法。而且，此后新建的实例p3也可以调用这个方法。这意味着，使用实例的__proto__属性改写原型，必须相当谨慎，不推荐使用，因为这会改变“类”的原始定义，影响到所有实例。
```
取值函(getter)和存值函数(setter)
与ES5一样，在'类'的内部可以使用get和set关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为
```
class MyClass{
    constructor(){

    }
    get prop(){
        return 'getter'
    }
    set prop(value){
        console.log('setter:'+value)
    }
}
let inst = new MyClass()
console.log(inst.props=123)//'setter:123'
console.log(inst.prop)//'getter'
上面，prop属性有对应的存值函数和取值函数，因此赋值和读取行为都被自定义了
```
存值函数和取值函数式设置在属性的 Desscriptor对象上的。
```
class CustomHTMLElement {
    constructor(element){
        this.element = element
    }
    get html(){
        return thi.element.innerHTML
    }
    set html(value){
        this.element.innerHTML=value
    }
}
var descriptor = Object.getOwnPropertyDescriptor(
    CustomHTMLElement.proptotype,'html'
)
'get' in descriptor//true
'set' in descriptor//true
上面代码中，存值函数和取值函数是定义在html属性的描述对象上面，这与ES5完全一致。
```
属性表达式
```
let nethodName = 'getArea'
class Square {
    constructor(length){

    }
    [methodName](){
        
    }
}
代码中，Square类的方法名getArea,是从表达式得到的。
```
Class 表达式
与函数一样，类也可以使用表达式的形式定义
```
 const MyClass = class Me{
    getClassName(){
        return Me.name
    }
}
这里使用表达式定义了一个类，类的名字是Me,但是Me只在Class的内部可用，指代当前类。在Class外部，这个类只能用myClass引用
let inst = new MyClass()
console.log(inst.getClassName())//Me
Me.name//Me is not defined
这里就可以说明，Me只在Class内部有定义

如果类的内部没有用到的话，可以省略Me,也就是可以下面的形式
const MyClass = class {//....}
```
```
采用Class 表达式，可以写出立即执行的Class
let person = new class{
    constructor(name){
        this.name = name
    }
    sayName(){
        console.log(this.name)
    }
}('李华')
person.sayName()
这里 person是一个立即执行的类的实例
```
注意点
（1）严格模式

类和模块的内部，默认就是严格模式，所以不需要使用use strict指定运行模式。只要你的代码写在类或模块之中，就只有严格模式可用。考虑到未来所有的代码，其实都是运行在模块之中，所以 ES6 实际上把整个语言升级到了严格模式。
（2）不存在提升
累不存在变量提升，这一点与ES5完全不同
```
new Foo()
class Foo{}
上面代码中，Foo类使用在前，定义在后，这样会报错，因为ES6不会把类的声明提升到代码头部。这种规定的原因与下文要提到的继承者有关，必须保证子类在父类之后定义。
```
```
{
    let Foo = class{}
    class Bar extends Foo{}
}
上面的代码不会报错，因为Bar继承Foo的时候，Foo已经有定义了。但是，如果存在class的提升，上面代码就会报错，因为class会被提升到代码头部，而let命令是不提升的，所以导致Bar继承Foo的时候，Foo还没有定义。
```
（3）name 属性
由于本质上，ES6 的类只是 ES5 的构造函数的一层包装，所以函数的许多特性都被Class继承，包括name属性。
```
class Point{}
Point.name//'Point'
name属性总是返回紧跟在class关键字后面的类。
```
（4）Generator 方法
如果某个方法之前加上星号（*），就表示该方法是一个 Generator 函数。
```
class Foo{
    constructor(...args){
        this.args = args
    }
    *[Symbol.iterator](){
        for(let arg of this.args){
            yield arg
        }
    }
}
for(let x of new Foo('hello','world')){
    console.log(x)
}
上面的代码中，Foo类的Symbol.interator方法前有一个星号，表示该方法是一个Generator 函数。Symbol.interator方法返回一个Foo类的默认遍历器，for...of循环会自动调用这个遍历器。
```
5）this 的指向
类的方法内部如果含有this，它默认指向类的实例。但是，必须非常小心，一旦单独使用该方法，很可能报错。
```
class Logger{
    printName(name='there'){
        this.print(`Hello ${name}`)
    }
    print(text){
        console.log(text)
    }
}
const logger = new Logger()
const { printName} = logger
console.log(printName())//Cannot read property 'print' of undefined
上面代码中，printName方法中的this，默认指向Logger类的实例，但是。如果将这个方法提取出来单独使用，this会指向该方法运行是所在的环境(由于class内部是严格模式，所以this实际指向的是undefined),从而导致找不到print方法而报错。
一个比较简单的解决方法是，在构造函数中绑定this。这样就不会找不到print方法了。
class Logger {
  constructor() {
    this.printName = this.printName.bind(this);
  }

  // ...
}
另一种解决方法是使用箭头函数。
class Obj{
    constructor(){
        this.getThis = () => this
    }
}
const myObj = new Obj()
myObj.getThis() === myObj//true
箭头函数内部的this总是指向定义时所在的对象。上面代码中，箭头函数位于构造函数内部，它的定义生效的时候，实在构造函数执行的时候，这时，箭头函数所在的运行环境，肯定是实例对象，所以this会总是指向实例对象
```
```
还有一种解决方法是使用Proxy，获取方法的时候，自动绑定this。
function selfish (target) {
  const cache = new WeakMap();
  const handler = {
    get (target, key) {
      const value = Reflect.get(target, key);
      if (typeof value !== 'function') {
        return value;
      }
      if (!cache.has(value)) {
        cache.set(value, value.bind(target));
      }
      return cache.get(value);
    }
  };
  const proxy = new Proxy(target, handler);
  return proxy;
}
const logger = selfish(new Logger());
```
2.静态方法
类相当于实例的原型。所有在类中定义的方法，都会被实例继承，如果在一个方法前，加上static关键字，就表示该方法不会被实例继承，而是直接通过类来调用，这就称为‘静态方法’
```
class Foo{
    static classMethod(){
        return 'hello'
    }
}
console.log(Foo.classMethod())//'hello'
var foo = new Foo()
console.log(foo.classMethod())//foo.classMethod is not a function
上面代码中，Foo类的classMethod方法前有static关键字，表明该方法是一个静态方法，可以直接在Foo类上调用
(Foo.classMethod()),而不是在Foo类的实例上调用。如果在实例上调用静态方法，会抛出一个错误，表示不存在该方法
```
注意：如果静态方法包含this关键字，这个this指的是类，而不是实例
```
class Foo{
    static bar(){
        this.baz()
    }
    static baz(){
        console.log('hello')
    }
    baz(){
        console.log('world')
    }
}
    console.log(Foo.bar())//hello

上面代码中，静态方法bar调用了this.baz，这里的this指的是Foo的类，而不是Foo的实例，等同于调用Foo.baz.另外，从这个例子还可以看出，静态方法可以与非静态方法重名
```
父类的静态方法，可以被子类继承
```
class Foo{
    static classMethod(){
        return 'hello'
    }
}
class Bar extends Foo{}
console.log(Bar.classMethod())//hello
这里，父类Foo有一个静态方法，子类Bar可以调用这个方法
```
```
静态方法也是可以从super对象上调用的
class Foo{
    static classMethod(){
        return 'hello'
    }
}
class Bar extends Foo{
    static classMethod(){
        return super.classMethod()+',too'
    }
}
console.log(Bar.classMethod())//hello,too
```
3.实例属性的新写法
实例属性除了定义在constructor()方法里面的this上面，也可以定义在类的最顶层。
```
class IncreasingCounter{
    constructor(){
        this._count = 0
    }
    get value(){
        console.log('Getting the current value')
        return this._count
    }
    increment(){
        this._count++
    }
}
代码中，实例属性this._count定义在constructor()方法里面，另一种写法是，这个属性也可以定义在类的最顶层，其他都不变
```
```
class IncreasingCounter{
    _count = 0
    get value(){
        console.log('Getter the current value')
        return this._count
    }
    increment(){
        this._count++
    }
}
代码中，实例属性_count与取值函数value()和increment()方法，处于同一层级。这时，不需要在实例属性前面加上this。
这种新写法的好处是，所有实例对象自身的属性都定义在类的头部，看上去比较整齐，一眼就能看出这个类有哪些实例属性
```
```
class foo{
    bar = 'hello'
    baz = 'world'
    constructor(){
        
    }
}
代码中，一眼就能看出，foo类有两个实例属性，一目了然。另外，写起来也比较简洁
```
4.静态属性
静态属性指的是Class 本身的属性，即Class.porpName,而不是定义在实例对象(this)上的属性
```
class Foo{

}
Foo.prop = 1
Foo.prop //1
上面的写法为Foo类定义了一个静态属性prop
```
目前，只有这种写法可行，因为ES6明确规定，Class内部只有静态方法，没有静态属性。现在有一个提案提供了类的静态属性。写法是在实例属性的前面，加上static关键字。
```
class MyClass{
    static myStaticProp = 42
    constructor(){
        console.log(MyClass.myStaticProp)
    }
}
new MyClass()
这个新写法大大方便了静态属性的表达
```
```
class Foo{//老写法

}
Foo.prop =1
class Foo{//新写法
    static prop =1
}
上面代码中，老写法的静态属性定义在类的外部，整个类生成以后，再生成静态属性。这样让人很容易忽略这个静态属性，也不符合相关代码应该放在一起的代码组织原则。另外，新写法是显式声明（declarative）,而不是赋值处理，语义更好。
```
5.私有方法和私有属性
现在的解决方案
私有方法和私有属性，是只能在类的内部访问的方法和属性，外部不能访问，这是常见需求，有利于代码的封装，但ES6不提供，只能通过变通方法模拟实现。
一种做法是在命名上加以区别。
```
class Widget{
    //公有方法
    foo(baz){
        this._bar(baz)
    }
    //私有属性
    _bar(baz){
        return this.snaf = baz
    }
}
上面代码中，_bar()方法前面的下划线，表示这是一个只限于内部使用的私有方法。但是这种命名是不保险的。在类的外部，还是可以调用到这个方法
```
另一种方法就是索性将私有方法移出类，因为类内部的所有方法都是对外可见的。
```
class Widget {
  foo (baz) {
    bar.call(this, baz);
  }

  // ...
}

function bar(baz) {
  return this.snaf = baz;
}
上面代码中，foo是公开方法，内部调用了bar.call(this, baz)。这使得bar()实际上成为了当前类的私有方法。

```
Class可以通过extends关键字实现继承，这比ES5的通过修改原型链实现继承,要清晰和方便很多。
```
class Point{

}
class Pointwo extends Point{
    
}
```
上面代码定义了一个ColorPoint类，该类通过extends关键字，继承了Point类的所有属性和方法。但是由于没有部署任何代码，所以这两个类完全一样，等于复制了一个Point类。下面，我们在ColorPoint内部加上代码。
```
class Pointwo extends Point{
    constructor(x,y,color){
        super(x,y)//调用父类的constructor(x,y)
        this.color = color
    }
    toString(){
        return this.color + '' +super.toString()//调用父类的toString()
    }
}
代码中，constructor方法和toString方法之中，都出现了super关键字，他在这里表示父类的构造函数，用来新建父类的this对象
子类必须在constructor方法中调用super方法，否则新建实例时会报错，这是因为子类自己的this对象，必须先通过父类的构造函数完成塑造，得到与父类同样的实例属性和方法，然后对其进行加工，加上子类自己的实例属性和方法，如果不调用super方法，子类就得不到this对象
```
```
class Point { /* ... */ }

class ColorPoint extends Point {
  constructor() {
  }
}

let cp = new ColorPoint(); // ReferenceError
上面代码中，ColorPoint继承了父类Point，但是它的构造函数没有调用super方法，导致新建实例时报错。

ES5 的继承，实质是先创造子类的实例对象this，然后再将父类的方法添加到this上面（Parent.apply(this)）。ES6 的继承机制完全不同，实质是先将父类实例对象的属性和方法，加到this上面（所以必须先调用super方法），然后再用子类的构造函数修改this。

如果子类没有定义constructor方法，这个方法会被默认添加，代码如下。也就是说，不管有没有显式定义，任何一个子类都有constructor方法。
```
```
class ColorPoint extends Point {
}

// 等同于
class ColorPoint extends Point {
  constructor(...args) {
    super(...args);
  }
}
另一个需要注意的地方是，在子类的构造函数中，只有调用super之后，才可以使用this关键字，否则会报错。这是因为子类实例的构建，基于父类实例，只有super方法才能调用父类实例。
```
```
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
}

class ColorPoint extends Point {
  constructor(x, y, color) {
    this.color = color; // ReferenceError
    super(x, y);
    this.color = color; // 正确
  }
}
上面代码中，子类的constructor方法没有调用super之前，就使用this关键字，结果报错，而放在super方法之后就是正确的。

下面是生成子类实例的代码。
let cp = new ColorPoint(25, 8, 'green');

cp instanceof ColorPoint // true
cp instanceof Point // true
上面代码中，实例对象cp同时是ColorPoint和Point两个类的实例，这与 ES5 的行为完全一致。
```
```
最后，父类的静态方法，也会被子类继承。
```
class A {
  static hello() {
    console.log('hello world');
  }
}

class B extends A {
}

B.hello()  // hello world
上面代码中，hello()是A类的静态方法，B继承A，也继承了A的静态方法。
```
2.Object.getPrototypeOf()
Object.getPrototypeOf()方法可以用来从子类上获取父类
```
Object.getPrototypeOf(ColorPoint) === Point//true
因此，可以使用这个方法判断，一个类是否继承了另一个类
```
3.super关键字
super这个关键字，既可以当作函数使用，也可以当作对象使用。在这两种情况下，它的用法完全不同
第一种情况，super作为函数用时，代表父类的构造函数。ES6要求，子类的构造函数必须执行一次super函数。
```
class A {}

class B extends A {
  constructor() {
    super();
  }
}
上面代码中，子类B的构造函数之中的super()，代表调用父类的构造函数。这是必须的，否则 JavaScript 引擎会报错。

注意，super虽然代表了父类A的构造函数，但是返回的是子类B的实例，即super内部的this指的是B的实例，因此super()在这里相当于A.prototype.constructor.call(this)。
```
```
class A {
  constructor() {
    console.log(new.target.name);
  }
}
class B extends A {
  constructor() {
    super();
  }
}
new A() // A
new B() // B
上面代码中，new.target指向当前正在执行的函数。可以看到，在super()执行时，它指向的是子类B的构造函数，而不是父类A的构造函数。也就是说，super()内部的this指向的是B。

作为函数时，super()只能用在子类的构造函数之中，用在其他地方就会报错。
```
```
class A {}

class B extends A {
  m() {
    super(); // 报错
  }
}
上面代码中，super()用在B类的m方法之中，就会造成语法错误。
```
第二种情况，super作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类
```
class A{
    p(){
        return 2
    }
}
class B extends A{
    constructor(){
        super()
        console.log(super.p())///2
    }
}
let b = new B()
代码中，子类B当中的super.p(),就是将super当作一个对象使用。这时，super在普通方法之中，指向A.prototype,所以super.p()就相当于A.prototype.p()
注意：由于super指向父类的原型对象，所以定义在父类实例上的方法或属性，是无法通过super调用的。
```
```
class A {
  constructor() {
    this.p = 2;
  }
}

class B extends A {
  get m() {
    return super.p;
  }
}

let b = new B();
b.m // undefined
上面代码中，p是父类A实例的属性，super.p就引用不到它。
```
如果属性定义在父类的原型对象上，super就可以取到
```
class A {}
A.prototype.x = 2;

class B extends A {
  constructor() {
    super();
    console.log(super.x) // 2
  }
}
let b = new B();
代码中,属性x是定义在A.prototype上面的，所以super.x可以取到它的值
```
ES6规定，在子类普通方法中通过super调用父类的方法时，方法内部的this指向当前的子类实例
```
class A {
  constructor() {
    this.x = 1;
  }
  print() {
    console.log(this.x);
  }
}

class B extends A {
  constructor() {
    super();
    this.x = 2;
  }
  m() {
    super.print();
  }
}

let b = new B();
b.m() // 2
代码中，super.print()虽然调用的是A.prototype.print(),但是A.prototype.print()内部的this指向子类B的实例，导致输出的是2，而不是1.也就是说，实际上执行的是super.print.call(this)
```
由于this指向子类实例，所以如果通过super对某个属性赋值，这时super就是this，赋值的属性会变成子类实例的属性
```
class A {
  constructor() {
    this.x = 1;
  }
}

class B extends A {
  constructor() {
    super();
    this.x = 2;
    super.x = 3;
    console.log(super.x); // undefined
    console.log(this.x); // 3
  }
}

let b = new B();
代码中，super.x赋值为3，这时等同于对this.x赋值为3.而当读取super.x的时候，读的是A.prototype.x,所以返回undefined
```
如果super作为对象，用在静态方法之中，这时super将指向父类，而不是父类的原型对象
```
class Parent{
    static myMethod(msg){
        console.log('static',msg)
    }
    myMethod(msg){
        console.log('instance',msg)
    }
}
class Child extends Parent{
    static myMethod(msg){
        super.myMethod(msg)
    }
    myMethod(msg){
        super.myMethod(msg)
    }
}
console.log(Child.myMethod(1))
var child = new Child()
console.log(child.myMethod(2))
上面代码中，super在静态方法之中指向父类，在普通方法之中指向父类的原型对象。
```
另外，在子类的静态方法中通过super调用父类方法时，方法内部的this指向当前的子类，而不是子类的实例
```
class A {
  constructor() {
    this.x = 1;
  }
  static print() {
    console.log(this.x);
  }
}

class B extends A {
  constructor() {
    super();
    this.x = 2;
  }
  static m() {
    super.print();
  }
}

B.x = 3;
B.m() // 3
上面代码中，静态方法B.m里面，super.print指向父类的静态方法。这个方法里面的this指向的是B，而不是B的实例。
```
```
使用super的时候，必须显式指定是作为函数、还是作为对象使用，否则会报错。
class A {}

class B extends A {
  constructor() {
    super();
    console.log(super); // 报错
  }
}
上面代码中，console.log(super)当中的super，无法看出是作为函数使用，还是作为对象使用，所以 JavaScript 引擎解析代码的时候就会报错。这时，如果能清晰地表明super的数据类型，就不会报错。
```
```
class A {}

class B extends A {
  constructor() {
    super();
    console.log(super.valueOf() instanceof B); // true
  }
}

let b = new B();
上面代码中，super.valueOf()表明super是一个对象，因此就不会报错。同时，由于super使得this指向B的实例，所以super.valueOf()返回的是一个B的实例。
```
```
最后，由于对象总是继承其他对象的，所以可以在任意一个对象中，使用super关键字。
var obj = {
  toString() {
    return "MyObject: " + super.toString();
  }
};

obj.toString(); // MyObject: [object Object]
```
4.类的 prototype 属性和__proto__属性 
大多数浏览器的ES5实现中，每一个对象都有__proto__属性，指向对应的构造函数的prototype属性。Class作为构造函数的语法糖，同时有prototype属性和__proto__属性,因此同时存在两条继承链
(1) 子类的__proto__属性，表示构造函数的继承，总是指向父类。
(2) 子类的prototype属性的__proto__属性，表示方法的继承，总是指向父类的prototype属性
```
class A{

}
class B extends A{

}
B.__proto__ === A //true
B.prototype.__proto__ === A.prototype //true
代码中，子类B的__proto__属性指向父类A，子类B的prototype属性的__proto__属性指向父类A的prototype属性
```
这样的结果是因为，类的继承是按照下面的模式实现的。
```
class A{

}
class B{

}
Object.setPrototypeOf(B.prototype,A.prototype)//B的实例继承A的实例
Object.setPrototypeOf(B,A)//B继承A的静态属性
const b = new B()
《对象的扩展》一章给出过Object.setPrototypeOf方法的实现。
```
```
Object.setPrototypeOf = function (obj, proto) {
  obj.__proto__ = proto;
  return obj;
}
因此就得到了上面这个结果
```
```
Object.setPrototypeOf(B.prototype, A.prototype);
// 等同于
B.prototype.__proto__ = A.prototype;

Object.setPrototypeOf(B, A);
// 等同于
B.__proto__ = A;
这两条继承链，可以这样理解：作为一个对象，子类（B）的原型（__proto__属性）是父类（A）；作为一个构造函数，子类（B）的原型对象（prototype属性）是父类的原型对象（prototype属性）的实例。
```
```
B.prototype = Object.create(A.prototype);
// 等同于
B.prototype.__proto__ = A.prototype;
```
extends关键字后面可以跟多种类型的值
```
class B extends A{

}
上面代码的A，只要是一个有prototype属性的函数，就能被B继承。由于函数都有prototype属性（除了Function.prototype函数），因此A可以是任意函数。
```
下面，讨论两种情况。第一种，子类继承Object类。
```
class A extends Object {
}

A.__proto__ === Object // true
A.prototype.__proto__ === Object.prototype // true
这种情况下，A其实就是构造函数Object的复制，A的实例就是Object的实例。
```
第二种情况，不存在任何继承。
```
class A {
}

A.__proto__ === Function.prototype // true
A.prototype.__proto__ === Object.prototype // true
这种情况下，A作为一个基类（即不存在任何继承），就是一个普通函数，所以直接继承Function.prototype。但是，A调用后返回一个空对象（即Object实例），所以A.prototype.__proto__指向构造函数（Object）的prototype属性。
```
实例的 __proto__ 属性
子类实例的__proto__属性的__proto__属性，指向父类实例的__proto__属性。也就是说，子类的原型的原型，是父类的原型。
```
var p1 = new Point(2, 3);
var p2 = new ColorPoint(2, 3, 'red');

p2.__proto__ === p1.__proto__ // false
p2.__proto__.__proto__ === p1.__proto__ // true
上面代码中，ColorPoint继承了Point，导致前者原型的原型是后者的原型。
```
因此，通过子类实例的__proto__.__proto__属性，可以修改父类实例的行为。
```
p2.__proto__.__proto__.printName = function () {
  console.log('Ha');
};

p1.printName() // "Ha"
上面代码在ColorPoint的实例p2上向Point类添加方法，结果影响到了Point的实例p1。
```