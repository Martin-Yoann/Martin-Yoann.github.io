---
title: HTML-CSS基础
date: 2018-3-1 12:00:00
categories: 
    - web前端开发
    - Html
    - Css
tags: 
    - Html
    - Css
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=504265014.mp3
cover: https://img2.baidu.com/it/u=3429416796,2324999190&fm=26&fmt=auto&gp=0.jpg
---
## 一、css和html 部分

### 一、css

#### 1、css 盒模型

    css盒模型分为标准盒模型和怪异盒模型/IE盒模型
    基础盒模型：content(内容) + border + padding + margin
    怪异盒模型/IE盒模型：content (content + border + padding) + margin
    正常情况下padding和border的设置会影响元素宽高的计算
    box-sizing: content-box (称为标准盒模型)     width = 元素内容的宽度
    box-sizing: border-box (称为怪异盒模型/IE盒模型)    width = 元素内容的宽度 + padding + border

#### 2、box-sizing常用的属性有哪些？分别有什么作用？

    box-sizing: content-box|border-box|inherit;
    content-box:宽度和高度分别应用到元素的内容框。
    border-box:通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度。

#### 3、清除浮动的方式有哪些

    （1）父级div定义height。
    （2）结尾处加空div标签clear:both。如：.clear {clear:both }
    （3）父级div定义伪类:after和zoom。 如： .clearfix:before,.clearfix:after { content: ''; display: table; }  .clearfix:after { clear: both }  .clearfix { *zoom: 1; /*此处是为ie6、7处理的方式 */}
    （4）父级div定义overflow:hidden。
    （5）父级div定义overflow:auto。
    （6）父级div也浮动，需要定义宽度。
    （7）父级div定义display:table。
    （8）结尾处加br标签clear:both。

#### 4、说下行内元素和块级元素的区别？行内块元素的兼容性使用？（IE8 以下）

行内元素：会在水平方向排列，不能包含块级元素，设置width无效，height无效(可以设置line-height)，margin上下无效，padding上下无效。
（行内元素 : span,a,label,input,img,strong,em;）

块级元素：各占据一行，垂直方向排列。从新行开始结束接着一个断行。（块级元素：div,p,h1,form,ul,li;）
兼容性：display:inline-block;*display:inline;*zoom:1;

#### 5、css 选择器有哪些

    id选择器（#id）
    类选择器（.class）
    标签选择器（div、p、li）
    子代选择器（ul>li）
    后代选择器（ul li）
    通配符选择器（*）
    属性选择器（input[type="text"]、p[class]）
    伪类选择器（li:first-child、li:nth-child(n)）
    相邻兄弟选择器（div+p）
    通用兄弟选择器（div~p）
    群组选择器（div,span,li,p）
    相同权重下：内联样式（标签内部） > 嵌入样式（当前文件style） > 外部样式（外部文件）

> 可以继承的属性：

    可继承的样式： font-size font-family color, UL LI DL DD DT;
    不可继承的样式：border padding margin width height ;
    
    优先级：!important > id > class > tag
    important 比 内联优先级高,但内联比 id 要高

#### 6、内容水平垂直居中有哪些方法

    文本居中：text-align:center; height:100px; line-height:100px;
    
    已知宽高：如width:20px;height:20px 
    
    父级position:relative 内容position:absolute; left: 50%; top: 50%; margin-left:-10px; margin-top: -10px;
    
    不知宽高：
    
    父级position:relative 内容position:absolute; left: 50%; top: 50%; transform: translate(-50%, -50%)
    
    父级display:flex; align-items: center; justify-content: center; (css3属性)
    
    父级display:table; 子级 display: table-cell; vertical-align: middle;

#### 7、display: none 和 visibility: hidden 有什么区别

display: none 隐藏 不占空间 （回流 + 重绘）
visibility: hidden 隐藏 保留原有空间 （重绘）

#### 8.回流与重绘

##### 一、什么是回流?

    当我们对 DOM 的修改引发了 DOM 几何尺寸的变化（比如修改元素的宽、高或隐藏元素等）时，浏览器需要重新计算元素的几何属性（其他元素的几何属性和位置也会因此受到影响），
    然后再将计算的结果绘制出来。这个过程就是回流（也叫重排）。每个页面都至少发生一次回流，也就是页面第一次加载的时候。

##### 二、什么是重绘?

    当我们对 DOM 的修改导致了样式的变化、却并未影响其几何属性（比如修改了颜色或背景色）时，
    浏览器不需重新计算元素的几何属性、直接为该元素绘制新的样式（跳过了上图所示的回流环节）。这个过程叫做重绘。

##### 三、两者的区别?

他们的区别很大：
回流必将引起重绘，而重绘不一定会引起回流。比如：只有颜色改变的时候就只会发生重绘而不会引起回流
当页面布局和几何属性改变时就需要回流
比如：添加或者删除可见的DOM元素，元素位置改变，元素尺寸改变——边距、填充、边框、宽度和高度，内容改变

##### 四、什么时候会发生回流？

1、添加或者删除可见的DOM元素的时候
2、元素的位置发生改变
3、元素尺寸改变
4、内容改变
5、页面第一次渲染的时候

##### 五、如何减少回流和重绘？

1. 使用 transform 替代 top
2. 使用 visibility 替换 display: none。因为前者只会引起重绘，后者会引发回流（改变了布局）
3. 不要把节点的属性值放在一个循环里当成循环里的变量
4. 不要使用 table 布局，可能很小的一个小改动会造成整个 table 的重新布局
5. 动画实现的速度的选择，动画速度越快，回流次数越多，也可以选择使用requestAnimationFrame
6. CSS 选择符从右往左匹配查找，避免节点层级过多

#### 9、BFC（Block Formatting Context） 是什么？应用？ 

BFC 就是 块级格式上下文 的格式，创建了BFC的元素就是一个独立的盒子，不过只有BLock-level box可以参与创建BFC，它规定了内部的Bloc-level Box 如何布局，并且与这个独立盒子里的布局不受外部影响，当然它也不会影响到外面的元素。 
应用场景： 
    解决margin叠加的问题 
    用于布局（overflow: hidden）,BFC不会与浮动盒子叠加。 
    用于清除浮动，计算BFC高度

