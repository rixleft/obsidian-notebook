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


```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link rel="icon" href="data:image/ico;base64,=">
</head>
<body>
  
<script>

// 普通代码JS引擎解析到之后会立即执行
// console.log(123);

// setTimeout()  设置延迟定时器
// 第一个参数：  要执行的函数
// 第二个参数：  延迟的时间   单位为  毫秒    1秒 = 1000毫秒
// 第三个参数到最后一个参数： 传递给第一个参数指定的函数的实参
// setTimeout(function() {
//   // 延迟定时器中的代码，会等待设置的延迟时间到了之后才执行
//   console.log('abc');
// }, 1000);

// setTimeout(function() {
//   console.log('hello');
//   // 延迟时间最小可以为0，但实际执行时间，会受代码复杂度影响，在不同浏览器中也有所不同
//   // chrome : 最小值大约是  12 ~ 15 毫秒之间
//   // firefox : 最小值在 4 ~ 6 毫秒之间
// }, 0);

// 延迟定时器是异步调用的指定函数，即使上面将延迟时间设置为0，也是后面的代码先执行（因为延迟定时器实际执行时间不是0，至少要等4~10毫秒以上才会调用函数）
// console.log('这行代码会比上面延迟定时器中的代码先执行');

// setTimeout(function() {
//   // 查看实参
//   console.log(arguments);

//   // 从第三个参数开始，后面的所有参数都是传入函数的实参
//   // IE8以下版本中只支持前两个参数，不支持传递实参。
// }, 1000, 1, 2, 3, 4)


// setTimeout(function() {
//   console.log('11111');
//   // 延迟时间的最大值为 2147483647，超过这个值，延迟定时器会立即执行，效果与延迟时间为 0 的效果相同。
//   // 2147483647 大约等于 24.8 天， 实际工作中不太可能设置这么大
// }, 2147483648);

// setTimeout() 方法的返回值为一个正整数，表示延迟定时器的编号，每一个定时器的编号都是唯一的 （与循环定时器使用同一套编号，即如果一个延迟定时器的编号为 10，那么就不会有一个同样编号的循环定时器）
// var timeout = setTimeout(function() {
//   console.log(222);
// }, 500);


// clearTimeout()   关闭延迟定时器
// 延迟定时器可以在延迟时间还没结束之前，提前关闭（延迟定时器中指定的函数不会再执行）。
// var timeout = setTimeout(function() {
//   console.log(222);
// }, 500);
// 关闭定时器，上面定时器中的匿名函数不会被调用，因为定时器被提前关闭了（代码从上到下执行，不需要花500毫秒）
// clearTimeout(timeout);

</script>

</body>
</html>
```
#### 循环定时器
setInterval(fn, time, arg1, arg2, …, argN);

**参数：**

**fn:** 执行代码的函数。

**time:** 延迟时间， 单位为毫秒 (ms) ，最大值2147483647    2的31次方减1

**arg1 ~ argN**: 传入函数 fn 的实参

**返回值：** 一个全局唯一的定时器序号。

循环定时器为异步调用，JS引擎会继续往下执行后续代码，不会等待定时器执行完成。

注意： 为避免循环定时器无法停止的BUG，在开启新定时器之前，应先清除旧的定时器。


```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<link rel="icon" href="data:image/ico;base64,=">
<body>
  
<script>

// setInterval() ： 参数含义与 setTimeout 完全相同，区别只在于延迟定时器只执行一次，循环定时器是重复执行。

var count = 0;

// 每间隔一秒钟，调用一次匿名函数。 只要不关闭定时器，就会一直执行
// setInterval(function() {
//   count++;
//   console.log(count);
// }, 1000)

// 循环定时器的返回值也是一个全局唯一的编号（不会与延迟定时器产生的编号重复） 
// var interval = setInterval(function() {
//   count++;
//   console.log(count);
//   if (count === 10) {
//     // 在循环定时器内部，可以通过判断来控制循环执行的次数
//     clearInterval(interval);
//   }
// }, 1000)
// 在循环定时器外面关闭定时器，将一次都不执行
// clearInterval(interval);

// var interval = setInterval(function() {
//   count++;
//   // 查看传入函数中的参数
//   console.log(count, arguments);
//   if (count === 10) {
//     clearInterval(interval);
//   }
// }, 1000, 10, 20, 30);

</script>
</body>
</html>
```
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


