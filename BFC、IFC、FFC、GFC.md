# FC
FC是Formatting Context的简写，直译过来是格式化上下文，FC就是html页面中的某个元素内的一套渲染规则，决定了其子元素如何布局，以及和其他元素在html页面中的位置。

**如何触发XFC（X为B，I，G，F之一）？**
通过设置某个元素的某些属性值来使得该元素应用某种渲染规则。例如将一个div的display属性设置为grid，那么就称触发了GFC，该元素内就形成了一个GFC,该元素内的渲染规则就要使用GFC规则。

## BFC（块级格式化上下文）
BFC（Block Formatting Context）叫做“块级格式化上下文”。BFC的布局规则例如以下：

1.内部的盒子会在垂直方向，一个个地放置；

2.盒子垂直方向的距离由margin决定，**属于同一个BFC的两个相邻Box的上下margin会发生重叠**；

3.每一个元素的左边，与包括的盒子的左边相接触，即使存在浮动也是如此；

4.BFC的区域不会与float重叠；

5.BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此；

6.计算BFC的高度时，浮动元素也參与计算。

触发BFC的条件。

1.根元素。

2.float的属性为left right；

3.position为absolute或fixed；

4.display为inline-block。table-cell，table-caption。flex；

5.overflow为hidden scroll auto。

## IFC（内联格式化上下文）

## FFC（弹性格式化上下文）
## GFC （网格格式化上下文）