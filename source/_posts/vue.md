---
title: Vue
date: 2020-4-1 12:00:00
categories: 
    - web前端开发
    - Vue
tags: 
    - Vue
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=493093412.mp3
cover: https://img2.baidu.com/it/u=3429416796,2324999190&fm=26&fmt=auto&gp=0.jpg
---
### vue

#### 一.vue的特点是什么？
1.遵循MVVM模式数据驱动视图
2.双向绑定
3.摒弃了原始的dom操作
3.可以轻松引入Vue插件或其他第三方库开发项目
#### 二.vue的原理是什么？

vue2.0采用数据劫持结合发布-订阅模式,通过 Object.defineproperty 来劫持各个属性的 setter,getter,在数据变动时发布消息给订阅者,触发响应的监听回调

#### 三.computed 和 watch 有什么区别及运用场景?

computed 计算属性 : 依赖其它属性值,并且 computed 的值有缓存,只有它依赖的属性值发生改变,下一次获取 computed 的值时才会重新计算 computed 的值。

watch 侦听器 : 更多的是「观察」的作用,**无缓存性**,类似于某些数据的监听回调,每当监听的数据变化时都会执行回调进行后续操作。

运用场景：

当我们需要进行数值计算,并且依赖于其它数据时,应该使用 computed,因为可以利用 computed 的缓存特性,避免每次获取值时,都要重新计算。

当我们需要在数据变化时执行异步或开销较大的操作时,应该使用 watch,使用 watch 选项允许我们执行异步操作 ( 访问一个 API ),限制我们执行该操作的频率,并在我们得到最终结果前,设置中间状态。这些都是计算属性无法做到的。
#### 四.Vue 中的 key 到底有什么用？
key 主要用在 Vue的虚拟DOM算法，在新旧Vnode的key是否相等。从而复用与新节点对应的老节点。如果不使用key，Vue就会根据标签相同替换里面的内容。使用key，它会基于key的变化重新排列元素顺序，并且会移除key不存在的元素。
#### 五.什么是MVVM？
MVVM是Model-View-ViewMode MVC中的Controller演变成ViewModel。Model层代表数据模型，View代表UI组件，ViewModel是View和Model层的桥梁，数据会绑定到viewModel层并自动将数据渲染到页面中，视图变化的时候会通知viewModel层更新数据。
#### 六.mvvm和mvc区别？它和其它框架（jquery）的区别是什么？哪些场景适合？
mvc和mvvm其实区别并不大。都是一种设计思想。主要就是mvc中Controller演变成mvvm中的viewModel。mvvm主要解决了mvc中大量的DOM 操作使页面渲染性能降低，加载速度变慢，影响用户体验。

区别：vue数据驱动，通过数据来显示视图层而不是节点操作。
场景：数据操作比较多的场景，更加便捷
#### 七.vuex是什么？怎么使用？哪种功能场景使用它？
vuex是管理vue状态的一个库
任何组件都可以和store通信
它是单一数据源
#### 八.vuex有哪几种属性？
有五种，分别是 State、 Getter、Mutation 、Action、 Module

·  vuex的State特性
A、Vuex就是一个仓库，仓库里面放了很多对象。其中state就是数据源存放地，对应于一般Vue对象里面的data
B、state里面存放的数据是响应式的，Vue组件从store中读取数据，若是store中的数据发生改变，依赖这个数据的组件也会发生更新
C、它通过mapState把全局的 state 和 getters 映射到当前组件的 computed 计算属性中

· vuex的Getter特性
A、getters 可以对State进行计算操作，它就是Store的计算属性
B、 虽然在组件内也可以做计算属性，但是getters 可以在多组件之间复用
C、 如果一个状态只在一个组件内使用，是可以不用getters

