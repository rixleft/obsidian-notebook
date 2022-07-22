# JavaScript基础 第七天

## 数组方法

#### 数组的提取方法 （不修改原数组）

**slice()**

从数组中提取出指定下标范围的值，并返回一个新数组。

**语法：**

数组.slice(start, end)；

start: 开始提取的下标位置

end: 结束提取的下标位置

**特点：**

1，提取范围包括开始位置的值，不包括结束位置的值。

2，开始位置必须小于结束位置。

3，只指定一个参数表示从指定下标位置开始，提取后面所有的值。

4，不指定参数，会复制整个数组。

5，参数可以为负数，表示从后往前数位置（但start表示的位置必须在end之前）
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
var arr = [10, 20, 30, 40, 50, 60];  
​  
var arr1 = arr.slice(1, 3);  
// 提取的范围包括开始下标1对应的10，但不包括结束下标3对应的40  
console.log(arr1);  
// slice() 方法是返回一个新的数组，原数组不会被修改  
console.log(arr);  
​  
// 开始位置必须小于结束位置，如果开始位置大于或等于结束位置，返回空数组  
console.log( arr.slice(3, 1) );  
console.log( arr.slice(2, 2) );  
​  
// 只指定一个参数，表示从这个参数位置开始，提取后面所有的值。  
console.log( arr.slice(3) );  
​  
// 不指定参数，会复制整个数组  
console.log( arr.slice() );  
​  
// 参数可以为负数，表示从右往左数下标位置，最后一个值的下标位置为 -1  
// 负数参数的第一个参数同样也必须小于第二个参数  
console.log( arr.slice(-4, -2) );  
// 正负参数可以同时使用，只要参数表示的下标位置是第一个小于第二个即可  
console.log( arr.slice(-4, 5) );  
console.log( arr.slice(2, -2) );  
​  
// -5 表示下标为2 的值，位置比4小，因此提取不到值，返回空数组  
console.log( arr.slice(4, -5) );  
</script>  
</body>  
</html>
```

#### 数组的添加、删除、替换（修改原数组）

**splice()**

删除数组中指定数量的值，并添加新的值到数组中。

**参数：** 任意多个

第一个参数： 进行添加、删除或替换的开始位置

第二个参数： 从开始位置往后要删除的值的个数

第三个参数开始到最后一个参数： 要添加到数组中的新值

**添加操作：** splice(开始位置, 0, 新值1,新值2,新值3, …,新值n);

**删除操作：** splice(开始位置, 删除个数)

**替换操作：** splice(开始位置, 替换个数, 替换值1,替换值2,替换值3, …,替换值n)

**说明：**

1，只指定一个参数，表示从指定位置开始删除后面所有的值，返回值为被删除的值。

2，不指定参数则不会删除任何值， 返回值为空数组。

**返回值：**

添加、删除、替换操作的返回值都为包含被删除的值的数组，如果删除长度为0，则返回空数组
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
var arr = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];  
​  
// 删除数据  
// 从下标2的位置开始删除4个值， 即删除 c d e f  
// arr.splice(2,4);   
// console.log(arr);  
​  
// 添加数据  
// 添加数据，就是将删除个数设置为0，然后添加新值  
// arr.splice(2, 0, 10, 20);  
// console.log(arr);  
​  
// 替换数据  
// 删除两个值，再添加两个新值，相当于是用新值替换掉了原来的值  
// arr.splice(2, 2, 10, 20);  
// console.log(arr);  
// 删除的个数与添加的个数并不是对应的, 可以少删除几个，多添加几个。  
// arr.splice(2, 2, 10, 20, 30);  
// 也可以多删除几个，少添加几个  
// arr.splice(2, 4, 10, 20);  
// console.log(arr);  
​  
// 如果只指定一个参数，表示从参数指定的位置开始，删除后面所有的值  
// arr.splice(3);  
// console.log(arr);  
​  
// 如果不指定参数，将不会删除任何值。  
// arr.splice();  
// console.log(arr);  
​  
​  
// 返回值  
// splice() 方法的返回值始终是一个数组，数组中的内容是被删除的值  
// 删除了四个值，返回值数组中保存的就是被删除的这四个值  
// var delArr = arr.splice(2, 4);  
// console.log(delArr);  
​  
// 删除了四个值，然后添加了2个新值，但返回值依然还是保存了被删除的四个值的数组。  
// var delArr = arr.splice(2, 4, 10, 20);  
// console.log(delArr);  
​  
// 因为删除的个数为0，即没有删除任何值，所以返回的是空数组 []  
// var delArr = arr.splice(2, 0, 10, 20);  
// console.log(delArr);  
​  
// 只指定一个参数，返回值就是包含从参数指定的位置开始的所有的值数组  
// var delArr = arr.splice(2);  
// console.log(delArr);  
​  
// 不指定参数，不删除任何值，所以返回值也是空数组 []  
// var delArr = arr.splice();  
// console.log(delArr);  
​  
</script>  
​  
</body>  
</html>
```

