# BFC
BFC（Block Formatting Context）叫做“块级格式化上下文”。BFC的布局规则例如以下：

1.内部的盒子会在垂直方向，一个个地放置；

2.盒子垂直方向的距离由margin决定，**属于同一个BFC的两个相邻Box的上下margin会发生重叠**；

3.每一个元素的左边，与包括的盒子的左边相接触，即使存在浮动也是如此；

4.BFC的区域不会与float重叠；

5.BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此；

6.计算BFC的高度时，浮动元素也參与计算。

会产生BFC的元素。

1.根元素。

2.float的属性不为none；

3.position为absolute或fixed；

4.display为inline-block。table-cell，table-caption。flex；

5.overflow不为visible