#### 10、列出display的值,说明他们的作用。position的值,relative和absolute分别是相对于谁进行定位的?

    block 象块类型元素一样显示。
    inline 缺省值。象行内元素类型一样显示。
    inline-block 象行内元素一样显示，但其内容象块类型元素一样显示。
    list-item 象块类型元素一样显示，并添加样式列表标记。
    
    absolute 
        生成绝对定位的元素，相对于 static 定位以外的第一个祖先元素进行定位。 
    fixed （老IE不支持）
        生成绝对定位的元素，相对于浏览器窗口进行定位。 
    relative 
        生成相对定位的元素，相对于其在普通流中的位置进行定位。 
     static  默认值。没有定位，元素出现在正常的流中
    （忽略 top, bottom, left, right z-index 声明）。
     inherit 规定从父元素继承 position 属性的值。

#### 11、CSS3新特性有哪些？

    1.颜色：新增RGBA，HSLA模式
    2.文字阴影（text-shadow、）
    3.边框： 圆角（border-radius）边框阴影： box-shadow
    4.盒子模型：box-sizing
    5.背景：background-size 设置背景图片的尺寸background-origin 设置背景图片的原点background-clip 设置背景图片的裁切区域，以”，”分隔可以设置多背景，用于自适应布局
    6.渐变：linear-gradient、radial-gradient
    7.过渡：transition，可实现动画
    8.自定义动画
    9.在CSS3中唯一引入的伪元素是 ：selection.
    10.媒体查询，多栏布局
    11.border-image
    12.2D转换：transform：translate(x，y) rotate(x，y) skew(x，y) scale(x，y)
    13.3D转换

#### 12、 css3新增的伪类

    p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
    p:last-of-type 选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
    p:only-of-type 选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
    p:only-child 选择属于其父元素的唯一子元素的每个 <p> 元素。 p:nth-child(2) 选择属于其父元素的第二个子元素的每个 <p> 元素。 :enabled、:disabled 控制表单控件的禁用状态。
    :checked，单选框或复选框被选中。html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？

#### 13、css3中单位px,em,rem,vh,vw,vmin,vmax的区别

px：绝对单位，页面按精确像素展示

em：相对单位，基准点为父节点字体的大小，如果自身定义了font-size按自身来计算（浏览器默认字体是16px），整个页面内1em不是一个固定的值。

rem：相对单位，可理解为”root em”, 相对根节点html的字体大小来计算，CSS3新加属性，chrome/firefox/IE9+支持。

vw：viewpoint width，视窗宽度，1vw等于视窗宽度的1%。
vh：viewpoint height，视窗高度，1vh等于视窗高度的1%。
vmin：vw和vh中较小的那个。
vmax：vw和vh中较大的那个。

vw, vh, vmin, vmax：IE9+局部支持，chrome/firefox/safari/opera支持，ios safari 8+支持，android browser4.4+支持，chrome for android39支持

viewport的概念

移动设备上的viewport就是设备的屏幕上能用来显示我们的网页的那一块区域.

就是浏览器上(也可能是一个app中的webview)用来显示网页的那部分区域，但viewport又不局限于浏览器可视区域的大小，它可能比浏览器的可视区域要大，也可能比浏览器的可视区域要小。

#### 14、CSS隐藏元素的几种方法(至少说出三种)

Opacity:元素本身依然占据它自己的位置并对网页的布局起作用。它也将响应用户交互;
Visibility:与 opacity 唯一不同的是它不会响应任何用户交互。此外，元素在读屏软件中也会被隐藏;
Display:display 设为 none 任何对该元素直接打用户交互操作都不可能生效。此外，读屏软件也不会读到元素的内容。这种方式产生的效果就像元素完全不存在;
Position:不会影响布局，能让元素保持可以操作;
Clip-path:clip-path 属性还没有在 IE 或者 Edge 下被完全支持。如果要在你的 clip-path 中使用外部的 SVG 文件，浏览器支持度还要低;

#### 15、解释下CSS  sprites,以及你要如何在页面或网站中使用它

CSS Sprites其实就是把网页中一些背景图片整合到一张图片文件中，再利用CSS的“background-image”，“background- repeat”，“background-position”的组合进行背景定位，background-position可以用数字能精确的定位出背景图片的位置。这样可以减少很多图片请求的开销，因为请求耗时比较长；请求虽然可以并发，但是也有限制，一般浏览器都是6个。对于未来而言，就不需要这样做了，因为有了(`http2`)。

#### 16、讨论CSS hacks, 条件引用或者其他

- hacks

```
 _width针对于ie6。*width,+width针对于ie6,7。
 color: red\9;/*IE8以及以下版本浏览器*/（但是测试可以兼容到ie10。
 *+html与*html是IE特有的标签, firefox暂不支持.而*+html又为IE7特有标签（但是测试*html兼容ie6-10。*+兼容ie7-10）。
 !important 在IE中会被忽视，ie6,7,8不识别，ie9+（包括ie9）是识别的。
```

- 条件引用

```
<!--[if !IE]><!--> 除IE外都可识别 <!--<![endif]-->
<!--[if IE]> 所有的IE可识别 <![endif]-->
<!--[if IE 6]> 仅IE6可识别 <![endif]-->
<!--[if lt IE 6]> IE6以及IE6以下版本可识别 <![endif]-->
<!--[if gte IE 6]> IE6以及IE6以上版本可识别 <![endif]-->
<!--[if IE 7]> 仅IE7可识别 <![endif]-->
<!--[if lt IE 7]> IE7以及IE7以下版本可识别 <![endif]-->
<!--[if gte IE 7]> IE7以及IE7以上版本可识别 <![endif]-->
<!--[if IE 8]> 仅IE8可识别 <![endif]-->
<!--[if IE 9]> 仅IE9可识别 <![endif]-->
```

#### 17、css预编译

就是预先编译处理CSS。它扩展了 CSS 语言，增加了变量、Mixin、函数等编程的特性，使 CSS 更易维护和扩展。CSS预编译的工作原理是提供便捷的语法和特性供开发者编写源代码，随后经过专门的编译工具将源码转化为CSS语法。

它从这几个方面提升了CSS开发的效率：增强编程能力；增强可复用性；增强可维护性；更便于解决浏览器兼容性。

##### 为什么要用css预编译

    优点：
        可以提供 CSS 缺失的样式层复用机制、减少冗余代码，提高样式代码的可维护性。大大提高了开发效率。
    缺点：
        调试更麻烦；
        容易造成后代选择器的滥用

##### css的缺点

语法不够强大，比如无法嵌套书写，导致模块化开发中需要书写很多重复的选择器；
没有变量和合理的样式复用机制，使得逻辑上相关的属性值必须以字面量的形式重复输出，导致难以维护。

##### 主流CSS预编译器的介绍

1.Sass

