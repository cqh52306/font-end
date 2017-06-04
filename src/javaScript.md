### 1 在String对象上定义一个repeatify函数。这个函数接受一个整数参数，来明确字符串需要重复几次

    这个函数要求字符串重复指定的次数。举个例子：
```js
console.log('hello'.repeatify(3));
//hellohellohello
```
```js
String.prototype.repeatify = String.prototype.repeatify || function(times) {
    var str = '';
    for (var i = 0; i < times; i++) {
        str += this;
    }
    return str;
};
```

### 2 介绍js的基本数据类型。
  Undefined、Null、Boolean、Number、String、
  ECMAScript 2015 新增:Symbol(创建后独一无二且不可变的数据类型 )

### 3 介绍js的数据类型。
  6种基本类型 Undefined、Null、Boolean、Number、String、Symbol
  一种引用类型 Object

### 4 介绍js有哪些内置对象？
 Object 是 JavaScript 中所有对象的父对象
 数据封装类对象：Object、Array、Boolean、Number 和 String
 其他对象：Function、Arguments、Math、Date、RegExp、Error

### 5 说几条写JavaScript的基本规范？
 1.不要在同一行声明多个变量。  
 2.请使用 ===/!==来比较true/false或者数值  
 3.使用对象字面量替代new Array这种形式  
 4.不要使用全局函数。  
 5.Switch语句必须带有default分支  
 6.函数不应该有时候有返回值，有时候没有返回值。  
 7.For循环必须使用大括号  
 8.If语句必须使用大括号  
 9.for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。  

### 6 JavaScript原型，原型链 ? 有什么特点？
 每个对象都会在其内部初始化一个属性，就是prototype(原型)，当我们访问一个对象的属性时， 
 如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，  
 于是就这样一直找下去，也就是我们平时所说的原型链的概念。  
 关系：`instance.constructor.prototype = instance.__proto__`

 特点：
 JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变。  
     当我们需要一个属性的时，Javascript引擎会先看当前对象中是否有这个属性， 如果没有的话，  
     就会查找他的Prototype对象是否有这个属性，如此递推下去，一直检索到 Object 内建对象。  
 ```js
function Func(){}
    Func.prototype.name = "Sean";
    Func.prototype.getInfo = function() {
    return this.name;
}
var person = new Func();//现在可以参考var person = Object.create(oldObject);
console.log(person.getInfo());//它拥有了Func的属性和方法
//"Sean"
console.log(Func.prototype);
// Func { name="Sean", getInfo=function()}
```
### 7 JavaScript有几种类型的值？，你能画一下他们的内存图吗？

 栈：原始数据类型（Undefined，Null，Boolean，Number、String）  
 堆：引用数据类型（对象、数组和函数）  

 两种类型的区别是：存储位置不同；  
 原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；  
 引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体  

### 8 如何将字符串转化为数字，例如’12.3b’?
  * parseFloat('12.3b');  
  * 正则表达式，`'12.3b'.match(/(\d)+(\.)?(\d)+/g)[0] * 1`, 但是这个不太靠谱，提供一种思路而已。

### 9 如何将浮点数点左边的数每三位添加一个逗号，如12000000.11转化为『12,000,000.11』?
```js
function commafy(num){
    return num && num
        .toString()
        .replace(/(\d)(?=(\d{3})+\.)/g, function($1, $2){
            return $2 + ',';
        });
}
```

### 10 如何实现数组的随机排序？

  方法一：
```js
var arr = [1,2,3,4,5,6,7,8,9,10];
function randSort1(arr){
    for(var i = 0,len = arr.length;i < len; i++ ){
        var rand = parseInt(Math.random()*len);
        var temp = arr[rand];
        arr[rand] = arr[i];
        arr[i] = temp;
    }
    return arr;
}
console.log(randSort1(arr));
```
  方法二：
```javascript
var arr = [1,2,3,4,5,6,7,8,9,10];
function randSort2(arr){
    var mixedArray = [];
    while(arr.length > 0){
        var randomIndex = parseInt(Math.random()*arr.length);
        mixedArray.push(arr[randomIndex]);
        arr.splice(randomIndex, 1);
    }
    return mixedArray;
}
console.log(randSort2(arr));
```
  方法三：
