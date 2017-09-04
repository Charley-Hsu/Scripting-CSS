# Scripting-CSS 
将会写一些关于javascript脚本化CSS知识点的内容
------


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

> * 1.如果一个CSS属性名包含一个或多个连字符，CSSStyleDeclaration属性名的格式应该是移除连字符，将每个连字符后面紧接着的字母大写

| background-color | backgroundColor |
 | :--- | :--- |
> * 2.Shorthand属性可以支持属性缩写
```javascript
test.style.border = '5px solid red';
```
> * 3.当一个CSS属性(如float)在JavaScript中对应的名字是保留字时，在之前加"css"前缀来创建合法的属性。

 | float | cssFloat |
 | :--- | :--- |

> * 4.如果设置的行间样式不符合预定格式，并不会报错，而是静默失败
> * 5.IE8-浏览器支持给属性设置值时不带单位
```javascript
test.style.height = '20';
```
> * 6.如果读取没有设置过的行间样式将返回空字符串 ' '
> * 7.当颜色属性设置为16进制颜色时，IE8-浏览器查询属性会返回对应rgb颜色。

## 2.3Properties

> *  1. **CSSStyleDeclaration.cssText**
    声明块的文本内容。设置这个属性会改变样式。 
    *IE8-浏览器返回的属性名是全大写的。*
    IE8-浏览器返回&#39;HEIGHT:40px;WIDTH:40px;&#39;其他浏览器返回&#39;height: 40px; width: 40px;&#39;

> *  2. **CSSStyleDeclaration.length**
    length属性返回内联样式中的样式个数。
    <i class="icon-warning-sign"></i>
    *IE8-浏览器不支持*

> *   3. **CSSStyleDeclaration.parentRule**
    parentRule属性表示CSS信息的CSSRule对象。
    *IE8-浏览器不支持*

### 2.4Method

> *  1. **getPropertyPriority()**
    返回可选的优先级，如果给定的属性使用了!important设置，则返回&quot;important&quot;；否则返回空字符串。
    *IE8-浏览器不支持*
    
    ```javascript
     priString= styleObj.getPropertyPriority(&#39;color&#39;)
     ```

> *  2. **getPropertyValue()**
    返回给定属性的值，字符串类型。
    
    ```javascript
    valString= styleObj.getPropertyValue(&#39;color&#39;)
    ```
    *IE8-浏览器不支持*

> *  3. **item()**
    返回给定位置的CSS属性的名称，也可以使用方括号语法
    
    ``` javascript
    nameString= styleObj.item(0)
    Or: nameString= styleObj[0]
    ```
    *IE8-浏览器不支持item()方法，只支持方括号语法*

> *  4. **removeProperty()**
    从样式中删除给定属性，并返回被删除属性的属性值
    
    ``` javascript 
    var String= styleObj.removeProperty(&#39;color&#39;)
    ```
    *IE8-浏览器不支持*

1. setProperty()

setProperty(propertyName,value,priority)方法将给定属性设置为相应的值，并加上优先级标志(&quot;important&quot;或一个空字符串)，该方法无返回值