2007年诞生，最早也是最成熟的CSS预处理器，拥有ruby社区的支持和compass这一最强大的CSS框架，目前受LESS影响，已经进化到了全面兼容CSS的SCSS。
其实现在的Sass已经有了两套语法规则：一个依旧是用缩进作为分隔符来区分代码块的；另一套规则和CSS一样采用了大括号（｛｝）作为分隔符。后一种语法规则又名SCSS，在Sass3之后的版本都支持这种语法规则。

    优点：
        用户多，更容易找到会用scss的开发，更容易找到scss的学习资源；
        可编程能力比较强，支持函数，列表，对象，判断，循环等；
        相比less有更多的功能；
        Bootstrap/Foundation等使用scss；
        丰富的sass库：Compass/Bourbon；
    缺点：
        安装node-sass会经常失败或者报错，需要使用cnpm或者手工安装

Sass中文文档：http://sass.bootcss.com/

2.Less

2009年出现，受SASS的影响较大，但又使用CSS的语法，让大部分开发者和设计师更容易上手，在ruby社区之外支持者远超过SASS，其缺点是比起SASS来，可编程功能不够，不过优点是简单和兼容CSS，反过来也影响了SASS演变到了SCSS的时代，著名的Twitter Bootstrap就是采用LESS做底层语言的。

    优点：
        可以在浏览器中运行，实现主题定制功能；
    缺点：
        编程能力弱，不直接支持对象，循环，判断等；
        @variable 变量命名和css的@import/media/keyframes等含义容易混淆；
        mixin/extend的语法比较奇怪；
        mixin的参数如果遇到多参数和列表参数值的时候容易混淆；

Less中文文档：https://less.bootcss.com/

3.Stylus

2010年产生，来自Node.js社区，主要用来给Node项目进行CSS预处理支持，在此社区之内有一定支持者，在广泛的意义上人气还完全不如SASS和LESS
Stylus被称为是一种革命性的新语言，提供一个高效、动态、和使用表达方式来生成CSS，以供浏览器使用。Stylus同时支持缩进和CSS常规样式书写规则。

    优点：
        来自NodeJS社区，所以和NodeJS走得很近，与JavaScript联系非常紧密。还有专门JavaScript API：
        http://learnboost.github.io/stylus/docs/js.html
        支持Ruby之类等等框架3.更多更强大的支持和功能
    缺点：
        人气不高，教程较少

Stylus官方文档：http://stylus-lang.com/
Stylus 中文文档：https://www.zhangxinxu.com/jq/stylus/

##### Sass和Less的比较

不同之处

1、Less环境较Sass简单

    Cass的安装需要安装Ruby环境，Less基于JavaScript，是需要引入Less.js来处理代码输出css到浏览器，也可以在开发环节使用Less，然后编译成css文件，
    直接放在项目中，有less.app、SimpleLess、CodeKit.app这样的工具，也有在线编辑地址。


2、Less使用较Sass简单

    LESS 并没有裁剪 CSS 原有的特性，而是在现有 CSS 语法的基础上，为 CSS 加入程序式语言的特性。只要你了解 CSS 基础就可以很容易上手。


3、从功能出发，Sass较Less略强大一些

    ①sass有变量和作用域。
    - $variable，like php；
    - #｛$variable｝like ruby；
    - 变量有全局和局部之分，并且有优先级。


    ②sass有函数的概念；
    - @function和@return以及函数参数（还有不定参）可以让你像js开发那样封装你想要的逻辑。
    -@mixin类似function但缺少像function的编程逻辑，更多的是提高css代码段的复用性和模块化，这个用的人也是最多的。
    -ruby提供了非常丰富的内置原生api。
    
    ③进程控制：
    -条件：@if @else；
    -循环遍历：@for @each @while
    -继承：@extend
    -引用：@import
    
    ④数据结构：
    -$list类型=数组；
    -$map类型=object；
    其余的也有string、number、function等类型

4、Less与Sass处理机制不一样

    前者是通过客户端处理的，后者是通过服务端处理，相比较之下前者解析会比后者慢一点

5、关于变量在Less和Sass中的唯一区别就是Less用@，Sass用$。

相同之处

Less和Sass在语法上有些共性，比如下面这些：

    1、混入(Mixins)——class中的class；
    2、参数混入——可以传递参数的class，就像函数一样；
    3、嵌套规则——Class中嵌套class，从而减少重复的代码；
    4、运算——CSS中用上数学；
    5、颜色功能——可以编辑颜色；
    6、名字空间(namespace)——分组样式，从而可以被调用；
    7、作用域——局部修改样式；
    8、JavaScript 赋值——在CSS中使用JavaScript表达式赋值。

#### 为什么选择使用Sass而不是Less？

    1、Sass在市面上有一些成熟的框架，比如说Compass，而且有很多框架也在使用Sass，比如说Foundation。
    
    2、就国外讨论的热度来说，Sass绝对优于LESS。
    3、就学习教程来说，Sass的教程要优于LESS。在国内LESS集中的教程是LESS中文官网，而Sass的中文教程，慢慢在国内也较为普遍。
    
    4、Sass也是成熟的CSS预处理器之一，而且有一个稳定，强大的团队在维护。
    
    5、同时还有Scss对sass语法进行了改良，Sass 3就变成了Scss(sassy css)。与原来的语法兼容，只是用{}取代了原来的缩进。
    
    6、bootstrap（Web框架）最新推出的版本4，使用的就是Sass。

### 二、html

#### 1、常用那几种浏览器测试？有哪些内核(Layout Engine)?

浏览器：IE，Chrome，FireFox，Safari，Opera。
　　 内核：Trident，Gecko，Presto，Webkit。

#### 2、HTML5 为什么只需要写<!　DOCTYPE html> ？

　　HTML5不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）。而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

#### 3、页面导入样式时，使用link和@import有什么区别？

　　（1）本质的差别：link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;
　　（2）加载顺序的差别：页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;所以在 @import加载CSS的时候，一开始会没有样式。
　　（3）兼容性的差别：import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题。
　　（4）使用DOM文档对象模型控制样式的差别：当使用JavaScript控制DOM区改变样式的时候，只能使用link标签，而@import是不可以的。
　　（5）作用不同：link是属于XHTML，除了可以加载css,还可以定义RSS等其它事务，而@import是属于css范畴，只能加载css。
　　（6）权重不同：link方式的权重高于@import的权重值。
　　（7）标签不同：import在html使用的时候需要标签，而link在html使用的时候不需要标签。

#### 4、在HTML当中引用CSS的三种使用方式有哪些？它们之间的区别是什么？

