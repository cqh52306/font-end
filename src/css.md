### 介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？

  （1）有两种， IE 盒子模型、W3C 盒子模型；  
  （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；  
  （3）区  别： IE的content部分把 border 和 padding计算了进去;  

### 实现不使用 border 画出1px高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。

 `<div style="height:1px;overflow:hidden;background:red"></div>`

### CSS选择符有哪些？哪些属性可以继承？
  *   1.id选择器（ # myid）  
      2.类选择器（.myclassname）  
      3.标签选择器（div, h1, p）  
      4.相邻选择器（h1 + p）  
      5.子选择器（ul > li）  
      6.后代选择器（li a）  
      7.通配符选择器（ * ）  
      8.属性选择器（a[rel = "external"]）  
      9.伪类选择器（a:hover, li:nth-child）  

  *   可继承的样式： font-size font-family color, UL LI DL DD DT;  

  *   不可继承的样式：border padding margin width height ;