·  vuex的Mutation特性
Action 类似于 mutation，不同在于：Action 提交的是 mutation，而不是直接变更状态；Action 可以包含任意异步操作。
#### 九. v-show和v-if指令的共同点和不同点
v-show指令是通过修改元素的display的CSS属性让其显示或者隐藏
v-if指令是直接销毁和重建DOM达到让元素显示和隐藏的效果
#### 十.vue-router有哪几种导航钩子？
三种，一种是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截。
第二种：组件内的钩子；
第三种：单独路由独享组件
#### 十一.什么是vue生命周期
Vue 实例从创建到销毁的过程，就是生命周期。也就是从开始创建、初始化数据、编译模板、挂载Dom→渲染、更新→渲染、卸载等一系列过程，我们称这是 Vue 的生命周期。
#### 十二.vue生命周期的作用是什么
它的生命周期中有多个事件钩子，让我们在控制整个Vue实例的过程时更容易形成好的逻辑。
#### 十三.第一次页面加载会触发哪几个钩子
第一次页面加载时会触发 beforeCreate, created, beforeMount, mounted 这几个钩子
#### 十四.简单描述每个周期具体适合哪些场景
生命周期钩子的一些使用方法：
beforecreate : 可以在这加个loading事件，在加载实例时触发
created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用
mounted : 挂载元素，获取到DOM节点
updated : 如果对数据统一处理，在这里写上相应函数
beforeDestroy : 可以做一个确认停止事件的确认框
nextTick : 更新数据后立即操作dom
#### 十五.为什么使用key？
当有相同标签名的元素切换时，需要通过 key 特性设置唯一的值来标记以让 Vue 区分它们，否则 Vue 为了效率只会替换相同标签内部的内容。
#### 十六.为什么避免 v-if 和 v-for 用在一起
当 Vue 处理指令时，v-for 比 v-if 具有更高的优先级，这意味着 v-if 将分别重复运行于每个 v-for 循环中。通过v-if 移动到容器元素，不会再重复遍历列表中的每个值。取而代之的是，我们只检查它一次，且不会在 v-if 为否的时候运算 v-for。
#### 十七.VNode是什么？虚拟 DOM是什么？
Vue在 页面上渲染的节点，及其子节点称为“虚拟节点 (Virtual Node)”，简写为“VNode”。“虚拟 DOM”是由 Vue 组件树建立起来的整个 VNode 树的称呼。
#### 十八.active-class是哪个组件的属性？嵌套路由怎么定义？
vue-router模块的router-link组件。
嵌套路由顾名思义就是路由的多层嵌套。 一级路由里面使用children数组配置子路由，就是嵌套路由。
#### 十九.怎么定义vue-router的动态路由？怎么获取传过来的动态参数？
在router目录下的index.js文件中，对path属性加上/:id。  使用router对象的params.id
#### 二十.请说出vue.cli项目中src目录每个文件夹和文件的用法？
assets文件夹是放静态资源；components是放组件；router是定义路由相关的配置;view视图；app.vue是一个应用主组件；main.js是入口文件
#### 二十一.指令v-el的作用是什么?
提供一个在页面上已存在的 DOM 元素作为 Vue 实例的挂载目标.可以是 CSS 选择器，也可以是一个 HTMLElement 实例
#### 二十二.请列举出3个Vue中常用的生命周期钩子函数?
created: 实例已经创建完成之后调用,在这一步,实例已经完成数据观测, 属性和方法的运算, watch/event事件回调. 然而, 挂载阶段还没有开始, $el属性目前还不可见

mounted: el被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子。如果 root实例挂载了一个文档内元素，当 mounted 被调用时 vm.$el 也在文档内。