在HTML当中引用CSS的三种使用方式：
    1） 第一种是内联样式表，样式通过style属性内嵌在css的样式当中，写在标签当中。
    2） 第二种是内部样式表，通过style标签将CSS的样式写在style属性当中，链入内部的CSS文件。
    3） 第三种是外部样式表，通过link标签或者是在style中通过@import的方式引入外部的CSS样式文件。
它们之间的区别：
    1） 优先级不同，内联样式表的优先级最高，而内部样式表和外部样式表的优先级与书写顺序有关，后书写的优先级高。
    2） 作用域不同，内联样式表的作用域最小，只能应用于当前的元素，内部样式表的作用域其次，只能应用于当前的HTML文件，最后是外部样式表的作用域最大，能够适用于所有链接的HTML文件。
    3）书写顺序不同，内联样式表写在标签当中，内部样式表写在style标签中来链入内部的CSS文件，外部样式表是通过link或者是@import的方式来链入外部的CSS文件。

#### 4、html5有哪些新特性？

HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。

    (1)拖拽释放(Drag and drop) API
    (2)视频和音频  用于媒介回放的 video 和 audio 元素;
    (3)画布(Canvas) API
    (4)地理(Geolocation) API
    (5)本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;
    (6)sessionStorage 的数据在浏览器关闭后自动删除;
    (7)语意化更好的内容标签，比如 （article、footer、header、nav、section、aside）;
    (8)表单控件，calendar、date、time、email、url、search;
    (9)新的技术webworker, websocket, Geolocation;

IE8/IE7/IE6支持通过document.createElement方法产生的标签， 可以利用这一特性让这些浏览器支持HTML5新标签， 浏览器支持新标签后，还需要添加标签默认的样式

#### 5、简述一下你对HTML语义化的理解？

    用正确的标签做正确的事情。
    html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
    即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;
    搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
    使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

#### 6、如何实现浏览器内多个标签页之间的通信?

调用localstorge、cookies等本地存储方式

#### 7、webSocket如何兼容低浏览器？

Adobe Flash Socket 、 ActiveX HTMLFile (IE) 、 基于 multipart 编码发送 XHR 、 基于长轮询的 XHR

#### 8、请写出一些前端性能优化的方式

    1.减少dom操作
    2.部署前，图片压缩，代码压缩
    3.优化js代码结构，减少冗余代码
    4.减少http请求，合理设置 HTTP缓存
    5.使用内容分发cdn加速
    6.静态资源缓存
    7.图片延迟加载

#### 9、iframe的优缺点？

```
1.<iframe>优点：
    解决加载缓慢的第三方内容如图标和广告等的加载问题
    Security sandbox
    并行加载脚本
2.<iframe>的缺点：
    *iframe会阻塞主页面的Onload事件；
    *即时内容为空，加载也需要时间
    *没有语意
iframe会阻塞主页面的Onload事件；
搜索引擎的检索程序无法解读这种页面，不利于SEO;
iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript动态给iframe添加src属性值，这样可以绕开以上两个问题。
```

#### 10、输入URL回车后的过程

1.读取缓存：
搜索自身的 DNS 缓存。(如果 DNS 缓存中找到IP 地址就跳过了接下来查找 IP 地址步骤，直接访问该 IP 地址。)
2.DNS 解析:将域名解析成 IP 地址
3.TCP 连接：TCP 三次握手，简易描述三次握手
客户端：服务端你在么？
服务端：客户端我在，你要连接我么？
客户端：是的服务端，我要链接。
连接打通，可以开始请求来
4.发送 HTTP 请求
5.服务器处理请求并返回 HTTP 报文
6.浏览器解析渲染页面
7.断开连接：TCP 四次挥手

关于第六步浏览器解析渲染页面又可以聊聊如果返回的是html页面
根据 HTML 解析出 DOM 树
根据 CSS 解析生成 CSS 规则树
结合 DOM 树和 CSS 规则树，生成渲染树
根据渲染树计算每一个节点的信息
根据计算好的信息绘制页面

第二种说法：

```
1.浏览器查找域名的 IP 地址
2.这一步包括 DNS 具体的查找过程，包括：浏览器缓存->系统缓存->路由器缓存…
3.浏览器向 web 服务器发送一个 HTTP 请求
4.服务器的永久重定向响应（从 http://example.com 到 http://www.example.com）
5.浏览器跟踪重定向地址
6.服务器处理请求
7.服务器返回一个 HTTP 响应
8.浏览器显示 HTML
9.浏览器发送请求获取嵌入在 HTML 中的资源（如图片、音频、视频、CSS、JS等等）
10.浏览器发送异步请求
```

#### 11、网页布局有哪几种，有什么区别

静态、自适应、流式、响应式四种网页布局
静态布局：意思就是不管浏览器尺寸具体是多少，网页布局就按照当时写代码的布局来布置；
自适应布局：就是说你看到的页面，里面元素的位置会变化而大小不会变化；
流式布局：你看到的页面，元素的大小会变化而位置不会变化——这就导致如果屏幕太大或者太小都会导致元素无法正常显示。
自适应布局：每个屏幕分辨率下面会有一个布局样式，同时位置会变而且大小也会变。

#### 12、怎么让Chrome支持小于12px 的文字？

这个我们在做移动端的时候，设计师图片上的文字假如是10px，我们实现在网页上之后。往往设计师回来找我们，这个字体能小一些吗？我设计的是10px？为啥是12px?其实我们都知道，谷歌Chrome最小字体是12px，不管你设置成8px还是10px，在浏览器中只会显示12px，那么如何解决这个坑爹的问题呢？

我们的做法是：

针对谷歌浏览器内核，加webkit前缀，用transform:scale()这个属性进行缩放！

```
<style>pspan{font-size:10px;-webkit-transform:scale(0.8);display:block;}</style><p><span>haorooms博客测试10px</span></p>
```

#### 13、Doctype作用? 严格模式与混杂模式如何区分？它们有何意义?

（1）、<!DOCTYPE> 声明位于文档中的最前面，处于 <html> 标签之前。告知浏览器以何种模式来渲染文档。 
（2）、严格模式的排版和 JS 运作模式是  以该浏览器支持的最高标准运行。
（3）、在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。
（4）、DOCTYPE不存在或格式不正确会导致文档以混杂模式呈现。

#### 14、Doctype文档类型？

该标签可声明三种 DTD 类型，分别表示严格版本、过渡版本以及基于框架的 HTML 文档。
 HTML 4.01 规定了三种文档类型：Strict、Transitional 以及 Frameset。
 XHTML 1.0 规定了三种 XML 文档类型：Strict、Transitional 以及 Frameset。
