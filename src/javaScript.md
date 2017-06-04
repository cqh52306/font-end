### 在String对象上定义一个repeatify函数。这个函数接受一个整数参数，来明确字符串需要重复几次
    这个函数要求字符串重复指定的次数。举个例子：
    ```js
    console.log('hello'.repeatify(3));//hellohellohello
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