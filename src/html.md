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