```js
var arr = [1,2,3,4,5,6,7,8,9,10];
arr.sort(function(){
    return Math.random() - 0.5;
})
console.log(arr);
```

### 11 Javascript如何实现继承？

 1、构造继承  
 2、原型继承  
 3、实例继承  
 4、拷贝继承  

### 12  原型prototype机制或apply和call方法去实现较简单，建议使用构造函数与原型混合方式。
 ```js
function Parent(){
    this.name = 'wang';
}
function Child(){
    this.age = 28;
}
Child.prototype = new Parent();//继承了Parent，通过原型
var demo = new Child();
alert(demo.age);
alert(demo.name);//得到被继承的属性
```

### 13  JavaScript继承的几种实现方式？

### 14  javascript创建对象的几种方式？

javascript创建对象简单的说,无非就是使用内置对象或各种自定义对象，当然还可以用JSON；但写法有很多种，也能混合使用。

    1. 对象字面量的方式

        person={firstname:"Mark",lastname:"Yun",age:25,eyecolor:"black"};

    2. 用function来模拟无参的构造函数
```js
function Person(){}
    var person=new Person();//定义一个function，如果使用new"实例化",该function可以看作是一个Class
    person.name="Mark";
    person.age="25";
    person.work=function(){
    alert(person.name+" hello...");
}
person.work();
```

    3. 用function来模拟参构造函数来实现（用this关键字定义构造的上下文属性）
```js
function Pet(name,age,hobby){
    this.name=name;//this作用域：当前对象
    this.age=age;
    this.hobby=hobby;
    this.eat=function(){
        alert("我叫"+this.name+",我喜欢"+this.hobby+",是个程序员");
    }
}
var maidou =new Pet("麦兜",25,"coding");//实例化、创建对象
maidou.eat();//调用eat方法
```

    4、用工厂方式来创建（内置对象）
```js
var wcDog =new Object();
wcDog.name="旺财";
wcDog.age=3;
wcDog.work=function(){
    alert("我是"+wcDog.name+",汪汪汪......");
}
wcDog.work();
```

    5、用原型方式来创建
```js
function Dog(){

}
Dog.prototype.name="旺财";
Dog.prototype.eat=function(){
    alert(this.name+"是个吃货");
}
var wangcai =new Dog();
wangcai.eat();
```
    5、用混合方式来创建
```js
function Car(name,price){
    this.name=name;
    this.price=price;
}
Car.prototype.sell=function(){
    alert("我是"+this.name+"，我现在卖"+this.price+"万元");
}
var camry =new Car("凯美瑞",27);
camry.sell();
```

### 15 Javascript作用链域?

 全局函数无法查看局部函数的内部细节，但局部函数可以查看其上层的函数细节，直至全局细节。  
 当需要从局部函数查找某一属性或方法时，如果当前作用域没有找到，就会上溯到上层作用域查找，  
 直至全局函数，这种组织形式就是作用域链。

### 16 谈谈This对象的理解。

this总是指向函数的直接调用者（而非间接调用者）；  
如果有new关键字，this指向new出来的那个对象；  
在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window；  

### 17 eval是做什么的？

 它的功能是把对应的字符串解析成JS代码并运行；  
 应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。  
 由JSON字符串转换为JSON对象的时候可以用eval，var obj =eval('('+ str +')');  

### 18 什么是window对象? 什么是document对象?

 window对象是指浏览器打开的窗口。  
 document对象是Documentd对象（HTML 文档对象）的一个只读引用，window对象的一个属性。  

### 19 null，undefined 的区别？

 null         表示一个对象是“没有值”的值，也就是值为“空”；  
 undefined     表示一个变量声明了没有初始化(赋值)；  
 undefined不是一个有效的JSON，而null是；  
 undefined的类型(typeof)是undefined；  
 null的类型(typeof)是object；  

