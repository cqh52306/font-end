#### HTML、XML、XHTML 有什么区别?

HTML即是超文本标记语言（Hyper Text Markup Language），是最早写网页的语言，但是由于时间早，规范不是很好，大小写混写且编码不规范,是语法较为松散的、不严格的Web语言
XHTML是升级版的html（Extensible Hyper Text Markup Language），对html进行了规范，编码更加严谨纯洁，也是一种过渡语言，html向xml过渡的语言。实际上XHTML 与 HTML 4.01 标准没有太多的不同。
XML是可扩展标记语言（Extensible Markup Language），是一种跨平台语言，编码更自由，可以自由创建标签（
比如像下面这样创建：
```js
`<note>  
    <to>Tove</to>  
    <from>Jani</from>  
    <heading>Reminder</heading>  
    <body>Don't forget me this weekend!</body>  
</note> `
```
），主要用于存储数据和结构，可扩展

#### HTML和XML的区别：

XML 被设计用来传输和存储数据，其焦点是数据的内容。  
HTML 被设计用来显示数据，其焦点是数据的外观。  
HTML 旨在显示信息，而 XML 旨在传输信息。  
XML在定义标记时区分大小写，而HTML标记不区分大小写。

#### HTML和XHTML的区别：

XHTML 元素必须被正确地嵌套。  
例如：  
XHTML必须要这样`<b><i>This text is bold and italic</i></b>`  
而在 HTML 中，某些元素可以像这样彼此不正确地嵌套：  
`<b><i>This text is bold and italic</b></i>`  
XHTML 元素必须被关闭。  
`<p>This is a paragraph</p> //这是正确的`  
`<p>This is a paragraph //这是错误的`  
标签名必须用小写字母。  
`<p>This is a paragraph</p> //这是正确的`  
`<P>This is a paragraph</P> //这是错误的`  
XHTML 文档必须拥有根元素。  
所有的 XHTML 元素必须被嵌套于 `<html>` 根元素中  

#### 怎样理解 HTML 语义化?

HTML语义化是让大家直观的认识标签(markup)和属性(attribute)的用途和作用，
选择合适的标签（代码语义化）便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫和机器很好地解析，
并且便于团队开发和维护。
  * html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;  
  * 即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;  
  * 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;  
  * 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。  

#### 怎样理解内容与样式分离的原则?

写 HTML 的时候先不管样式, 重点放在HTML的结构和语义化上，让 HTML 能体现页面结构或者内容。之后再去写样式。
写 JS 的时候，尽量不要用 JS 去直接操作样式，而是通过给元素添加删除class来控制样式变化。
文档结构与文档样式的分离可以确保网页的平稳退化，也让内容和样式在可以分开独立编辑。

#### 有哪些常见的meta标签?

指定字符集  
`<meta charset="utf-8">`  
向搜索引擎说明你的网页的关键词  
`<meta name="keywords" content="">`  
告诉搜索引擎你的站点的主要内容  
`<meta name="description" content="">`  
告诉搜索引擎你的站点的制作的作者  
`<meta name="author" content="your name">`  
响应式页面  
`<meta name="viewport" content="width=device-width, initial-scale=1.0">`  
定时让网页在3秒内跳转到mozilla首页(http-equiv 属性为名称/值对提供了名称。并指示服务器在发送实际的文档之前先在要传送给浏览器的 MIME 文档头部包含名称/值对。)  
`<meta http-equiv="refresh" content="3" url=https://www.mozilla.org">`
如果安装了GCF (Google Chrome Frame)，则使用GCF来渲染页面 ("chrome=1"), 如果没有安装GCF，则使用最高版本的IE内核进行渲染 ("IE=edge")。X-UA-Compatible(浏览器采取何种版本渲染当前页面)  
`<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">`  
浏览器的内核控制  
`<meta name="renderer" content="webkit|ie-comp|ie-stand">`

### 文档声明的作用?

文档声明用来告知浏览器当前文档所使用的类型，让浏览器解析器知道要用什么规范来解析文档。

### 严格模式和混杂模式指什么?

在严格模式中，浏览器以其支持的最高标准呈现页面。  
在混杂模式中，又称怪异模式或兼容模式，浏览器用自己的方式解析代码，页面以一种比较宽松的向后兼容的方式显示。混杂模式通常模拟老式浏览器的行为以防止老站点无法工作。

