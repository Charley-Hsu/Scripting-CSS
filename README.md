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
> 类似大多数HTML属性，style也是元素对象的属性，它可以在javascript操作，但是style属性不同：它的值不是字符串，而是一个CSSStyleDeclaration对象。该style对象的javascript属性代表了HTML代码中通过style指定的css属性。
## 2.2Used
常用javascript操作css属性对应列表：

| **CSS** | **JavaScript** |
| :--- | :--- |
| background | background |
| background-attachment | backgroundAttachment |
| background-color | backgroundColor |
| background-image | backgroundImage |
| background-position | backgroundPosition |
| background-repeat | backgroundRepeat |
| border | border |
| border-bottom | borderBottom |
| border-bottom-color | borderBottomColor |
| border-bottom-style | borderBottomStyle |
| border-bottom-width | borderBottomWidth |
| border-color | borderColor |
| border-left | borderLeft |
| border-left-color | borderLeftColor |
| border-left-style | borderLeftStyle |
| border-left-width | borderLeftWidth |
| border-right | borderRight |
| border-right-color | borderRightColor |
| border-right-style | borderRightStyle |
| border-right-width | borderRightWidth |
| border-style | borderStyle |
| border-top | borderTop |
| border-top-color | borderTopColor |
| border-top-style | borderTopStyle |
| border-top-width | borderTopWidth |
| border-width | borderWidth |
| clear | clear |
| clip | clip |
| color | color |
| cursor | cursor |
| display | display |
| filter | filter |
| font | font |
| font-family | fontFamily |
| font-size | fontSize |
| font-variant | fontVariant |
| font-weight | fontWeight |
| height | height |
| left | left |
| letter-spacing | letterSpacing |
| line-height | lineHeight |
| list-style | listStyle |
| list-style-image | listStyleImage |
| list-style-position | listStylePosition |
| list-style-type | listStyleType |
| margin | margin |
| margin-bottom | marginBottom |
| margin-left | marginLeft |
| margin-right | marginRight |
| margin-top | marginTop |
| overflow | overflow |
| padding | padding |
| padding-bottom | paddingBottom |
| padding-left | paddingLeft |
| padding-right | paddingRight |
| padding-top | paddingTop |
| page-break-after | pageBreakAfter |
| page-break-before | pageBreakBefore |
| position | position |
| float | cssFloat |
| text-align | textAlign |
| text-decoration | textDecoration |
| text-decoration: blink | textDecorationBlink |
| text-decoration: line-through | textDecorationLineThrough |
| text-decoration: none | textDecorationNone |
| text-decoration: overline | textDecorationOverline |
| text-decoration: underline | textDecorationUnderline |
| text-indent | textIndent |
| text-transform | textTransform |
| top | top |
| vertical-align | verticalAlign |
| visibility | visibility |
| width | width |
| z-index | zIndex |