activated::keep-alive组件激活时调用
#### 二十三.怎样理解单向数据流
这个概念出现在组件通信。父组件是通过 prop 把数据传递到子组件的，但是这个 prop 只能由父组件修改，子组件不能修改，否则会报错。子组件想修改时，只能通过 $emit 派发一个自定义事件，父组件接收到后，由父组件修改。
#### 二十四.各个生命周期的作用
beforeCreate 组件实例被创建之初，组件的属性生效之前
created 组件实例已经完全出创建，属性也绑定，但是真实 DOM 没有生成，$el 还不可以用
beforeMount 在挂载开始之前被调用，相关的render函数首次被调用
mounted el 被新创建的 vm.$el 替换，并挂载实例上去调动该钩子
beforeUpdate 组件数据更新之前调用，发生在虚拟 DOM 打补丁之前
update 组件数据更新之后
activated keep-alive 专属，组件被激活时调用
deactivated keep-alive 专属，组件被销毁时调用
beforeDestory 组件销毁前调用
destroyed 组件销毁后调用
#Vue 的父组件和子
#### 二十五.在哪个生命周期内调用异步请求？
在 钩子函数 created 、beforeMount、mounted 中进行调用，因为在这三个钩子函数中，data 已经创建，可以将服务器点的数据返回进行赋值
#### 二十六.在什么阶段才能访问操作 DOM
在钩子函数 mounted 被调用前，Vue 已经将编译好的模板挂载到页面上，所以可以在 mounted 中访问到 DOM
#### 二十七.Proxy 与 Object.defineProperty 优劣对比
Proxy 可以直接监听对象而非属性；
Proxy 可以直接监听数组的变化；
Proxy 有多达 13 种拦截方法,不限于 apply、ownKeys、deleteProperty、has 等等是 Object.defineProperty 不具备的；
Proxy 返回的是一个新对象,我们可以只操作新的对象达到目的,而 Object.defineProperty 只能遍历对象属性直接修改；
Proxy 作为新标准将受到浏览器厂商重点持续的性能优化，也就是传说中的新标准的性能红利
#### 二十八.使你用过 Vuex 吗？
主要包含一下几种模块：
#State
定义了应用状态的数据结构，可以在这里设置默认的初始化状态。
#Getter
允许组件从 Store 中获取数据，mapGetters 辅助函数仅仅是将 store 中的 getter 映射到局部计算属性中。
#Mutation
是唯一更改 store 中状态的方法，且必须是同步函数。
#Action
用于提交 mutation，而不是直接变更状态，可以任何异步操作。
#Module
允许将单一的 Store 拆分为多个 store 且同时保持在单一的状态数中
#### 二十九.使用过 Vue SSR 吗？ 说说 SSR
SSR 将 Vue 在客户端将标签渲染成HTML 片段的工作放到了服务端完成，服务端形成的 HTML 片段直接返回给客户端这个过程，叫做服务端渲染 
#### 三十.计算属性和methods的区别？为什么要用计算属性而不用methods？
它两的执行结果是一样的。计算属性 是只有它的依赖发生变化的时候它会自动的进行计算求值，如果依赖没有发生变化，那么每次访问的时候计算属性都会立刻返回之前的执行结果，而事件函数需要手动调用，并且调用一次触发一次比较粗暴一点，每当重新触发渲染时，调用方法总是再次执行函数。
#### 三十一.vue-router 的原理是什么？
vue-router是什么：他可以让单页面应用拥有了多页面应用的效果，一个url对应一个页面。
它主要是通过h5新增的history和hash两种模式来实现的
hash —— 即地址栏 URL 中的 # 符号。它的特点在于：hash 虽然出现在 URL 中，但不会被包括在 HTTP 请求中，对后端完全没有影响，因此改变 hash 不会重新加载页面。每次hash值得变化，会触发hashchange这个时间，通过这个时间我就可以知道hash值发生了哪些变化。然后我们就可以监听hashchange来实现更新页面部分内容的操作。
history —— 利用了 HTML5 History Interface 中新增的 pushState() 和 replaceState() 方法。（需要特定浏览器支持）这两个方法应用于浏览器的历史记录栈，在当前已有的 back、forward、go 的基础之上，它们提供了对历史记录进行修改的功能。只是当它们执行修改时，虽然改变了当前的 URL，但浏览器不会立即向后端发送请求。
因此可以说，hash 模式和 history 模式都属于浏览器自身的特性，Vue-Router 只是利用了这两个特性（通过调用浏览器提供的接口）来实现前端路由.   
#### 三十二.插槽的作用：
为了让组件更加具有扩展性。抽取共性，保留不同为插槽，让其他组件可以传递自己想展示的标签到预留插槽。它包含具名插槽，匿名插槽、还有作用域插槽。
#### 三十三.keep-alive的作用？
缓存组件的状态，在组件还原的时候能够把状态还原到组件上。然后它有3个属性，分别是：include(包括)、exclude(不包括)、max(可缓存的最大组件实例数量)
利用keep-alive组件把想要缓存的组件包一下，并且给被缓存的组件添加name属性，在include属性里面写上我们要缓存的组件name
#### 三十四.vuex与全局对象的区别？
Vuex的状态存储是响应式的。当Vue组件从store中读取状态的时候，若store中的状态发生变化，那么相应的组件也会得到高效更新。
不能直接改变store中的状态，改变store中的状态的唯一途径就是显示地提交(commit)mutation。这样使得我们可以方便地跟踪每一个状态的变化，从而让我们能够实现一些工具帮助我们更好地了解我们的应用。
#### 三十五.为什么组件里的data是个函数？
一个组件被复用多次的话，也就会创建多个实例。本质上， 这些实例都是同一个构造函数
如果data是对象的话，对象属于引用类型，会影响到所有的实例
所以为了保证组件不同的实例之间data不冲突，data必须是个函数
#### 三十六.vue2.x和vue3.x渲染器的diff算法有什么区别？
Vue3.x借鉴了 ivi算法和 inferno算法
在创建VNode时就确定其类型，以及在mount/patch的过程中采用位运算来判断一个VNode的类型，在这个基础之上再配合核心的Diff算法，使得性能上较Vue2.x有了提升 
Vue2的核心Diff算法采用了双端比较的算法，同时从新旧children的两端开始进行比较，借助key值找到可复用的节点，再进关相关操作
#### 三十七.那你知道Vue3.x响应式数据原理吗？
Vue3.x改用Proxy替代Object.defineProperty。因为Proxy可以直接监听对象和数组的变化，并且有多达13种拦截方法。并且作为新标准将受到浏览器厂商重点持续的性能优化。
Proxy只会代理对象的第一层，那么Vue3又是怎样处理这个问题的呢？
答：判断当前Reflect.get的返回值是否为Object，如果是则再通过reactive方法做代理， 这样就实现了深度观测。
监测数组的时候可能触发多次get/set，那么如何防止触发多次呢？？
答：我们可以判断key是否为当前被代理对象target自身属性，也可以判断旧值与新值是否相等，只有满足以上两个条件之一时，才有可能执行trigger。 
#### 三十八.nextTick知道吗，实现原理是什么？
在下次 DOM 更新循环结束之后执行延迟回调。nextTick主要使用了宏任务和微任务。根据执行环境分别尝试采用
PromiseMutationObserversetImmediate如果以上都不行则采用setTimeout
定义了一个异步方法，多次调用nextTick会将方法存入队列中，通过这个异步方法清空当前队列。 
#### 三十九.说一下Vue的生命周期
beforeCreate是new Vue()之后触发的第一个钩子，在当前阶段data、methods、computed以及watch上的数据和方法都不能被访问。
created在实例创建完成后发生，当前阶段已经完成了数据观测，也就是可以使用数据，更改数据，在这里更改数据不会触发updated函数。可以做一些初始数据的获取，在当前阶段无法与Dom进行交互，如果非要想，可以通过vm.$nextTick来访问Dom。
beforeMount发生在挂载之前，在这之前template模板已导入渲染函数编译。而当前阶段虚拟Dom已经创建完成，即将开始渲染。在此时也可以对数据进行更改，不会触发updated。
mounted在挂载完成后发生，在当前阶段，真实的Dom挂载完毕，数据完成双向绑定，可以访问到Dom节点，使用$refs属性对Dom进行操作。
beforeUpdate发生在更新之前，也就是响应式数据发生更新，虚拟dom重新渲染之前被触发，你可以在当前阶段进行更改数据，不会造成重渲染。
updated发生在更新完成之后，当前阶段组件Dom已完成更新。要注意的是避免在此期间更改数据，因为这可能会导致无限循环的更新。
beforeDestroy发生在实例销毁之前，在当前阶段实例完全可以被使用，我们可以在这时进行善后收尾工作，比如清除计时器。
destroyed发生在实例销毁之后，这个时候只剩下了dom空壳。组件已被拆解，数据绑定被卸除，监听被移出，子实例也统统被销毁。
#### 四十.说一下v-model的原理?
v-model本质就是一个语法糖，可以看成是value + input方法的语法糖。 可以通过model属性的prop和event属性来进行自定义。原生的v-model，会根据标签的不同生成不同的事件和属性。
#### 四十一.Vue事件绑定原理说一下?
原生事件绑定是通过addEventListener绑定给真实元素的，组件事件绑定是通过Vue自定义的$on实现的。
#### 四十一.Vue中组件生命周期调用顺序说一下?
组件的调用顺序都是先父后子,渲染完成的顺序是先子后父。
组件的销毁操作是先父后子，销毁完成的顺序是先子后父。
加载渲染过程
父beforeCreate->父created->父beforeMount->子beforeCreate->子created->子beforeMount- >子mounted->父mounted
子组件更新过程
父beforeUpdate->子beforeUpdate->子updated->父updated
父组件更新过程
父 beforeUpdate -> 父 updated
销毁过程
父beforeDestroy->子beforeDestroy->子destroyed->父destroyed
#### 四十二.Vue2.x组件通信有哪些方式？
父子组件通信
父->子props，子->父 $on、$emit
获取父子组件实例 $parent、$children
Ref 获取实例的方式调用组件的属性或者方法
Provide、inject 官方不推荐使用，但是写组件库时很常用
兄弟组件通信
Event Bus 实现跨组件通信 Vue.prototype.$bus = new Vue
Vuex
跨级组件通信
Vuex
$attrs、$listeners
Provide、inject
#### 四十三.你都做过哪些Vue的性能优化？
编码阶段

