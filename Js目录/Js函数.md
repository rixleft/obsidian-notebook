# function
### 函数的声明

函数是只有被调用时才会执行的，可以重复使用的代码块。

**结构**：
```js
 function 函数名(参数) {  
    //代码块;  
 }
```

四个组成部分： function 关键字、函数名称、形参列表 ()、代码块 {}

**规则**：

1，函数名与变量名的命名规范相同。

2，函数的 {} 内部可以书写任意多行代码。

3，函数里面的代码默认并不会执行。

4，函数属于复杂数据类型， typeof 值为 function。

### 函数调用

函数默认不会执行，只有被调用之后，函数里面的代码才会被执行。

**语法：**
```js
函数名();
```

**特点：**

1，不调用，里面的代码就不会执行

2，同一函数可以多次调用，次数不限。

3，可以在同一作用域下的任意位置中调用。

4，每次调用，里面的代码都会重新执行。

5，函数里面能否访问到函数外面的变量，与调用位置无关，与声明位置有关（作用域）。

6，函数里面的代码执行完毕之后，才会继续往下执行代码。

### 函数的参数

可以给函数传递参数，让函数使用更灵活，更通用。

参数分为 **形参** 和 **实参** 两部分：

**形参**： 形式上的参数，声明函数时定义，用来等待接收实参传递过来的值。

**实参**： 实际传入函数中的参数，调用函数时传递，用来给形参赋值。

**结构**：

```js
// 定义带参数的函数  
function 函数名(形参1，形参2，…, 形参n) {  
    ... // 代码块  
}  
// 调用函数，并传递参数  
函数名(实参1，实参2，…, 实参n); 
```

**规则**：

1，实参与形参的顺序是一一对应的。

2，形参就是一个在函数内部声明的变量，命名规则与变量命名规范相同。

3，实参是在给对应的形参赋值，实参的数据类型决定了形参的数据类型。

###   函数内的特殊对象 arguments

函数的 **形参** 与 **实参** 数量可以是不相等的：

1，当形参的数量多于实参时，没有实参对应的形参的默认值为 undefined。

2，当实参的数量多于形参时，对应关系不变，没有形参的实参也会传入函数内，但无法直接使用。

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

function fn1(a, b, c) {
  // 当形参的数量多于实参时，没有实参对应的形参的默认值为 undefined。
  console.log(a, b, c);
}

fn1(1,2); // 1, 2, undefined

function fn2(a, b) {
  // 当实参的数量多于形参时，对应关系不变，没有形参的实参也会传入函数内，但无法直接使用
  console.log(a, b);
}

fn2(10, 20, 30, 40); // 10, 20

</script>

</body>
</html>
```

**arguments:**

所有的实参除了会赋值给对应的形参之外，同时会被保存到函数内部的特殊对象 **arguments** 中。

**arguments 特点：**

1，arguments 是一个类数组对象，里面保存了所有实际传入函数中的参数的值。

2，通过 [下标] 的方式访问和修改 arguments 中保存的具体参数的值。

3，通过 length 属性 可以获取到 arguments 中保存的参数个数。

4，arguments 中的值与形参的值是相互关联的，修改对应的形参，arguments 对应位置的值也会被修改，反之，修改arguments指定位置的值，对应位置的形参也会被修改。

5，arguments 是函数内部特有的，外部无法使用。

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

function fn1(a, b, c, d) {
  // arguments 中保存了所有实参
  console.log(arguments);

  // 可以通过下标的方式访问每一个实参，下标从0开始
  console.log(arguments[0]);
  console.log(arguments[1]);
  console.log(arguments[2]);
  console.log(arguments[3]);

  // length 属性的值表示实参的数量
  console.log(arguments.length);

  // arguments中的值 与 形参是相互关联的
  arguments[0] = 10;
  console.log(a);
  b = 200;
  console.log(arguments[1]);
}
fn1(1,2,3,4);

// arguments 是函数内部特有的，外部无法使用。
console.log(arguments);

</script>

</body>
</html>
```

### 函数返回值 return

函数可以将内部的值返回到函数外部，供外部使用。

**结构：**

 function 函数名() {  
    ... // 代码块;  
    return 要返回给外面的值;  
 }
**规则：**