#### 数组排序（修改原数组）

**reverse()**

将数组顺序完全颠倒过来， 没有参数， 返回值为颠倒之后的新数组。
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
  var arr = [1,2,3,4];  
​  
  // 将数组完全颠倒过来  
  arr.reverse()  
  console.log(arr); // [4,3,2,1]  
​  
  var arr2 = ['a','b','c'];  
  // 返回值是被颠倒之后的数组  
  console.log( arr2.reverse() );  
  console.log(arr2);  
​  
</script>  
    
</body>  
</html>
```

**sort()**

将数组按指定规则进行排序。

**不指定参数：**

将数组中的所有值都当作字符串（临时转换为字符值），然后按字符串比较大小规则从小到大排序。

**指定参数：**

参数必须是一个返回值为number类型数字的函数，否则为非法参数，直接忽略。

**指定函数参数之后的排序规则：**

sort() 方法会自动传递两个值给函数，函数内部需要对传入的两个参数进行大小比较，然后根据比较结果返回对应值，实现排序（假设传入的两个值为a, b）：

返回负值： 表示a, b 的位置不变。

返回正值： 表示a, b 两个值需要交换位置。

返回 0 ：表示a, b 为两个相等的值，位置不需要交换（不同浏览器版本效果有差异）

**注意：**

指定的函数内部必须明确对 a, b 进行处理，直接返回数值会有兼容问题（ff 与 chrome）。
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
var arr = [2,1,4,8,7,9,6,3];  
​  
// 查看数组所有值  
// console.log(arr);  
​  
// 默认排序  sort 方法不传递参数，使用默认排序方式进行排序。  
// arr.sort();  
// console.log(arr);  
​  
var arr2 = [112, 21, 13, 205, 78];  
// 默认排序会先将数组的所有值转换成字符串（临时转换，不是直接把数组中的值转成了字符串），然后按字符串比较大小的规则进行从小到大排序。  
// arr2.sort();  
// console.log(arr2);  
​  
/*   
  字符串比较大小规则：  
    字符串值是比较的字符的 unicode 编码，不是直接比较的字符串值。  
    因为字符串并不全是数字，更多的是其他字符，没办法直接比较大小。  
    每个字符都有一个唯一的字符编码，可以通过字符串的 charCodeAt() 方法查看  
*/  
​  
// 字符串类型的数字也是有唯一的字符编码的  
// console.log( '1'.charCodeAt() ); // 49  
// console.log( 'A'.charCodeAt() ); // 65  
// console.log( '你'.charCodeAt() ); // 20320  
// console.log( '我'.charCodeAt() ); // 25105  
​  
​  
// 自定义排序   传递参数  sort 方法会按照自定义规则进行排序  
/*   
  要使用自定义排序， 传递的参数必须符合以下规则，否则仍然使用默认排序方式：  
    1，只能传递一个参数，并且这个参数必须是一个函数。  
    2，传递的函数参数必须有返回值。  
    3，函数参数的返回值必须是 正数 负数 或 0 的 number 类型的数字  
​  
  符合自定义排序规则的参数函数，称为排序函数  
​  
  sort 方法 每次只能对两个值进行比较，确定这两个值的先后顺序。  
  sort 方法会不断调用排序函数，并自动将每次需要排序的两个值作为参数传入排序函数中，排序函数需要根据实际排序需求，返回指定的数值来实现排序功能。  
​  
  sort() 方法根据排序函数的返回值，来确定传入的两个值在数组中的位置是否需要交换，规则为：  
    1，如果返回值是正负，sort会交换两个值的位置。  
    2，如果返回值是负数，sort不会交换两个值的位置。  
    3，如果返回值是0，表示传入的两个值是相等的，不同浏览器中，sort方法的处理方式有所不同，有可能会交换两个值的位置，有可能不会交换（对结果不会有影响）。  
    
  需要注意：  
    排序函数的返回值必须是经过运算之后的结果，直接返回数值，会导致不同浏览器的兼容问题。（比如 firefox 与 chrome 浏览器中的结果就完全相反）  
*/  
​  
// 直接返回数字，不同浏览器中效果不同，有兼容问题  
// chrome 正数 不排序   负数  倒序      
// firefox  正负   倒序    负数   不排序  
// arr.sort(function() {  
//   return 1;  
//   // return -1;  
//   // return 0;  
// });  
// console.log(arr);  
​  
​  
// 从小到大排序  
// arr.sort(function(a, b) {  
​  
//   if (a > b) {  
//     // 从小到大是小的值在前面，大的值在后面  
//     // 所以如果 a > b ，需要交换这两个数字在数组中的位置  
//     // 只需要返回一个正数，sort方法就会自动交换两个数字的位置  
//     return 112;  
//   } else if (a < b) {  
//     // 如果 a < b ，小的数字已经是在前面的了，不需要交换位置  
//     // 返回一个任意的负数  
//     return -10;  
//   } else {  
//     // 既不大于，也不小于，两个数是相等的。  
//     // 返回 0 ，让 sort 方法自己决定要不要交换  
//     return 0;  
//   }  
​  
// });  
// console.log(arr);  
​  
// 从大到小排序  
// arr.sort(function(a, b) {  
​  
//   if (a > b) {  
//     // 从大到小是大的值在前面，小的值在后面  
//     // 所以如果 a > b ，不需要交换这两个数字在数组中的位置  
//     // 返回一个负数，告诉 sort 方法，不需要交换两个数字的位置  
//     return -112;  
//   } else if (a < b) {  
//     // 如果 a < b ，小的数字在前面，需要交换一下位置  
//     // 返回一个任意的正数  
//     return 10;  
//   } else {  
//     // 既不大于，也不小于，两个数是相等的。  
//     // 返回 0 ，让 sort 方法自己决定要不要交换  
//     return 0;  
//   }  
​  
// });  
// console.log(arr);  
​  
/*   
  由于：  
    如果 a > b 时： a - b  一定会得到一个正数；  
    如果 a < b 时:  a - b  一定会得到一个负数;  
    如果 a == b 时:  a - b  一定会得到一个0;  
    因此，从小到大的规则可以简化为:  return a - b;  
​  
  反之：  
    如果 a > b 时： b - a  一定会得到一个负数；  
    如果 a < b 时:  b - a  一定会得到一个正数;  
    如果 a == b 时:  b - a  一定会得到一个0;  
    因此，从大到小的规则可以简化为:  return b - a;  
*/  
​  
// 随机排序  
// var arr3 = [1,2,3,4,5,6,7,8];  
// arr3.sort(function() {  
//   // 随机排序的公式是固定的  
//   return Math.random() - 0.5;  
// })  
// console.log(arr3);  
​  
// 排序函数可以直接写在 sort 方法的小括号中：  
// 使用匿名函数即可  
// arr.sort(function(a, b) {   
//   // 从小到大排序  
//   return a - b;  
// });  
// console.log(arr);  
​  
// 排序函数也可以是提前写好的函数， sort 方法的小括号里只需要写 函数名 即可  
// 函数名后面不需要写 () !!!  
// arr2.sort( cmp );  
// console.log(arr2);  
​  
// function cmp(a, b) {   
//   // 从大到小排序  
//   return b - a;  
// }  
​  
​  
/*   
  总结：  
  从小到大排序  
    sort(function(a, b) {  
      return a - b;  
    });  
​  
  从大到小排序  
    sort(function(b, a) {  
      return b - a;  
    })  
​  
  随机排序  
    sort(function() {  
      return Math.random() - 0.5;  
    })  
​  
*/  
// 如果数组中的值为字符串，排序函数中需要注意在运算前要将字符串值转换为数字  
var arr = ['12.50元', '48元', '26元', '99.99元', '48.90元', '8.80元'];  
​  
// 对价格进行从小到大排序  
arr.sort(function(a, b) {  
  // 注意要保留小数  
  return parseFloat(a) - parseFloat(b);  
})  
console.log(arr);  
​  
// 只有数字和字符串类型的数组才有排序的意义。  
​  
</script>  
​  
</body>  
</html>
```

