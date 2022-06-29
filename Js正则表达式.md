## **数字方法** toFixed()

toFixed() 是一个数字方法，作用是设置保留小数点后面指定长度的小数值（四舍五入） 。

**参数：** 指定保留的小数位数

返回值为字符串类型

**用法：**

数字.toFixed(length)

**规则：**

1，只能用在typeof 类型为 number 的字面量或变量值中。

2，数字字面量需要使用 () 包裹

3，不指定参数，则以四舍五入的方式去除小数，保留整数。

4，NaN.toFixed(length) 无论 length 值是多少，都会得到 "NaN"

5，正负 Infinity 值使用 toFixed() 方法得到对应的 'Infinity' 或 '-Infinity'。

6，标准规范中 length 的有效范围为 0~20，但主流浏览器中的范围基本都是 0~100。
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

// toFixed()
var num1 = 123.55678;

// 保留小数点后面两位，会进行四舍五入
// console.log(num1.toFixed(2));

// 如果不指定参数，则以四舍五入的方式去除小数，保留整数。
console.log(num1.toFixed());

// 数字字面量必须使用小括号，因为不加小括号，JS无法区分小点是小数点中的还是方法的。
// console.log((12.3456).toFixed(2))

// 如果设置的保留长度大于数字本身的小数位数，不足的自动补零
// console.log( (12.34).toFixed(4) ) // '12.3400'
// console.log( (12).toFixed(2) ) // '12.00'

// NaN 没有小数，只会返回字符串 'NaN'
console.log( NaN.toFixed() ); // 'NaN'
console.log( NaN.toFixed(4) ); // 'NaN'

// 正负 Infinity 也没有小数，返回 'Infinity' 或 '-Infinity'
console.log( (+Infinity).toFixed(4) ); // 'Infinity'
console.log( (-Infinity).toFixed(4) ); // '-Infinity'

// 负数 或 大于 100 的参数会抛出错误 （标准中的参数最大值为20, 浏览器支持的最大值为100）
// console.log( (123).toFixed(-1) );
// console.log( (123).toFixed(101) );

// 参数的小数部分会直接忽略
// console.log( (123).toFixed(0.5) );
// console.log( (123).toFixed(2.5) );

</script>
</body>
</html>
```