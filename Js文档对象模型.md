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

title : <title> 标签

head: <head> 标签， 只读

body: <body> 标签(框架集页面为 frameset标签)， 可以赋值，但值必须是一个 body 对象。

documentElement : <html> 标签，只读

forms: 所有 <form> 标签的集合，只读

images: 所有 <img> 标签的集合， 只读

scripts: 所有 <script> 标签的集合，只读

cookie: 与当前文档关联的 cookie 信息