#### 数组合并为字符串 （不修改数组）

**join()**

将数组中的所有值转成字符串，并使用连接符将所有字符串依次拼接成字符串。

**参数：**

一个 ， 指定要作为连接符的字符串

**返回值：**

拼接之后的字符串。

**说明：**

1，不指定参数，默认使用逗号作为连接符。

2，null 与 undefined 会转成空字符串 ""
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
// 不指定参数，默认使用 逗号 作为连接符  
// var str = arr.join();  
// join() 方法不会修改原数组，返回的是一个新字符串  
// console.log(arr, str);  
​  
// 指定参数，则以参数中的字符串为连接符  
// var str = arr.join('^_^');  
// console.log(arr, str)  
​  
​  
// 如果参数不是字符串，会按规则转换成字符串  
// var str = arr.join(true);  
// var str = arr.join(null);  
// var str = arr.join(NaN);  
// console.log(arr, str)  
​  
// undefined 作为参数会被忽略，以默认的逗号为连接符  
// var str = arr.join(undefined);  
// console.log(arr, str)  
​  
// 数组中的 null 和 undefined 值会被转换成空字符串 ''。  
var arr2 = [1, 'abc', null, undefined, true];  
var str2 = arr2.join();  
console.log(str2);  
​  
</script>  
</body>  
</html>
```


## 遍历数组

遍历数组，即查看并输出数组的每一个值。

**手动遍历：**

手动写出所有数组的下标 。

**循环遍历：**

for 循环（常用）， while 循环

**递归遍历：**

利用 pop() 或 shift() 方法，需要使用slice() 复制，并要判断数组中是否有值。
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
// 手动遍历   手动遍历又称为硬编码 （hard code 或  hard-coded）  
// 手动遍历 只会在调试的时候偶尔使用  
// console.log(arr[0]);  
// console.log(arr[1]);  
// console.log(arr[2]);  
// console.log(arr[3]);  
​  
// 循环遍历  
// for 循环  
// for (var i=0; i<4; i++) {  
//   // 利用循环的 i 值正好与 数组下标相同，将i当作数组下标使用  
//   console.log(arr[i]);  
// }  
​  
// 使用数组的length属性作为循环条件，让循环更灵活  
// for (var i=0; i<arr.length; i++) {  
//   // 利用循环的 i 值正好与 数组下标相同，将i当作数组下标使用  
//   console.log(arr[i]);  
// }  
​  
// while 循环   
// var i = 0;  
// while (i < arr.length) {  
//   console.log(arr[i]);  
//   // 千万别忘记让 i 自增，否则会变成死循环！  
//   i++;  
// }  
​  
​  
// 递归遍历  
function loop(arr) {  
  // 使用 slice() 方法复制一份，防止修改原数组  
  var tmpArr = arr.slice();  
​  
  // 从前往后遍历  
  // console.log(tmpArr.shift());  
​  
  // 从后往前遍历  
  console.log(tmpArr.pop());  
​  
  // 数组的 length 只要不为 0 ，就说明还有值  
  // 如果 length 为 0 , tmpArr.length 为假，判断条件不成立，递归停止  
  if (tmpArr.length) {  
    loop(tmpArr);  
  }  
}  
// 递归遍历与循环遍历相比，代码阅读难度更大，维护成本更高，容易造成死循环，并不常用。  
// 注意： 递归遍历，一定要使用 slice() 方法复制数组，否则原数组会被修改！  
loop(arr);  
​  
</script>  
​  
</body>  
</html>
```

