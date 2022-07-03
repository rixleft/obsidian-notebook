### 作用域

---

作用域是指变量或函数能够被访问的有效范围，即变量或函数在哪个范围内可以使用。

在 ECMAScript 3.0 及以前版本中，只有函数才会产生作用域。

**作用域特点：**

1, 在函数外部声明的变量或函数，函数内部可以访问。

2, 在函数内部声明的变量或函数，函数外部无法访问。


**注意：**

1，作用域是在调用函数时产生的，因为函数不调用，里面的代码不会被解析。

2，变量如果不声明而直接赋值，默认会成为一个全局变量（严格模式中会报错），这个变量称为隐式全局变量。要严格避免使用这种赋值方式，即变量赋值之前必须先声明。

### 作用域链

---

作用域链是指当有多层函数嵌套时，访问变量或函数时的查找顺序。

当访问一个变量或函数时，JS 引擎会优先在访问位置所在的当前作用域下查找该变量或函数有没有声明，如果声明了，则使用当前作用域下的变量或函数；如果当前作用域下没有声明，则会往上一层作用域中查找，依此类推，一直查找到顶层作用域， 如果顶层作用域中也没有声明，则会抛出错误信息。

**顶层作用域：** 指的是不包任何函数包裹的，script 标签的最外层。

**注意：**

1，不同script标签之间没有作用域，所有的script标签共同组成顶层作用域。

2，上面的script标签中无法访问下面标签中声明的变量或函数，是因为js引擎，是按script标签分别依次解析的（可以通过延迟定时器来验证）。
- 作用域链： 是指当有多层函数嵌套时，访问变量或函数时的查找顺序。 
- 如果当前的局部作用域 与 全局作用域 有同名变量时， 会优先访问当前的局部作用域中的变量 （就近原则）  
- 、父作用域中无法访问子作用域中的变量
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
​  
<script>  
​  
// 作用域链： 是指当有多层函数嵌套时，访问变量或函数时的查找顺序。  
​  
var num = 10; // 全局变量  
var str = 'hello world';  
​  
// function fn1() {  
//   console.log(num); // 10 访问全局变量  
// }  
// fn1();  
​  
// function fn2() {  
//   var num = 20;  
//   // 如果当前的局部作用域 与 全局作用域 有同名变量时， 会优先访问当前的局部作用域中的变量 （就近原则）  
//   console.log(num); // 20 访问局部变量  
// }  
// fn2();  
​  
// function fn3() {  
//   var num = 20;  
    