Javascript将未赋值的变量默认值设为undefined；  
Javascript从来不会将变量设为null。它是用来让程序员表明某个用var声明的变量时没有值的。  

typeof undefined  
    //"undefined"  
    undefined :是一个表示"无"的原始值或者说表示"缺少值"，就是此处应该有一个值，但是还没有定义。当尝试读取时会返回 undefined；  
    例如变量被声明了，但没有赋值时，就等于undefined  

typeof null  
    //"object"  
    null : 是一个对象(空对象, 没有任何属性和方法)；  
    例如作为函数的参数，表示该函数的参数不是对象；  

注意：  
    在验证null时，一定要使用　=== ，因为 == 无法分别 null 和　undefined  
        null == undefined // true  
        null === undefined // false  

再来一个例子：  

    null  
    Q：有张三这个人么？  
    A：有！  
    Q：张三有房子么？  
    A：没有！  

    undefined  
    Q：有张三这个人么？  
    A：有！  
    Q: 张三有多少岁？  
    A: 不知道（没有被告诉）  


18，写一个通用的事件侦听器函数。

     // event(事件)工具集，来源：github.com/markyun
     markyun.Event = {
         // 页面加载完成后
         readyEvent : function(fn) {
             if (fn==null) {
                 fn=document;
             }
             var oldonload = window.onload;
             if (typeof window.onload != 'function') {
                 window.onload = fn;
             } else {
                 window.onload = function() {
                     oldonload();
                     fn();
                 };
             }
         },
         // 视能力分别使用dom0||dom2||IE方式 来绑定事件
         // 参数： 操作的元素,事件名称 ,事件处理程序
         addEvent : function(element, type, handler) {
             if (element.addEventListener) {
                 //事件类型、需要执行的函数、是否捕捉
                 element.addEventListener(type, handler, false);
             } else if (element.attachEvent) {
                 element.attachEvent('on' + type, function() {
                     handler.call(element);
                 });
             } else {
                 element['on' + type] = handler;
             }
         },
         // 移除事件
         removeEvent : function(element, type, handler) {
             if (element.removeEventListener) {
                 element.removeEventListener(type, handler, false);
             } else if (element.datachEvent) {
                 element.detachEvent('on' + type, handler);
             } else {
                 element['on' + type] = null;
             }
         },
         // 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
         stopPropagation : function(ev) {
             if (ev.stopPropagation) {
                 ev.stopPropagation();
             } else {
                 ev.cancelBubble = true;
             }
         },
         // 取消事件的默认行为
         preventDefault : function(event) {
             if (event.preventDefault) {
                 event.preventDefault();
             } else {
                 event.returnValue = false;
             }
         },
         // 获取事件目标
         getTarget : function(event) {
             return event.target || event.srcElement;
         },
         // 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
         getEvent : function(e) {
             var ev = e || window.event;
             if (!ev) {
                 var c = this.getEvent.caller;
                 while (c) {
                     ev = c.arguments[0];
                     if (ev && Event == ev.constructor) {
                         break;
                     }
                     c = c.caller;
                 }
             }
             return ev;
         }
     };
19，[“1”, “2”, “3”].map(parseInt) 答案是多少？
 parseInt() 函数能解析一个字符串，并返回一个整数，需要两个参数 (val, radix)，
 其中 radix 表示要解析的数字的基数。【该值介于 2 ~ 36 之间，并且字符串中的数字不能大于radix才能正确返回数字结果值】;
 但此处 map 传了 3 个 (element, index, array),我们重写parseInt函数测试一下是否符合上面的规则。

 function parseInt(str, radix) {
     return str+'-'+radix;
 };
 var a=["1", "2", "3"];
 a.map(parseInt);  // ["1-0", "2-1", "3-2"] 不能大于radix

 因为二进制里面，没有数字3,导致出现超范围的radix赋值和不合法的进制解析，才会返回NaN
 所以["1", "2", "3"].map(parseInt) 答案也就是：[1, NaN, NaN]