### 对栅格系统的理解

Bootstrap内置了一套响应式、移动设备优先的流式栅格系统，随着屏幕设备或视口（viewport）尺寸的增加，系统会自动分为最多12列。  
我在这里是把Bootstrap中的栅格系统叫做布局。它就是通过一系列的行（row）与列（column）的组合创建页面布局，然后你的内容就可以放入到你创建好的布局当中。下面就简单介绍一下Bootstrap栅格系统的工作原理：  
网格系统的实现原理非常简单，仅仅是通过定义容器大小，平分12份(也有平分成24份或32份，但12份是最常见的)，再调整内外边距，最后结合媒体查询，就制作出了强大的响应式网格系统。Bootstrap框架中的网格系统就是将容器平分成12份。  
在使用的时候大家可以根据实际情况重新编译LESS（或Sass）源码来修改12这个数值（也就是换成24或32，当然你也可以分成更多，但不建议这样使用）

### `<!doctype html>` 的作用?

它是html5标准网页声明,告诉浏览器用最新的 HTML5标准来解析渲染页面；如果不写，浏览器就会进入混杂模式。

### 浏览器乱码的原因是什么？如何解决？

乱码产生的根本原因是保存的编码格式和浏览器解析时的解码格式不匹配导致的。  
解决方式： 写代码的时候在html 的 `<head>`里添加`<meta charset='xxx'>`并且保存的时候仍选择同样的编码方式。

### 常见的浏览器有哪些？什么内核？

Internet explorer 使用的是Trident  
Firefox使用的是Gecko。  
opera之前使用的是Presto，后来用Blink  
苹果的Safari，谷歌的Chrome使用的是WebKit，还有国产的大部分双核浏览器其中一核就是WebKit。

### Doctype作用？标准模式与兼容模式各有什么区别?

（1）、<!DOCTYPE>声明位于位于HTML文档中的第一行，处于 `<html>` 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。  
（2）、标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。

### HTML5 为什么只需要写 <!DOCTYPE HTML>？

HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；  
而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

### 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

首先：CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。  

  （1）行内元素有：a b span img input select strong（强调的语气）  
  （2）块级元素有：div ul ol li dl dt dd h1 h2 h3 h4…p  
  （3）常见的空元素：  
      `<br> <hr> <img> <input> <link> <meta>`
      鲜为人知的是：  
      `<area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>`  
不同浏览器（版本）、HTML4（5）、CSS2等实际略有差异

### 页面导入样式时，使用link和@import有什么区别？

（1）link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;  
（2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;  
（3）import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;  

### 介绍一下你对浏览器内核的理解？

主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。  
   1. 渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。  
   2. JS引擎则：解析和执行javascript来实现网页的动态效果。  
最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

### html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和HTML5？

 * HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。  
          绘画 canvas;  
          用于媒介回放的 video 和 audio 元素;  
          本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;  
          sessionStorage 的数据在浏览器关闭后自动删除;  
          语意化更好的内容元素，比如 article、footer、header、nav、section;  
          表单控件，calendar、date、time、email、url、search;  
          新的技术webworker, websocket, Geolocation;  

      移除的元素：  
          纯表现的元素：basefont，big，center，font, s，strike，tt，u;  
          对可用性产生负面影响的元素：frame，frameset，noframes；  

    * 支持HTML5新标签：  
         IE8/IE7/IE6支持通过document.createElement方法产生的标签，  
           可以利用这一特性让这些浏览器支持HTML5新标签，  
           浏览器支持新标签后，还需要添加标签默认的样式。  

         当然也可以直接使用成熟的框架、比如html5shim;  
         `<!--[if lt IE 9]>`  
            `<script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>`  
         `<![endif]-->`  

    * 如何区分HTML5： DOCTYPE声明\新增的结构元素\功能元素  

### HTML5的离线储存怎么使用，工作原理能不能解释一下？

  在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。  
  原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。  
如何使用：  
    1、页面头部像下面一样加入一个manifest的属性；  
    2、在cache.manifest文件的编写离线存储的资源；  
        CACHE MANIFEST  
        #v0.11 
        CACHE:  
        js/app.js  
        css/style.css  
        NETWORK:  
        resourse/logo.png  
        FALLBACK:  
        / /offline.html  
    3、在离线状态时，操作window.applicationCache进行需求实现。  

