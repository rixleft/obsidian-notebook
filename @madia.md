### 媒体查询
使用@media查询，可以针对不同的媒体类型定义不同的样式，@media可以针对不同的屏幕尺寸设置不同的样式，特别是如果你需要设置设计响应式的页面，@media 是非常有用的。当重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面。

- @media 设备（all screen speech print）（范围）{对应的css}
- @media 设备 （所有 电脑手机等 阅读器 打印）and（范围）and（范围）and（范围）......{对应的css}
- `@media not|only mediatype and (mediafeature and|or|not mediafeature) {CSS-Code;}`
- 下列css代码表示宽度为500像素到700像素之间时，`<body>`的背景色为蓝色。
```css
	@media (min-width:500px) and (max-width:700px) {
            body {
                background: blue;
            }
```

在媒体查询功能里显示`display:none`和隐藏`display:block`比较常用   
注意：如果使用了弹性盒还存在显示和隐藏  那么此时显示的时候只需要写`dispaly:flex`。

注意：媒体查询时，一定要添加样式表，防止溜掉某个尺寸的样式没写，要注意它的使用顺序，书写时元素的属性值要从小向大写。