---
title: React
date: 2020-4-1 12:00:00
categories: 
    - web前端开发
    - React
tags: 
    - React
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=493093412.mp3
cover: https://img2.baidu.com/it/u=3429416796,2324999190&fm=26&fmt=auto&gp=0.jpg
---

#### 什么是react？

它是facebook在2011年发布的一个框架
react和vue大体是差不多一个开发框架，都支持组件并且可以引入第三方UI库
react更接近原生一点，vue相对来比较更容易上手。

#### react有什么特点？

它使用虚拟dom而不是真正的dom
它可以用服务器端渲染
它遵循单向数据流或者数据绑定

#### vue和react的区别？

react严格上针对的是mvc模式的view层，vue则是mvvm模式。
操作dom的方式不同，vue使用的是指令操作dom，react是通过js进行操作。
数据绑定不同，vue实现的是双向绑定，react的数据流动是单向的。
react中state是不能直接改变的，需要使用setState改变。vue中的state不是必须的，数据主要是由data属性在vue对象中管理的。

#### 列出React的一些主要优点？

它提高了应用的性能
可以方便地在客户端和服务器端使用
由于 JSX，代码的可读性很好
React 很容易与 Meteor，Angular 等其他框架集成
使用React，编写UI测试用例变得非常容易

#### React有哪些限制？

React 只是一个库，而不是一个完整的框架
它的库非常庞大，需要时间来理解
新手程序员可能很难理解
编码变得复杂，因为它使用内联模板和 JSX

#### 什么是虚拟DOM？

虚拟 DOM (VDOM)是真实 DOM 在内存中的表示。UI 的表示形式保存在内存中，并与实际的 DOM 同步。这是一个发生在渲染函数被调用和元素在屏幕上显示之间的步骤，整个过程被称为调和。

#### 什么是JSX？

JSX 是JavaScript XML 的简写。是 React 使用的一种文件，它利用 JavaScript 的表现出和类似 HTML 的模板语法。这使得 HTML 文件非常容易理解。此文件能使应用非常可靠，并能够提高其性能。

#### 为什么不直接更新 state 呢 ?

如果试图直接更新 state ，则不会重新渲染组件
要使用setState()方法来更新 state。它调度对组件state对象的更新。当state改变时，组件通过重新渲染来响应：

#### 使用 React Hooks 好处是啥？

首先，Hooks 通常支持提取和重用跨多个组件通用的有状态逻辑，而无需承担高阶组件或渲染 props 的负担。Hooks 可以轻松地操作函数组件的状态，而不需要将它们转换为类组件。

Hooks 在类中不起作用，通过使用它们，咱们可以完全避免使用生命周期方法，例如 componentDidMount、componentDidUpdate、componentWillUnmount。相反，使用像useEffect这样的内置钩子。

#### 什么是 React Hooks？

Hooks是 React 16.8 中的新添加内容。它们允许在不编写类的情况下使用state和其他 React 特性。使用 Hooks，可以从组件中提取有状态逻辑，这样就可以独立地测试和重用它。Hooks 允许咱们在不改变组件层次结构的情况下重用有状态逻辑，这样在许多组件之间或与社区共享 Hooks 变得很容易。

#### 什么是 React Context？

Context 通过组件树提供了一个传递数据的方法，从而避免了在每一个层级手动的传递 props 属性。

#### 什么是纯函数？

纯函数是不依赖并且不会在其作用域之外修改变量状态的函数。本质上，纯函数始终在给定相同参数的情况下返回相同结果。

#### 你了解 Virtual DOM 吗？解释一下它的工作原理？

Virtual DOM 是一个轻量级的 JavaScript 对象，它最初只是 real DOM 的副本。它是一个节点树，它将元素、它们的属性和内容作为对象及其属性。 React 的渲染函数从 React 组件中创建一个节点树。然后它响应数据模型中的变化来更新该树，该变化是由用户或系统完成的各种动作引起的。
Virtual DOM 工作过程有三个简单的步骤：
每当底层数据发生改变时，整个 UI 都将在 Virtual DOM 描述中重新渲染。
然后计算之前 DOM 表示与新表示的之间的差异。
完成计算后，将只用实际更改的内容更新 real DOM

#### 为什么浏览器无法读取JSX？

浏览器只能处理 JavaScript 对象，而不能读取常规 JavaScript 对象中的 JSX。所以为了使浏览器能够读取 JSX，首先，需要用像 Babel 这样的 JSX 转换器将 JSX 文件转换为 JavaScript 对象，然后再将其传给浏览器。

#### 与 ES5 相比，React 的 ES6 语法有何不同？

#### 你理解“在React中，一切都是组件”这句话？

组件是 React 应用 UI 的构建块。这些组件将整个 UI 分成小的独立并可重用的部分。每个组件彼此独立，而不会影响 UI 的其余部分。

####  解释 React 中 render() 的目的？

每个React组件强制要求必须有一个 render()。它返回一个 React 元素，是原生 DOM 组件的表示。如果需要渲染多个 HTML 元素，则必须将它们组合在一个封闭标记内，例如 <form>、<group>、<div> 等。此函数必须保持纯净，即必须每次调用时都返回相同的结果。

#### 什么是 Props?

Props 是 React 中属性的简写。它们是只读组件，必须保持纯，即不可变。它们总是在整个应用中从父组件传递到子组件。子组件永远不能将 prop 送回父组件。这有助于维护单向数据流，通常用于呈现动态生成的数据。

#### React中的状态是什么？它是如何使用的？

状态是 React 组件的核心，是数据的来源，必须尽可能简单。基本上状态是确定组件呈现和行为的对象。与props 不同，它们是可变的，并创建动态和交互式组件。可以通过 this.state() 访问它们

#### 如何更新组件的状态？

可以用 this.setState()更新组件的状态。

#### 详细解释 React 组件的生命周期方法。

componentWillMount**()** – 在渲染之前执行，在客户端和服务器端都会执行。
componentDidMount**()** – 仅在第一次渲染后在客户端执行。
componentWillReceiveProps**()** – 当从父类接收到 props 并且在调用另一个渲染器之前调用。
shouldComponentUpdate**()** – 根据特定条件返回 true 或 false。如果你希望更新组件，请返回true 否则返回 false。默认情况下，它返回 false。
componentWillUpdate**()** – 在 DOM 中进行渲染之前调用。
componentDidUpdate**()** – 在渲染发生后立即调用。
componentWillUnmount**()** – 从 DOM 卸载组件后调用。用于清理内存空间。

#### React中的合成事件是什么？

合成事件是围绕浏览器原生事件充当跨浏览器包装器的对象。它们将不同浏览器的行为合并为一个 API。这样做是为了确保事件在不同浏览器中显示一致的属性。

#### 你对 React 的 refs 有什么了解？

Refs 是 React 中引用的简写。它是一个有助于存储对特定的 React 元素或组件的引用的属性，它将由组件渲染配置函数返回。用于对 render() 返回的特定元素或组件的引用。当需要进行 DOM 测量或向组件添加方法时，它们会派上用场。

#### 什么是高阶组件（HOC）？

高阶组件是重用组件逻辑的高级方法，是一种源于 React 的组件模式。 HOC 是自定义组件，在它之内包含另一个组件。它们可以接受子组件提供的任何动态，但不会修改或复制其输入组件中的任何行为。你可以认为 HOC 是“纯（Pure）”组件。

#### 你能用HOC做什么？

代码重用，逻辑和引导抽象
渲染劫持
状态抽象和控制
Props 控制

#### 什么是纯组件？

纯（Pure） 组件是可以编写的最简单、最快的组件。它们可以替换任何只有 render() 的组件。这些组件增强了代码的简单性和应用的性能。

#### React 中 key 的重要性是什么？

key 用于识别唯一的 Virtual DOM 元素及其驱动 UI 的相应数据。它们通过回收 DOM 中当前所有的元素来帮助 React 优化渲染。这些 key 必须是唯一的数字或字符串，React 只是重新排序元素而不是重新渲染它们。这可以提高应用程序的性能。