20，事件是？IE与火狐的事件机制有什么区别？ 如何阻止冒泡？
  1. 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。
  2. 事件处理机制：IE是事件冒泡、Firefox同时支持两种事件模型，也就是：捕获型事件和冒泡型事件；
  3. ev.stopPropagation();（旧ie的方法 ev.cancelBubble = true;）

21，什么是闭包（closure），为什么要用它？

 闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量,利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。

 闭包的特性：

 1.函数内再嵌套函数
 2.内部函数可以引用外层的参数和变量
 3.参数和变量不会被垃圾回收机制回收

 //li节点的onclick事件都能正确的弹出当前被点击的li索引
  <ul id="testUL">
     <li> index = 0</li>
     <li> index = 1</li>
     <li> index = 2</li>
     <li> index = 3</li>
 </ul>
 <script type="text/javascript">
       var nodes = document.getElementsByTagName("li");
     for(i = 0;i<nodes.length;i+= 1){
         nodes[i].onclick = (function(i){
                   return function() {
                      console.log(i);
                   } //不用闭包的话，值每次都是4
                 })(i);
     }
 </script>

    执行say667()后,say667()闭包内部变量会存在,而闭包内部函数的内部变量不会存在
    使得Javascript的垃圾回收机制GC不会收回say667()所占用的资源
    因为say667()的内部函数的执行需要依赖say667()中的变量
    这是对闭包作用的非常直白的描述

      function say667() {
        // Local variable that ends up within closure
        var num = 666;
        var sayAlert = function() {
            alert(num);
        }
        num++;
        return sayAlert;
    }

     var sayAlert = say667();
     sayAlert()//执行结果应该弹出的667

22，javascript 代码中的”use strict”;是什么意思 ? 使用它区别是什么？
 use strict是一种ECMAscript 5 添加的（严格）运行模式,这种模式使得 Javascript 在更严格的条件下运行,

 使JS编码更加规范化的模式,消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为。
 默认支持的糟糕特性都会被禁用，比如不能用with，也不能在意外的情况下给全局变量赋值;
 全局变量的显示声明,函数必须声明在顶层，不允许在非函数代码块内声明函数,arguments.callee也不允许使用；
 消除代码运行的一些不安全之处，保证代码运行的安全,限制函数中的arguments修改，严格模式下的eval函数的行为和非严格模式的也不相同;

 提高编译器效率，增加运行速度；
 为未来新版本的Javascript标准化做铺垫。

23，如何判断一个对象是否属于某个类？
    使用instanceof （待完善）
    if(a instanceof Person){
        alert('yes');
    }

24，new操作符具体干了什么呢?

     1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
      2、属性和方法被加入到 this 引用的对象中。
       3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。

 var obj  = {};
 obj.__proto__ = Base.prototype;
 Base.call(obj);

25，Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？

 hasOwnProperty

 javaScript中hasOwnProperty函数方法是返回一个布尔值，指出一个对象是否具有指定名称的属性。此方法无法检查该对象的原型链中是否具有该属性；该属性必须是对象本身的一个成员。
 使用方法：
 object.hasOwnProperty(proName)
 其中参数object是必选项。一个对象的实例。
 proName是必选项。一个属性名称的字符串值。

 如果 object 具有指定名称的属性，那么JavaScript中hasOwnProperty函数方法返回 true，反之则返回 false。

26，JSON 的了解？
 JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。
 它是基于JavaScript的一个子集。数据格式简单, 易于读写, 占用带宽小
 如：{"age":"12", "name":"back"}

 JSON字符串转换为JSON对象:
 var obj =eval('('+ str +')');
 var obj = str.parseJSON();
 var obj = JSON.parse(str);

 JSON对象转换为JSON字符串：
 var last=obj.toJSONString();
 var last=JSON.stringify(obj);

27，js延迟加载的方式有哪些？
 defer和async、动态创建DOM方式（用得最多）、按需异步载入js