//   function fn4() {  
//     var num = 30;  
//     // 优先访问当前作用域中的变量  
//     console.log(num); // 30  
//   }  
//   fn4();  
​  
//   // 父作用域中无法访问子作用域中的变量  
//   console.log(num); // 20 访问局部变量  
// }  
// fn3();  
​  
function fn5() {  
  var num = 20;  
    
  function fn6() {  
    // 如果当前作用域中没有声明，就去上一层作用域中查找。  
    console.log(num); // 20  上层作用域中的变量  
​  
    // 如果在所有父级作用域中都找不到，就到顶层作用域中查找  
    console.log(str); // 'hello world'    顶层作用域中的变量  
​  
    // 如果顶层作用域中也没有找到，代码终止执行，并抛出错误信息。  
    // console.log(result); // 报错： result is not defined  
  }  
  fn6();  
​  
  // 父作用域中无法访问子作用域中的变量  
  console.log(num); // 20 访问局部变量  
}  
fn5();  
​  
// 如果上面的代码中有错误，js将无法执行到这里。  
console.log("这是最后一条输出信息");  
​  
</script>  
​  
</body>  
</html>
```


### 闭包

---

闭包( Closure )是作用域的一种特殊使用场景。

**定义：**

两层函数嵌套，子函数中引用了父函数中的变量或函数，并且父函数将子函数作为返回值返回到函数外部，那么这个子函数通常称为闭包。

个人理解，闭包就是为了将局部变量的值返回给全局使用，套用两层function函数可以达到此效果，所以用闭包。

**说明：**

1，函数只要嵌套，就会产生闭包环境，但通常只会把跟父函数之间有引用关系并被父级return返回的函数称作闭包。

2，存在闭包关系的函数，函数本身和里面的局部变量无法被垃圾回收机制自动回收。

3，闭包通常只会有两层函数嵌套，过多的函数嵌套会增加内存溢出的风险。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
    
<script>  
 
function fn1() { // 父函数  
  var a = 10;  
 
  function fn2() { // 子函数  
    var b = 20;  
    // 虽然有函数嵌套 ，但子函数中并没有引用父函数中的任何函数或变量，因此不称为闭包。  
    console.log(b);  
  }  
  fn2();  
}  
// fn1();  

function fn3() {  
  var c = 1;  

  function fn4() {  
    var d = 100;  
    // 虽然引用了父函数中的变量，但没有被作为返回值返回，因此也不称为闭包。  
    console.log(c);   
  }  
  fn4();  
}  
// fn3();  
 
 
// function fn5() {  
//   var e = 1;  

//   function fn6() {  
//     // 闭包函数：   1，引用了父级的变量   2，被父函数作为返回值返回  
//     console.log(e);   
//   }  
//   return fn6;  
// }  
// var innerFn = fn5();  
// innerFn(); //1;  
 
// 简化写法  
function fn5() {  
  var e = 1;  
 
  // 作为返回值的函数，不需要命名  
  return function () {  
    console.log(e);   
  }  
}  
// var innerFn = fn5();  
// innerFn(); //1;  

// 由于 innerFn 会被调用多少次无法预知，所以JS引擎必须保证局部变量e和return后面的匿名函数一直存在，无法被垃圾回收机制回收。  
 
 
// 闭包实例  
// 1， 计数器  

// 用来创建计数器的函数  
function counter() {  
  var num = 0;  
  return function () {  
    num ++;  
    return num;  
  }  
}  
  
// 计数器1  
var c1 = counter();  
// 计数器2  
var c2 = counter();  

// 多个计数器之间互不干扰  
console.log( c1() ); // 1  
console.log( c1() ); // 2  
console.log( c2() ); // 1  
console.log( c2() ); // 2  
console.log( c2() ); // 3  
console.log( c2() ); // 4  
console.log( c1() ); // 3   
 
 
// 2，谎报年龄  
// 输出年龄比实际年龄大或小  

// 用来创建不同的人物  
function faker(age) { // age :  真实年龄  
  return function(num) { // num : 谎报的岁数    正数： 比实际年龄大     负数： 比实际年龄小  
    return age + num;  
  }  
}  
 
// xiaoming 实际年龄 20  
var xiaoming = faker(20);  
// 谎报年龄，比实际年龄大5岁  
console.log(xiaoming(5));  
 
// xiaohong 实际年龄 20  
var xiaohong = faker(20);  
// 谎报年龄，比实际年龄小5岁  
console.log(xiaohong(-5));  

</script>  
</body>  
</html>
```

**垃圾回收机制：**

js 在执行过程中，会自动将不再使用的变量或函数进行销毁，收回这些变量或函数所占用的内存空间。

1，所有全局变量和函数都不会被垃圾回收机制回收，因为全局变量和函数随时有可能会被再次使用。

2，所有普通的局部变量和局部函数，在函数调用执行完成之后，都会被回收，因为函数每次调用，都会产生新的局部变量和局部函数。

3，被外部调用过的闭包函数，产生的局部变量或局部函数不会被回收，因为随时有可能会被再次调用。

```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  

<script>  

function fn1() {  
  var num = 10;  

  function fn2() {  
    console.log('hello world!');  
  }  
  console.log(num)  
  fn2();  
}  
// 第一次调用，声明一个局部变量 num 和 局部函数 fn2  
// fn1();   
// 第一次调用完成之后， num 和 fn2 不会再被使用了， 垃圾回收机制会将它们回收。  
 
// 第二次调用，会声明一个新的局部变量 num 和 局部函数 fn2  
// fn1();   
// 第二次调用完成之后， 新的 num 和 fn2 也会被垃圾回收机制回收。  
 
 
function counter() {  
  var num = 1;  
  return function () {  
    num ++;  
    return num;  
  }  
}  
  
// 调用 counter ，声明 num 和 匿名函数，并将匿名函数返回  
var c1 = counter();  
  
// 调用匿名函数，让 num 自增  
c1();  
 
// 因为不确定 c1 会被调用多少次，垃圾回收机制无法回收 num 和 匿名函数  
c1();  
c1();  
c1();  
 
</script>  
 
</body>  
</html>
```