####  MVC框架的主要问题是什么？

对 DOM 操作的代价非常高
程序运行缓慢且效率低下
内存浪费严重
由于循环依赖性，组件模型需要围绕 models 和 views 进行创建

#### 解释一下 Flux？

Flux 是一种强制单向数据流的架构模式。它控制派生数据，并使用具有所有数据权限的中心 store 实现多个组件之间的通信。整个应用中的数据更新必须只能在此处进行。 Flux 为应用提供稳定性并减少运行时的错误。

#### 什么是Redux？

Redux 是当今最热门的前端开发库之一。它是 JavaScript 程序的可预测状态容器，用于整个应用的状态管理。使用 Redux 开发的应用易于测试，可以在不同环境中运行，并显示一致的行为。

#### Redux遵循的三个原则是什么？

单一数据源
使用纯函数进行修改
状态是只读的

####  你对“单一事实来源”有什么理解？

Redux 使用 “Store” 将程序的整个状态存储在同一个地方。因此所有组件的状态都存储在 Store 中，并且它们从 Store 本身接收更新。单一状态树可以更容易地跟踪随时间的变化，并调试或检查程序。

#### 列出 Redux 的组件。

Action – 这是一个用来描述发生了什么事情的对象。
Reducer – 这是一个确定状态将如何变化的地方。
Store – 整个程序的状态/对象树保存在Store中。
View – 只显示 Store 提供的数据。

#### redux中间件？

redux-logger：提供日志输出
redux-thunk：处理异步操作
redux-promise：处理异步操作，actionCreator的返回值是promise

#### 如何在 Redux 中定义 Action？

React 中的 Action 必须具有 type 属性，该属性指示正在执行的 ACTION 的类型。必须将它们定义为字符串常量，并且还可以向其添加更多的属性。在 Redux 中，action 被名为 Action Creators 的函数所创建。以下是 Action 和Action Creator 的示例：

#### 解释 Reducer 的作用？

Reducers 是纯函数，它规定应用程序的状态怎样因响应 ACTION 而改变。Reducers 通过接受先前的状态和 action 来工作，然后它返回一个新的状态。它根据操作的类型确定需要执行哪种更新，然后返回新的值。如果不需要完成任务，它会返回原来的状态。

#### Store 在 Redux 中的意义是什么？

Store 是一个 JavaScript 对象，它可以保存程序的状态，并提供一些方法来访问状态、调度操作和注册侦听器。应用程序的整个状态/对象树保存在单一存储中。因此，Redux 非常简单且是可预测的。我们可以将中间件传递到 store 来处理数据，并记录改变存储状态的各种操作。所有操作都通过 reducer 返回一个新状态。

#### 什么是React 路由？

React 路由是一个构建在 React 之上的强大的路由库，它有助于向应用程序添加新的屏幕和流。这使 URL 与网页上显示的数据保持同步。它负责维护标准化的结构和行为，并用于开发单页 Web 应用。 React 路由有一个简单的API。

#### 为什么React Router v4中使用 switch 关键字 ？

虽然 <div> ** 用于封装 Router 中的多个路由，当你想要仅显示要在多个定义的路线中呈现的单个路线时，可以使用 “switch” 关键字。使用时，<switch>** 标记会按顺序将已定义的 URL 与已定义的路由进行匹配。找到第一个匹配项后，它将渲染指定的路径。从而绕过其它路线。

#### 为什么需要 React 中的路由？

Router 用于定义多个路由，当用户定义特定的 URL 时，如果此 URL 与 Router 内定义的任何 “路由” 的路径匹配，则用户将重定向到该特定路由。所以基本上我们需要在自己的应用中添加一个 Router 库，允许创建多个路由，每个路由都会向我们提供一个独特的视图

#### react性能优化的方案？

重写shouldComponentUpdate来避免不必要的dom操作。
使用 production 版本的react.js。
使用key来帮助React识别列表中所有子组件的最小变化。

#### 介绍一下webpack？

webpack是一个前端模块化打包工具，主要由入口，出口，loader，plugins四个部分。前端的打包工具还有一个gulp，不过gulp侧重于前端开发的过程，而webpack侧重于模块，例如他会将css文件看作一个模块，通过css-loader将css打包成符合css的静态资源。

#### react生命周期中，最适合与服务端进行数据交互的是哪个函数？

componentDidMount：在这个阶段，实例和dom已经挂载完成，可以进行相关的dom操作。

#### shouldComponentUpdate 是做什么的，（react 性能优化是哪个周期函数？）

询问组件是否需要更新的一个钩子函数，判断数据是否需要重新渲染，返回一个布尔值。默认的返回值是true，需要重新render()。若如果返回值是false则不触发渲染,利用这个生命周期函数可以强制关闭不需要更新的子组件来提升渲染性能。

这个方法用来判断是否需要调用 render 方法重新描绘 dom。
因为 dom 的描绘非常消耗性能，如果我们能在 shouldComponentUpdate 方法中能够写出更优化的 dom diff 算法，可以极大的提高性能。

#### 指出(组件)生命周期方法的不同？

componentWillMount – 多用于根组件中的应用程序配置
componentDidMount – 在这可以完成所有没有 DOM 就不能做的所有配置，并开始获取所有你需要的数据；如果需要设置事件监听，也可以在这完成
componentWillReceiveProps – 这个周期函数作用于特定的 prop 改变导致的 state 转换
shouldComponentUpdate – 如果你担心组件过度渲染，shouldComponentUpdate 是一个改善性能的地方，因为如果组件接收了新的 prop， 它可以阻止(组件)重新渲染。shouldComponentUpdate 应该返回一个布尔值来决定组件是否要重新渲染
componentWillUpdate – 很少使用。它可以用于代替组件的 componentWillReceiveProps 和 shouldComponentUpdate(但不能访问之前的 props)
componentDidUpdate – 常用于更新 DOM，响应 prop 或 state 的改变
componentWillUnmount – 在这你可以取消网络请求，或者移除所有与组件相关的事件监听器

#### 调用 setState 之后发生了什么？

代码中调用 setState 函数之后，React 会将传入的参数对象与组件当前的状态合并，然后触发所谓的调和过程（Reconciliation）。

经过调和过程，React 会以相对高效的方式根据新的状态构建 React 元素树并且着手重新渲染整个 UI 界面；
在 React 得到元素树之后，React 会自动计算出新的树与老树的节点差异，然后根据差异对界面进行最小化重渲染；
在差异计算算法中，React 能够相对精确地知道哪些位置发生了改变以及应该如何改变，这就保证了按需更新，而不是全部重新渲染。

#### react diff 原理（常考，大厂必考）

把树形结构按照层级分解，只比较同级元素。
列表结构的每个单元添加唯一的 key 属性，方便比较。
React 只会匹配相同 class 的 component（这里面的 class 指的是组件的名字）
合并操作，调用 component 的 setState 方法的时候, React 将其标记为 dirty.到每一个事件循环结束, React 检查所有标记 dirty 的 component 重新绘制.
选择性子树渲染。开发人员可以重写 shouldComponentUpdate 提高 diff 的性能。

#### 为什么建议传递给 setState 的参数是一个 callback 而不是一个对象？

因为 this.props 和 this.state 的更新可能是异步的，不能依赖它们的值去计算下一个 state

#### 除了在构造函数中绑定 this，还有其它方式吗？

你可以使用属性初始值设定项(property initializers)来正确绑定回调，create-react-app 也是默认支持的。
在回调中你可以使用箭头函数，但问题是每次组件渲染时都会创建一个新的回调。

#### setState第二个参数的作用?

因为setState是一个异步的过程，所以说执行完setState之后不能立刻更改state里面的值。如果需要对state数据更改监听，setState提供第二个参数，就是用来监听state里面数据的更改，当数据更改完成，调用回调函数。