28，Ajax 是什么? 如何创建一个Ajax？
 ajax的全称：Asynchronous Javascript And XML。
 异步传输+js+xml。
 所谓异步，在这里简单地解释就是：向服务器发送请求的时候，我们不必等待结果，而是可以同时做其他的事情，等到有了结果它自己会根据设定进行后续操作，与此同时，页面是不会发生整页刷新的，提高了用户体验。

 (1)创建XMLHttpRequest对象,也就是创建一个异步调用对象
 (2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息
 (3)设置响应HTTP请求状态变化的函数
 (4)发送HTTP请求
 (5)获取异步调用返回的数据
 (6)使用JavaScript和DOM实现局部刷新

29，Ajax 解决浏览器缓存问题？
  1、在ajax发送请求前加上 anyAjaxObj.setRequestHeader("If-Modified-Since","0")。

  2、在ajax发送请求前加上 anyAjaxObj.setRequestHeader("Cache-Control","no-cache")。

  3、在URL后面加上一个随机数： "fresh=" + Math.random();。

  4、在URL后面加上时间搓："nowtime=" + new Date().getTime();。

  5、如果是使用jQuery，直接这样就可以了 $.ajaxSetup({cache:false})。这样页面的所有ajax都会执行这条语句就是不需要保存缓存记录。

30，同步和异步的区别?

同步的概念应该是来自于OS中关于同步的概念:不同进程为协同完成某项工作而在先后次序上调整(通过阻塞,唤醒等方式).同步强调的是顺序性.谁先谁后.异步则不存在这种顺序性.

同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求,等请求完，页面刷新，新内容出现，用户看到新内容,进行下一步操作。

异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求。等请求完，页面不刷新，新内容也会出现，用户看到新内容。

31，如何解决跨域问题?
 jsonp、 iframe、window.name、window.postMessage、服务器上设置代理页面

32，模块化开发怎么做？

立即执行函数,不暴露私有成员

     var module1 = (function(){
     　　　　var _count = 0;
     　　　　var m1 = function(){
     　　　　　　//...
     　　　　};
     　　　　var m2 = function(){
     　　　　　　//...
     　　　　};
     　　　　return {
     　　　　　　m1 : m1,
     　　　　　　m2 : m2
     　　　　};
     　　})();

33，AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？

 Asynchronous Module Definition，异步模块定义，所有的模块将被异步加载，模块加载不影响后面语句运行。所有依赖某些模块的语句均放置在回调函数中。

  区别：

     1. 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.
     2. CMD 推崇依赖就近，AMD 推崇依赖前置。看代码：

 // CMD
 define(function(require, exports, module) {
     var a = require('./a')
     a.doSomething()
     // 此处略去 100 行
     var b = require('./b') // 依赖可以就近书写
     b.doSomething()
     // ...
 })

 // AMD 默认推荐
 define(['./a', './b'], function(a, b) { // 依赖必须一开始就写好
     a.doSomething()
     // 此处略去 100 行
     b.doSomething()
     // ...
 })

34，requireJS的核心原理是什么？（如何动态加载的？如何避免多次加载的？如何
缓存的？）

35，异步加载JS的方式有哪些？
   (1) defer，只支持IE

   (2) async：

   (3) 创建script，插入到DOM中，加载完毕后callBack

36，documen.write和 innerHTML的区别
  document.write只能重绘整个页面

  innerHTML可以重绘页面的一部分

37，DOM操作——怎样添加、移除、移动、复制、创建和查找节点?
  （1）创建新节点
    createDocumentFragment()    //创建一个DOM片段
    createElement()   //创建一个具体的元素
    createTextNode()   //创建一个文本节点
  （2）添加、移除、替换、插入
    appendChild()
    removeChild()
    replaceChild()
    insertBefore() //在已有的子节点前插入一个新的子节点
  （3）查找
    getElementsByTagName()    //通过标签名称
    getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的)
    getElementById()    //通过元素Id，唯一性

38，.call() 和 .apply() 的区别？
      例子中用 add 来替换 sub，add.call(sub,3,1) == add(3,1) ，所以运行结果为：alert(4);

      注意：js 中的函数其实是对象，函数名是对 Function 对象的引用。

        function add(a,b)
        {
            alert(a+b);
        }

        function sub(a,b)
        {
            alert(a-b);
        }

        add.call(sub,3,1);

