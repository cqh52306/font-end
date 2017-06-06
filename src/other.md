### AMD 和 CMD 的区别有哪些？
AMD 是 RequireJS 在推广过程中对模块定义的规范化产出。  
CMD 是 SeaJS 在推广过程中对模块定义的规范化产出。  
类似的还有 CommonJS Modules/2.0 规范，是 BravoJS 在推广过程中对模块定义的规范化产出。  
这些规范的目的都是为了 JavaScript 的模块化开发，特别是在浏览器端的。  
目前这些规范的实现都能达成浏览器端模块化开发的目的。  
区别：  
1. 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.  
2. CMD 推崇依赖就近，AMD 推崇依赖前置。看代码：  
```js
// CMD
define(function(require, exports, module) {
       var a = require('./a')   
       a.doSomething()   
       // 此处略去 100 行   
       var b = require('./b') // 依赖可以就近书写   
       b.doSomething()   
       // ... 
})

// AMD 默认推荐的是
define(['./a', './b'], function(a, b) {  // 依赖必须一开始就写好    
    a.doSomething()    
    // 此处略去 100 行    
    b.doSomething()    
    ...
})
```
虽然 AMD 也支持 CMD 的写法，同时还支持将 require 作为依赖项传递，但 RequireJS 的作者默认是最喜欢上面的写法，也是官方文档里默认的模块定义写法。  
3. AMD 的 API 默认是一个当多个用，CMD 的 API 严格区分，推崇职责单一。比如 AMD 里，require 分全局 require 和局部 require，都叫 require。CMD 里，没有全局 require，而是根据模块系统的完备性，提供 seajs.use 来实现模块系统的加载启动。CMD 里，每个 API 都简单纯粹。  

来源 [玉伯-知乎](https://www.zhihu.com/question/20351507/answer/14859415)

### 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？
分为4个步骤：  
1. 当发送一个URL请求时，不管这个URL是Web页面的URL还是Web页面上每个资源的URL，浏览器都会开启一个线程来处理这个请求，同时在远程DNS服务器上启动一个DNS查询。这能使浏览器获得请求对应的IP地址。
2. 浏览器与远程Web服务器通过TCP三次握手协商来建立一个TCP/IP连接。该握手包括一个同步报文，一个同步-应答报文和一个应答报文，这三个报文在 浏览器和服务器之间传递。该握手首先由客户端尝试建立起通信，而后服务器应答并接受客户端的请求，最后由客户端发出该请求已经被接受的报文。
3. 一旦TCP/IP连接建立，浏览器会通过该连接向远程服务器发送HTTP的GET请求。远程服务器找到资源并使用HTTP响应返回该资源，值为200的HTTP响应状态表示一个正确的响应。
4. 此时，Web服务器提供资源服务，客户端开始下载资源。
    
请求返回后，便进入了我们关注的前端模块  
简单来说，浏览器会解析HTML生成DOM Tree，其次会根据CSS生成CSS Rule Tree，而javascript又可以根据DOM API操作DOM
