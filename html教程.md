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
4.
     
```
