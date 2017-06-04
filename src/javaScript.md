### 在String对象上定义一个repeatify函数。这个函数接受一个整数参数，来明确字符串需要重复几次
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

### 介绍js的基本数据类型。
  Undefined、Null、Boolean、Number、String、
  ECMAScript 2015 新增:Symbol(创建后独一无二且不可变的数据类型 )

### 介绍js的数据类型。
  6种基本类型 Undefined、Null、Boolean、Number、String、Symbol
  一种引用类型 Object

### 介绍js有哪些内置对象？
 Object 是 JavaScript 中所有对象的父对象
 数据封装类对象：Object、Array、Boolean、Number 和 String
 其他对象：Function、Arguments、Math、Date、RegExp、Error

### 说几条写JavaScript的基本规范？
 1.不要在同一行声明多个变量。  
 2.请使用 ===/!==来比较true/false或者数值  
 3.使用对象字面量替代new Array这种形式  
 4.不要使用全局函数。  
 5.Switch语句必须带有default分支  
 6.函数不应该有时候有返回值，有时候没有返回值。  
 7.For循环必须使用大括号  
 8.If语句必须使用大括号  
 9.for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。  

### JavaScript原型，原型链 ? 有什么特点？
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
### JavaScript有几种类型的值？，你能画一下他们的内存图吗？

 栈：原始数据类型（Undefined，Null，Boolean，Number、String）  
 堆：引用数据类型（对象、数组和函数）  

 两种类型的区别是：存储位置不同；  
 原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；  
 引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体  

### 如何将字符串转化为数字，例如’12.3b’?
  * parseFloat('12.3b');  
  * 正则表达式，`'12.3b'.match(/(\d)+(\.)?(\d)+/g)[0] * 1`, 但是这个不太靠谱，提供一种思路而已。

### 如何将浮点数点左边的数每三位添加一个逗号，如12000000.11转化为『12,000,000.11』?
 ```js
  function commafy(num){
      return num && num
          .toString()
          .replace(/(\d)(?=(\d{3})+\.)/g, function($1, $2){
              return $2 + ',';
          });
  }
 ```

### 如何实现数组的随机排序？

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
  ```javascript
    var arr = [1,2,3,4,5,6,7,8,9,10];
    arr.sort(function(){
        return Math.random() - 0.5;
    })
    console.log(arr);
  ```

### Javascript如何实现继承？

 1、构造继承  
 2、原型继承  
 3、实例继承  
 4、拷贝继承  

 原型prototype机制或apply和call方法去实现较简单，建议使用构造函数与原型混合方式。
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