#### (在构造函数中)调用 super(props) 的目的是什么?

在 super() 被调用之前，子类是不能使用 this 的，在 ES2015 中，子类必须在 constructor 中调用 super()。
传递 props 给 super() 的原因则是便于(在子类中)能在 constructor 访问 this.props。

#### 在 React 当中 Element 和 Component 有何区别？

React Element 是描述屏幕上所见内容的数据结构，是对于 UI 的对象表述。
典型的 React Element 就是利用 JSX 构建的声明式代码片然后被转化为 createElement 的调用组合。

React Component 是一个函数或一个类，可以接收参数输入，并且返回某个 React Element

#### (组件的)状态(state)和属性(props)之间有何不同?

State 是一种数据结构，用于组件挂载时所需数据的默认值。State 可能会随着时间的推移而发生突变，但多数时候是作为用户事件行为的结果。
Props(properties 的简写)则是组件的配置。props 由父组件传递给子组件，并且就子组件而言，props 是不可变的(immutable)。组件不能改变自身的 props，但是可以把其子组件的 props 放在一起(统一管理)。Props 也不仅仅是数据–回调函数也可以通过 props 传递。

#### 受控组件和非受控组件区别?

受控组件：
1.没有维持自己的状态
2.数据由父组件控制
3.通过 props 获取当前值，然后通过回调通知更改

非受控组件：
1、保持着自己的状态
2、数据由 DOM 控制
3、Refs 用于获取其当前值

### TS

#### TS的优势？

它可以做类型检查，在ts中允许你为变量指定类型。
语法提升
重构

#### TS的缺点？

有一定学习成本，需要理解接口、泛型、类、枚举等前端开发可能不是很熟悉的知识点

#### TS中的接口？

接口就是一个规范或者约束，让我们的对象都去遵循它

#### 什么是TS？

TS就像是法律它是针对任何人的，我们在做某一件事时就要遵循相关的约束

#### 泛型?

泛型就是在定义函数或者接口的时候，不预先指定具体类型，而在使用的时候再指定类型的一种特性。

### babel(转码工具/解析器)7.X版本

@babel/cli:命令
@babel/core:核心库
@babel/preset-env:转码es6-->es5
@babel/polyfill:垫片 低端浏览器IE8 IE7
@babel/runtime:运行时
@babel/plugin-transfrom-runtime:优化class

### webpack

#### 怎么处理客户端缓存更新问题？

可以在webpack.base.js文件的output出口里，有个filename属性在文件名字的后面加上hash值就行

#### webpack打包一般分为几个文件？

3个文件 webpack.base.js(公共)webpack.dev.js(开发环境)webpack.prod.js(线上环境)分为这3个

#### 线上和线下的地址有什么不同？

线上的不需要加/api     开发环境需要加上/api

#### 线上测试还是线下测试？

主要区分要看地址是什么127.0.0.1:3000 是上下测试  192.168.1.123也是线下测试
远程地址或者域名就是线上测试  118.89.234.135

### koa 

#### koa和express最大的区别

就是koa有洋葱圈模式和async、await   koa执行完还可以再掉头回去
koa是express原版人马打造的，可以说是express的精装版

#### 粘性定位？

#### vue封装组件的方式有几种？

全局组件 局部组件 插件式组件

#### elementUI 表格数据过大，造成卡顿怎么办？

自己封装虚拟渲染配合和一个插件

#### 浏览器事件循环？

js的运行机制是单线程的，它是先执行同步的也就是宏任务，依次执行完毕后，进入另一个子线程就是异步，而异步又分宏任务和微任务
这里先执行微任务然后进行gui渲染，然后再执行宏任务，在这个宏任务里它又会区分哪些是同步或异步，所以就相当于又回到最初
开始的时候，这种循环就是事件循环

#### 你项目里做过的亮点或者你在项目里遇到的问题？

对elementUI的二次封装，就是在引入elementUI里的tabel表格，数据条数超过成千上万的时候，我们在使用的时候会因为数据庞大出现卡顿的现象，我采用了比较成熟的一种方案，就是利用clusteriza插件配合elementUI解决这个问题。就是把这个插件通过cdn的方式引入到vue的index.html中，然后再组件的monted生命周期里面进行对tabel进行配置就可以实现卡顿的效果，而且效果非常好。

#### proxy代理在打包上线之后出现问题你是怎么解决的？

这个是因为开发环境的变化造成的问题，我们开发时可以在webpack的devServer里面使用historyApiFallback:true这个方法来解决。而打包后可以在后端进行一个重定向到index.html页面，也可以用另一种方式（nlinc）来解决。

#### 按钮级别权限？

#### 大厂的路由模块化？

#### 利用render函数代替v-if v-else v-else-if这些low爆代码

#### 二次封装elementUI tabel组件

#### css3的新特性？

过渡 动画 伪类 语义化标签 弹性布局 盒模型定义 渐变 媒体查询 阴影 选择器等

#### 如果让你自己写一个去重的方法你会怎么写？不用人家封装的

#### H5 的新特性  socked 用过吗

严格的来说，socket并不是一种协议，只是一组接口api，能让程序员更方便的使用TCP/IP协议。简单地说我们可以使用socket套接字来建立起一种TCP/IP协议族中协议的链接关系。(正常情况下后端是不可以向前端发请求的，有了socked就可以实现双向沟通，发送请求)

#### let和var const的区别

#### 说一下asyc、await 

#### 闭包里面用过asyc、await吗 ？遇到过什么问题吗？可以用到循环里面吗？

#### 讲讲vue的双向绑定？

#### 讲一下vuex

#### 你为什么用计算属性来拿数据？

因为计算属性它有一个缓存，就是在依赖没有发生变化的时候可以是使用上次计算的值。避免了每次渲染都要进行大量的计算。

#### 用过vuex里面分模块的那个吗 就是那个module

#### 对象的深浅拷贝怎么用的？

#### 写个冒泡排序

#### 项目中遇见的问题 让你印象最深的

#### 实现一个web 根据最新数据实现滚动显示最新的数据的功能

#### 封装过的全局组件有哪些

#### query和parmas 路由传参在获取的时候有什么不同？

#### 路由里返回的back和go(-1)有什么区别？

简单的说就是：go(-1):返回上一页，原页面表单中的内容会丢失；back():返回上一页，原页表表单中的内容会保留。

#### 用cdn 的方式引入echat，但是与本公司的服务器接不通 你要怎么办？

#### 重绘与回流

比如我们增删DOM节点，修改一个元素的宽高，页面布局发生变化，DOM树结构发生变化，那么肯定要重新构建DOM树，而DOM树与渲染树是紧密相连的，DOM树构建完，渲染树也会随之对页面进行再次渲染，这个过程就叫回流。

当你给一个元素更换颜色，这样的行为是不会影响页面布局的，DOM树不会变化，但颜色变了，渲染树得重新渲染页面，这就是重汇。

结合上面的解释，引起DOM树结构变化，页面布局变化的行为叫回流，且回流一定伴随重绘。

只是样式的变化，不会引起DOM树变化，页面布局变化的行为叫重绘，且重绘不一定会便随回流。

#### 手写节流防抖

#### 手写promise

#### 手写call bind apply

#### 手写发布订阅

#### 手写深浅拷贝

#### 封装一个ajax

#### 你怎么在其中一个module里面获取另外一个module的数据？

就是可以通过context解构出来一个rootState这个参数，利用它就可以获取别的modules的数据了。

#### 通过render函数来代替v-if这种一直判断的渲染，集中管理一个标签

首先利用父子传参把button的类型和内容传进来组件，然后用render(h)里面的回调函数，来创建一个元素，并且给他绑定不同个的class和内容。这样就形成了集中管理某一个元素，而不是多判断形成的，那样看着很low

#### 路由分模块（动态引入路由）