Standards （标准）模式（也就是严格呈现模式）用于呈现遵循最新标准的网页，而 Quirks
 （包容）模式（也就是松散呈现模式或者兼容模式）用于呈现为传统浏览器而设计的网页。

#### 15、HTML与XHTML——二者有什么区别

    1.所有的标记都必须要有一个相应的结束标记
    2.所有标签的元素和属性的名字都必须使用小写
    3.所有的XML标记都必须合理嵌套
    4.所有的属性必须用引号""括起来
    5.把所有<和&特殊符号用编码表示
    6.给所有属性赋一个值
    7.不要在注释内容中使“--”
    8.图片必须有说明文字

#### 16、常见兼容性问题？

* png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.也可以引用一段脚本处理.
* 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。
* IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。 
* 浮动ie产生的双倍距离（IE6双边距问题：在IE6下，如果对元素设置了浮动，同时又设置了margin-left或margin-right，margin值会加倍。）
  #box{ float:left; width:10px; margin:0 0 0 100px;} 
   这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)
* 渐进识别的方式，从总体中逐渐排除局部。 
  首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。 
  接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
  css
      .bb{
       background-color:#f1ee18;/*所有识别*/
      .background-color:#00deff\9; /*IE6、7、8识别*/
      +background-color:#a200ff;/*IE6、7识别*/
      _background-color:#1e0bd1;/*IE6识别*/ 
      } 
* IE下,可以使用获取常规属性的方法来获取自定义属性,
  也可以使用getAttribute()获取自定义属性;
  Firefox下,只能使用getAttribute()获取自定义属性. 
  解决方法:统一通过getAttribute()获取自定义属性.
* IE下,event对象有x,y属性,但是没有pageX,pageY属性; 
  Firefox下,event对象有pageX,pageY属性,但是没有x,y属性.
* 解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。
* Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示, 
  可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决.
* 超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:
  L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}
* 怪异模式问题：漏写DTD声明，Firefox仍然会按照标准模式来解析网页，但在IE中会触发怪异模式。为避免怪异模式给我们带来不必要的麻烦，最好养成书写DTD声明的好习惯。现在可以使用[html5](http://www.w3.org/TR/html5/single-page.html)推荐的写法：`<doctype html>`
* 上下margin重合问题
  ie和ff都存在，相邻的两个div的margin-left和margin-right不会重合，但是margin-top和margin-bottom却会发生重合。
  解决方法，养成良好的代码编写习惯，同时采用margin-top或者同时采用margin-bottom。
* ie6对png图片格式支持不好(引用一段脚本处理)

#### 17、线程与进程的区别

一个程序至少有一个进程,一个进程至少有一个线程. 
线程的划分尺度小于进程，使得多线程程序的并发性高。 
另外，进程在执行过程中拥有独立的内存单元，而多个线程共享内存，从而极大地提高了程序的运行效率。 
线程在执行过程中与进程还是有区别的。每个独立的线程有一个程序运行的入口、顺序执行序列和程序的出口。但是线程不能够独立执行，必须依存在应用程序中，由应用程序提供多个线程执行控制。 
从逻辑角度来看，多线程的意义在于一个应用程序中，有多个执行部分可以同时执行。但操作系统并没有将多个线程看做多个独立的应用，来实现进程的调度和管理以及资源分配。这就是进程和线程的重要区别。

#### 18、如何对网站的文件和资源进行优化？

期待的解决方案包括：
 文件合并
 文件最小化/文件压缩
 使用 CDN 托管
 缓存的使用（多个域名来提供缓存）
 其他

#### 19、请说出三种减少页面加载时间的方法。

1.优化图片 
 2.图像格式的选择（GIF：提供的颜色较少，可用在一些对颜色要求不高的地方） 
 3.优化CSS（压缩合并css，如margin-top,margin-left...) 
 4.网址后加斜杠（如www.campr.com/目录，会判断这个“目录是什么文件类型，或者是目录。） 
 5.标明高度和宽度（如果浏览器没有找到这两个参数，它需要一边下载图片一边计算大小，如果图片很多，浏览器需要不断地调整页面。这不但影响速度，也影响浏览体验。 
当浏览器知道了高度和宽度参数后，即使图片暂时无法显示，页面上也会腾出图片的空位，然后继续加载后面的内容。从而加载时间快了，浏览体验也更好了。） 
6.减少http请求（合并文件，合并图片）。

#### 20、什么是 FOUC（无样式内容闪烁）？你如何来避免 FOUC？

```
FOUC - Flash Of Unstyled Content 文档样式闪烁
 <style type="text/css" media="all">@import "../fouc.css";</style> 
而引用CSS文件的@import就是造成这个问题的罪魁祸首。IE会先加载整个HTML文档的DOM，然后再去导入外部的CSS文件，
因此，在页面DOM加载完成到CSS导入完成中间会有一段时间页面上的内容是没有样式的，这段时间的长短跟网速，电脑速度都有关系。
解决方法简单的出奇，只要在<head>之间加入一个<link>或者<script>元素就可以了。
```

#### 21、在form表单中，get方式和post方式提交数据的区别是什么？如何判断在实际开发中的应用？

get方式和post方式提交数据的区别：
1） 大小不同，get方式传输的数据量较小，而post可以传输大量的数据。
2） 安全程度不同，get方式传输数据能够被别人轻易的看到数据内容，所以安全程度较低，而post则可以很好的隐藏。
3） 速度不同，post方式速度较慢，而get方式速度较快。
4） 在服务器上的作用不同，get是从服务器上获取数据，而post是向服务器上传送数据。

在实际开发中的应用：
1）在重要数据进行传输数据的时候，用post的方式进行提交数据。
2）在做数据查询的时候，用get的方式进行提交数据。
3）在做增加、删除和修改数据的时候，用post的方式进行提交数据。

#### 22、在input表单控件中，value和placeholder的区别是什么？

placeholder: 表示在输入框中显示的提示信息，用户点击之后，提示信息就会消失。
value: 叫做默认值，当用户想要在输入框中输入信息的时候，必须先手动的删除value的值 。




## 二、js 部分

### 1、js是什么语言

js是一种运行在浏览器的脚本语言，这种语言主要的功能是可以制作出动态的页面的效果
我们可以通过js+css+html布局来形成我们现在可以访问展示的页面

js语言是弱语言类型， 因此我们在项目开发中当我们随意更改某个变量的数据类型后
有可能会导致其他引用这个变量的方法中报错等等。

### 1、js 的基本数据类型有哪些，基本数据类型和复杂数据类型的区别

