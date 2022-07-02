### 定时器
#### 延迟定时器 
setTimeout(fn,time,arg1,arg2,.....,argN);

**参数：**

**fn:** 执行代码的函数。

**time:** 延迟时间， 单位为毫秒 (ms) ，最大值2147483647   2的31次方减1

**arg1 ~ argN**: 传入函数 fn 的实参

**返回值：** 一个全局唯一的定时器序号。

**关闭延迟定时器**： 清除指定的延迟定时器，让定时器不再执行。

clearTimeout(index);
index是由 setTimeout() 返回值提供的序号

#### 循环定时器
setInterval(fn, time, arg1, arg2, …, argN);

**参数：**

**fn:** 执行代码的函数。

**time:** 延迟时间， 单位为毫秒 (ms) ，最大值2147483647    2的31次方减1

**arg1 ~ argN**: 传入函数 fn 的实参

**返回值：** 一个全局唯一的定时器序号。

循环定时器为异步调用，JS引擎会继续往下执行后续代码，不会等待定时器执行完成。

注意： 为避免循环定时器无法停止的BUG，在开启新定时器之前，应先清除旧的定时器。


## DOM
#### document对象

document 对象 是 DOM 的内置对象，是DOM中最顶层的对象，表示整个 HTML 文档。

document 提供了所有 HTML 元素的访问和修改 API。

document 中的常用属性：

title : `<title>` 标签

head: `<head>` 标签， 只读

body: `<body>` 标签(框架集页面为 frameset标签)， 可以赋值，但值必须是一个 body 对象。

documentElement : `<html>` 标签，只读

forms: 所有 `<form>` 标签的集合，只读

images: 所有 `<img>` 标签的集合， 只读

scripts: 所有 `<script>` 标签的集合，只读

cookie: 与当前文档关联的 cookie 信息

```js
<script>
//几个常用的唯一标签被当作属性保存在了document对象中
console.log(document.head); // <head> 标签
console.log(document.title); // <title> 标签
console.log(document.body); // <body> 标签
console.log(document.documentElement); // <html> 标签
console.log(document.forms); // 所有 <form> 标签的集合
console.log(document.images); // 所有 <img> 标签的集合
console.log(document.scripts); // 所有 <script> 标签的集合
console.log(document.cookie); // 与当前文档关联的 cookie 信息
</script>
```

#### 获取元素

获取元素 是指通过 DOM 提供的方法获取 HTML 元素。

getElementById() 通过元素id获取，如果有多个同名id元素，只会获取第一个

getElementsByTagName() 通过元素名称获取，使用通配符 * 可以获取所有html元素

getElementsByClassName() 通过元素类名获取 (IE8 以下浏览器不支持)

**注意：**

1，getElementById() 方法只能在 document 对象上调用。

2， getElementsByTagName() / getElementsByClassName() 可以在所有 DOM 对象上调用。

3， getElementsByTagName() / getElementsByClassName()

获取到的是一个HTML元素集合（HTMLCollection），是一个类数组对象。需要使用下标访问具体的 DOM 元素，即便是只获取到了一个元素。

**获取 HTML 元素的内容：**

普通元素： innerHTML 属性

表单元素： value 属性