39，数组和对象有哪些原生方法，列举一下？

40，JS 怎么实现一个类。怎么实例化这个类

41，JavaScript中的作用域与变量声明提升？

42，如何编写高性能的Javascript？

43，那些操作会造成内存泄漏？

44，JQuery的源码看过吗？能不能简单概况一下它的实现原理？

45，jQuery.fn的init方法返回的this指的是什么对象？为什么要返回this？

46，jquery中如何将数组转化为json字符串，然后再转化回来？

47，jQuery 的属性拷贝(extend)的实现原理是什么，如何实现深拷贝？

48，jquery.extend 与 jquery.fn.extend的区别？
 * jquery.extend 为jquery类添加类方法，可以理解为添加静态方法
 * jquery.fn.extend:
     源码中jquery.fn = jquery.prototype，所以对jquery.fn的扩展，就是为jquery类添加成员函数
 使用：
 jquery.extend扩展，需要通过jquery类来调用，而jquery.fn.extend扩展，所有jquery实例都可以直接调用。

49，jQuery 的队列是如何实现的？队列可以用在哪些地方？

50，谈一下Jquery中的bind(),live(),delegate(),on()的区别？


51，JQuery一个对象可以同时绑定多个事件，这是如何实现的？

52，是否知道自定义事件。jQuery里的fire函数是什么意思，什么时候用？

53，jQuery 是通过哪个方法和 Sizzle 选择器结合的？（jQuery.fn.find()进入Sizzle）

54，针对 jQuery性能的优化方法？

55，Jquery与jQuery UI 有啥区别？
    *jQuery是一个js库，主要提供的功能是选择器，属性修改和事件绑定等等。

    *jQuery UI则是在jQuery的基础上，利用jQuery的扩展性，设计的插件。
     提供了一些常用的界面元素，诸如对话框、拖动行为、改变大小行为等等

56，JQuery的源码看过吗？能不能简单说一下它的实现原理？

57，jquery 中如何将数组转化为json字符串，然后再转化回来？

58，jQuery中没有提供这个功能，所以你需要先编写两个jQuery的扩展：
    $.fn.stringifyArray = function(array) {
        return JSON.stringify(array)
    }

    $.fn.parseArray = function(array) {
        return JSON.parse(array)
    }

    然后调用：
    $("").stringifyArray(array)

59，jQuery和Zepto的区别？各自的使用场景？

60，针对 jQuery 的优化方法？
 *基于Class的选择性的性能相对于Id选择器开销很大，因为需遍历所有DOM元素。

 *频繁操作的DOM，先缓存起来再操作。用Jquery的链式调用更好。
  比如：var str=$("a").attr("href");

 *for (var i = size; i < arr.length; i++) {}
  for 循环每一次循环都查找了数组 (arr) 的.length 属性，在开始循环的时候设置一个变量来存储这个数字，可以让循环跑得更快：
  for (var i = size, length = arr.length; i < length; i++) {}

61，Zepto的点透问题如何解决？

62，jQueryUI如何自定义组件?

63，需求：实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。给出你的技术实现方案？

64，如何判断当前脚本运行在浏览器还是node环境中？（阿里）
  this === window ? 'browser' : 'node';

  通过判断Global对象是否为window，如果不为window，当前脚本没有运行在浏览器中

65，移动端最小触控区域是多大？

66，jQuery 的 slideUp动画 ，如果目标元素是被外部事件驱动, 当鼠标快速地连续触发外部元素事件, 动画会滞后的反复执行，该如何处理呢?
jquery stop(): 如：$("#div").stop().animate({width:"100px"},100);

67，把 Script 标签 放在页面的最底部的body封闭之前 和封闭之后有什么区别？浏览器会如何解析它们？

68，移动端的点击事件的有延迟，时间是多久，为什么会有？ 怎么解决这个延时？（click 有 300ms 延迟,为了实现safari的双击事件的设计，浏览器要知道你是不是要双击操作。）

69，知道各种JS框架(Angular, Backbone, Ember, React, Meteor, Knockout…)么? 能讲出他们各自的优点和缺点么?