String、Number、Boolean、Null、undefined

Object为复杂数据类型

基本数据类型把数据名和值直接存储在栈当中

复杂数据类型在栈中存储数据名和一个堆的地址，在堆中存储属性和值，访问时先从栈中获取地址再到堆中取相应的值

### 2、== 和 === 有什么区别

==用于一般比较 比较时可以转换数据类型 

===用于严格比较 比较时只要类型不匹配就返回false

### 3、split () 和 join () 的区别

split() 字符串转数组 如：var str = "hello?word?welcome"  console.log(str.split(“？”)) 返回值为 ["hello", "word", "welcome"]

join() 数组转字符串 如：var arr = new Array() arr[0] = "hello" arr[1] = "world" arr[3] = "welcome" arr.join("、")  返回值为 "hello、world、welcome"

### 4、call ()、bind ()、apply () 区别

三者都是可以改变this的指向

bind() 返回对应函数便于稍后调用；call()、apply()则是立即调用

call() call(thisArg, case1, case2, case3,...) 第一个参数是对象 后面是字符串

apply() apply(thisArg, [case1, case2, case3,...]) 第一个参数是对象  后面是数组

### 5、数组有哪些操作方法

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
filter() 筛选数组
Map()  循环数组的每一项

### 6、什么是闭包

可以调用其它函数内部变量的函数
简单来说就是函数嵌套函数，内部函数引用来外部函数的变量，从而导致来垃圾回收机制没有生效，变量被保存来下来。
也就是所谓的内存泄漏，然后由于内存泄漏又会导致你项目逐渐变得卡顿等等问题。因此要避免内存泄漏。

优点：避免变量污染、加强了封装性，逻辑性比较强代码的可读性高；加载到内存中执行效率高；

缺点：在内存中，造成了内存浪费，如果滥用闭包是灾难性的；

### 7、null 和 undefined 的区别

null表示没有对象，该处不该有值，转为数值时为0

undefined表示缺少值，该处应该有值，但是未定义，转为数值时为NaN

### 8、什么是变量提升

变量提升是js的默认行为，变量提升会将所有变量声明移动到当前作用域的顶部，并可以在声明之前使用该变量，初始化不会被提升，提升的仅作用于变量的声明

### 9、什么是事件委托

利用事件冒泡的原理，把原本需要绑定的事件委托给父元素，让父元素负责事件监听

### 10、深拷贝和浅拷贝

浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。

    通过ES6新特性Object.assign()与扩展运算符来达到浅拷贝的目的

深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象

    通过利用JSON.parse(JSON.stringify(Object))来达到深拷贝的目的
    但是JSON深拷贝的缺点是undefined和function还有symbol类型是无法进行深拷贝的
    如有需要可以自己手动封装函数来达到目的

### 11、async 与 defer 区别

异步(async) 脚本将在其加载完成后立即执行，而 延迟(defer) 脚本将等待 HTML 解析完成后，并按加载顺序执行。

### 12、cookies，sessionStorage 和 localStorage 有什么区别？

cookies可以和服务端交互，数据大小不会超过4k，设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭，使用方法需要自己封装不够友好;

sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存，虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大，有封装好的方法，可以直接存取值

localStorage 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；sessionStorage 数据在当前浏览器窗口关闭后自动删除。

### 13、数组去重有哪些方法

```
new Set()  如：var arr = [1,2,3,9,6,3,1,2,6] new set(arr)
```

#### 1.利用冒泡 for 循环嵌套，然后 splice () 去重 如：

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

#### 2.indexOf () 去重 如：

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

#### 3.sort () 去重 如：

```
function unique(arr) { if (!Array.isArray(arr)) { console.log('type error!') return; } arr = arr.sort() var arrry= [arr[0]]; for (var i = 1; i < arr.length; i++) { if (arr[i] !== arr[i-1]) { arrry.push(arr[i]); } } return arrry; }

var arr = [1,2,3,9,6,3,1,2,6]

console.log(unique(arr))
```

#### 4.filter () 去重 如:

```
function unique(arr) { return arr.filter(function(item, index, arr) { return arr.indexOf(item, 0) === index; }); }

var arr = [1,2,3,9,6,3,1,2,6]

console.log(unique(arr))
```

### 14、GET 和 POST 有什么区别

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

### 15、跨域有几种解决方案

因为浏览器出于安全考虑，有同源策略。也就是说，如果协议、域名或者端口有一个不同就是跨域，Ajax 请求会失败。
为来防止CSRF攻击

```
1.JSONP
    JSONP 的原理很简单，就是利用 <script> 标签没有跨域限制的漏洞。
    通过 <script> 标签指向一个需要访问的地址并提供一个回调函数来接收数据当需要通讯时。
    <script src="http://domain/api?param1=a&param2=b&callback=jsonp"></script>
    <script>
        function jsonp(data) {
        console.log(data)
    }
    </script>
    JSONP 使用简单且兼容性不错，但是只限于 get 请求。
```

```
2.CORS
    CORS 需要浏览器和后端同时支持。IE 8 和 9 需要通过 XDomainRequest 来实现。
3.document.domain
    该方式只能用于二级域名相同的情况下，比如 a.test.com 和 b.test.com 适用于该方式。
    只需要给页面添加 document.domain = 'test.com' 表示二级域名都相同就可以实现跨域
4.webpack配置proxyTable设置开发环境跨域
5.nginx代理跨域
6.iframe跨域
7.postMessage
    这种方式通常用于获取嵌入页面中的第三方页面数据。一个页面发送消息，另一个页面判断来源并接收消息
```

### 16、typeof 和 instanceof 有什么区别

    typeof 判断一个数据是什么数据类型；一般只能返回如下几个结果："number"、"string"、"boolean"、"object"、"function" 和 "undefined"。
    instanceof 判断一个对象是否在另一个对象的原型链上

### 17、原型

构造函数 ，是一种特殊的方法。主要用来在创建对象时初始化对象。
每个函数都有prototype(原型)属性，这个属性是一个指针，指向一个对象，
这个对象的用途是包含特定类型的所有实例共享的属性和方法，即这个原型对象是用来给实例共享属性和方法的。
而每个实例内部都有一个指向原型对象的指针。

### 18、/

### 19、/

### 20、/

### 21、/

## 三、vue 部分

### 1、vue 的生命周期以及页面初次加载会触发哪些钩子

beforeCreate
created
beforeMount
mounted
beforeUpdate
updated
beforeDestroy
destroyed
第一次会触发前四个钩子

