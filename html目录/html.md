# html简介
## html骨架
 html有不同的版本，在建立html页面时，首先得生成一个html骨架。
如下：
```html
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
属性分类：
     必有属性  如图片的必有属性`<img src="地址">  <alt>`
     可选属性  `<width>  <height>`
     通用属性  `<title>  <id> <class> <style>`
     事件属性  java script 相关的事件

## [[html标签]] 

 在html中，标签通常又被称作元素，它是由尖括号包围的关键词，比如`<html>，<body>`
 
 html标签通常是成对出现的，比如`<b>，</b>.<div>，</div>.`
 
 标签对中的第一个标签是开始标签，第二个标签是结束标签。

 
 HTML元素根据其表现形式可以分为两种，一种叫==块级元素==，一种叫==行内元素==。
 
块级元素在浏览器中占据整行，并排斥其它元素与其位于同一行。它的宽度是 100%。

行内元素也叫内联元素，在浏览器中可以与其它行内元素共占一行，只有当多个元素的总宽度大于浏览器的宽度时，才会换行显示。
 
## 起名

起名规则规范
使用因为字母区分大小写，可以使用数字下划线，中划线，但是不能以数字开头，也不可以使用汉字，最好不要使用关键字，如(html标签)。

 语法规则：代码使用小写字母，起名使用驼峰命名法，由多个单词组成时，可写下划线，introduce_myself。


### 1.[[标题标签]]
标题标签是块级元素，一般独占一行，常用于模块部分的标题字段。
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>标题标签</title>
</head>
<body>
    <h1>一级标题</h1>
    <h2>二级标题</h2>
    <h3>三级标题</h3>
    <h4>四级标题</h4>
    <h5>五级标题</h5>
    <h6>六级标题</h6>
</body>
</html>

```

### 2.[[段落标签]]

```
     <p>段落与段落之间会空一行文字的距离</p>
```

### 3. [[图片标签]]

```
     <img src="图片的路径" width="300" border="10" title="提示信息" alt="替换文本">
     这是一个单标签，src为必有属性，其余属性为可选属性。
     src="图片的路径"  路径
     width 图片的宽度  如果只设置宽度是等比例缩放。
     height 图片的高度 如果只设置高度是等比例缩放。
     border 图片的边框。
     title 提示信息  当鼠标放在图片上是显示的内容。
     alt 替换文本  当图片发生错误不能正常加载时显示的内容。
     属性之间无前后顺序

```

### 4.[[修饰类标签]]
```
    加粗   <b></b>      <strong></strong>
    倾斜   <i></i>      <em></em>
    下划线 <u></u>      <ins></ins>
    删除线 <del></del>  <s></s>
    上角标 <sup></sup>
    下角标 <sub></sub>
    水平线 <hr>       单标签
    强制换行标签 <br>  点标签

```


### 5.[[特殊字符]]
```
    空格 &emsp; 中文  &nbsp;英文  
    版权图标 &copy;
    注册商标 &reg;
    小于号 &lt;
    大于号 &gt;
```