## for 循环、数组与闭包的结合使用

数组中可以存储任意类型的数据，包括函数。

在循环中使用函数时，要注意函数执行时的变量引用问题。

**案例：**

使用for循环批量存储多个函数到数组中，每个函数被执行时，都输出for循环在执行过程中对应的循环变量的值。
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
// for 循环回顾  
// for (var i=0; i<5; i++) {  
//   console.log(i);  
// }  
// 先不在浏览器中运行，通过观察分析，说出下面这行代码的 i 会输出几？  
// 分析之后再在浏览器中运行，验证答案。  
// 如果结果与分析的不一致，思考并找出原因。  
// console.log(i);  
​  
// 定义一个空数组。  
var arr = [];  
​  
// 实例  
// for (var i=0; i<5; i++) {  
//   // 每次循环，都往数组中存入一个匿名函数。  
//   arr.push( function(){  
//     // 函数里面输出变量 i 的值  
//     console.log(i);  
//   } )  
// }  
​  
// 查看数组中的保存结果  
// console.log(arr);  
​  
// 数组里保存的都是函数，函数可以通过 () 来调用执行  
// 执行数组的第一个位置上保存的函数  
// 先不在浏览器中执行，分析一下输出结果  
// 如果输出结果与分析结果不一致，思考并找出原因  
// arr[0]();  
​  
/*   
  分析思路引导：  
    1，for 循环在执行过程中， 匿名函数有没有执行？  
    2，当 执行 arr[0]() 时，for循环已经执行结束了，此时 i 的值是多少？  
    3，匿名函数中的 console.log(i) , 这里的 i 访问的是哪里声明的 i ？  
*/  
​  
// 通过执行其他位置上的函数，来验证前面的分析。  
// arr[1]();  
// arr[2]();  
// arr[3]();  
// arr[4]();  
​  
/*   
  总结 arr[0]() 的执行过程：  
    1，当执行匿名函数里面的 console.log(i) 时，因为 匿名函数中没有声明过 i 变量，所以需要往上一层作用域中查找 i 是否有声明。  
    2，上一层就是顶层作用域了，只有 for 循环的 () 里面声明了变量 i ，因此匿名函数中的 i ,就是for循环时声明的 i 。  
    3，因为 执行 console.log(i) 时，for 循环已经结束了，i 的值就是 for 循环结束之后的 i 的值。   
*/  
​  
​  
// 新要求： 期望调用数组中每一个位置上的函数，分析对应输出当前这个位置的下标值。 如：  
// arr[0](); // 期望输出结果： 0  
// arr[1](); // 期望输出结果： 1  
// arr[2](); // 期望输出结果： 2  
// arr[3](); // 期望输出结果： 3  
// arr[4](); // 期望输出结果： 4  
​  
/*   
  面临问题：  
    因为在for 循环执行过程中，匿名函数不会执行，而当执行匿名函数时，for循环早已经执行完成，所以 i 的值总是为 for 循环结束之后的值。  
    
  解决思路：  
    想办法在循环过程中，将每次循环的 i 值都保存起来。  
​  
  具体办法：  
    使用 IIFE 函数将 匿名函数嵌套起来，然后把 i 当作参数传入 IIFE 函数中。  
    将IIFE里面的匿名函数作为返回值返回出来给 push() 方法当参数。  
​  
  IIFE 函数 与 里面的 匿名函数 是嵌套关系， 匿名函数中引用了 IIFE 函数中的形参， IIFE函数 将 匿名函数作为返回值返回，这些是闭包函数的特征，因此，里面的匿名函数是一个闭包函数。  
*/  
​  
//   
for (var i=0; i<5; i++) {  
  // 每次循环，都往数组中存入一个匿名函数。  
  arr.push( (function(n){  
    // 将匿名函数作为返回值返回到外面，当作 push() 方法的参数。  
    return function(){  
      // 调用匿名函数时，输出 n 中保存的值。  
      console.log(n);  
    }  
  // 将每次循环的 i 值作为参数输入函数中，赋值给形参 n;  
  })(i) )  
}  
​  
​  
arr[0](); // 0  
arr[1](); // 1  
arr[2](); // 2  
arr[3](); // 3  
arr[4](); // 4  
​  
</script>  
​  
</body>  
</html>
```

## 对象

对象是带有名称的数据集合。

**创建方式：** 字面量 和 构造函数 两种方式

字面量方式： {}

构造函数方式： new Object()

**说明：**

1，对象的各项之间使用逗号分隔。

2，对象中的每一个值对应个名称，称为属性名称，值称为属性值。

3，每个属性值都可以是单独的任意数据类型。

4，对象属于引用类型，将对象赋值给变量，是将对象的引用地址赋值给变量。

5，对象的 typeof 值为 object。
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
// 字面量方式创建对象  
// 创建空对象  
// var obj = {};  
​  
// 创建一个包含两个属性的对象  
var obj = {name: '小明', age: 18};  
​  
// 查看对象  
console.log(obj);  
​  
// 查看对象的数据类型  
console.log(typeof obj);  
</script>  
</body>  
</html>
```