1，返回值可以是字面量或运算表达式，也可以是变量，甚至可以是一个函数。

2，return 会提前终止函数内部的代码执行，return 下面到 } 之间的所有代码都不会再执行。

3，return 是函数内部特有的，函数外部不能使用。

4，如果函数内部不使用 return 返回具体的值，默认会返回 undefined。

5，函数只有调用了才会执行，所以只有在调用函数时，才能得到return 的返回值。

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

function demo() {
  // 函数可以将任何类型的值作为返回值返回到函数外面。
  // return 1234;
  // return 'abc';
  // return true;
  // return 10 + 100;
}
console.log(demo());
    
function sum(a, b) {
  return a + b;
}
// 函数的返回值也可以继续参与运算
console.log(sum(1 + 2) * 10);

function fn1() {
  console.log('hello');
  console.log(10 * 10);
  return 3 + 4;
  // return 会提前结束函数执行 后面的代码都不会再执行
  console.log("前端开发");
  console.log(12345);
}
fn1();

// return 是函数内部特有的关键字，外部无法使用。
// return;
function fn2() {
  for(var i=0; i<5; i++) {
    // return 也会直接终止循环，并且直接让函数提前结束执行。
    if(i == 2) return;
    console.log(i);
  }
  console.log("函数执行完毕");
}
fn2();

function fn3() {
  console.log("这不是返回值");
}
// 如果函数内部没有使用 return ，或者return 后面没有任何内容，函数的返回值 默认为 undefined
console.log("这里才是返回值: ", fn3());

</script>

</body>
</html>
```

###   模块化编程思想

模块化编程是基于函数使用的一种编程思想。

**模块化：** 将固定的可重复使用的公共代码写成函数(封装函数)，供后续重复使用。

生活中的模块化例子：

1，15天建造30层酒店

2，自行车组装，电脑组装等。

案例：

查找任意整数范围内的所有完美数。

完美数定义：一个数的所有除了本身之外的约数之和，还等于这个数

如： 6 为完美数 （6 除自身之外的约数为 1 , 2 , 3 。 1 + 2 + 3 = 6）

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

// 计算一个数的除自身之外的所有约数的和
function sum(num) {
  var result = 0;
  for (var i=1; i<num; i++) {
    if (num % i == 0) result += i;
  }
  return result;
}
// console.log( sum(6) )

// 寻找指定范围内的完美数
function getNum(num) {
  for(var i=1; i<num; i++) {
    if ( i == sum(i) ) {
      console.log(i);
    }
  }
}
// 寻找 1000 之内的完美数，并输出到控制台
getNum(1000);
</script>

</body>
</html>
```
通常会将封装好的功能函数单独放到一个js文件中，让函数使用范围更广，更灵活。


### 函数表达式

定义函数的两种方式：
```js
 // 1，声明式定义：
 function 函数名称() {
 	... // 代码块
 }

 // 2，函数表达式：
 var 函数名 = function () {
 	... // 代码块
 };
```

两种定义方式声明的函数，都使用 函数名() 调用。

**说明：**

1，声明式定义函数后面不需要以分号结束，但函数表达式后面建议使用分号结束。

2，函数表达式右边的函数为匿名函数（也称拉姆达函数）。

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

// 声明式定义
function fn1() {
  console.log("函数声明");
}
fn1();

// 表达式定义
var fn2 = function() {
  console.log("函数表达式");
}
fn2();

var fn3 = function fn4() {
  console.log('函数表达式的函数后面不需要名称');
}
fn3();
// 名称会被自动忽略
fn4();

/* 
  表达式方式定义，后面的函数是一个匿名函数，不需要命名，即使命名，浏览器也会忽略。
*/

</script>

</body>
</html>
```

### 函数的声明提升

与变量的声明提升类似，函数的声明也会有提升。

JavaScript 引擎在解析时，会将所有函数的声明提升到当前作用域的最上面。

**注意：**

1，通过函数声明式定义的函数，会将整个函数提升到最上面。

2，通过函数表达式定义的函数，只会将函数名定义提升到最上面（相当于变量声明），函数赋值还是在原来的位置（在执行到函数赋值位置之前，函数名就只是一个普通变量名）。

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

// 函数可以在声明之前调用，是因为函数的声明会被自动提升到当前作用域的最上面。
fn1();

function fn1() {
  console.log(111);
}

fn1();

// 函数表达式只会提升变量声明，匿名函数的赋值不会提升。
fn2();

var fn2 = function() {
  console.log(2222);
}

fn2();

</script>

</body>
</html>
```