### 即时调用函数 – IIFE

---

IIFE 是 immediately-invoked function expression 的缩写，立即调用函数表达式

IIFE 是一个在定义时就会立即执行的函数，也叫自执行函数，是匿名函数的特定使用场景。

**语法结构：**

(function(形参) {  
    ... // 代码块;  
})(实参)

**说明：**

1，IIFE 函数的作用是产生类似闭包一样的局域作用域，保护数据。

2，IIFE 函数不需要命名，也不会被声明提升。

**IIFE 函数变体版：** 可以使用 ~ + - ! 等一元运算符实现变体版 IIFE 函数。
```js

// 位运算符版  
~function(形参) {  
  ...// 代码块;  
}(实参);  
      
// + 运算符版  
+function(形参) {  
  ...// 代码块;  
}(实参);  
      
// - 运算符版  
-function(形参) {  
  ...// 代码块;  
}(实参);  
      
// ! 运算符版  
!function(形参) {  
  ...// 代码块;  
}(实参);  
```


```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
    
<script>  
​  
var num = 100;  
​  
// IIFE 是匿名函数，不需要命名  
(function () {  
  console.log("hello");  
})();  
​  
(function() {  
  // 在 IIFE 中声明的变量为局部变量，即使与全局变量同名也没关系。  
  var num = 200;  
  /*   
    在团队协作开发项目时，经常会因为不同开发人员声明了相同的全局变量，  
    而导致变量冲突，造成代码BUG。  
    IIFE 函数可以很好地避免这一点。  
  */  
  console.log(num);  
})();  
console.log(num);  
​  
/*   
  var fn1 = function() {  
    console.log("这是一个函数表达式");  
  }  
  // 函数表达式必须使用分号结束，这里没有添加分号，JS引擎将  
  // 下面的 IIFE 函数解析成了 fn1 函数的一部分，导致报错。  
  (function() {  
    console.log("world");  
  })()  
*/  
​  
// IIFE 函数传参  
(function(/* 这里是IIFE函数的形参位置 */ a) {  
  console.log(a);  
})(/* 这里是IIFE的实参位置 */ 123);  
​  
// IIFE 函数返回值  
// var num = (function() {  
//   return 10 + 20;  
// })();  
// console.log(num);  
​  
var a = (function() {  
  return "12.50元";  
})();  
// 有返回值的 IIFE 函数的结果可以参与运算。  
console.log( parseFloat(a) * 3 );  
​  
// IIFE 函数的变体版本  
var p1 = ~function() {  
  console.log(123);  
  return '12.50元';  
}();  
var p2 = +function() {  
  console.log(123);  
  return '12.50元';  
}();  
var p3 = -function() {  
  console.log(123);  
  return '12.50元';  
}();  
var p4 = !function() {  
  console.log(123);  
  return '12.50元';  
}();  
// 变体版 IIFE 函数的最终结果与期望的返回值不一致，不适合应用在需要参与运算的场景中。  
console.log(p1, p2, p3, p4);  
​  
</script>  
</body>  
</html>
```


IIFE 函数会增加代码阅读难度，除非必要，不建议使用（如果没有理由来表明需要使用 IIFE 函数，那就不要使用它！）。

### 数组

---

数组是多个数据的集合，数据本身可以是字面量，也可以是变量，可以是任何数据类型。

**数组创建：** 数组可以通过 字面量 和 构造函数 两种方式创建。

字面量方式： []

构造函数方式： new Array()

**说明：**

1，数组的各项之间使用逗号分隔。

2，数组中的每一个值都可以是单独的任意数据类型。

