# Scripting-CSS 
将会写一些关于javascript脚本化CSS知识点的内容
------
## 0.什么是脚本化CSS
脚本化CSS简单来说就是通过JavaScript脚本的方式对页面元素的css样式进行动态的增删改查。
------
## 1.前释
*默认文章阅览者具有一定的CSS和HTML基础
> CSSStyleDeclaration：是style的属性的一个样式声明对象，表示一个CSS属性键值对的集合;
------
Javascript有3种对象可以被用作查询和修改CSS。

| 对象| 浏览器支持   |  备注  |
| -----                     | :-----:        | :----:        |
| Style(CSSStyleDeclaration)| IE7以上全浏览器 |               |
| currentStyle              |   IE&Opera2    |只能查询不能修改|
| runtimeStyle              |    IE          |只能添加和修改  | 
------
## 2.脚本化内联样式
## 2.1Description
```javascript
var test = document.getElementById("test"); 
test.style.border = '5px solid red';
```
> 类似大多数HTML属性，style也是元素对象的属性，它可以在javascript操作，但是style属性不同寻常：它的值不是字符串，而是一个CSSStyleDeclaration对象。该style对象的javascript属性代表了HTML代码中通过style指定的css属性。
## 2.2Used
常用javascript操作css属性对应列表：