### 全局变量与局部变量

局部变量：

在函数内部声明的变量，被称为局部变量。

局部变量只有在定义变量的函数中能访问到，在函数外部访问不到。

全局变量：

变量声明时，没有被任何函数包裹，这样的变量被称为全局变量。

全局变量可以在任何函数的内部或外部访问到。

注意：

变量和函数能否被访问到，还会受 JavaScript 引擎解析影响，不同的 script 标签中：

1，后面的script标签中定义的变量或函数，前面的script标签中无法被访问。

2，前面的script标签中定义的变量或函数，后面的script标签中可以访问。

这跟 JavaScript 引擎解析顺序有关，与作用域无关。

3，这里有一个地方需要注意，函数内部声明变量的时候，一定要使用var命令。如果不用的话，你实际上声明了一个全局变量！
```js
function f1(){  
　　　　n=999;  
　　}

　　f1();

　　alert(n); // 999
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
var a = 10;

function outerFn() {
  var b = 10;

  // 函数内部可以访问全局变量
  console.log(a);
  console.log(b);

  function innerFn() {
    var c = 100;
    console.log(c);

    // 内部函数中可以访问外部函数中的局部变量
    console.log(b)
  }
  innerFn();

  // 外部函数中访问不到内部函数中的局部变量
  console.log(c);
  
}

outerFn();

// a 为全局变量，在 a 的赋值语句下面所有位置都可以访问到
console.log(a);
// b 为局部变量，全局环境下无法访问
console.log(b);

// innerFn 是局部函数，外部无法访问
innerFn();

</script>

</body>
</html>
```

### 全局变量的应用

全局变量可以被后面的所有函数访问和修改，利用这个特性，全局变量可以在多个函数之间共享，实现多个函数之间的数据互通目的。

**注意：**

在使用全局变量共享数据时，函数内部不能声明与全局变量同名的局部变量，否则函数内部不会访问全局变量。

**全局变量使用原则：**

尽量减少使用全局变量，只有需要在多个函数之间共享数据时才使用全局变量。

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

<script>
// // 全局变量
// var num = 0;
// // 增加num
// function addNum() {
//     num++;
//     console.log(num);
// }
// // 减少num
// function reduceNum() {
//     num--;
//     console.log(num);
// }
// // 通过全局变量在两个函数中通信
// addNum();
// addNum();
// addNum();
// reduceNum();
// reduceNum();
// reduceNum();
// addNum();
// addNum();
// addNum();
// addNum();

// function addNum() {
//    // 函数内部不能声明与全局变量同名的局部变量，否则内部将不会访问外面的全局变量
//     var num = 0;
//     num++;
//     console.log(num);
// }
// addNum();
// addNum();
// addNum();
// console.log(num);
</script>
</body>
</html>
```

### 递归函数

递归函数是指在函数内部调用自己的特定函数使用方式。

**注意：**

递归函数内部一定要作越界判断，否则很容易变成死循环，导致内存溢出BUG。

案例：

累加器： 计算 1 ~ 10 之间的所有数字相加的和。

```js
// 循环写法
var result = 0;
for (var i=1; i<=10; i++) {
  result += i;
}
console.log(result);

// 递归写法
function sum(num) {
  if (num == 1) return 1;
  return num + sum(num - 1);
}
console.log( sum(10) );

```



### 斐波那契数列

斐波那契数列定义 ：

又称黄金分割数列，因数学家莱昂纳多·斐波那契（Leonardo Fibonacci）以兔子繁殖为例子而引入，故又称为"兔子数列"，指的是这样一个数列：

1，1，2，3，5，8，13，21，34，55，89...

这个数列从第3项开始，每一项都等于前两项之和。

```js
 function fibonacci(n) { // n 表示数列中的第几个数字
    if ( n == 1 || n == 2) return 1
    return fibonacci(n - 1) + fibonacci(n - 2);
  }

  var result = fibonacci(6);
  console.log(result);
```