```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title> 获取元素 </title>
</head>
<body>
  
<h2 id="title">第九课 DOM操作</h2>

<ul id="list">
  <li>列表1</li>
  <li>列表2</li>
  <li>列表3</li>
  <li>列表4</li>
  <li>列表5</li>
</ul>

<div id="test">我的id是 test</div>
<div id="test">我的id也是 test</div>

<div id="parent">
  <div id="child">哈喽</div>
</div>

<div class="active">这是一个div</div>

<p class="active">这是一个p标签</p>

<form action="#">
  <label>
    用户名: <input type="text" value="请输入用户名">
  </label>
  <br />
  <label>
    密&emsp;码: <input type="password" value="123456">
  </label>
</form>

<script>

/* 
  css中，要给元素添加样式，需要先使用选择器选中元素
  js中， 要操作HTML元素，也需要先获取到这个元素
*/

// 通过 id 的方式获取元素
// console.log(document.getElementById('title'));
// 查看元素的内容
// console.log( document.getElementById('title').innerHTML );
// 修改元素的内容  = 覆盖原内容    +=  在原内容后面追加新内容
// 覆盖 h2 原来的标题
// document.getElementById('title').innerHTML = '前端开发';
// 在 h2 原来的标题后面追加新的内容
// document.getElementById('title').innerHTML += ' hello world';

// 可以先将获取到的元素保存到变量中，简化代码
// 使用变量，优化上面的代码
// var title = document.getElementById('title');
// console.log(title);
// console.log(title.innerHTML);
// title.innerHTML = '前端开发';
// title.innerHTML += ' hello world';

// // id 应该是唯一的，如果有多个相同id的元素，只会获取第一个。
// var test = document.getElementById('test');
// // 只会往第一个id为 test 的div中追加新内容
// test.innerHTML += ' 通过js添加新内容';


// // 通过 标签名 的方式获取元素,  结果为类数组
// // 获取所有的li元素
// var lis = document.getElementsByTagName('li');
// // 通过标签名方式获取元素，结果是一个类数组，要获取或修改具体的标签，需要使用下标，即使是只获取到了一个元素。
// lis[0].innerHTML += " 通过下标操作具体元素";
// // 查看获取到的li的数量
// console.log(lis.length);
// // 遍历所有li标签，并输出每个li的内容
// for (var i=0; i<lis.length; i++) {
//   console.log(lis[i].innerHTML);
// }
// // 即使只获取到了一个p标签，也需要使用下标，才能访问到这个p标签
// var p = document.getElementsByTagName('p');
// // 错误写法，p 本身是一个类数组，真正的p标签在类数组的第0个值中
// console.log(p.innerHTML);  // undefined
// // 正确写法
// console.log(p[0].innerHTML); // 这是一个p标签

// 使用通配符 * ,可以获取所有元素 （不常用）
// console.log(document.getElementsByTagName("*"));

// 通过标签名方式获取元素，只能获取同类型标签，不够灵活
// 通过类名的方式获取元素，可以获取所有有相同类名的元素
// IE8 以下版本不支持以 类名 的方式获取元素
// var elements = document.getElementsByClassName('active');
// // 通过类名的方式获取元素，结果也是一个类数组。
// elements[1].innerHTML += ' 通过类名的方式获取元素';
// // 查看获取到的元素数量
// console.log(elements.length);
// for (let i = 0; i < elements.length; i++) {
//   console.log(elements[i].innerHTML);
// }

// 通过 id 方式获取元素，只能在 document 对象上调用
// var parent = document.getElementById('parent');
// console.log(parent);
// var child = parent.getElementById('child');
// console.log(child);

// 通过 标签名 和 类名 方式获取元素，可以通过已经获取到的父元素获取后代元素
// 可以直接连着获取
// console.log( document.getElementById('list').getElementsByTagName('li') );
// 也可以先保存变量
// 先获取到 ul 
// var list = document.getElementById('list');
// // 再通过 ul 获取 li
// var lis = list.getElementsByTagName('li');
// console.log(lis);
// // 先获取到 body 标签，注意要添加下标
// var body = document.getElementsByTagName('body')[0];
// var actives = body.getElementsByClassName('active');
// console.log(actives);


// 获取元素的内容
// 普通元素使用 innerHTML 属性来获取和修改内容
var child = document.getElementById('child');
console.log(child.innerHTML);
child.innerHTML = "哈哈哈哈";

// 表单元素使用 value 属性来获取和修改内容
var inputs = document.getElementsByTagName('input');
// 获取第二个input的value值
console.log(inputs[1].value);
// 设置第一个input的value值
inputs[0].value = '文本输入';

</script>
</body>
</html>
```

