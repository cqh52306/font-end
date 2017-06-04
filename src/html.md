1，HTML、XML、XHTML 有什么区别?
HTML即是超文本标记语言（Hyper Text Markup Language），是最早写网页的语言，但是由于时间早，规范不是很好，大小写混写且编码不规范,是语法较为松散的、不严格的Web语言
XHTML是升级版的html（Extensible Hyper Text Markup Language），对html进行了规范，编码更加严谨纯洁，也是一种过渡语言，html向xml过渡的语言。实际上XHTML 与 HTML 4.01 标准没有太多的不同。
XML是可扩展标记语言（Extensible Markup Language），是一种跨平台语言，编码更自由，可以自由创建标签（
比如像下面这样创建：
<note>
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>
），主要用于存储数据和结构，可扩展

2，HTML和XML的区别：

XML 被设计用来传输和存储数据，其焦点是数据的内容。
HTML 被设计用来显示数据，其焦点是数据的外观。
HTML 旨在显示信息，而 XML 旨在传输信息。
XML在定义标记时区分大小写，而HTML标记不区分大小写。

3，HTML和XHTML的区别：
XHTML 元素必须被正确地嵌套。
例如：XHTML必须要这样<b><i>This text is bold and italic</i></b>
而在 HTML 中，某些元素可以像这样彼此不正确地嵌套：
<b><i>This text is bold and italic</b></i>
XHTML 元素必须被关闭。
例如<p>This is a paragraph</p>===>>这是正确的
<p>This is a paragraph===>>这是错误的
标签名必须用小写字母。
例如: <p>This is a paragraph</p>==>>这是正确的
<P>This is a paragraph</P>===>>这是错误的
XHTML 文档必须拥有根元素。
所有的 XHTML 元素必须被嵌套于 <html> 根元素中