在模块里面把某个路由下面的所有的子路由都陪在在childen里，然后只需要把这个模块引入到index主路由中就行。首先在主路由中定义一个数组，然后再定义一个函数来动态引入，它接受的参数是require.context('./',false,/\.router.js/)这个方法，里面配置的是路由文件，然后再引入函数里面遍历这个对象，把它push到最初的数组里面，最后在把数组写在主文件通过解构的方式。这样就完成了路由的模块，避免在主文件里写好多的import来引路由

#### 打包上线之后出现首屏白屏问题怎么解决？

出现这个问题主要是主JS文件过大加载时间过长造成的，我可以利用插件来优化包的体积，排除一些包减小体积。也可以用seo服务端渲染的方式来解决，也可以使用一个障眼法骨架屏的效果。                          

#### 如何实现async和await的多并发

#### 什么是递归组件

#### 为什么vue只有一个根标签

#### 柯里化函数

就是保证每一个函数或者返回的函数参数只有一个。而偏函数就是它的参数是多个。他们其实都是高阶函数，因为函数中返回一个高阶函数

#### 怎么解决异步并发的问题？

计数法，有多少个计多少个。没有更高级的了，不管怎么着都是计数法。使用after函数计数，传连个参数一个是次数，一个是回调函数，然后再after里面进行操作，最后返回一个函数

#### sesion 和cookie 相对token来说不安全的地方？

#### 
自我介绍：您好，我叫刘猛，来自河北沧州，上家公司在石家庄，前端开发岗位，主要运用vue框架来写项目，写过维康的APP和维康的后台管理。有3年的开发经验，因为年前的疫情关系，另外觉得北京更有发展前景，技术更新也快，所以想来北京发展，正好看见贵公司招人，我觉得我能胜任前端岗位，所以今天来到这面试，也希望能顺利进入公司。
技术栈：

#### 怎么封装一个全局的弹窗 利用this.$load（）就能调用出来一个弹窗怎么写

#### 说一下购物车的实现逻辑

1.首先校验是否登录 ，离线的怎么把商品添加到缓存里面去
2.离线的数据怎么和线上的数据添加到一起
3.在添加购物车的时候有没有向后台发送什么数据，如果是想后端发送了，那么又发送了什么信息？商品id ，cookie ,
4.如果库存没有了 那还能加入购物车吗？
5.支付流程，跳到支付页面时，首先如果是支付宝的话，他要先引入支付宝的sdk,其次要向后台发送接口，然后向后台得到它的id，然后是商品的id，然后是有个私钥和公钥，之后要发送到支付宝的服务器（后台做），支付的时候它会返回一个支付页面，需要输入密码，现在这些过程都是提交到支付宝的服务器，支付宝会把最终的信息返回给自己公司的服务器，然后公司的服务器会把你的成功或者失败返回给客户端，这样一个订单就完成了

#### 使用elementUI里的tabel有没有遇到什么问题？

因为他没有实现虚拟渲染，当数据过于庞大的时候，会出来卡顿的现在，一直也没解决。我们可以对他进行一个二次封装，利用clusteriza对他进行优化，从而实现了不会卡顿的现象。

#### 怎么用css实现三角形？

#### 如果有人恶意刷你的前端接口，你怎么办？

首先可以经过token校验他是不是用户，然后再看看是不是浏览器访问的接口，然后我们可以在接口设置一个访问时间，让他间隔一段时间才能访问。

#### Promise .then()的运行机制是什么？

主要靠的就是一个发布订阅的模式
当代码逻辑有异步的时候，如果调用then的时候没有成功也没有失败，它是先保存成功和失败的回调，可以认为then是个订阅，resolve，reject是个发布，然后把成功和失败进行分类。在Promise里面分别有两个存放成功和失败的数组，在执行异步的时候把成功和失败分别push到各自的数组中，当我们调用的时候让数组的成功和失败循环调用就可以了。为了解决在执行时我们可以做一些其他的操作，我们可以用一个AOP切片编程，我们可以在push的时候，push一个函数在这个函数里面在执行成功失败。当我们调用成功和失败的时候，循环数组的每个函数并且执行就行了。

#### 为什么要拷贝？

如果是原始值的它只是拷贝的值。如果是对象的话，实际上是两个变量指向了同一个地址。

#### 浅拷贝

就是需要拷贝对象的一层的时候就是浅拷贝，可以用 for...in(es3写法)循环进行拷贝。
Object.keys(obj)返回源对象键名的数组(es6写法)
Object.values(obj)返回源对象键值的数组(es6写法)
Object.entries(obj)返回源对象键值对的数组(es6写法)

#### 什么是虚拟dom

用JS对象表示dom信息和结构，当状态变更的时候，重新渲染这个js的对象结构。这个对象被称为虚拟dom

#### 为什么用虚拟dom 

#### 当浏览器输入url都发生了什么？

首先解析url,去域名系统内匹配IP，如果是第二次的话，它会去浏览器的缓存里面找是否有这个url
然后当拿到IP 之后，浏览器和网站会建立链接（tcp三次握手）建立链接时是不会携带数据的，
三次握手之后，请求数据，渲染页面
渲染完页面他就会进行4次挥手，断开链接

#### https是什么？

他就是在http tcp协议又加了一层tsl或ssl安全层

#### 页面渲染又是什么？

它分别有一个dom树和css结构体。它两形成一个渲染树，通过计算布局信息，调动UI引擎模块来进行渲染

#### css加载会造成阻塞吗？

css结构体和dom树是并行解析的。它会不会阻塞dom的解析，但是它会阻塞dom的渲染，因为只有等到他们两者都解析完，
解析完才进行渲染。而且css会阻塞JS，所以我们会把css放在前面。

#### 前端要从哪些方面进行优化？

1.减少http请求(精灵图或雪碧图、css或js文件的合并、用css代替图片)
2.缩减文件大小(资源的压缩，webpack资源打包，GZip压缩(要配合后端))
3.CDN(大图加载、大文件、类库)
4.HTTP2()
5.vue相关的ssr服务端渲染、预渲染
6.懒加载，减少首屏加载量
7.减少回流，使用定位等，对于操作量比较大dom,用文档碎片去做(虚拟dom的原理)
8.缓存

#### html严格模式和怪异模式

有！doctype就是严格模式。否则就是怪异模式

#### 闭包的缺点

（1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，
在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。
（2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，
把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，
不要随便改变父函数内部变量的值。

#### 观察者模式和发布订阅区别？

观察者和被观察者有密切的关系 。而发布 订阅他两之间是没有关系的

#### JavaScript垃圾回收机制

Javascript中，如果一个对象不再被引用，那么这个对象就会被GC(garbage collection) 回收。如果两个对象互相引用，
而不再被第3者所引用，那么这两个互相引用的对象也 会被回收。垃圾回收不是时时的，因为其开销比较大，
所以垃圾回收器会按照固定的 时间间隔周期性的执行 
函数a被b引用，b又被a外的c引用，这就是为什么函数a执行后不会被回收的原因

#### 垃圾回收的两个方法：

标记清除法： 1.垃圾回收机制给存储在内存中的所有变量加上标记，然后去掉环境中的变量以及被 环境中变量所引用的变
量（闭包）。 2.操作1之后内存中仍存在标记的变量就是要删除的变量，垃圾回收机制将这些带有标 记的变量回收。

引用计数法： 1.垃圾回收机制给一个变量一个引用次数，当声明了一个变量并将一个引用类型赋值 给该变量的时候这个值的引
用次数就加1。 2.当该变量的值变成了另外一个值，则这个值得引用次数减1。 3.当这个值的引用次数变为0的时候，说明没有变
量在使用，垃圾回收机制会在运行的 时候清理掉引用次数为0的值占用的空间

#### 浅拷贝 vs 深拷贝

