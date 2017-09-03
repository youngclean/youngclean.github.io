官方定义：一个元素盒子的位置和大小有时相对于某个矩形来计算的，此矩形称为此元素的包含块。
简写为：C.B.

有以下几种情况：

1、根元素所在的包含块是一个长方形，称为初始的包含块。

2、假如元素的position设为‘relative’或‘static’，包含块是由最近的父容器块的内容区边缘形成的。

3、假如元素的position设为‘fixed’，包含块是由所在的viewpoint或page area决定。

4、假如元素的position设为‘absolute’，包含块是由最近带有‘position’属性的祖先决定。
 - 祖先元素是行内元素，包含块是第一个和最后一个内联盒子所包围的填充盒子，在CSS2.1，行内元素跨越多行，那么包含块是未定义的，否则，包含块是由祖先的补白形成。（~~翻译的有些不清楚~~）

  **假如没有那样的祖先，包含块就是初始 C.B.**

代码示例：

    <!DOCTYPE HTML">
    <html>
        <head>
           <TITLE>Illustration of containing blocks</TITLE>
        </head>
        <body id="body">
            <div id="div1">
                <p id="p1">This is text in the first paragraph...</P>
                <p id="p2">This is text <em id="em1"> in the 
                <strong id="strong1">second</strong> paragraph.</em></P>
           </div>
        </body></html>

元素 --- 包含块

html --- 初始 C.B.

body --- html

div1 --- body

p1 --- div1

p2 --- div1

em1 --- p2

strong1 --- p2


假如设置div1:

    #div1 { position: absolute; left: 50px; top: 50px }

div1的包含块将不是body，而变成html.

假如也设置em1:

    #div1 { position: absolute; left: 50px; top: 50px }
    #em1  { position: absolute; left: 100px; top: 100px }
上述包含块发生什么变化？

元素 --- 包含块

body --- html

**div1 --- 初始 C.B.**

p1 --- div1

p2 --- div1

**em1 --- div1**

strong1 --- p2

W3c传送门：[containing-block-details][1]

参考：

1、[CSS核心：包含块（Containing Block）][2]

2、[CSS 中，为什么绝对定位（absolute）的父级元素必须是相对定位（relative）？][3]

  [1]: http://www.w3.org/TR/2011/REC-CSS2-20110607/visudet.html#containing-block-details
  [2]: http://www.ddcat.net/blog/?p=1336
  [3]: http://www.zhihu.com/question/19926700