#### 对象的访问与删除

对象通过 . 和 [] 两种方式访问和修改。

**语法：**

点语法： 对象.属性名

[] 语法： 对象\["属性名"]

**说明：**

1，点语法方式后面必须是属性名，不能使用变量表示属性名。

2，[]语法里面的属性名必须使用引号，不使用引号将作为变量解析。

3，访问对象中没有的属性名，不会报错，返回 undefined.

4，给对象中不存在的属性名赋值，会给对象添加新的数据。

5，当对象的值为一个函数时，这个函数称为对象的方法。

**删除指定数据：** delete 对象.属性名 或 delete 对象\["属性名"];

**对象遍历：** 对象没有 length 属性，需要使用 for..in 循环进行遍历。
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
  var obj = {  
    a: 123,  
    b: "abc",  
    c: true,  
    d: function() {  
      console.log('hello');  
    }  
  };  
​  
  // 通过 点语法 访问属性  
  // console.log(obj.a);  
​  
  // 通过 []语法 访问属性  
  // console.log(obj['b']);  
  // []语法 访问属性时，属性名称如果没有加引号，会被解析为变量  
  // console.log(obj[b]); // 因为没有声明过变量 b ，这里会报错。  
​  
  // 通过 点语法 修改指定属性的值  
  // obj.a = 456;  