Example: styleObj.setProperty(&#39;color&#39;, &#39;red&#39;, &#39;important&#39;)

IE8-浏览器不支持

1. getPropertyCSSValue()

返回包含两个属性的CSSRule类型，这两个属性分别是cssText和cssValueType。其中cssText属性的值与getPropertyValue()返回的值相同，而cssValueType属性则是一个数值常量，表示值的类型：0表示继承的值，1表示基本的值，2表示值列表，3表示自定义的值

Example: cssString= window.getComputedStyle(elem, null).getPropertyCSSValue(&#39;color&#39;).cssText;

不支持大部分浏览器，支持的部分浏览器也经常性的抛出错误，不就将会被放弃，所以不要使用。

1. 3.查询计算出的样式

### 3.1Description

let title = document.getElementById(&quot;section1title&quot;);

let titlestyles = window.getComputedStyle(element,null);

元素的渲染结果是多个CSS样式博弈后的最终结果，这也是CSS中的C(cascade)层叠的含义。

元素的计算样式是一组属性值，它由浏览器通过把内联样式结合所有链接样式表中所有可应用的样式规则后导出（或计算）得到的,是元素最终呈现时使用的属性值。

### 3.2 Method

**getComputedStyle()**

getComputedStyle()方法原本是window对象下的方法，DOM Level 2 Style中增强了该方法，所以getComputedStyle()方法一共有下面3种写法：

-
  -
    -
      - defaultView.getComputedStyle(div).width
      - getComputedStyle(div).width
      - getComputedStyle(div).width

getComputedStyle()方法接收两个参数：第一个是要取得计算样式的元素，第二个是一个伪元素字符串。如果不需要伪元素信息，第二个参数可以是null，如果没有默认为null（The pseudo-element or null if none.）。

getComputedStyle()方法返回一个CSSStyleDeclaration对象，其中包含当前元素的所有计算的样式。

### 3.3Notes

1. 计算样式的属性是只读的；
2. 计算样式的值是绝对值，类似百分比和点之类相对的单位将全部转换绝对值。所有指定尺寸的属性都有一个以像素为度量单位的值。该值将是一个冠以&quot;px&quot;后缀的字符串，使用时仍然需要解析它，但是不用担心单位的解析或转换。其值是颜色的属性将以&quot;rgb（#，#，#）&quot;或&quot;rgba（#，#，#，#）&quot;的格式返回;
3. 计算样式的cssText属性未定义；
4. 对于font、background、border等复合属性。chrome会返回整个复合样式，而IE9+、firefox和safari则输出空字符串&quot; &quot;
5. 在CSS3 的动画中，Firefox 的getComputedSytle会返回原始的属性值， 但在Webkit的浏览器中会返回最终属性值.
6. 如果没有使用绝对定位，试图通过计算样式的top和left属性会返回&quot;auto&quot;。
7. 在Firefox中，属性值为auto的会直接返回 used value, 而不是 &#39;auto&#39;。 比如，你在设定了一个元素的样式为&quot;height:30px; top: auto; bottom:0;&quot;  它的父元素样式为&quot;height:100px;&quot; 那么top的Computed value 为 &quot;auto&quot;,  used value 为 &#39;70px&#39; = 100px - 30px;
8. 计算样式具有欺骗性：

比如font-family属性：为了适应跨平台可移植性，可能会接受字体列表，当查询一个计算样式的fontFamily属性时，可能返回一系列的字体如&quot;arial,helvetica,san-serif&quot;，而无法告诉你实际使用哪种字体。

比如，浏览者看过某个网站， 它的链接通常会变成蓝色带下划线的链接，通过判断链接的颜色（getComputedSytle(node, null).color) 是否为蓝色，就会泄露用户的浏览历史， 所以浏览器会特意返回不准确的值，保护用户隐私。

### 3.4        IE-浏览器

IE8-浏览器不支持getComputedStyle()方法，但在IE中每个具有style属性的元素有一个currentStyle属性，这个属性是CSSStyleDeclaration的实例，currentStyle属性中的计算样式并不会输出复合样式，对颜色、百分比设置不会进行相应转换，而是原样输出。

IE8-浏览器无法对opacity属性进行正常渲染，但可以读出opacity属性的值。

IE9+浏览器的getComputedStyle()方法以及IE浏览器的currentStyle属性有一个特别的地方，就是可以识别自定义样式的值，虽然无法正常渲染，但是可以取出值。

&lt;div id=&quot;test&quot; style=&quot;a:1&quot;&gt;&lt;/div&gt;

&lt;script&gt;

//其他浏览器输出undefined，而IE9+浏览器输出1

console.log(getComputedStyle(test).a);

//其他浏览器输出undefined，而IE浏览器输出1

console.log(test.currentStyle.a);

&lt;/script&gt;

1. 4.脚本化CSS类

### 4.1Description

var test = document.getElementById(&quot;test&quot;);

test.className = &#39;small&#39;;

改变了元素的class就改变了应用于元素的一组样式表选择器，它能在同一时刻改变多个CSS属性。

相比于修改cssText，修改class类具有更好的性能体验。

### 4.2Used

**className**

更改为已经提前设置好的类名改变样式。

只能指定零个或一个类名，如果有多个类名就无法工作了。

**classList**

为了解决上面的问题，HTML5给元素定义了classList属性。该属性的值是DOMTokenList对象：一个只读的类数组对象，它包含元素的单独类名。它表示了实时元素类名的集合，修改后在className属性中及时可见。

### 4.3 Method

1. 使用 **add** 方法，可以往页面元素是新增一个或多个css类：

myDiv.classList.add(&#39;myCssClass&#39;);

IE-浏览器不支持多参数传递

1. 使用 **remove** 方法，可以删除单个CSS类：

myDiv.classList.remove(&#39;myCssClass&#39;);

删除不存在的类不会引发错误。

IE-浏览器不支持多参数传递

1. 使用 **toggle** 方法，可以反转CSS类的有无

myDiv.classList.toggle(&#39;myCssClass&#39;);

当只有一个参数存在时：切换类值; 即，如果它是类存在，那么删除它并返回false，如果没有，那么添加它并返回true。

当存在第二个参数时：如果第二个参数的值为true，则添加指定的类值，如果它的值为false，则将其删除。

IE-浏览器不支持第二个参数

1. 使用 **contains** 方法，检查是否含有某个CSS类

myDiv.classList.contains(&#39;myCssClass&#39;); //returns true or false

1. 使用 **replace** 方法，用新类替换现有的CSS类

myDiv.classList.replace(&quot;foo&quot;, &quot;bar&quot;);

仅chrome和Firefox浏览器支持

1. 5.脚本化样式表

### 5.1Description

var firstRule = document.styleSheets[0].cssRules[0];

除了可以单独设置和查询某一个元素或者类的样式之外，也可以对样式表进行脚本化操作。

在脚本化样式表时，将会碰到两类需要使用的对象。第一类是元素对象，由&lt;style&gt;和&lt;link&gt;元素表示，两种元素包含或引用样式表。这些是常规的文档元素，如果他们有id属性值，可以使用document.getElementById()函数来选择它们。第二类是CSSStyleSheet对象，它表示样式表本身。document.styleSheets属性是一个只读的类数组对象，它包含CSSStyleSheet对象，表示与文档关联在一起的样式表。

如果为定义或引用了样式表的&lt;style&gt;或&lt;link&gt;元素设置title属性值，该title作为对应CSSStyleSheet对象的title属性就可以。

### 5.2Used

- **开启和关闭样式表**

&lt;style&gt;、&lt;link&gt;元素和CSSStyleSheet对象都定义了一个在javascript中可以设置和查询的disabled属性。顾名思义，如果disabled属性为true，样式表就被浏览器关闭并忽略。

Example：document.styleSheets[0].disabled=true;

- **查询、插入、删除样式表**

document.styleSheets[]数组的元素是CSSStyleSheet对象。CSSStyleSheet对象有一个cssRules[]数组，它包含所有样式表规则。

Example：var firstRule = document.styleSheets[0].cssRules[0];

Note: IE8及更早版本实现的API和其它浏览器实现的标准API之间有一些轻微的区别。IE使用不同的属性名rules代替cssRules。后面将会提到二者之间细微的区别。

- **创建新的样式表**

创建整个新样式表并将其添加到文档是中可能的。在大多数浏览器中，可以用标准的DOM技术:只要创建一个新的&lt;style&gt;元素，将其插入到文档的头部,然后用其innerHTML属性来设置样式表内容。但是在IE8以及更早的版本中，CSSStyleSheet对象通过非标准方法document.createStyleSheet()来创建，其样式文本用cssText属性值来指定。

### 5.3Properties

- **CSSStyleSheet对象**

CSSStyleSheet对象只是一个类数组对象，它继承自Stylesheet。CSSStyleSheet具有以下属性：

| **属性** | **描述** | **备注** |
| --- | --- | --- |
| 从Stylesheet接口继承的属性 |
| disabled | 是否禁用。 |   |
| href | 如果样式表是通过&lt;link&gt;包含的，则表示样式表的URL；否则，是null。 |   |
| media | media属性表示当前样式表支持的所有媒体类型的集合MediaList。 | IE8-浏览器，media是一个反映&lt;link&gt;和&lt;style&gt;元素media特性值的字符串。 |
| ownerNode | ownerNode属性返回StyleSheet对象所在的DOM节点，通常是&lt;link&gt;或&lt;style&gt;。如果当前样式表通过@import导入的，则这个属性值为null。 | IE8-浏览器不支持。 |
| parentStyleSheet | 如果当前样式表是通过@import导入的，这个属性是一个指向导入它的样式表的指针，否则为null |   |
| title | title属性表示ownerNode中title属性的值 |   |
| type | type属性表示样式表类型的字符串。对CSS样式表而言，这个字符串是&quot;type/css&quot; |   |
| cssText | 样式表中所有样式的字符串表示 | 只有IE浏览器支持 |
| 自有属性 |
| cssRules | 样式表中包含的样式规则的集合 | IE8-浏览器不支持cssRules属性，但有一个类似的rules属性。Firefox不支持rules属性。 |
| ownerRule | 如果样式表是通过@import导入的，ownerRule属性就是一个指针，指向表示导入的规则；否则，值为null | IE8-浏览器不支持。 |

- **CSSRule对象**

CSSRule对象表示样式表中的每一条规则。实际上，CSSRule是一个供其他多种类型继承的基类型，其中最常见的就是CSSStyleRule类型，表示样式信息。其他规则还包括@import、@font-face、@page和@charset。

CSSRule对象列表可以通过CSSStyleSheets对象的cssRules属性或ruls属性得到

document.styleSheets[0].cssRules[0] || document.styleSheets[0].rules[0]

| **属性** | **描述** | **备注** |
| --- | --- | --- |
| cssText | cssText属性返回整条规则对应的文本 | IE8-浏览器不支持。 |
| style | style属性返回一个CSSStyleDeclaration对象，通过它设置和取得规则中特定的样式值 |   |
| selectorText | selectorText属性返回当前规则的选择符文本 |   |
| parentRule | 如果当前规则是导入的规则，这个属性引用的就是导入规则；否则，这个值为null | IE8-浏览器不支持。 |
| parentStyleSheet | 表示当前规则所属的样式表 | IE8-浏览器不支持。 |
| type | 返回一个整数值，表示当前规则的类型 | 1：样式规则 3：输入规则4：Media规则5：字体规则IE8-浏览器不支持。 |

### 5.4 Method

**CSSStyleSheet对象中的方法：**

- **insertRule()**

insertRule(rule,index)方法表示向cssRules集合中指定的位置插入rule字符串，并返回当前样式表的索引值。

document.styleSheets[0].insertRule(&#39;div{color:red;}&#39;,0)

Note：IE8-浏览器方法addRule(ruleKey,ruleValue,index)向cssRules集合中指定的位置插入rule字符串，并返回-1。

      Firefox浏览器不支持。

- **deleteRule()**

deleteRule(index)方法删除cssRules集合中指定位置的规则，无返回值。document.styleSheets[0].deleteRule(0)

Note：IE8-浏览器方法removeRule(index)方法删除cssRules集合中指定位置的规则，无返回值。

Firefox浏览器不支持。