3，数组属于引用类型，将数组赋值给变量，是将数组的引用地址赋值给变量。

4，数组的 typeof 值为 object。

**引用类型：** 引用类型又称复杂数据类型。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
​  
<script>  
// 字面量方式定义数组  
var arr = [];  
​  
// 普通变量只能保存一个值  
var a = 1;  
var b = 2;  
var c = 3;  
var d = 4;  
​  
// 数组可以保存任意多个值  
var arr = [1,2,3,4];  
console.log(arr);  
​  
// 数组中可以保存任何数据类型，包括数组，但通常约定只存储一种数据类型的值  
var arr2 = [1, 'abc', true, [2,3]];  
console.log(arr2);  
​  
// 数组的 typeof 值为 object  
console.log(typeof arr);  
</script>  
</body>  
</html>

### 数组访问和修改

---

数组使用下标来访问里面每一项的值。

**语法：**

var arr = [1,2,3,4];

console.log(arr[0]); // 1

**说明：**

1，数组使用 [] 来表示下标

2，下标从0开始

3，修改一个数组中不存在的下标的值，不会出错，而是会在该位置直接添加新值。

4，访问一个数组中不存在的下标的值，不会出错，而是返回 undefined，表示没有值。

<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
    
<script>  
​  
var arr = [1,2,3,4];  
​  
// 通过下标来访问数组中具体的每一个值，下标从0开始  
console.log(arr[0]);  
console.log(arr[1]);  
console.log(arr[2]);  
console.log(arr[3]);  
​  
// 也可以通过下标来修改数组中的指定值。  
arr[1] = 20;  
​  
// 访问一个不存在的变量会抛出错误  
// console.log(a);  
// 访问数组中不存在的值，并不会抛出错误，而是返回 undefined  
console.log(arr[10]);  
​  
// 给一个不存在的下标位置赋值，会将值存储到这个位置中  
arr[10] = 100;  
console.log(arr[10]);  
​  
// 没有存储值的位置不会有任何数据，不占用内存空间  
// 访问不存在的位置，会返回 undefined ，这个 undefined 值是由  
// JS 解析器运算获得的，并不是存在数组中的。  
console.log(arr);  
​  
</script>  
</body>  
</html>
```


### 数组的 length 属性

---

数组的 length 属性 表示数组中保存的数据总数。

**使用方式：** 数组名称.length

**特点：**

数组的 length 属性可以被修改。

1，如果修改之后的 length 值比原来的小，超出部分的数据会被舍弃。

将 length 设置为0 ，可以快速清空数组。

2，如果修改之后的 length 值比原来的大，不足部分默认为空，不会产生任何新数据。

3，通过 数组名称[数组名称.length - 1] 可以访问到数组最后一项。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
    
<script>  
​  
var arr = [1,2,3,4];  
​  
// 数组的 length 属性表示数组中一共保存了多少数据。  
console.log(arr.length);  
​  
// 数组的最后一条数据的下标可以用 arr.length - 1 计算得出。  
console.log(arr[arr.length - 1]);  
​  
// 数组的 length 属性可以被修改  
arr.length = 2;  
// 如果新的length值小于原来的值，超过length长度的数据会被丢弃。  
console.log(arr);  
arr.length = 6  
// 如果新的length值大于原来的值，不会增加新的数据，新增的位置中都是空的，没有任何数据。  
console.log(arr);  
​  
</script>  
</body>  
</html>
```

### 数组方法

---

通过数组方法，可以操作数组里面各项的值，也可以添加或删除数组中的值。

方法本质上是一个JS内置封装好的函数。

**使用：** 数组名称.方法名称(参数);

**说明：**

1，并不是所有方法都有参数。

2，有些方法会修改数组本身；有些方法不会修改本身，而是产生新的数组。

3，有些方法有返回值，有些没有。

##### 数组的首尾操作方法（修改原数组）

**方法：**

push() : 往数组的尾部添加一个或多个值。

pop() : 从数组的尾部删除最后一个值。

unshift() : 往数组的头部添加一个或多个值。

shift() : 从数组的头部删除第一个值。

**参数：**