#### 元素的属性操作

元素的属性，即HTML标签上的属性，如 id , class 等。

**元素属性有三种操作方式：**

1，点语法

2，[] 语法

3，getAttribute() / setAttribute() 方法

**注意：**

1，HTML 元素的标准属性 在 DOM 对象中有直接关联的属性，自定义属性则被存放在特定属性中。

2，点语法 和 []语法 操作标准属性时会自动更新 HTML 元素中的对应属性，操作自定义属性时，不会自动更新到 HTML 元素中。

3， getAttribute() / setAttribute() 操作的是 HTML 元素中的属性，操作标准属性时会自动更新 DOM 对象中的对应属性，操作自定义属性时，不会自动更新到 DOM 对象中。

4，以下属性为关键字或保留字，点和[]语法需要使用替换名称， getAttribute() / setAttribute() 不需要：

class → className for → htmlFor owspan → rowSpan colspan → colSpan

5，操作style属性时：

点和[] 操作的是 DOM 对象，可以进行链式操作（连续使用 . 和 []语法）。

getAttribute() / setAttribute() 操作的是 HTML 元素中的属性，所有 html 元素的属性值都是字符串
```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    .active {color: red;}
    .fz30 {font-size: 30px;}
  </style>
</head>
<body>

  <!-- abc 为自定义属性 -->
<div id="div1" class="active" abc="001">这是div标签</div>

<script>

var div = document.getElementById('div1');

// 点语法 和 []语法 获取和修改属性
// 获取id属性的值
console.log(div.id);
// 修改id属性的值
div['id'] = 'div2';
// 点 和 [] 语法操作关键字和保留字时要使用替代名称
// class 是关键字，不能直接用来获取类名
// console.log(div.class);
// 需要使用 className 来表示类名，目前需要注意替换的只有四个属性，分别是：
// class --> className     for --> htmlFor    rowspan --> rowSpan   colspan --> colSpan
// console.log(div.className);

// html标签上的自定义属性无法通过 点 和 [] 获取和修改
// console.log(div['abc']);
// console.log(div.abc);

// HTML标签中的自定义属性 与 JS的dom对象中的自定义属性没有关联
// 修改 div 对象中的 abc 属性，div1 标签上的 abc 属性不会有变化
div['abc'] = 'dom对象中的自定义属性';
// console.log(div.abc);

// getAttribute() / setAttribute() 获取和修改属性
// 获取 id 属性的值
// console.log( div.getAttribute('id') );
// 修改 id 属性的值
// div.setAttribute('id', 'div3');
// getAttribute() / setAttribute() 不需要避开关键字和保留字
// 获取 class 属性的值
// console.log(div.getAttribute('class'));
// 设置 class 属性的值 （会覆盖原来的值）
// div.setAttribute('class', 'active fz30');
// 修改 HTML 标签的自定义属性
// div.setAttribute('abc', 'html标签中的自定义属性');
// dom 对象 上的同名自定义属性不会被修改
// console.log(div.abc);
// console.log(div['abc']);

</script>
</body>
</html>
```


#### 设置元素样式

JavaScript 只能设置或修改行间样式，无法添加或修改内部或外部样式表中的样式。

设置样式可以使用 点语法、[]语法 和 setAttribute() 方法，通常使用 点语法和[]语法。

**语法规则：**

元素.style.样式属性名称 = "样式值";

元素.style\['样式属性名称'] = "样式值";

**注意：**

1，除数字值外，其他样式值必须使用引号包裹。

2，点语法的样式属性名称必须使用驼峰式命名。

3，[]语法的样式属性名称必须使用引号包裹。

**批量设置：**

元素.style.cssText = '样式名称1: 样式值1; 样式名称2: 样式值2';

元素.setAttribute("style", "样式名称1: 样式值1;样式名称2: 样式值2;");

**注意：** 批量设置会覆盖行间原来的所有样式。



```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
</head>
<body>
  
<div id="div1">前端开发</div>

<script>

var div = document.getElementById('div1');

// 通过点或[]语法设置样式
div.style.color = "red";
// 点语法要使用驼峰式写法
div.style.backgroundColor = 'pink';
// []语法既可以使用-写法，也可以使用驼峰式写法
div.style['font-size'] = "30px";
div.style['borderTop'] = "5px solid #333";
// 不带单位的数字类型值可以直接写，其它类型的值必须使用引号。
div.style.opacity = 0.5;


//批量修改样式   写法与css样式写法一样，会覆盖原来的行间样式
// div.style.cssText = "background: orange; color: blue;";
// 注意 setAttribute() 方法是直接在 dom 对象上调用的，不是 style 属性上调用
// div.setAttribute('style', 'font-size: 50px; border: 5px dotted #666;') 

</script>
</body>
</html>
```