​  
  // 通过 []语法 修改指定属性的值  
  // obj['c'] = false;  
​  
  // 如果属性的值是一个函数，那么这个属性被称为这个对象的方法  
  // 方法可以通过小括号调用  
  // obj.d();  
  // obj['d']();  
​  
  // 访问一个不存在的属性，会返回 undefined.  
  // console.log(obj.n);  
​  
  // 给对象添加新的属性和值  
  // obj.m = '哈哈';  
  // console.log(obj);  
​  
  // 删除指定的属性和值  
  // delete obj.a;  
  // console.log(obj);  
​  
​  
  // 遍历  
  // 对象没有 length 属性，无法使用 for 循环遍历  
  // 对象使用 for..in 循环遍历  
  // for (var i in obj) {  
  //   // for ..in 循环会自动按顺序遍历对象的每一个属性  
  //   console.log(i, obj[i]);  
  // }  
​  
</script>  
​  
</body>  
</html>
```

#### 类数组对象

类数组对象是指像数组一样具有 下标 和 length 属性的对象。

类数组不是数组，不能使用数组方法。

类数组对象无法通过修改length属性来修改对象中的数据总数。

函数中的 arguments 对象就是内置的类数组对象。

修改 arguments 的length，不会删除或增加arguments里面保存的数据。

**案例：**

利用 arguments 实现函数重载（）。

sum() 函数:

1个参数：乘方

2个参数： 求和

3个参数：自定义运算

**自定义类数组对象：**

通过模拟数组的特征，可以实现自定义的类数组对象。
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
/*   
  类数组特征：  
    1，本身是对象  
    2，像数组一样，有length属性，表示保存的数据的数量。  
    3，可以通过下标的方式访问每一条数据  
  与数组的区别：  
    1，类数组不是数组，不能使用数组的方法。  
    2，修改类数组的length，不会影响类数组中保存的数据。  
*/  
​  
// arguments 对象  
// function fn1() {  
  // arguments 是一个类数组对象  
  // console.log(arguments.length);  
  // console.log(arguments[0]);  
​  
  // arguments.length = 2;  
  // 修改 arguments 的 length, 里面的数据不会变化  
  // console.log(arguments);  
​  
// }  
​  
// fn1(1,2,3,4);  
​  
// 利用 arguments 实现函数重载  
// 函数重载： 传递的参数数量不同，函数功能也不同。  
function sum(a, b, c) {  
  var length = arguments.length;  
  if (length === 1) {  
    return a * a;  
  }  
​  
  if (length === 2) {  
    return a + b;  
  }  
​  
  if (length === 3) {  
    switch (c) {  
      case "+":  
        return a + b;  
        break;  
      case "-":  
        return a - b;  
        break;  
      case "*":  
        return a * b;  
        break;  
      case "/":  
        return a / b;  
        break;  
      case "%":  
        return a % b;  
        break;  
    }  
  }  
}  
​  
// 自定义类数组  
// 通过模拟数组的特征，可以创建自定义的类数组对象  
var obj2 = {  
  // 对象的属性名称也可以是数字，但需要使用引号包含。  
  // 数字必须像数组的下标一样，是从0开始的有序数字  
  "0": 123,  
  "1": 456,  
  "2": 'abc',  
  "3": true,  
  // 通过 length 属性指定数据的总数  
  length: 4  
}  
​  
// 类数组对象可以像数组对象一样使用 for 循环  
for (var i=0; i<obj2.length; i++) {  
  console.log(i, obj2[i]);  
}  
</script>  
​  
</body>  
</html>
```