拷贝其实就是对象复制，为了解决对象复制是产生的引用类型问题
浅拷贝：利用迭代器，循环对象将对象中的所有可枚举属性复制到另一个对象上，但 是浅拷贝的有一个问题就是只是拷贝了对象
的一级，其他级还如果是引用类型的值的 话依旧解决不了
浅拷贝只是增加了一个指针，指向已存在对象的内存。
深拷贝：深拷贝解决了浅拷贝的问题，利用递归的形势便利对象的每一级，实现起来 较为复杂，得判断值是数组还是对象；
深拷贝是增加了一个指针，并新开辟了一块空 间，让指针指向这块新开辟的空 间

#### 介绍一下 async 和 await；

async 会将其后的函数（函数表达式或 Lambda）的返回值封装成一个 Promise 对 象，而 await 会等待这个 Promise 完成，
并将其 resolve 的结果返回出来。
async / await 是 ES7 的重要特性之一，也是目前社区里公认的优秀异步解决方案。 目前 async / await 在 IE edge 中
已经可以直接使用了，但是 chrome 和 Node.js 还 没有支持。幸运的是，babel 已经支持 async 的 transform 了，
所以我们使用的时候 引入 babel 就行。在开始之前我们需要引入以下的 package，preset-stage-3 里就 有我们需要
的 async/await 的编译文件。

#### 什么是跨域？(非同源策略请求)怎么解决？

1. JSONP:script img  link 这些标签不存在跨域的限制，jsonp就是利用这个向服务器发请求。它把本地的一个函数，作为
   回到函数传给服务器。服务器接到请求包括那个函数，然后准备json格式的数据，当做参数放进这个函数里返回给浏览器。
   相当于把浏览器的全局函数执行了一遍。jsonp需要得到后端的支持的。而且只能处理get请求。
2. cors跨域资源共享
   客户端正常发请求，服务端要通过中间件设置请求头，允许哪个源，哪个方式，是否携带cookie,还有一些请求头，来做处理
   如果写*号的话，他就不能携带cookie
3. proxy代理
   在webpack-devServer 配置proxy，让所有请求统一，发送后端的地址，然后设置changeorigin 为true。也就是devServer
   帮我们启动一个服务，来做中层的代理。devServer本身就是用node写的，也相当于用node写了一个中间件，也就是我们的请求
   先到node下，而node中间件里面帮我们实现了一个跨域请求，通过这个地址帮我们把数据拿到，拿到之后在返回给客户端
4. ngnix 服务器的代理(前端不需要配置，都是后端)
5. postMessage

#### 为什么操作虚拟dom不会对真实dom产生影响

虚拟dom是用js对象表示dom信息和结构，当状态变更的时候，重新渲染这个js的对象结构。真实dom是html里的dom元素
虚拟dom是在内存中体现的，而在操作时也是在内存中，还没有去渲染成真实dom,所以不会对真实的dom产生影响

#### 为什么虚拟dom更新到真实dom，和直接操作真实dom有什么区别？

将页面改变的内容应用到虚拟 DOM 上，而不是直接应用到 DOM 上。
变化被应用到虚拟 DOM 上时，虚拟 DOM 并不急着去渲染页面，而仅仅是调整虚拟 DOM 的内部状态，这样操作虚拟 DOM 的代价
就变得非常轻了。
在虚拟 DOM 收集到足够的改变时，再把这些变化一次性应用到真实的 DOM 上

#### 为什么会影响性能？

#### 都是最终到真实dom，为什么虚拟dom就是快呢？

虚拟dom是频繁更新的，最终结果反映到真实dom上。真实dom只做必要更新。并不是因为用虚拟dom就会快，主要是更新策略
优化的终点还是减少不必要的真实dom更新

#### 说一下同步和异步

同步:同步是指在主线程上排队的执行的任务，只有前一个任务执行完毕，才能继续下一个任务，按照代码的执行顺序依次执行
异步:

#### 如何计算rem？

calc饰扣换算：当前设备尺寸/设计图尺寸*100
js计算：根元素字体大小：设备宽度/设计图宽度如果是640的图（6.4）+‘px’

#### new vue 发生了什么？

它会创建一个空间，改变它的指向，然后vue的一些原型方法进行挂载，最后调用vue的挂载的函数。

#### jq的出现解决了什么问题？

提高开发效率（封装了很多dom操作）
帮我们做了很好的兼容性

#### jq的弊端是什么？为什么会逐渐淘汰？

1.本质还是操作dom。必然会带来性能的损耗，对性能不友好。引起重绘回流
2.没有帮我们做业务分层

#### vue1.0版本的好坏处？

vue1.0没有虚拟dom
好处：在少量的数据下更新的速度要比虚拟dom快，因为它是一对一的。
坏处：当大量的数据更新时，就相当于操作大量dom,违背了性能的问题。

#### vue 渲染过程？

首先它要编译模板，然后执行渲染函数，形成虚拟dom树进行计算，最后创建出真实的dom进行挂载

#### fetch和axios的区别？

fetch是h5新增的api它是链式调用的方式，可以一直.then()下去。第一次.then的时候它得到的是数据格式，我们需要res.json
给他转一下数据，第二步就可以拿到真实数据，如果出现错误的话，可以通过.catch。
axios它是基于xhlhttprequest，它的返回结果是promise,它的链式调用跟fetch是比较相似的。axios它既可以在浏览器内运行
又可以在node运行。
fetch是h5新增的有可能低版本的浏览器不太兼容。相当于从以前的列式请求变成了链式请求。这就不涉及到回调的问题。

#### express

它是基于node后台封装的一个框架，利用express可以快速搭建fixbal API简单的一个封装。它提供了很多中间件的机制。

#### 构建工具webpack ？

#### 说一下你的项目流程 你负责的地方？遇到的难题，还有亮点？

#### 主要是你在项目中的问题？

#### 设置一个空对象

null 不是空对象  它只是空引用  可以利用let obj=Object.create('null')创建一个真正的空对象

#### es6新特性

1.反引号模板字符串
2.let const
3.解构赋值
4.导入导出
5.promise
6.对象的方法 keys  values  entries

#### JS 组成的部分

1.ECMAscript 语法
2.bom 和浏览器进行交互
3.dom 操作文档

#### 技术亮点

1.我们当时有两种权限，一种是路由权限一个按钮级别的权限。根据这两种权限我们跟后台接口进行了一个沟通最终确定了一套
方案，当我们鉴权了之后我们会每次把携带的token传给后端，后端对token进行校验。当我们每次访问一个页面的时候都会进
行一个路由的拦截判断它有没有获取用户的角色，通过这个角色我们会动态的获取路由的配置文件，然后通过这个文件我们去动态的
加载，同时结合了仓库。

#### 难点 首页白屏的问题？

出现这个问题其实有很多的解决方案，我们采用了一个比较主流的一个方案。首先是效果上的我们使用了一个骨架屏然后让用户在这个
感官上有一个过渡。
第二个是从这个实际加载速度上，我们进行了一个质的提升，通过webpack的lanzy给他进行分析，分析完了发现有的包确实比较大
这个时候我们去把这个包发布到网络对象存储就是cdn,把它发布到cdn之后直接引入一个路径，打包的时候不打包这个文件。
第三就是我们把项目的模块该抽离的抽离，引用次数多的我们通过webpack4的新特性opnasition优化项给他进行一个chunk的处理
就是切片处理，在处理自己的包的时候我们会进行dl打包，进行一个动态链接给他抽离，抽离完之后我们会把动态链接库的文件放到
cdn上，这样让项目的加载速度提高很多。

#### 第三方登录的二维码？

比如现在做的是第三方登录的，需要引入微信的gssdk,采用微信登录，前端不需要做什么，只要请求接口就行。

#### 通过网页扫描二维码？  

如果使用原生的相机肯定是不太合适的，因为原生的相机它只是负责拍照。此时我们应该用自定义的vedio结合canvas进行
拍照的处理

#### 你和同事是怎么分工的？