尽量减少data中的数据，data中的数据都会增加getter和setter，会收集对应的watcherv-if和v-for不能连用如果需要使用v-for给每项元素绑定事件时使用事件代理SPA 页面采用keep-alive缓存组件在更多的情况下，使用v-if替代v-showkey保证唯一使用路由懒加载、异步组件防抖、节流第三方模块按需导入长列表滚动到可视区域动态加载图片懒加载
SEO优化

预渲染服务端渲染SSR
打包优化

压缩代码Tree Shaking/Scope Hoisting使用cdn加载第三方模块多线程打包happypacksplitChunks抽离公共文件sourceMap优化
用户体验

骨架屏 PWA

#### 四十四.vue中的修饰符?
.stop 阻止事件冒泡
.prevent 清除默认行为
.once 只触发一次回调
.lazy 取代input 监听change 事件
.number 输入字符串转为有效的数字
.trim 输入首尾空格过滤
#### 四十五.vue中的指令有哪些？
v-if、v-else、v-for、v-bind、v-model、v-on v-text
#### 四十六.插槽之间是怎么传值的？
可以用作用域插槽进行传值。子组件的slot标签中动态绑定属性，父组件中给template标签绑定(v-slot)值，子组件抛出来的接口，可以通过这个值访问到子组件的数据
#### 四十七.vue中的内置组件有哪些？
component、
transition、
transition-group、
keep-alive、
slot
#### 四十八.vue中的transfrom组件是什么？
使用transfrom可以完成任何元素进入/离开的过渡效果。
它的用法是：首先在这个组件内设置一个那么属性，然后再css中用v-enter、v-enter-active、v-leave、v-leave-active
来实现整体的效果。
#### 四十九.computed 是什么？实现原理？
是：计算属性。基于当前的数据进行简单的加工返回新的数据，当计算属性所依赖的数据发生变化时，它会自动进行计算。
写起来像函数，本质是属性。