push() / unshift() : 参数为要添加的一个或多个值;

pop() / shift() ： 没有参数。

**返回值：**

push() / unshift() : 返回值为添加值之后的新数组的length。

pop() / shift() : 返回值为被删除的值

**堆栈与队列：**

堆栈：push - pop（最后一个元素后进先出）

队列：push - shift（最后一个元素后进后出，第一个新元素先进先出）

**案例：** \["春","夏","秋","冬"] 将数组最后一项移动到开头
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
    
<script>  
​  
var arr = [1,2,3,4];  
​  
// 往数组的尾部添加新的值，可以添加一个值，也可以添加多个值  
arr.push(5);  
arr.push(6,7,8);  
console.log(arr)  
​  
// 从数组的尾部删除最后一个值，没有参数，调用一次只能删除一个值  
arr.pop();  
// 删除几个值，就需要调用几次  
arr.pop();  
console.log(arr);  
​  
// 往数组的头部添加新的值，可以添加一个值，也可以添加多个值。  
arr.unshift(5);  
arr.unshift(6,7,8);  
console.log(arr);  
​  
// 从数组的头部删除第一个值，没有参数，调用一次只能删除一个值  
arr.shift();  
// 要删除几个值，就需要调用几次  
arr.shift();  
console.log(arr);  
​  
var arr2 = ['a','b','c','d'];  
​  
// push() 和  unshift() 方法的返回值都为添加新值之后的数组的 length   
console.log(arr2.push('e','f'));  
console.log(arr2.unshift('g','h'));  
console.log(arr2);  
​  
// pop() 和 shift() 的返回值 都为被删除的值  
console.log(arr2.pop());  
console.log(arr2.shift());  
console.log(arr2);  
​  
/*   
  push() / pop() / unshift() / shift() 都是修改的原数组  
​  
  四个方法 与 堆栈 和 队列的对应关系  
      堆栈：堆栈的特点是后进先出  
      push  - pop（最后一个元素后进先出）     
      队列：队列的特点是先进先出  
      push - shift（最后一个元素后进后出，第一个新元素先进先出）  
  堆栈 与 队伍 是计算机底层的处理逻辑，前端只需要了解即可。  
*/  
​  
// 案例： ["春","夏","秋","冬"] 将数组最后一项移动到开头  
var arr = ["春","夏","秋","冬"];  
​  
// 常规写法  
// var str = arr.pop();  
// arr.unshift(str);  
// console.log(arr);  
​  
// 简化写法  
// arr.unshift(arr.pop());  
// console.log(arr)  
​  
// 同理，也可以将第一项移动到最后  
arr.push(arr.shift());  
console.log(arr);  
​  
</script>  
​  
</body>  
</html>
```


#### 数组的合并方法（不修改原数组）

concat()

合并一个或多个数组。

**语法：** 数组1.concat(数组2，数组3，… , 数组n)；

**特点：**

1，合并顺序为书写顺序。

2，参数可以是数组，也可以是普通字面量或变量。

3，返回值是合并之后的新数组。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
​  
<script>  
​  
var arr1 = [1,2,3,4];  
var arr2 = [5,6,7,8];  
​  
var arr3 = arr1.concat(arr2);  
// concat() 方法将多个数组合并，返回一个新数组  
console.log(arr3);  
// concat() 方法并不会修改原来的数组  
console.log(arr1, arr2);  
​  
// 调用顺序决定了合并顺序  
var arr3 = arr2.concat(arr1);  
console.log(arr3);  
​  
var arr4 = arr1.concat(arr2, 100, 'true', null, undefined, function(){});  
// 必须是通过数组来调用 concat()， concat() 的参数不要求一定是数组，可以是任何类型的数据。   
// console.log(arr4);  
​  
// 可以直接在数组字面量后面调用 concat() 方法  
// var arr5 = [].concat(arr1, arr2);  
// console.log(arr5);  
​  
// 只会合并第一层数组  
var arr6 = [].concat(arr1, ['a','b', [7,8,9]]);  
console.log(arr6);  
​  
</script>  
​  
</body>  
</html>
```