我们做的电商是类似于购物的网站，这个网站当时我分了4个模块，第一个是产品列表页、第二个商品详情、第三个是个人中心页、
第四个是购物车页、最后还有这个付款详情页。其中一个模块有个会员和优惠券，我们会调用后端的接口。然后向后台传递了
用户的id 、token这些字段。请求了三个接口分别是探测针请求(目的是保证我的后台token鉴权这块能拿到。如果)
我主要负责了一个产品列表、详情、和购物车。然后再说一下每个模块的详细实现


#### map

返回一个对原数组有映射关系的数组

#### reduce 迭代器 累加器

#### 防抖节流 

防抖：通过setTimeout,在一定的时间间隔内，将多次触发变成一次触发
节流：在一段时间内执行一次  

说一下你们的项目流程：
我们是项目经理把原型图给我们，然后UI设计图纸来过来。然后配合着后端方面有接口文档啥的。然后我们开始对项目分模块
进行排版最后项目写完开始部署上线
说一下你在项目中都负责哪些？
当时我们有一个电商的APP，我们主要分了商品列表模块、商品详情模块、购物车模块、订单、付款、还要个用户模块。
我主要是负责了商品列表详情还有这个购物车。

#### alert

alert的输出结果都是字符串

#### 堆栈内存

栈内存：提供代码运行机制，存储基本类型机制
堆内存：提供引用类型存储的空间

#### 发布订阅

发布者和订阅者可以说他们之间是没有联系的，互不关心对方，他们关注的对象时事件本身
发布者通过事件调度中心提供的publish方法进行事件订阅操作，他并不关心有没有订阅者
订阅者通过事件调度中心提供的subscribe方法进行事件订阅的操作，它也并不关心有没有人发布事件，但是只要自己订阅的事件
发生变化，他就做出响应

#### 观察者模式

观察者Observer和目标对象Subject耦合度相对较高
观察者需要实现update方法，在目标对象通知更新时被调用
目标对象需要维护观察者列表，在自身状态改变时，通过notify方法遍历观察者列表，通知所有观察者

#### 你怎么理解vue和react的 数据单向流？

#### vue中对数组某一项单独赋值时页面不刷新遇到过吗？什么导致不刷新

#### keep-alive 两个页面都缓存了 从a页面到B页面，再回来时怎么改变a页面的状态？

#### 比如他两都缓存 从a页面到b页面，在回来他还会走生命周期吗？比如create？

#### Object.assgin()它做了什么？

用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象
如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性。

#### webpack里的soesWeper。配置它？

他就是开发环境时，配置它就可以看见源码

#### hash和chunkHash有什么区别？

#### webpack打包会生成的文件它是怎么加载的？路由把代码分割了，它是怎么去到那个路由加载js这块了解吗？

#### 工作中遇到的大问题？怎么解决的？说下思路和想法。

比如说我们在打包上线完，发现有很多图标出不来了包括elementUI的图标，我们就通过webpack的fileloder给他处理下利用
svg.loader

#### 你做的webpack哪些优化？

1.效果方面：使用骨架屏
2.webpack的动态链接库：把一些包抽离出来，把新的文件放到cdn的里面，这样放在本地的代码量就最小化了，实现加载速度变快。
3.webpack4的一个新特性一个优化项也是拆分包。比如node-modules里面包不止使用一次，他在很多页面都有使用，这样他的打包体积就会非常的大。就用这个新特性optimization(奥泼耐贼神)配置优化项。引用次数超过2次的我们可以给他单独分成JS文件
这样在打包的过程中他就不会每个页面都打包 
4.配置动态链接库：主要使用webpack.DllPlugin 和webpack.DllReferencePlugin这两配置项。一般我们在webpack配置文件分三个，分别是base、dev、prodciton。首先新建一个文件，比如要抽离vue相关的生态，然后配置命令运行它，它会生成一个文件manifest.json 这个文件会描述抽离的包的依赖关系。然后再生产环境包配置配置json,这样在打包的时候他就不会打包manifest.json这个包里的依赖关系了。
5.抽离css文件，通过mini-css-extract-plugin。这个不是webpack自带的，所以要安装一下。在base文件引入，然后替换里面的style.loder。这样抽离完我们就可以把它们放进cdn里面，这样他就会分开加载，这样也就形成一个异步的加载环境。

#### 你怎么把你的优化webpack这块做成通用的解决方案？做成组件什么的，就是能方便多人使用（个人理解封装）

其实当时我们封装的那些就完全可以说是个方案了。就差利用cli方式给它发成一包让别人来使用

#### 你觉得你通过技术能对团队帮上忙的？或者能为团队做的一些事情？

#### webpack?

我们当时是自己手搭的一个webpack,没用框架自带的，主要是考虑到一些自定义的优化和多页面。在打包的时候希望它能有个加速
不让他在上线的时候有速度的问题。我们采用的dllplugin结合cdn给他加速

#### BFC

BFC
一个块格式化上下文（block formatting context）是Web页面的可视化CSS渲染的一部分。它是块盒子的布局发生，浮动互相交互的区域。
具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性。

通俗一点来讲，可以把 BFC 理解为一个封闭的大箱子，箱子内部的元素无论如何翻江倒海，都不会影响到外部。

触发 BFC：

body 根元素
浮动元素：float 除 none 以外的值
绝对定位元素：position (absolute、fixed)
display 为 inline-block、table-cells、flex
overflow 除了 visible 以外的值 (hidden、auto、scroll)
注意根元素就创建了个BFC

那么BFC 又有以下特点：

内部块级盒子垂直方向排列
盒子垂直距离由margin 决定，同一个BFC 盒子的外边距会重叠
BFC 就是一个隔离的容器，内部子元素不会影响到外部元素
BFC 的区域不会与float box叠加
每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。
BFC 的用途：

清楚浮动
解决外边距合并
布局

### 被问的面试题：

#### http从输入网址到用户能看到页面的过程？

域名解析：浏览器获得URL地址，向操作系统请求该URL对应的IP地址，操作系用查询DNS(域名系统) 首先查询本地HOST文件，没有则查询网络获得对应的IP地址
(解释：把URL分割成几个部分：协议，网络地址，资源路径。其中协议是指该计算机获取资源的方式，常见的是HTTP,FTP;网络地址可以是域名或者IP地址，也可以包括端口号，如果不注明端口号，默认是80端口。)
确认好了IP和端口号，则可以向该IP地址对应的服务器发起TCP连接
服务器接收到TCP连接请求后，回复可以连接请求
浏览器收到回传的数据后，还会向服务器发送数据包，表示三次握手完成
握手成功后，开始通讯，根据HTTP协议的要求，组织一个请求的数据包，里边包含请求的资源路径，你的身份信息等，例如：www.abc.com/images///表示的资源路径是images/// 发送后，服务器响应请求，将数据返回给浏览器，数据可以是根据html协议组织的网页，（里边包含页面的布局，文字等等，也可以是图片或者脚本程序等）如果资源路径指定的资源不存在，服务器就会返回404错误。如果返回的是一个页面，则根据页面里的一些外链URL地址，重复解析URL
渲染页面，并开始响应用户的操作

#### JS的事件循环？

#### ES6性特性的去重？

new set()

#### 给对象解构时，给他了一个默认值。默认值啥时候生效？

```
const {a = 123} = {a:null,b:345}

```

#### 实现一个异步编程？除了promise

#### js中同步、异步

js的同步和异步问题通常是指ajax的回调，如果是同步调用，程序在发出ajax调用后就会暂停，直到远程服务器产生回应后才会继续运行。而如果是异步调用，程序发出ajax调用后不会暂停，而是立即执行后面的代码，服务器返回信息后会自动触发回调函数进行处理。相比较而言，异步调用的性能最佳，程序不会出现卡顿的现象，而同步调用则通常用于需要立即获得结果并实时处理的情况。

#### 有3个接口前两个接口是第三个接口的参数，怎么实现？

#### promise和async、await 有什么区别？