### 浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？

在线的情况下，浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。  
离线的情况下，浏览器就直接使用离线存储的资源。

### 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

  cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。  
  cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。  
  sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。  
  存储大小：  
      cookie数据大小不能超过4k。  
      sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。  
  有期时间：  
      localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；  
      sessionStorage  数据在当前浏览器窗口关闭后自动删除。  
      cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭  

### iframe有那些缺点？

  * iframe会阻塞主页面的Onload事件；  
  * 搜索引擎的检索程序无法解读这种页面，不利于SEO;  
  * iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。  
  使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript  
  动态给iframe添加src属性值，这样可以绕开以上两个问题。

### Label的作用是什么？是怎么用的？

label标签来定义表单控制间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。

  `<label for="Name">Number:</label>`  
  `<input type=“text“name="Name" id="Name"/>`  
  `<label>Date:<input type="text" name="B"/></label>`  

### HTML5的form如何关闭自动完成功能？

给不想要提示的 form 或某个 input 设置为 autocomplete=off。 

### 如何实现浏览器内多个标签页之间的通信? (阿里)

  WebSocket、SharedWorker；  
  也可以调用localstorge、cookies等本地存储方式；  
  localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，  
  我们通过监听事件，控制它的值来进行页面信息通信；  
  注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；

### 页面可见性（Page Visibility API） 可以有哪些用途？

  通过 visibilityState 的值检测页面当前是否可见，以及打开网页的时间等;  
  在页面被切换到其他后台进程的时候，自动暂停音乐或视频的播放；

### 如何在页面上实现一个圆形的可点击区域？

  1、map+area或者svg  
  2、border-radius  
  3、纯js实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等

### 网页验证码是干嘛的，是为了解决什么安全问题。

  区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水；  
  有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试。  

### title与h1的区别、b与strong的区别、i与em的区别？

 title属性没有明确意义只表示是个标题，H1则表示层次明确的标题，对页面信息的抓取也有很大的影响  
  strong是标明重点内容，有语气加强的含义，使用阅读设备阅读网络时：`<strong>`会重读，而<B>是展示强调内容。  
  i内容展示为斜体，em表示强调的文本；  
  Physical Style Elements -- 自然样式标签  
  b, i, u, s, pre  
  Semantic Style Elements -- 语义样式标签  
  strong, em, ins, del, code  
  应该准确使用语义样式标签, 但不能滥用, 如果不能确定时首选使用自然样式标签。  

### 列出常见的标签，并简单介绍这些标签用在什么场景？

标签	              运用场景  

`<html>`	      HTML 页面的根元素  
`<body>`	      文档的内容  
`<head>`	      用于定义文档的头部  
`<meta>`	      提供了元数据.元数据也不显示在页面上，被浏览器解析  
`<title>`	      文档的标题  
`<h1>-<h6>`  	  定义了一级标题到六级标题，标题字体大小逐渐减弱  
`<p>`	          定义一个段落  
`<a>`	          网页链接  
`<div>`  	      块级元素，它可用于组合其他 HTML 元素的容器,没有特定的含义  
`<span>`	      内联元素，也没有特定的含义，可用作文本的容器  
`<u>`	          下划线  
`<em>`	          强调文本  
`<strong>`	      加重文本  
`<ol>`	          有序列表  
`<ul>`	          无序列表  
`<li>`	          定义列表项目  
`<img>`	          图片  
`<br >`	          换行  
`<input>`	      定义输入控件  
`<i>`	          斜体字  
`<table>`	      定义表  
`<tr>`	          定义表格中的行  
`<td>`	          定义表中的单元格  
`<th>`	          定义表格的表头  
`<tbody>`	      定义表格的主体  
`<tfoot>`	      定义表格的页脚  
`<hr>`	          创建一条水平线  
`<iframe>`	      定义内联框架  
`<cite>`	      定义作品的标题  
`<button>`	      按钮  
`<b>`	          定义粗体文本  
`<form>`	      定义用于用户输入的HTML表单  
`<caption>`	      定义表标题  
`<footer>`	      定义文档或节的页脚  