#### 获取元素样式

元素的行间样式可以通过 点语法 和 []语法 获取，需要注意的是：

1，只有行间的 style 属性中定义过的样式才可以被获取到。

2，点语法属性名称要使用驼峰命名，[]语法属性名要加引号。

**获取计算样式：** 计算样式是指元素最终生效的样式，包括内部、外部和行间样式，计算样式的获取有兼容问题。

IE8以上及其它浏览器：

getComputedStyle(obj) BOM 方法（属于window对象）

参数： obj 需要获取计算样式的 DOM对象

返回值： 包含所有计算样式的对象，通过点和[]语法获取具体样式值。

（也可以使用内置的 getPropertyValue() 方法获取，不推荐）

IE所有版本浏览器：

currentStyle DOM 属性

所有具有样式属性的DOM对象，都有该属性，通过点和[]语法获取具体样式值。

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    #div1 {
      background: pink;
      border-left: 10px solid #333;
      padding: 8px 15px;
    }
  </style>
</head>
<body>
  
  <div id="div1" style="color: red; font-size: 30px;">前端开发</div>

  <script>
    var div = document.getElementById('div1');

    // 行间样式可以使用 点和[] 语法获取
    console.log( div.style.color );
    console.log( div.style['font-size']);
    // 内部或外部样式表中的样式无法通过点和[]语法获取
    // console.log( div.style.backgroundColor );
    // console.log( div.style['border-left'] );

    // IE9以上及其他标准浏览器中获取计算样式
    // 计算样式： 最终生效的样式
    // getComputedStyle() 方法是 window 对象的内置方法，参数是要获取样式的 dom 对象， 返回值是包含元素所有样式的对象
    // console.log( getComputedStyle(div).backgroundColor );
    // console.log( getComputedStyle(div)['borderLeft'] );
    // console.log( getComputedStyle(div)['padding-left'] );
    // // 也可以通过 getPropertyValue() 方法获取指定样式 （不推荐）
    // console.log( getComputedStyle(div).getPropertyValue('padding'));

    // IE8以下浏览器获取计算样式
    // currentStyle 是IE浏览器专有的样式属性
    // IE浏览器中的值是一个包含所有样式的对象，其他浏览器中的值为 undefined
    // console.log(div.currentStyle);
    // console.log(div.currentStyle.backgroundColor)
    // console.log(div.currentStyle['borderLeftColor'])
  </script>
</body>
</html>
```

#### 能力检测

由于计算样式的获取有兼容问题，需要通过能力检测来处理兼容问题。

**能力检测：** 通过判断浏览器有没有指定属性或方法，来实现检测浏览器是否支持该属性或方法。

能力检测是判断浏览器是否支持指定属性或方法最常用的方式。

**封装函数：** 将检测代码写到函数中，重复使用。

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    #div1 {
      background: pink;
      border-left: 10px solid #333;
      padding: 8px 15px;
    }
  </style>
</head>
<body>
  
  <div id="div1" style="color: red; font-size: 30px;">前端开发</div>

  <script>

    var div = document.getElementById('div1');

    // 判断浏览器的 window 对象中有没有 getComputedStyle() 方法
    // 方法就是函数， 函数为真值
    // 所以如果有该方法，条件成立 ，没有该方法（值为undefined），条件不成立
    // if ( window.getComputedStyle ) {
    //   // 如果条件成立，说明是ie9以上IE或其他浏览器
    //   console.log( getComputedStyle(div)['color'] );
    // } else if (div.currentStyle) {
    //   // 如果条件成立，说明是ie8以下浏览器
    //   console.log( div.currentStyle['color'] );
    // }

    console.log(getStyle(div, 'border-left'));
    console.log(getStyle(div, 'opacity'));

    // 封装成通用函数
    // obj  要获取样式的dom对象   attr 要获取的样式
    function getStyle(obj, attr) {
      if ( window.getComputedStyle ) {
        // 变量只能使用[]语法
        return getComputedStyle(obj)[attr];
      } else if (obj.currentStyle) {
        return obj.currentStyle[attr];
      }
    }

  </script>
</body>
</html>
```