70，Underscore 对哪些 JS 原生对象进行了扩展以及提供了哪些好用的函数方法？

71，解释JavaScript中的作用域与变量声明提升？

72，那些操作会造成内存泄漏？
内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。
 垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为 0（没有其他对象引用过该对象），或对该对象的惟一引用是循环的，那么该对象的内存即可回收。

 setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。
 闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）

73，JQuery一个对象可以同时绑定多个事件，这是如何实现的？
 * 多个事件同一个函数：
     $("div").on("click mouseover", function(){});
 * 多个事件不同函数
     $("div").on({
         click: function(){},
         mouseover: function(){}
     });
74，Node.js的适用场景？

75，(如果会用node)知道route, middleware, cluster, nodemon, pm2, server-side rendering么?

76，解释一下 Backbone 的 MVC 实现方式？

77，什么是“前端路由”?什么时候适合使用“前端路由”? “前端路由”有哪些优点和缺点?

78，知道什么是webkit么? 知道怎么用浏览器的各种工具来调试和debug代码么?

  Chrome,Safari浏览器内核。

80，如何测试前端代码么? 知道BDD, TDD, Unit Test么? 知道怎么测试你的前端工程么(mocha, sinon, jasmin, qUnit..)?

81，前端templating(Mustache, underscore, handlebars)是干嘛的, 怎么用?

82，简述一下 Handlebars 的基本用法？

83，简述一下 Handlerbars 的对模板的基本处理流程， 如何编译的？如何缓存的？

84，用js实现千位分隔符?(来源：前端农民工，提示：正则+replace)

    function commafy(num) {
        return num && num
            .toString()
            .replace(/(\d)(?=(\d{3})+\.)/g, function($0, $1) {
                return $1 + ",";
            });
    }
    console.log(commafy(1234567.90)); //1,234,567.90

85，检测浏览器版本版本有哪些方式？
  功能检测、userAgent特征检测

  比如：navigator.userAgent
  //"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWebKit/537.36
    (KHTML, like Gecko) Chrome/41.0.2272.101 Safari/537.36"

86，What is a Polyfill?
 polyfill 是“在旧版浏览器上复制标准 API 的 JavaScript 补充”,可以动态地加载 JavaScript 代码或库，在不支持这些标准 API 的浏览器中模拟它们。
  例如，geolocation（地理位置）polyfill 可以在 navigator 对象上添加全局的 geolocation 对象，还能添加 getCurrentPosition 函数以及“坐标”回调对象，
  所有这些都是 W3C 地理位置 API 定义的对象和函数。因为 polyfill 模拟标准 API，所以能够以一种面向所有浏览器未来的方式针对这些 API 进行开发，
  一旦对这些 API 的支持变成绝对大多数，则可以方便地去掉 polyfill，无需做任何额外工作。

87，做的项目中，有没有用过或自己实现一些 polyfill 方案（兼容性处理方案）？
 比如： html5shiv、Geolocation、Placeholder

88，我们给一个dom同时绑定两个点击事件，一个用捕获，一个用冒泡。会执行几次事件，会先执行冒泡还是捕获？

89，使用JS实现获取文件扩展名？
  function getFileExtension(filename) {
    return filename.slice((filename.lastIndexOf(".") - 1 >>> 0) + 2);
  }

  String.lastIndexOf() 方法返回指定值（本例中的'.'）在调用该方法的字符串中最后出现的位置，如果没找到则返回 -1。
  对于'filename'和'.hiddenfile'，lastIndexOf的返回值分别为0和-1无符号右移操作符(»>) 将-1转换为4294967295，将-2转换为4294967294，这个方法可以保证边缘情况时文件名不变。
  String.prototype.slice() 从上面计算的索引处提取文件的扩展名。如果索引比文件名的长度大，结果为""。