Promise 有三个状态 pending（执行中）、success（成功）、rejected（失败）
错误捕获：
Promise.prototype.catch用于指定Promise状态变为rejected时的回调函数，可以认为是.then的简写形势，返回值跟.then一样
async await
async用于申明一个function是异步的，而await可以认为是async wait的简写，等待一个异步方法执行完成。
规则：
1 async和await是配对使用的，await存在于async的内部。否则会报错
2 await表示在这里等待一个promise返回，再接下来执行
3 await后面跟着的应该是一个promise对象，（也可以不是，如果不是接下来也没什么意义了…）
错误捕获:
如果是reject状态，可以用try-catch捕捉

区别：
promise是ES6，async/await是ES7
2 async/await相对于promise来讲，写法更加优雅
3 reject状态：
    1）promise错误可以通过catch来捕捉，建议尾部捕获错误，
    2）async/await既可以用.then又可以用try-catch捕捉

#### 暂时性死区是什么？

暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

#### 浏览器的同源策略是?

同源策略，是浏览器对javascript施加的安全限制。所谓同源是指，域名，协议，端口均相同。

#### 怎么解决跨域的？

#### 反向代理是谁配的？生产环境可以吗？

#### css 盒模型

标准盒模型：内容+padding+margin+border
IE盒模型:内容包含padding+border

#### 做过移动端自适应页面吗？

#### rem和em的区别？

px:px这个单位用的非常多，我们大多数人都很熟悉了吧。px单位的名称为像素，它是一个固定大小的单元。对手机之类的设备不太友好，做不到自适应的效果。
em：单位的名称为相对长度单位，它是用来设置文本的字体 尺寸的，它是相对于当前对象内文本的字体尺寸；一般浏览器默认1em=16px，通过设置font-size大小来代表如：16px*0.625=10px，其则代表1em=10px，直接上代码(注释的样式为浏览器默认 （1em=16px）的长宽) 

em是相对于父级元素的单位，会随父级元素的属性（font-size或其它属性）变化而变化

rem（css3新增的相对长度单位）
rem是css3新增的一个相对长度单位，它的出现是为了解决em的缺点，em可以说是相对于父级元素的字体大小，当父级元素字体大小改变时，又得重新计算。rem出现就可以解决这样的问题，rem只相对于根目录，即HTML元素。所以只要在html标签上设置字体大小，文档中的字体大小都会以此为参照标准，一般用于自适应布局。

rem是相对于根目录（HTML元素）的，所有它会随HTML元素的属性（font-size）变化而变化

#### webpack三个hash值得区别？

#### hash和chunkHash的区别？

#### 前端做过的性能优化？

#### 一个项目的开发流程？

#### 深浅拷贝？

#### flex值设为1是什么意思？

首先flex是flex-grow flex-shrink flex-basis的缩写。如果设为1的话，那就相当于：

```
.item{
   flex-grow:1;
   flex-shrink:1;
   flex-basis:0%;
}
```

#### margin：auto 属性是什么意思？margin:left auto;会怎么样

#### es6数组新增的方法？

#### forEach和map输出有什么区别？能输出中断吗？

forEach(): 针对每一个元素执行提供的函数,除了抛出异常以外，没有办法中止或跳出 forEach() 循环
map():创建一个新的数组，其中每一个元素由调用数组中的每一个元素执行提供的函数得来,map 方法会给原数组中的每个元素都按顺序调用一次 callback 函数。callback 每次执行后的返回值（包括 undefined）组合起来形成一个新数组。 callback 函数只会在有值的索引上被调用；那些从来没被赋过值或者使用 delete 删除的索引则不会被调用
共同点：
都是循环遍历数组中的每一项
每一次执行匿名函数都支持三个参数，数组中的当前项item，当前项的索引index，原始数组input
匿名函数中的this都是指window
只能遍历数组
差异点：
map有返回值，可以return出来一个length和原数组一致的数组
map()方法会分配内存空间存储新数组并返回。
没有返回值，返回结果为undefined
forEach没有返回值，返回结果为undefined
forEach()方法不会返回执行结果，而是undefined。也就是说，forEach()会修改原来的数组。

#### 哪个循环方法能中断循环？

breack  continir

#### JS有哪些异步事件？

回调函数 定时器 AJAX dom事件 promise 

#### promise和setTimeout都能做异步事件，他们有什么区别？

#### JS的宏任务和微任务？

#### JS怎么处理宏任务和微任务？

#### 代码管理用什么？

gitHUB

#### 讲几个git常用的命令？

git init 本地创建仓库
git clone '远程仓库地址' 克隆仓库
git add.
git commit -m 'XXX'
git push origin dev

git reflog提交记录
git pull origin dev
git branch 查看分支
git checkout -b index 创建分支
git checkout 分支名   切换分支
git merge   合并分支

#### vue用哪个版本的？

#### 整个项目结构是怎么初始化的？

#### cli用的是哪个版本？

#### proxy相比vue2的监听有什么好处？

#### vue2不能监听数组是怎么处理的？

#### 计算属性和watch的区别？

#### 组件内，最早能在那个生命周期访问到this.data属性

#### 在子组件调用父组件的方法？dd

#### 导航守卫的next和await的next有什么关系？

#### ajax中get和post的区别？


#### 请描述一下cookies，sessionStorage和localStorage的区别？

sessionStorage用于本地存储一个会话(session)中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁。因此sessionStorage不是一种持久化的本地存储，仅仅是会话级别的存储。而localStorage用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。

web storage和cookie的区别

Web Storage的概念和cookie相似，区别是它是为了更大容量存储设计的。Cookie的大小是受限的，并且每次你请求一个新的页面的时候Cookie都会被发送过去，这样无形中浪费了带宽，另外cookie还需要指定作用域，不可以跨域调用。

除此之外，Web Storage拥有setItem,getItem,removeItem,clear等方法，不像cookie需要前端开发者自己封装setCookie，getCookie。但是Cookie也是不可以或缺的：Cookie的作用是与服务器进行交互，作为HTTP规范的一部分而存在 ，而Web Storage仅仅是为了在本地“存储”数据而生。

#### 什么叫优雅降级和渐进增强?

渐进增强 progressive enhancement：
针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。
优雅降级 graceful degradation：
一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。
区别：
a. 优雅降级是从复杂的现状开始，并试图减少用户体验的供给

b. 渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要

c. 降级(功能衰减)意味着往回看;而渐进增强则意味着朝前看，同时保证其根基处于安全地带

#### webpack 实现多页面打包？

我们可以通过webpack.config里面的入口文件的值给他换成对象的形式，让他拥有多个JS文件。然后再需要配置html文件，改一下它的输出文件名[name]-boundle.js，最主要的是chunk每个html文件都需要配置一个chunk里面写的是JS文件在入口的键名。这样也就可以分开开发了。

#### http解析还有一个lns查找过程，当我们知道这个过程，其实还是可以做一些优化的。

#### 其实我们在真实项目中用到的webpack做proxy代理不是很多，因为我们前端基本就是一个静态页面，后端来做这个跨域方式，不管在什么地方是都能请求到的。如果说用到proxy做代理的话，那就说明我们要在前端单独启动一个node服务来做这个反向代理，其实这样上线相对于服务器来说是不健康的。

#### 高并发

可以理解为就是我点击一下，它可以把所有的请求都完成。但是在前端可能我点击一下它是一条一条来执行的。这种情况就要使用高并发的机制来处理

#### vue 服务端渲染

1.它是使用了一个vue-serve-render 模块

#### ecmascript和script

前者是对JS 的一种规范，而后者是对前者的实现

#### axios的理解使用

Axios 是一个基于 Promise 的 HTTP 客户端，拥有以下特性：

支持 Promise API；
能够拦截请求和响应；
能够转换请求和响应数据；
客户端支持防御 CSRF 攻击；
同时支持浏览器和 Node.js 环境；
能够取消请求及自动转换 JSON 数据。