## DOM事件

#### 事件分类

当用户浏览HTML页面时，在与页面交互过程中会触发各种类型的事件。

具体包括：

键盘事件

鼠标事件

DOM事件

BOM事件

多媒体事件等。

**鼠标事件：**

onclick 单击 ondblclick 双击

onmouseenter 鼠标进入 onmouseleave 鼠标离开

onmousedown 鼠标按下 onmouseup 鼠标释放

**键盘事件：**

onfocus 获取焦点 onblur 失去焦点

onkeydown 键盘按下 onkeyup 键盘释放

**绑定事件处理函数：**

元素.事件名称 = 处理函数名称; （函数后面不能加(), 可以是匿名函数）

事件处理函数： 当事件被触发时，期望被执行的函数。

**注意：**

只要用户有对应的操作，就一定会触发对应的事件，与是否绑定事件函数无关。

比如：只要用户点击了页面，就一定会触发 onclick 事件。

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    #div1 {
      width: 300px;
      height: 300px;
      background: pink;
    }
  </style>
</head>
<body>
  
<div id="div1"></div>

<input type="text" id="txt"><br /><br />
<input type="button" id="btn" value="按钮">

<script>

  var div = document.getElementById('div1');
  var txt = document.getElementById('txt');
  var btn = document.getElementById('btn');

  div.onclick = function() {
    console.log("点击事件");
  };

  div.ondblclick = function() {
    console.log("双击事件");
  };

  div.onmouseenter = function() {
    console.log("鼠标移入");
  };

  div.onmouseleave = function() {
    console.log("鼠标移出");
  };

  div.onmousedown = function() {
    console.log("鼠标按下");
  };

  div.onmouseup = function() {
    console.log("鼠标抬起");
  };

  txt.onfocus = function() {
    console.log("获得焦点");
  };

  txt.onblur = function() {
    console.log("失去焦点");
  };

  txt.onkeydown = function() {
    console.log("键盘按键按下");
  };

  txt.onkeyup = function() {
    console.log("键盘按键释放");
  };

  // 将函数赋值给事件，这个函数被称为事件处理函数
  // btn.onmouseenter = function() {
  //   console.log('这是一个事件处理函数');
  // };
  // 将命名函数作为事件处理函数， 函数名称后面不能加() !!!
  // btn.onmouseenter = fn1;
  function fn1() {
    console.log('函数是不是事件处理函数，要看函数是不是被事件触发执行的');
  }

  // 这里的事件处理函数是匿名函数
  document.onclick = function() { 
    // 函数如果需要传参数，就不能直接作为事件处理函数使用，需要在外层使用匿名函数作为事件处理函数。
    fn2(10, 20);
  }

  function fn2(a, b) {
    console.log(a, b);
  }

  btn.onclick = function() {
    console.log("我被点击了！");
  };

  // 一个元素只能绑定一个事件处理函数，绑定多个函数，后面会覆盖前面
  btn.onclick = function() {
    console.log("点了我一下！");
  };

  btn.onclick = function() {
    console.log("点了我一下！");
  };

</script>
</body>
</html>
```

#### onload 事件

onload 事件是 BOM 事件，当页面中的所有资料都加载完成之后，通过 window 对象自动触发。

**使用场景：**

当 script 写在 HTML 其他元素之上时，如果期望在 script 标签中获取下面的其它 HTML 标签，则需要将 获取元素的代码写在 onload 事件的处理函数中。

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
</head>
<body>

  <div id="div1">前端开发</div>

  <script>
    // var div1 = document.getElementById('div1');
    // var div2 = document.getElementById('div2');
    
    // 只能获取script标签上面的标签，无法获取到script标签下面的标签
    // 因为 JS 代码是按标签顺序依次加载的，执行script标签里面的代码时，在script标签下面的标签还没有加载到。
    // console.log(div1);
    // console.log(div2);

    // 要获取script标签下面的元素,需要等下面的标签加载完成
    // window对象的 onload 事件,是一个自动执行事件, 在浏览器加载完所有资源之后,就会自动触发  onload 事件.
    // 所有资源包括: html 标签, 图片, 音频, 视频, css , js 等资源.
    window.onload = function() {

      var div1 = document.getElementById('div1');
      var div2 = document.getElementById('div2');

      // 在 window.onload 事件的事件处理函数里面获取元素,可以保证能获取到页面中的所有元素.
      console.log(div1);
      console.log(div2);

    }
  </script>
  
  <div id="div2">hello world</div>

</body>
</html>
```