90，Object.is() 与原来的比较操作符“ ===”、“ ==”的区别？

  两等号判等，会在比较时进行类型转换；
  三等号判等(判断严格)，比较时不进行隐式类型转换,（类型不同则会返回false）；

  Object.is 在三等号判等的基础上特别处理了 NaN 、-0 和 +0 ，保证 -0 和 +0 不再相同，
  但 Object.is(NaN, NaN) 会返回 true.

   Object.is 应被认为有其特殊的用途，而不能用它认为它比其它的相等对比更宽松或严格。


for (var i = 0; i < 5; i++) {
    setTimeout(function() {
        console.log(new Date, i);
}, 1000);
}
console.log(new Date, i);

结果
2017-03-18T00:43:45.873Z 5
2017-03-18T00:43:46.866Z 5
2017-03-18T00:43:46.868Z 5
2017-03-18T00:43:46.868Z 5
2017-03-18T00:43:46.868Z 5
2017-03-18T00:43:46.868Z 5

60% 的人会描述为：5 -> 5 -> 5 -> 5 -> 5，即每个 5 之间都有 1 秒的时间间隔；

改成闭包
1---------
for (var i = 0; i < 5; i++) {
    (function(j) {  // j = i
        setTimeout(function() {
            console.log(new Date, j);
        }, 1000);
    })(i);
}
console.log(new Date, i);
2---------
var output = function (i) {
    setTimeout(function() {
        console.log(new Date, i);
    }, 1000);
};
for (var i = 0; i < 5; i++) {
    output(i);  // 这里传过去的 i 值被复制了
}
console.log(new Date, i);
3---------
for (let i = 0; i < 5; i++) {
    setTimeout(function() {
        console.log(new Date, i);
    }, 1000);
}
console.log(new Date, i); // i 会报错

继续追问：如果期望代码的输出变成 0 -> 1 -> 2 -> 3 -> 4 -> 5，并且要求原有的代码块中的循环和两处 console.log 不变，该怎么改造代码？新的需求可以精确的描述为：代码执行时，立即输出 0，之后每隔 1 秒依次输出 1,2,3,4，循环结束后在大概第 5 秒的时候输出 5（这里使用大概，是为了避免钻牛角尖的同学陷进去，因为 JS 中的定时器触发时机有可能是不确定的
简单粗暴版，但是不会加分
for (var i = 0; i < 5; i++) {
    (function(j) {
        setTimeout(function() {
            console.log(new Date, j);
        }, 1000 * j));  // 这里修改 0~4 的定时器时间
    })(i);
}
setTimeout(function() { // 这里增加定时器，超时设置为 5 秒
    console.log(new Date, i);
}, 1000 * i);
------
考察ES6用Promise
const tasks = [];
for (var i = 0; i < 5; i++) {   // 这里 i 的声明不能改成 let，如果要改该怎么做？
    ((j) => {
        tasks.push(new Promise((resolve) => {
            setTimeout(() => {
                console.log(new Date, j);
                resolve();  // 这里一定要 resolve，否则代码不会按预期 work
            }, 1000 * j);   // 定时器的超时时间逐步增加
        }));
    })(i);
}

Promise.all(tasks).then(() => {
    setTimeout(() => {
        console.log(new Date, i);
    }, 1000);   // 注意这里只需要把超时设置为 1 秒
});

//promise 版本2
const tasks = []; // 这里存放异步操作的 Promise
const output = (i) => new Promise((resolve) => {
    setTimeout(() => {
        console.log(new Date, i);
        resolve();
    }, 1000 * i);
});
// 生成全部的异步操作
for (var i = 0; i < 5; i++) {
    tasks.push(output(i));
}

// 异步操作完成之后，输出最后的 i
Promise.all(tasks).then(() => {
    setTimeout(() => {
        console.log(new Date, i);
    }, 1000);
});

接着考察ES7 用 async await 让代码更简洁
// 模拟其他语言中的 sleep，实际上可以是任何异步操作
const sleep = (timeountMS) => new Promise((resolve) => {
    setTimeout(resolve, timeountMS);
});
(async () => {  // 声明即执行的 async 函数表达式
    for (var i = 0; i < 5; i++) {
        await sleep(1000);
        console.log(new Date, i);
    }

    await sleep(1000);
    console.log(new Date, i);
})();