对大量计算有优化效果。仅仅在依赖的数据发生变化时，才执行。
computed 内部实现了一个惰性的 watcher，在实例化的时候不会去求值，其内部通过 dirty 属性标记计算属性是否需要重新求值。当 computed 依赖的任意状态发生改变，都会通知这个惰性的 watcher，让它把 dirty 属性设置为 true，所以，当再次读取这个计算属性的时候，就会重新去求值。
惰性的watcher 计算属性在创建时不会去求值的，是在使用时去求值。

computed 本质是一个惰性求值的观察者。

computed 内部实现了一个惰性的 watcher,也就是 computed watcher,computed watcher 不会立刻求值,同时持有一个 dep 实例。

其内部通过 this.dirty 属性标记计算属性是否需要重新求值。

当 computed 的依赖状态发生改变时,就会通知这个惰性的 watcher,

computed watcher 通过 this.dep.subs.length 判断有没有订阅者,

有的话,会重新计算,然后对比新旧值,如果变化了,会重新渲染。 (**Vue 想确保不仅仅是计算属性依赖的值发生变化，而是当计算属性最终计算的值发生变化时才会触发渲染 watcher 重新渲染，本质上是一种优化。**)
没有的话,仅仅把 this.dirty = true。 (**当计算属性依赖于其他数据时，属性并不会立即重新计算，只有之后其他地方需要读取属性的时候，它才会真正计算，即具备 lazy（懒计算）特性。**)