## JSON

JSON(JavaScript Object Notation, JS 对象表示法)

是轻量级的文本数据交换格式，是具有特定格式的字符串。

JSON 作用是方便进行前后端数据交互。

**结构：**

'{"属性名1 " ： "属性值1 " ， "属性名2 " ： "属性值2 "}'

**说明：**

1，JSON格式与对象类似，但本质上是一个字符串值。

2，JSON数据的所有属性名称必须使用双引号包裹，字符串值也必须使用双引号包裹

3，JSON格式文件一般是由后端返回，或者前端通过 ajax 请求获取。

#### 数组、对象转换成JSON字符串

JSON.stringify(obj) 将数组或对象转换成标准JSON字符串。

**参数** obj 表示要转换的对象或数组。

JSON.stringify() 应该只用来转换标准的数组或对象，但实际可以转换所有JS中支持的数据类型。

**所有数据类型在转换时的规则如下 ：**

1， null, NaN, 正负Infinity 值会转换成 "null"

2，单独的 函数，symbol值 和 undefined 会转换成 "undefined"

3，布尔值，数字，字符串按类型转换规则转换成字符串。

4，对象转换成字符串之后，数据的顺序是不固定的。

5，函数，undefined，symbol值 在对象中时转换后被忽略，在数组中时转换为 "null"
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
  var obj = {name: "小明", age: 18};  
​  
  // 将数组转换成JSON字符串  
  // console.log( JSON.stringify(arr) );  
​  
  // 将对象转换成JSON字符串  
  // console.log( JSON.stringify(obj) );  
​  
  // 普通值转换成JSON字符串： 除了数组 和 对象，其它类型的值，转换之后就是一个普通字符串。  
  // JSON.stringify() 一般用来将数组或对象转成json字符串，其他类型数据转成字符串没有实际意义。  
  // console.log( JSON.stringify(1) );  
  // console.log( JSON.stringify(true) );  
​  
  // null, NaN, 正负Infinity 值会转换成 "null"  
  console.log( JSON.stringify( [null, NaN, +Infinity, -Infinity] ) ); // '[null,null,null,null]'  
  console.log( JSON.stringify( {  
    a: null, b: NaN, c: +Infinity, d: -Infinity  
  } ) ); // '{"a":null,"b":null,"c":null,"d":null}'  
​  
  // 单独的 函数，symbol值 和 undefined 会转换成 "undefined"  
  // symbol 是 ES6 新增的数据类型，后面课程再介绍  
  console.log( JSON.stringify(function() {}) ); // "undefined"  
  console.log( JSON.stringify(undefined) ); // "undefined"  
​  
  // 数组转换成字符串，数据的顺序跟之前的数组一致  
  console.log( JSON.stringify([1,2,3,4]) ); // '[1,2,3,4]'  
​  
  // 对象转成字符串， 数据的顺序是不固定的，与原来的可能不一样  
  console.log( JSON.stringify( {a: 123, "0": 'abc', "1": true} ) ); // '{"0":"abc","1":true,"a":123}'  
​  
  // 函数，undefined，symbol值 在对象中时转换后被忽略    
  var obj2 = {  
    a: 123,  
    b: "abc",  
    c: function() {},  
    d: undefined,  
    e: true  
  };  
  console.log( JSON.stringify(obj2) ); // '{"a":123,"b":"abc","e":true}'  
​  
  // 函数，undefined，symbol值 在数组中时转换为 "null"   
  var arr2 = [10, function(){ console.log(111)}, undefined, 'hello'];  
  console.log( JSON.stringify(arr2) ); // '[10,null,null,"hello"]'  