### 2、v-if 和 v-for 哪一个优先级高

v-for优先级高

### 3、v-if 和 v-show 有什么异同

两者都可以控制元素的显示和隐藏

v-if 是动态的向DOM树内添加或者删除DOM元素，若初始值为false，就不会编译了。而且v-if不停的销毁和创建比较消耗性能。

v-show 是通过控制css中的display设置为none，控制隐藏，只会编译一次

### 4、vue 中 data 为什么必须是一个函数

防止组件在重复使用时，数据互相干扰，使用函数将产生新作用域，所以同一个组件在不同位置被使用时，不适用同一份数据

### 5、v-for 里面 key 的作用

key的作用是为了在diff算法执行时更快的找到对应的节点，提高diff速度，具有唯一性

### 6、传值方式有哪些

父传子 在子元素中用 props 接收
子传父 在子元素中用 $emit 传值
同级传值 使用路由query/params传参 如 this.$router.push({path: '/', query: {参数名: '参数值'})  使用this.$route.query.参数名 接收
本地存储传值

### 7、初始化页面闪动问题

在css里加上[v-cloak] {display: none;}
如果没有彻底解决问题，则在根元素加上 style=“display: none;” :style="{display: ‘block’}"

### 8、route和route和 router 的区别

$router是VueRouter的实例，在script标签中想要导航到不同的URL,使用$router.push方法。返回上一个历史history用$router.to(-1)
$route为当前router跳转对象。里面可以获取当前路由的name,path,query,parmas等。

### 9、vuex 有哪几种状态

Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态
并以相应的规则保证状态以一种可预测的方式发生变化。

    state 基本数据(数据源存放地)
    
    Getter 过滤/计数。store 的计算属性 返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算。
    
    mutation 更改 Vuex 的 store 中的状态的唯一方法是提交 mutation 必须是同步函数
    
    Action 类似于 mutation 提交的是 mutation，而不是直接变更状态。 可以包含任意异步操作。
    
    Module 将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割

### 10、vue-router 有几种模式

    hash模式 地址栏URL中的#符号，不会被包含在HTTP请求中，对后端完全没有影响，因此改变hash不会重新加载页面。
    
    history模式 利用了HTML5 History Interface 中新增的pushState() 和replaceState() 方法，这两个方法应用于浏览器的历史记录站，在当前已有的back、forward、go 的基础之上，它们提供了对历史记录进行修改的功能。只是当它们执行修改是，虽然改变了当前的URL，但你浏览器不会立即向后端发送请求。history模式，会出现404 的情况，需要后台配置。

### 11、vue 实现数据双向绑定的原理

采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty（）来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应监听回调。即数据和视图同步，数据发生变化，视图跟着变化，视图变化，数据也随之发生改变

### 12、路由跳转的原理以及方式

路由就是根据不同的url地址展示不同的内容或页面
静态路由是在路由器中设置的固定的路由表。
动态路由是网络中的路由器之间相互通信，传递路由信息，利用收到的路由信息更新路由器表的过程。

this.$router.push({name:'master',params:{id:'参数'}});
//name和params搭配，刷新的话，参数会消失
this.$router.push({path:'/master',query:{id:'参数'}});
//path和query搭配，刷新页面的话，url中的参数不会丢失,query中的参数成了url中的一部分
this.$router.push()
跳转到不同的url，但这个方法回向history栈添加一个记录，点击后退会返回到上一个页面。
this.$router.replace()
描述：同样是跳转到指定的url，但是这个方法不会向history里面添加新的记录，点击返回，会跳转到上上一个页面。上一个记录是不存在的。
this.$router.go(n)
相对于当前页面向前或向后跳转多少个页面,类似 window.history.go(n)。n可为正数可为负数。正数返回上一个页面

### 13、Vue路由守卫有哪些，怎么设置，使用场景等

    常用的两个路由守卫：router.beforeEach 和 router.afterEach
    
    每个守卫方法接收三个参数：
    
    to: Route: 即将要进入的目标 路由对象
    
    from: Route: 当前导航正要离开的路由
    
    next: Function: 一定要调用该方法来 resolve 这个钩子。
    
    在项目中，一般在beforeEach这个钩子函数中进行路由跳转的一些信息判断。
    判断是否登录，是否拿到对应的路由权限等等。

### 13、computed 和 watch 有什么区别

computed是多条数据影响一个数据，而watch，则是一个数据影响多个数据

computed 支持缓存，只有数据发生变化才会重新进行计算，不支持异步。 购物车商品结算

watch 不支持缓存，支持异步，默认初次不会执行。 搜索数据 

immediate 选项为 true，可以立即执行一次方法
deep: true 深度监听 方法 下面的属性层层遍历，都加上监听事件

### 14、VUE 里 data 为什么是函数

组件中的data写成一个函数，数据以函数返回值形式定义，这样每复用一次组件，就会返回一份新的data，类似于给每个组件实例创建一个私有的数据空间，让各个组件实例维护各自的数据。而单纯的写成对象形式，就使得所有组件实例共用了一份data，就会造成一个变了全都会变的结果。


## 四、其它

### 1、什么是 MVC 和 MVVM

MVC模式：Controller负责将Model的数据用View显示出来

M：Model（数据模型），用于存放数据
V：View（视图），也就是用户界面
C：Controller是Model和View的协调者

MVVM模式：VM双向绑定，在 MVVM 框架中，View(视图) 和 Model(数据) 是不可以直接通讯的

M：Movel（数据模型）
V：View
VM：ViewModel 是一个同步View 和 Model的对象

### 2、页面导入样式时，使用 link 和 @import 有什么区别？

link属于XHTML标签，除了加载CSS外，还能用于定义RSS,定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;

页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;

import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;

### 3、优雅降级和渐进增强

渐进增强 progressive enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

优雅降级 graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。

区别：优雅降级是从复杂的现状开始，并试图减少用户体验的供给，而渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要。降级（功能衰减）意味着往回看；而渐进增强则意味着朝前看，同时保证其根基处于安全地带。

### 4、浏览器页面有哪三层构成，分别是什么，作用是什么？

构成：结构层、表示层、行为层

分别是：HTML、CSS、JavaScript

作用：HTML实现页面结构，CSS完成页面的表现与风格，JavaScript实现一些客户端的功能与业务。

### 5、页面重构怎么操作？

页面重构是指：在不改变外部行为的前提下，简化结构、添加可读性，而在网站前端保持一致的行为。也就是说在不改变UI的情况下，对网站进行优化，在扩展的同时保持一致的UI。

编写css、让页面结构更合理化，提升用户体验，实现良好的页面效果和提升性能。

### 6、前端性能优化

避免使用css表达式，避免使用高级选择器，通配选择器。

缓存Ajax，使用CDN，使用外部js和css文件以便缓存，添加Expires头，服务端配置Etag，减少DNS查找等

css放在顶部，js放在底部

减少@import导入css（同步操作）

合并样式和脚本

使用css图片精灵，图片懒加载

减少http请求

初始首屏之外的图片资源按需加载，静态资源延迟加载。

压缩文件，开启GZIP，

少用全局变量，合理使用闭包

用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能

避免图片和iFrame等的空Src。空Src会重新加载当前页面，影响速度和效率

### 7、http 请求过程

HTTP是超文本传输协议，它是TCP/IP协议的一个应用层协议，用于定义WEB浏览器与WEB服务器之间交换数据的过程以及通迅的格式

    域名解析
    发起TCP的3次握手
    建立TCP连接后发起http请求
    服务器端响应http请求，浏览器得到html代码
    浏览器解析html代码，并请求html代码中的资源
    浏览器对页面进行渲染呈现给用户

### 8、HTTP 常见状态码

    200 OK 客户端请求成功。
    301 Moved Permanently 请求永久重定向。
    302 Moved Temporarily 请求临时重定向。
    304 Not Modified 文件未修改，可以直接使用缓存的文件。
    400 Bad Request 由于客户端请求有语法错误，不能被服务器所理解。
    401 Unauthorized 请求未经授权，无法访问。
    403 Forbidden 服务器收到请求，但是拒绝提供服务。服务器通常会在响应正文中给出不提供服务的原因。
    404 Not Found 请求的资源不存在，比如输入了错误的URL。
    500 Internal Server Error 服务器发生不可预期的错误，导致无法完成客户端的请求。
    503 Service Unavailable 服务器当前不能够处理客户端的请求，在一段时间之后，服务器可能会恢复正常。

### 9、一个完整的 url 包括哪几部分

协议部分、域名部分、端口部分、虚拟目录部分、文件名部分、参数部分、锚部分

### 10、webpack配置入口出口

```
module.exports={
    //入口文件的配置项
    entry:{},
    //出口文件的配置项
    output:{},
    //模块：例如解读CSS,图片如何转换，压缩
    module:{},
    //插件，用于生产模版和各项功能
    plugins:[],
    //配置webpack开发服务功能
    devServer:{}
}
```

### 11、webpack3和webpack4区别

```
1.mode
 
webpack增加了一个mode配置，只有两种值development | production。对不同的环境他会启用不同的配置。
 
2.CommonsChunkPlugin
 
CommonChunksPlugin已经从webpack4中移除。
可使用optimization.splitChunks进行模块划分（提取公用代码）。
但是需要注意一个问题，默认配置只会对异步请求的模块进行提取拆分，如果要对entry进行拆分
需要设置optimization.splitChunks.chunks = 'all'。
 
3.webpack4使用MiniCssExtractPlugin取代ExtractTextWebpackPlugin。
 
4.代码分割。
 
使用动态import，而不是用system.import或者require.ensure
 
5.vue-loader。
 
使用vue-loader插件为.vue文件中的各部分使用相对应的loader，比如css-loader等
 
6.UglifyJsPlugin
 
现在也不需要使用这个plugin了，只需要使用optimization.minimize为true就行，production mode下面自动为true
 
optimization.minimizer可以配置你自己的压缩程序
```

### 12、es6新特性
1.ES6引入来严格模式
    变量必须声明后在使用
    函数的参数不能有同名属性, 否则报错
    不能使用with语句 (说实话我基本没用过)
    不能对只读属性赋值, 否则报错
    不能使用前缀0表示八进制数,否则报错 (说实话我基本没用过)
    不能删除不可删除的数据, 否则报错
    不能删除变量delete prop, 会报错, 只能删除属性delete global[prop]
    eval不会在它的外层作用域引入变量
    eval和arguments不能被重新赋值
    arguments不会自动反映函数参数的变化
    不能使用arguments.caller (说实话我基本没用过)
    不能使用arguments.callee (说实话我基本没用过)
    禁止this指向全局对象
    不能使用fn.caller和fn.arguments获取函数调用的堆栈 (说实话我基本没用过)
    增加了保留字（比如protected、static和interface）
 
2.关于let和const新增的变量声明
 
3.变量的解构赋值
 
4.字符串的扩展
    includes()：返回布尔值，表示是否找到了参数字符串。
    startsWith()：返回布尔值，表示参数字符串是否在原字符串的头部。
    endsWith()：返回布尔值，表示参数字符串是否在原字符串的尾部。
5.数值的扩展
    Number.isFinite()用来检查一个数值是否为有限的（finite）。
    Number.isNaN()用来检查一个值是否为NaN。
6.函数的扩展
    函数参数指定默认值
7.数组的扩展
    扩展运算符
8.对象的扩展
    对象的解构
9.新增symbol数据类型
 
10.Set 和 Map 数据结构
    ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。Set 本身是一个构造函数，用来生成 Set 数据结构。
    
    Map它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。
11.Proxy
    Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问
    都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。
    Proxy 这个词的原意是代理，用在这里表示由它来“代理”某些操作，可以译为“代理器”。
    Vue3.0使用了proxy
12.Promise
    Promise 是异步编程的一种解决方案，比传统的解决方案——回调函数和事件——更合理和更强大。
    特点是：
        对象的状态不受外界影响。
        一旦状态改变，就不会再变，任何时候都可以得到这个结果。
13.async 函数
    async函数对 Generator 函数的区别：
    （1）内置执行器。
    Generator 函数的执行必须靠执行器，而async函数自带执行器。也就是说，async函数的执行，与普通函数一模一样，只要一行。
    （2）更好的语义。
    async和await，比起星号和yield，语义更清楚了。async表示函数里有异步操作，await表示紧跟在后面的表达式需要等待结果。
    （3）正常情况下，await命令后面是一个 Promise 对象。如果不是，会被转成一个立即resolve的 Promise 对象。
    （4）返回值是 Promise。
    async函数的返回值是 Promise 对象，这比 Generator 函数的返回值是 Iterator 对象方便多了。你可以用then方法指定下一步的操作。
14.Class
    class跟let、const一样：不存在变量提升、不能重复声明...
    ES6 的class可以看作只是一个语法糖，它的绝大部分功能
    ES5 都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。
15.Module
    ES6 的模块自动采用严格模式，不管你有没有在模块头部加上"use strict";。
    import和export命令以及export和export default的区别