### 6.[[超链接]]
```
	<a href="路径">内容</a>
	超链接默认是蓝色的文字带有下划线，存在具体网址的会显示成紫色，和默认链接点击过后的效果相同。
	超链接的属性
	    href 必有属性，如果没有此属性，a标签就不是一个超链接
        target属性规定超链接的打开方式。
        默认_self为当前窗口
        _blank为打开新窗口
        download为下载属性，页面需要在服务器端打开才能看到此属性的效果。
	    例:<a href="路径" target="_blank">内容</a>

```
### 7.[[列表]]
```

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
```
### 8.[[表格]]
```
table表格 
	tr代表行（几个tr代表几行）  
		height 高度
        align 代表的是这一行内容的水平对齐方式 left 默认 center 居中 right 居右
        bgcolor 这个一行的背景颜色
        valign 这一行内容的垂直对齐方式 top 上 middle 默认值  bottom 下
        
	td代表列（几个td代表几列）
		width 宽度
        height 高度
        bgcolor 背景颜色  这个单元格的背景颜色
        align 水平对齐方式 这个单元格内容的水平对齐方式 left 默认 center 居中 right 居右
        valign 垂直对齐方式 这个单元格内容的垂直对齐方式 top 上 middle 默认居中  bottom 下
        行合并 rowspan  行不同就是行合并  纵向合并
        列合并 colspan  列不同就是列合并  横向合并
        
    表格的标题 caption
	    <caption>表格的标题</caption>
	    无论写在table的上边还是下边都会显示在表格上边居中的位置，写多个这样的标签就会显示多少次， 
        默认是处在表格的居中位置。
        
    表格的列标题 th
	    th是表格的列标题 默认是加粗的效果 默认是水平垂直居中。
	    
	表格的数据行分组
		可以分成 thead 表头  tbody 表体  tfoot 表尾
		注意：一个表格中只有一个表头 一个表尾 可以同时存在多个表体，要用就一起使用，要么就不用。
		在实际工作中一般这三个分组的顺序是 thead tfoot tbody 不影响最终显示效果，但是可以提高 
        用户体验，有利于SEO。
        
    rules属性
		可以给表格添加一些线条
	     all 横向与竖向的线
         cols 竖向的线
         rows 横向的线
         none 没有
         groups 组分割线  一般与col 或者 colgroup 连用
        注意：如果使用组分割线进行表格的合并，那么表格的下面td里就不要使用其他的合并
        col与colgroup有相同的功能
        col是单标签  没有竖着的分割线  
        colgroup是双标签  有竖着的分割线
        
	表格的边框 border
    表格的宽度 width
    表格的高度 height
    内容和边框之间的距离 cellpadding
    单元格与单元格的间隙 cellspacing
    设置表格的背景颜色 bgcolor
    设置表格边框的颜色 bordercolor
    设置表格的水平对齐方式 align="left 默认 center 居中 right 居右"

```
### 9.[[表单]]
```
表单域 form
	属性
		name  表单名称
	    action 表单的提交地址
	    method 表单的提交方式和方法
		值 get  默认是get，从服务器上获取信息，get会将一些信息放到地址栏中，因此安全性低，但效率高，做查询数据时使用
        post  向服务器上传，安全性高，效率低，一些密码安全等级比较高的用post
        target 表单的提交方式  默认是在当前窗口 _self 可以在新的窗口提交 _blank
            
	表单控件 input
		
		input可以设置的属性
			
			type input的类型
				
			    1：text  文本框  输入什么就显示什么
			    2：password  密码框  不管输入的是什么都显示星号 *
			    3：radio  单选按钮    单选时使用
			    4：checkbox  复选框   多选时使用
			    5：file    文件域  可以上传文件 如图片文件
			    6：image   图片域  可以当做提交按钮使用
			    7：button  普通按钮  无效果
			    8：reset   重置按钮  将所填内容恢复到默认状态
			    9：submit  提交按钮  上传信息到指定地址
			    10：hidden  隐藏按钮  允许Web开发者存放一些用户不可见、不可改的数据
				用户名：<input type="text"><br>
			    密码框：<input type="password"><br>
			    单选按钮：<input type="radio"><br>
			    复选框：<input type="checkbox"><br>
			    文件域：<input type="file"><br>
			    图像域：<input type="image" src="./bg.png"><br>
			    普通按钮：<input type="button" value="按钮">
			    重置按钮：<input type="reset" value="重置">
			    提交按钮：<input type="submit" value="提交">
				隐藏按钮: <input type="hidden" value="隐藏" name="qwe">
				   
		        name input的名称  需要就写不需要可以不用 但是radio这个标签必须要有name 一组 
                保持一致，必然不能实现单选。
		        checked 默认选中状态
		        disabled 禁用
		        multiple 实现选择多个的效果，如选择上传多个文件等。
		        value  默认值  是值这个input的值 它也是数据 是可以提交的
		        placeholder 提示信息  这个只能对用户起到提示的效果，不是input的值 不可以提交 
                （注意：html5新增属性，低版本浏览器不支持）
		        maxlength 最多可以输入的字符
		        minlength 最少可以输入的字符
		        size 文本框input的长度 （了解）
		        
	表单控件 select
			multiple可以实现多选  默认只能选择一条
			每一条选项都是一个option
			
	表单控件 textarea
			textarea 多行文本框 用来写评价或发表言论
			cols 宽度 一行显示的字符数，一个汉字代表两个字节，超过行限制字数则会显示滚动条。
	        rows 高度 一共可以显示多少行，如果超过这个行数就会显示滚动条。

```
![[表单标签2.png]]
### 10.布局标签
```
	div 布局块 用来划分网页的各个模块
	span 布局节点 用来修饰网页中的某一个小部分 不影响整体布局

```
### 11.[[其他标签]]
```
	iframe 框架集  可以在一个页面中嵌套其他页面
		通过src属性  如果你嵌套的页面比较大 可以设置宽度高度，如果没有设置那么会有左右上下滚动条
		与超链接合作  超链接的target属性值是ifram的name名称
		frameborder="no" 去掉默认的边框
		scrolling="no" 无论是否能够放下所有内容都不会显示滚动条

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