​  
</script>  
​  
</body>  
</html>
```


#### JSON字符串转换成数组或对象

JSON.parse(string) 将一个JSON字符串转换成对象或数组。

转换结果是对象还是数组，取决于字符串的格式。

**注意：**

1，JSON字符串的外层使用单引号，里面的属性名称和属性值使用双引号。

2，对象格式的属性名称必须有双引号。

3，对象或数组格式的最后一个值后面不允许有逗号。

4，非对象或数组格式的字符串值无法转换成对象或数组，甚至可能会直接报错。
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
  var json = '{"a": 123, "b": "abc"}';  
  var arr = '[1,20,"abc", true, "false"]';  
​  
  // 如果字符串是对象格式，会被转换成对象  
  // console.log( JSON.parse(json) ); // {a: 123, b: 'abc'}  
​  
  // 如果字符串是数组格式，会被转换成数组  
  // console.log( JSON.parse(arr) ); // [1, 20, 'abc', true, 'false']  
​  
  // 这样写会报错，因为JSON格式字符串要求对象的属性名称必须使用双引号  
  // console.log( JSON.parse( '{a: 123, b: true}') );  
​  
  // 这样也会报错，因为JSON格式字符串中，数组或对象的最后一项后面不允许有逗号  
  // console.log( JSON.parse( '{"a": 123, "b": 100,}' ) );  
  // console.log( JSON.parse( '[1,2,3,4,]' ) );  
​  
  // 数字使用 JSON.parse() 返回的还是123  
  // console.log( JSON.parse(123) );  
​  
  // 会报错，无法正常转换  
  // console.log( JSON.parse( undefined ) );  
​  
  // 数组或对象字符串中的值不允许为函数，会报错  
  // console.log( JSON.parse( '[1,2,function(){}, 10,20]' ) );   
  // console.log( JSON.parse( '{"a": 100, "b":"hello", "f": function(){}}' ) );   
​  
​  
  // 为了避免出错，JSON.parse() 方法应该只用来将对象或数组格式的字符串。  
</script>  
</body>  
</html>
```


## this 关键字

this 是 JavaScript 中的一个特殊的内置对象。

在浏览器端，全局作用域中的 this 指向 window 对象。

函数中的 this 值并不是固定的，当函数被调用时才会确定 this 的值。

调用方式不同，this 指向的值也不同。

this 通常在函数内部使用

**通常情况下：**

1， 当函数是通过使用 () 直接调用时， this 指向 window 对象。

2，IIFE 函数中的 this 指向 window 对象。

3，当函数属于某个对象的方法时，this 指向这个对象。
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
// 全局作用域中的 this 指向 window 对象  
// window 是浏览器中内置的对象，属于 BOM。  
// console.log( this );  
​  
// this 通常在函数内部使用  
function fn1() {  
  // 函数中的this 指向谁，要看函数是通过什么方式调用的  
  // 也就是说，函数中的this的值是在函数调用的时候确定的  
  console.log(this);  
}  
​  
// 直接加 () 调用，this 指向 window 对象  
// fn1();  
// 通过定时器调用，this 指向 window 对象  
// setTimeout(fn1, 1000);  
// 通过触发事件调用， this 指向触发事件的对象 （这里指向document对象）  
// 事件是后续课程中的内容  
// document.onclick = fn1;  
// var obj = {  
//   name: "小明",  
//   age: 18,  
//   say: fn1  
// };  
// 如果函数属于对象的方法， this 指向这个对象  
// obj.say();  
​  
// IIFE 函数中的 this 也指向 window 对象  
// (function() {  
//   console.log(this);  
// })()  
​  
​  
// this 使用场景  
​  
var person = {  
  name: "小明",  
  age:18,  
  say: function() {  
    // 直接使用对象的变量名称  
    // console.log(person.name + ', ' + person.age);  
    // 使用 this 对象  
    console.log(this.name + ', ' + this.age);  
  }  
}  
person.say();  
​  
var p1 = person;  
// person 指向对象时，可以正常执行 say 方法。  
p1.say();  
// 修改 person 的值， person 不再存的是对象，而是字符串。  
person = "小明";  
// 再使用 say() 方法，如果是通过对象获取属性值，将获取不到正确的值。  
// 如果通过 this 对象获取属性值，不受影响。   
p1.say();  
​  
</script>  
</body>  
</html>
```

