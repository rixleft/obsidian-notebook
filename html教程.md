# html简介
## html骨架
 html有不同的版本，在建立html页面时，首先得生成一个html骨架。
如下：
```
<!-- 声明文档类型，声明类型根据html版本不同会有不同的写法，该写法为html5版本写法-->
<!DOCTYPE html>
<!-- html的根标签，向搜索引擎表示该页面语言为英文，如果写其他语言会提示你是否需要翻译 -->
<html lang="en">
    <!-- head头部信息 -->
<head>
    <!-- 字符集编码UTF-8三个字节,国内也用GB2312，文件体积小，一个汉字两个字节。-->
    <meta charset="UTF-8">
    <!-- 设置页面的一些信息 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- 视口 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 网页的标题 -->
    <title>我的第一个页面</title>
</head>
<!-- body主体内容 -->
<body>
    
</body>
</html>

```
## 属性
```
属性分类：
     必有属性  src alt
     可选属性  width  height
     通用属性  title  id class style
     事件属性  js相关的事件
```
## html标签
```
 html标签是由尖括号包围的关键词，比如<html>，<body>
 
 html标签通常是成对出现的，比如<b>，</b>.<div>，</div>.
 
 标签对中的第一个标签是开始标签，第二个标签是结束标签。

1.标题标签
     <h1>一级标题</h1>
     <h2>二级标题</h2>
     <h3>三级标题</h3>
     <h4>四级标题</h4>
     <h5>五级标题</h5>
     <h6>六级标题</h6>
2.段落标签
     <p>段落与段落之间会空一行文字的距离</p>
3.图片标签
     <img src="图片的路径" width="300" border="10" title="提示信息" alt="替换文本">
     这是一个单标签，src为必有属性，其余属性为可选属性。
     src="图片的路径"  路径
     width 图片的宽度  如果只设置宽度是等比例缩放。
     height 图片的高度 如果只设置高度是等比例缩放。
     border 图片的边框。
     title 提示信息  当鼠标放在图片上是显示的内容。
     alt 替换文本  当图片发生错误不能正常加载时显示的内容。
     属性之间无前后顺序
4.修饰类标签
    加粗   <b></b>      <strong></strong>
    倾斜   <i></i>      <em></em>
    下划线 <u></u>      <ins></ins>
    删除线 <del></del>  <s></s>
    上角标 <sup></sup>
    下角标 <sub></sub>
    水平线 <hr>       单标签
    强制换行标签 <br>  点标签
5.特殊字符
    空格 &emsp; 中文  &nbsp;英文  
    版权图标 &copy;
    注册商标 &reg;
    小于号 &lt;
    大于号 &gt;
6.超链接
	<a href="路径">内容</a>
	超链接默认是蓝色的文字带有下划线，存在具体网址的会显示成紫色，和默认链接点击过后的效果相同。
	超链接的属性
	    href 必有属性，如果没有此属性，a标签就不是一个超链接
        target属性规定超链接的打开方式。
        默认_self为当前窗口
        _blank为打开新窗口
        download为下载属性，页面需要在服务器端打开才能看到此属性的效果。
	    例:<a href="路径" target="_blank">内容</a>
7.列表标签
	有序列表
	    <ol><li></li></ol>  通过type属性更改列表符号
		列表符号 默认阿拉伯数字1  A  a  I i
		start属性可以决定列表符号从第几个开始  值只能是数字
		reversed 倒序
	无序列表 
		 <ul><li></li></ul>  通过type属性更改列表符号
		 列表符号 
			disc 默认的实心圆  
			circle 空心圆 
			square 实心方块  
			none 没有
	注意：ul只能使用ul的type值，ol只能使用ol的type值，li可以使用任何一个type值
	自定义列表 
		<dl><dt></dt><dd></dd></dl>
		注意：一个自定义列表里有一个dt 可以同时存在多个dd，默认情况下dd是存在一定的缩进效果
8.表格标签
	table表格 tr代表行（几个tr代表几行）  td代表列（几个td代表几列）
	表格的边框 border
    表格的宽度 width
    表格的高度 height
    内容和边框之间的距离 cellpadding
    单元格与单元格的间隙 cellspacing
    设置表格的背景颜色 bgcolor
    设置表格边框的颜色 bordercolor
    设置表格的水平对齐方式 align="left 默认 center 居中 right 居右"
	




```
## 路径
```
相对路径
	以引用文件的网页所在位置为参考基础，而建立出的目录路径，即以当前所在文件夹为起点。
绝对路径
    所有网页引用同一个文件时，所使用的路径都是一样的,绝对路径一般有具体的盘符。
    ../  上一级目录
    ./  当前目录
```