#### 遍历dom元素集合

通过 类名 和 标签名 方式获取到的元素集合，是一个类数组对象，可以使用 for 循环进行遍历。

**遍历时的元素索引问题：**

如果遍历时给元素添加事件处理函数，函数内部不能将遍历时的索引变量当作元素索引使用。

可以通过两种方式解决：

1，将遍历索引当作自定义属性保存到每个 DOM 对象中，在函数内部使用 this 关键字获取。

2，事件处理函数使用 IIFE 函数，将遍历索引当作参数传入IIFE 函数中。

**案例：**

有五个li元素，点击每个li元素时，输出被点击的li元素的索引和内容。

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
</head>
<body>

<ul>
  <li>列表1</li>
  <li>列表2</li>
  <li>列表3</li>
  <li>列表4</li>
  <li>列表5</li>
</ul>

<script>

  var lis = document.getElementsByTagName('li');

  // 遍历所有li元素
  // for (var i=0; i<lis.length; i++) {
  //   // 输出每个元素的内容
  //   console.log(lis[i].innerHTML);
  // }

  // for (var i=0; i<lis.length; i++) {
  //   // 利用 for 循环给所有 li 绑定事件处理函数
  //   lis[i].onclick = function() {
  //     // 事件函数内部无法直接获取每一个li对应的索引（li的下标）
  //     console.log(i);
  //   }
  // }

  // 点击元素 输出元素索引的两种方式
  // 1， 通过自定义属性方式保存下标
  // for (var i=0; i<lis.length; i++) {
  //   // 每次循环时，给对应的li添加一个自定义属性，值就是当前循环的i的值
  //   lis[i].index = i;
  //   lis[i].onclick = function() {
  //     // 点击li时，利用 this 对象获取li自身的自定义属性index。
  //     console.log(this.index);
  //     // 输出当前li（被点击的li）的内容
  //     console.log(this.innerHTML);
  //   }
  // }

  // 2，通过 IIFE + 闭包 组合保存下标
  for (var i=0; i<lis.length; i++) {
    // 每次循环时，给对应的li添加一个自定义属性，值就是当前循环的i的值
    lis[i].onclick = (function(index) { // index 接收传进来的 i 值

      return function() { 
        // 输出当前点击 li 的索引
        console.log(index);
        // 输出当前li（被点击的li）的内容
        console.log(lis[index].innerHTML);        
      }

    })(i); // 将循环的 i 值作为参数传入 IIFE函数中
  }

</script>
</body>
</html>
```


#### 对应与排它思想

对应与排它思想是使用频繁非常高的一种元素交互实现逻辑。

对应思想：通过索引值，将一组元素与另一组元素进行一一对应。

排它思想：给指定索引值的元素设置状态，清空其他所有元素的状态。

**案例：**

选项卡效果

1，当前选项选中状态： 对应思想

2，其他选项清空状态： 排它思想

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    #tab {
      border: 5px solid #333;
      width: 300px;
    }
    #tab input {
      font-size: 20px;
    }
    #tab div {
      height: 200px;
      display: none;
      font-size: 40px;
      background: lightblue;
    }
    #tab input.active {
      background: red;
    }
    #tab div.active {
      display: block;
    }
  </style>
</head>
<body>
  
  <div id="tab">
    <input type="button" value="选项一" class="active">
    <input type="button" value="选项二">
    <input type="button" value="选项三">
    <div class="active">内容一内容一内容一内容一</div>
    <div>内容二内容二</div>
    <div>内容三内容三内容三内容三内容三内容三</div>
  </div>

  <script>

    var tab = document.getElementById('tab');
    // 获取所有的按钮
    var btns = tab.getElementsByTagName('input');
    // 获取所有的内容div
    var divs = tab.getElementsByTagName('div');

    // 使用for循环给所有选项添加点击事件
    for (var i=0; i<btns.length; i++) {

      // 将 i 作为索引值存入到每一个选项按钮中
      btns[i].index = i;
      btns[i].onclick = function() {

        // 排它思想： 清空所有元素的状态
        for (var j=0; j<btns.length; j++) {
          btns[j].className = '';
          divs[j].className = '';
        }

        // 对应思想： 用当前点击的选项的索引与内容的索引进行对应。
        btns[this.index].className = 'active';
        divs[this.index].className = 'active';
      }

    }
  </script>
</body>
</html>
```