拦截器简介
对于大多数 SPA 应用程序来说， 通常会使用 token 进行用户的身份认证。这就要求在认证通过后，我们需要在每个请求上都携带认证信息。针对这个需求，为了避免为每个请求单独处理，我们可以通过封装统一的 request 函数来为每个请求统一添加 token 信息。

但后期如果需要为某些 GET 请求设置缓存时间或者控制某些请求的调用频率的话，我们就需要不断修改 request 函数来扩展对应的功能。此时，如果在考虑对响应进行统一处理的话，我们的 request 函数将变得越来越庞大，也越来越难维护。那么对于这个问题，该如何解决呢？Axios 为我们提供了解决方案 —— 拦截器。

请求拦截器：该类拦截器的作用是在请求发送前统一执行某些操作，比如在请求头中添加 token 字段。
响应拦截器：该类拦截器的作用是在接收到服务器响应后统一执行某些操作，比如发现响应状态码为 401 时，自动跳转到登录页。
在 Axios 中设置拦截器很简单，通过 axios.interceptors.request 和 axios.interceptors.response 对象提供的 use 方法，就可以分别设置请求拦截器和响应拦截器：
（interceptors.request.use）

（axios.interceptors.response.use）

#### typeOf 和 instanceof的区别？

typeof判断所有变量的类型，返回值有number，boolean，string，function，object，undefined。
typeof对于丰富的对象实例，只能返回"Object"字符串。
instanceof用来判断对象，代码形式为obj1 instanceof obj2（obj1是否是obj2的实例），obj2必须为对象，否则会报错！其返回值为布尔值。
instanceof可以对不同的对象实例进行判断，判断方法是根据对象的原型链依次向下查询，如果obj2的原型属性存在obj1的原型链上，（obj1 instanceof obj2）值为true。

#### sourceMap是什么？

它需要在webpack里面进行配置。sourceMap就是一个文件，里面储存着位置信息。

仔细点说，这个文件里保存的，是转换后代码的位置，和对应的转换前的位置。

有了它，出错的时候，通过断点工具可以直接显示原始代码，而不是转换后的代码。

#### url解析的时候再解析静态资源的时候可以做的一些优化指的是什么？

#### 跨域到底指的是什么？

#### 反向代理和正向代理？

#### 说说node.

#### 闭包的使用场景

防抖节流

#### promise.all假如其中一个reject了，我还想让其他继续执行怎么解决

只需要再外面再包一层Promise就行了，不管内部的Promise是resolved或者rejected了，外层的Promise都resolve就可以了。这样，Promise.all接收到的，永远都是resolved的Promise。两层的Promise看起来有些别扭，为了代码写起来稍微好看一点，我们用await和try..catch来处理。

Promise.allSettled()方法返回一个在所有给定的promise已被resolve或被reject后的promise，并带有一个对象数组，每个对象表示对应的promise结果

#### fetch 和ajax哪个可以做请求的丢弃？假如过了30秒来丢弃？

对于原生XHR对象来说，取消的ajax的关键是调用XHR对象的.abort()方法
如果我们经常使用vue等框架的话，就会使用axios发送ajax请求。在axios中取消ajax请求不同于上面两种形式，在axios中是通过axios.CancelToken.source()方法取消请求

#### axios可以做请求的丢弃吗？

如果我们经常使用vue等框架的话，就会使用axios发送ajax请求。在axios中取消ajax请求不同于上面两种形式，在axios中是通过axios.CancelToken.source()方法取消请求
但如果我们有多个通过axios发送的ajax请求，需要精准的取消掉指定的请求应该这么做呢？在上面的代码中有注释“cancelToken的值起标识作用，标识由source控制的、将要被取消的ajax操作”，下面的栗子会更加清楚的展示cancelToken的作用

#### promise.race用过吗？r

用过,其参数是一个数组，他的then的参数是第一次请求成功的参数，一旦请求成功，对接下来的不会进行检测。

#### webWorker项目中用到过吗？

通过使用Web Worker， 我们可以在浏览器后台运行Javascript， 而不占用浏览器自身线程。Web Worker可以提高应用的总体性能，并且提升用户体验。
Web Worker可以在后台执行脚本，而不会阻塞页面交互。Worker对象分为两种：专用式Web Worker和共享式Web Worker：专用式的Web Worker只能被当个页面使用，而共享式的Web Worker可以在被多个页面使用。另外，本文还介绍了Web Worker的错误处理机制，以及使用Ajax与服务端交互。

#### serviceWorker是什么？

作为一个比较新的技术，大家可以把 Service Worker 理解为一个介于客户端和服务器之间的一个代理服务器。在 Service Worker 中我们可以做很多事情，比如拦截客户端的请求、向客户端发送消息、向服务器发起请求等等，其中最重要的作用之一就是离线资源缓存。
对于 Service Worker ，了解过 Web Worker 的同学可能会比较好理解。它和 Web Worker 相比，有相同的点，也有不同的地方。
相同：

Service Worker 工作在 worker context 中，是没有访问 DOM 的权限的，所以我们无法在 Service Worker 中获取 DOM 节点，也无法在其中操作 DOM 元素；
我们可以通过 postMessage 接口把数据传递给其他 JS 文件；
Service Worker 中运行的代码不会被阻塞，也不会阻塞其他页面的 JS 文件中的代码；

不同的地方在于，Service Worker 是一个浏览器中的进程而不是浏览器内核下的线程，因此它在被注册安装之后，能够被在多个页面中使用，也不会因为页面的关闭而被销毁。因此，Service Worker 很适合被用与多个页面需要使用的复杂数据的计算——购买一次，全家“收益”。
如果想使用首先要进行安装

#### 是通过ide还是手敲命令行做这个和代码的管理？

#### merge和redce这些？

#### git rebase 是什么？

git merge 操作合并分支会让两个分支的每一次提交都按照提交时间（并不是push时间）排序，并且会将两个分支的最新一次commit点进行合并成一个新的commit，最终的分支树呈现非整条线性直线的形式

git rebase操作实际上是将当前执行rebase分支的所有基于原分支提交点之后的commit打散成一个一个的patch，并重新生成一个新的commit hash值，再次基于原分支目前最新的commit点上进行提交，并不根据两个分支上实际的每次提交的时间点排序，rebase完成后，切到基分支进行合并另一个分支时也不会生成一个新的commit点，可以保持整个分支树的完美线性

另外值得一提的是，当我们开发一个功能时，可能会在本地有无数次commit，而你实际上在你的master分支上只想显示每一个功能测试完成后的一次完整提交记录就好了，其他的提交记录并不想将来全部保留在你的master分支上，那么rebase将会是一个好的选择，他可以在rebase时将本地多次的commit合并成一个commit，还可以修改commit的描述等

如果你想要你的分支树呈现简洁，不罗嗦，线性的commit记录，那就采用rebase

否则，就用merge吧

#### 开发中git有几个分支

#### 你们怎么不用git flow这种流程

#### 你们在代码的提交的时候有没有做一些 强约束或者代码风格的约束或者人工的remil这种流程有吗？

#### eslint他能约束css吗？

可以的，但是需要在配置项里面进行配置，让他可以约束css代码规范

#### vue中没有css文件所有的样式写在js里面？你可以看一下css in JS

#### vue-cli 3 和 vue-cli 2的区别

2.0启动npm run dev
3.0启动npm run serve
原来放在static下的文件，放在了public文件夹下
build文件config文件都没了，脚手架3.0安装项目时会自动下载node-model。

#### vue中的use是干什么的？

在开发中，有时候我们需要给vue注入自己的插件。如果每引入一个组件，再注册一下，明显加大了开发的工作量，所以我们需要让每一个vue都具备这个插件功能因此我们首选vue.use这个vue的API

#### vue中某个组件的逻辑需要多个组件都能使用你怎么解决？

#### eslint

确保你的电脑安装了 node 和 npm 环境
提供编码规范；
提供自动检验代码的程序，并打印检验结果：告诉你哪一个文件哪一行代码不符合哪一条编码规范，方便你去修改