##### 五十.为什么在 Vue3.0 采用了 Proxy,抛弃了 Object.defineProperty？
Object.defineProperty 本身有一定的监控到数组下标变化的能力,但是在 Vue 中,从性能/体验的性价比考虑,尤大大就弃用了这个特性([Vue 为什么不能检测数组变动](https://link.zhihu.com/?target=https%3A//segmentfault.com/a/1190000015783546) )。为了解决这个问题,经过 vue 内部处理后可以使用以下几种方法来监听数组
#### 五十一.$route和$router的区别？
$route是路由信息对象，包含path、params、hash,query,fullPath,matched,name等路由信息参数。而$router是路由实例对象包括了路由的跳转方法，钩子函数。
#### 五十二.vue实现数据双向绑定的原理？
它主要是采用数据劫持结合发布订阅的方式，通过Object.definedProperty()来劫持各个属性的get、set，在数据变动时发布消息给订阅者，触发相应监听回调。当把一个普通JS对象传给vue实例作为它的data选项时，vue将遍历它的属性，用Object.defineproperty()将他们转为getter和setter。用户看不见getter和setter，但是在内部他们让vue追踪依赖，在属性背访问和修改时通知变化。
vue的数据双向绑定 将mvvm作为数据绑定的入口，整合Observer,compile和watcher三者，整合Observer来监听自己的model的数据变化，通过compile来解析编译模板指令，最终利用watcher搭起observer和compile之间的桥梁，达到数据变化
#### 五十三.虚拟dom的优缺点？
虚拟dom可以经过diff算法找出最小差异，然后批量进行patch.
不需要手动操作dom
它可以跨平台，能在服务器端渲染和移动端开发
缺点：无法进行极致优化
#### 五十四.router-link和a标签的区别？
通过router-link进行跳转不会跳转到新的页面，也不会重新渲染，它会选择路由所指的组件进行渲染，避免了重复渲染。
a标签它是从一个页面跳转到另一个页面等于从新打开一个页面，这就违背了多视图单页面开
#### 五十五.diff算法的作用？
就是在patch子Vnode过程中，找到与新Vnode对应的老Vnode，复用真实的dom节点，避免不必要的性能开销。
#### vue中的懒加载的原理：
当输入完地址按下回车的时候，它会去.router里面匹配对应的路径，然后再把它加载出来，并不会在一开始的时候都加载出来。
#### render 和template是什么关系？
性质一样 他们都是类编译器 他们是互补的关系 vue中大部分都是template搞定的 有一小部分是render搞定的 （一直多判断的情况就是render）
#### 为什么不用ref操作dom
简单快捷 使代码更优雅 解耦 高内聚 

代码。