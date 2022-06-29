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

## 字符串方法

#### 字符串的下标和length

字符串也可以像数组一样，通过下标来获取指定位置上的字符，通过 length 获取字符串长度。

**与数组不同的是：**

1，字符串只能通过下标来获取值，不能修改值。

2，字符串的 length 属性是只读的，无法被修改。

3，低版本 IE 浏览器中（IE8以下），不支持通过下标方式获取。

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

var str = 'abcdefg';

console.log(str);
// 查看length属性的值
console.log(str.length);

// 字符串的length属性是只读的，只能获取，无法被修改
str.length = 2;
console.log(str.length);

// 字符串也可以通过下标的方式获取指定字符 （IE8以下不支持）
// console.log(str[0]);

// 字符串无法通过下标修改指定位置上的字符
str[0] = 1; // 赋值不会生效
console.log(str);

</script>
</body>
</html>
```


#### 位置获取类方法

**所有字符串方法都会产生新的字符串，并不修改原来的字符串。**

**charAt(index)**

获取字符串中指定位置上的字符 （与下标方式获取效果相同）

**参数：** 指定要获取字符的位置，不指定默认为0

**返回值：** 获取到的字符

**charCodeAt(index)**

获取字符串中指定位置上字符在unicode字符集中的编号（unicode编码）

**参数：** 指定要获取编码的字符位置，不指定默认为0

**返回值：** 指定字符的编码

**indexOf(str, index)**

按从左往右的顺序，查找字符串中指定子字符串第一次出现的位置。

**参数：** 1， 指定要查找的子字符串 2， 开始查找的位置

**返回值：** 如果字符串中有指定的子字符串，返回第一次出现的位置，没有返回 -1。

**lastIndexOf(str, index)**

按从右往左的顺序，查找字符串中指定子字符串第一次出现的位置。

**参数：** 1， 指定要查找的子字符串 2， 开始查找的位置

**返回值：** 如果字符串中有指定的子字符串，返回第一次出现的位置，没有返回 -1。

**静态方法：**

**String. fromCharCode(num1, num2, …, numN)**

根据字符编码，返回对应的字符。

**参数：** 任意多个 指定要返回字符的字符编码

**返回值：** 跟编码对应的字符。

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

var str = 'abcdefgfgdeasbcew';

// charAt() 方法
// 获取指定位置的字符
// console.log( str.charAt(2) );
// 负数和超出字符范围的参数，返回空字符串
// console.log( str.charAt(-2) );
// console.log( str.charAt(10) );
// 不指定参数，默认获取第 0 位置的字符（即字符串开头的字符）
// console.log( str.charAt() );

// charCodeAt() 方法
// 获取指定位置字符的字符编码
// console.log( str.charCodeAt(3) )
// 负数 和 超出范围的参数  返回 NaN
// console.log( str.charCodeAt(-3) )
// console.log( str.charCodeAt(10) )
// 不指定参数，默认返回第0位置上的字符的字符编码
// console.log( str.charCodeAt() )

// indexOf() 方法   从左往右查找字符
// 查找指定字符，如果找到了，返回这个字符在字符串中第一次出现的位置
// console.log( str.indexOf('d') );
// 如果字符串中没有要查找的字符，返回 -1
// console.log( str.indexOf('z') );
// 查找多个字符的子字符串时，如果有，返回的是子字符第一个字符第一次出现的位置
// console.log( str.indexOf('cde') );
// 默认从第0位置开始查找，可以传递第二个参数，指定开始查找的位置
// console.log( str.indexOf('a', 2) );
// 第二个参数为负数时自动重置为 0
// console.log( str.indexOf('a', -10) );
// 第二个参数超出字符范围，返回 -1
// console.log( str.indexOf('a', 20) );

// lastIndexOf();    从右往左查找字符
// 返回从右往左查找的第一次出现的位置
// console.log( str.lastIndexOf('a') );
// 第二个参数， 指定开始查找的位置
// console.log( str.lastIndexOf('a', 10) );

// 静态方法   String.fromCharCode();
// 固定写法，  fromCharCode() 点的前面只能是 String。
// 参数个数是任意多个， 参数表示的是字符编码
console.log(String.fromCharCode(48)); // 返回字符串数字 0
console.log(String.fromCharCode(65, 66, 67)); // 'ABC'
// 所有被 unicode 支持的字符都有一个对应的字符编码
// unicode 是世界通用字符集，包含各国文字
console.log(String.fromCharCode(47088,47051,47123)); // '런럋렓'
console.log(String.fromCharCode(12345,12387,12389,12367,12354)); // '〹っづくあ'
console.log(String.fromCharCode(23456,24356,26435,26871)); // '宠弤权棷'

</script>
</body>
</html>
```


#### 分割、合并及转换类方法

所有字符串方法都会产生新的字符串，并不修改原来的字符串。

**toUpperCase()**

将字符串全部转换为大写。

**toLowerCase()**

将字符串全部转换为小写。

**concat()**

将多个字符串合并为一个字符串 （与 + 功能相同）

**参数：** 要合并的值，可以是任意数据类型

非字符串类型的值会被转换为字符串类型的值。

**split()**

将字符串以分割符为依据分割为数组。

**参数：** 指定要作为分割依据的字符串 返回值： 保存分割之后的字符串的数组。

1，不指定分割符，默认不分割，将整个字符串作为一个值存入数组。

2，分割符必须是 字符串 中有的子字符串，否则为非法，以不指定分割符处理。

3，作为分割符的字符串不会作为值存入数组。

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

// var str = 'abcdefg';

// 全部转换成大写   没有参数，不能单独转换其中某一个字符
// console.log(str.toUpperCase());

// 全部转换成小写   没有参数，不能单独转换其中某一个字符
// console.log('ABCD'.toLowerCase());

// concat() 方法
// var str1 = '1234';
// var str2 = 'abcd';
// 将多个字符串拼接成一个字符串
// console.log(str1.concat(str2));
// 用法与数组的concat()方法类似，参数顺序决定了字符串拼接之后的顺序
// console.log(str2.concat(str1));
// 可以接收任意多个参数，非字符串类型的值会转换成字符串值
// console.log(str1.concat(str2, 'hello', true, null, undefined));
// 实际工作中，字符串拼接通常使用 + 
// console.log(str1 + str2);
// console.log(str2 + str1);

// split() 方法
var str = 'abcdefg';

// 以字符'c'为分割符， 将字符串分割成数组。
// 作为分割符的字符本身不会存入数组中
// console.log(str.split('c'));
// 不指定参数，表示没有分割符，字符串不会被分割，直接存入数组中
// console.log(str.split());
// 作为分割符的字符必须是字符串中能够找到的字符，否则为非法分割符，相当于没有指定参数。
// console.log(str.split('z'));
// 以空字符串作为分割符，会将字符串的每一个字符单独都拆开。
// console.log(str.split(''));
// 以字符串本身作为分割符，会返回一个有两个空字符串的数组（分别是字符串开头位置左边和结束位置右边的空字符串）
// console.log(str.split(str));

</script>
</body>
</html>
```

## 正则表达式

全称 regular expression ， 简写 RegExp ， 中文简称 正则

**定义：** 正则是一个字符串工具 用于匹配字符串中特定字符组合的子字符串，常用于表单验证。

如： 验证用户名是否合法、手机号是否正确等

创建方式：

字面量方式： /正则规则/修饰符

构造函数方式： new RegExp("正则规则", "修饰符");

特点：

1，正则的数据类型为复杂类型。

2，正则的 typeof 值为 object。

#### 正则对象属性

所有正则对象都默认自带以下属性：

| 属性名称   | 含义                            |
| ---------- | ------------------------------- |
| lastIndex  | 下一次匹配开始的位置，默认值为0 |
| ignoreCase | 是否使用了 i 修饰符（布尔值）   |
| global     | 是否使用了 g 修饰符（布尔值）   |
| multiline  | 是否使用了 m 修饰符 （布尔值）  |
| source     | 正则表达式内容                  |


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
// 创建一个正则表达式对象
var re = /a/;

// 正则表达式 也是复杂数据类型（引用类型） typeof 值为 object
// console.log(typeof re);

// 正则的属性
// lastIndex  正则匹配的开始位置，默认为0
// console.log( re.lastIndex );
// 是否设置了 i 修饰符，  已设置为 true, 未设置 为 false  默认 false
// console.log( re.ignoreCase );
// 是否设置了 g 修饰符，  已设置为 true, 未设置 为 false  默认 false
// console.log( re.global );
// 是否设置了 m 修饰符，  已设置为 true, 未设置 为 false  默认 false
// console.log( re.multiline );
// 返回正则内容 （即 / /  中间的内容）
// console.log( re.source );
</script>
</body>
</html>
```

## 正则方法

**exec(str)**

匹配字符串中是否有符合的子字符串。

**参数：** str 指定要进行正则匹配的字符串。

**返回值：** 如果匹配成功，返回数组，并更新 lastIndex 属性的值；

如果匹配失败，返回 null，并将 lastIndex 属性的值重置为0。

**匹配成功的数组内容：**

1，数组的第0个值为匹配到的字符串

2，从第1个值开始后面所有的值都表示对应捕获分组的值

3，index 属性： 匹配到的字符串在整个字符串中从lastIndex往后第一次出现的位置

4，input 属性： 进行正则匹配的字符串

**test(str)**

测试字符串中是否有符合匹配规则的子字符串。

**参数：** str 指定要进行正则匹配的字符串。

**返回值：** 如果有符合匹配规则的子字符串，返回 true; 如果没有，返回 false。

**注意：** exec() 和 test() 方法的结果受 g 修饰符影响，如果指定了 g 修饰符，每次匹配之后都会更新 lastIndex 的值为当前匹配到的位置加上匹配到的字符串的length；如果不指定 g 修饰符， lastIndex 值始终为 0。

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

var str = 'abcdefgabcdefgabcdefg';
var re = /abc/; // 匹配字符串 'abc'

// 正则方法
// exec()  类似于字符串的indexOf()方法，用来查找字符串中有没有符合正则表达式
/* 内容的子字符串
  如果匹配成功，返回值为数组   数组包含一个保存匹配的值，和三个特殊属性。
    数组的值为成功匹配的结果
    三个特殊属性分别为：
      index  匹配结果在字符串中第一次出现的位置
      input  用来进行正则匹配的字符串
      groups  正则的所有命名分组，当正则没有命名分组时，该属性的值为 undefined；当正则有命名分组时，该属性的值为包含所有命名分组的数组。（命名分组非常不常用）
  如果匹配不成功，返回值为 null。 
*/
// console.log(re.exec(str));


// test()   检测字符串中有没有符合正则表达式内容的子字符串
// 如果有， 返回 true    如果没有  返回 false

// 查找字符串 str 中是否有子字符串 'abc'
// console.log( /abc/.test(str)); 
// 查找字符串 'abcdefg1234567' 中是否有子字符串 '89'
// console.log( /89/.test('abcdefg1234567')); 


/* 
  扩展知识：  数组也可以像对象一样添加带有属性名称的值，并且这些值既可以通过 点语法 的方式访问，也可以通过 []语法 的方式访问。但这些属性不在正常的有序数组集合中，无法使用 for 循环遍历这些属性。
*/
// var arr = [1,2,3,4];
// 查看数组中的值
// console.log(arr);
// 给数组添加一个带属性名称为a的值
// arr.a = 'abc';
// 分别通过 点语法 和  []语法 访问新添加的值
// console.log(arr.a);
// console.log(arr['a']);
// for 循环 并不会遍历带有属性名称的值
// for (var i=0; i<arr.length; i++) {
//   console.log(arr[i]);
// }

</script>
</body>
</html>
```

#### 简单匹配

简单匹配 又称精确匹配， 是使用精确的子字符串进行匹配。

简单匹配不够灵活，无法进行不确定字符的匹配，比如匹配任意数字。
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

var str = 'abc123def456ghk789';

// 精确匹配
var re1 = /123/;
// 精确匹配就是匹配与正则表达式中完全一致的子字符串
// 精确匹配不够灵活，不能发挥正则的优势。
// console.log( re1.exec(str) );
// console.log( re1.exec('asd234jlh890vz') );

// 特殊匹配（模糊匹配）
var re2 = /\d+/g;
// 模糊匹配 是根据正则约定的特定规则来匹配符合要求的子字符串，匹配到的字符串不是固定的。
// 比如 \d 是指匹配任意一个数字  \d+  是匹配任意多个数字
// 特殊匹配非常灵活，配合特殊字符可以实现任意字符组合要求的匹配，是常规的正则匹配方式。
// console.log( re2.exec(str) );
// console.log( re2.exec('asd234jlh890vz') );
</script>

</body>
</html>
```


#### 特殊匹配

特殊匹配 又称模糊匹配， 是使用有特定含义的特殊字符进行匹配。

特殊匹配非常灵活，配合特殊字符可以实现任意字符组合要求的匹配，是常规的正则匹配方式。

## 特殊字符

特殊字符是正则中具有特殊含义的字符，用来增强正则表达式的功能。

一个特殊字符匹配一个字符。

**字符 \ :** \ 是一个特殊字符

1， \ 用在有特殊字符前面，表示取消字符的特殊含义，只作为普通字符使用。

2，\ 可以与部分数字或字母组合成特殊字符。

**特殊字符包含：**

1，元字符 `\d \D \w \W \s \S . \t \n \r`

2，字符集合 `[] [^]`

3，捕获分组 `()`

4，非捕获分组`(?=) (?!)`

5，边界字符 `^ $ \b \B`

6，量词 `{n} {n,m} {n,} + * ?`

7，或操作符`|`

#### 元字符

元字符是有特定含义的字符，也称预定义类：
| 元字符 | 含义                                           |
| ------ | ---------------------------------------------- |
| `.``     | 匹配除 换行符(\n) 和 回车符(\r) 之外的所有字符 |
| `\d`    | 匹配 0~9 之间的任意数字                        |
|`\D`   | 匹配除了数字以外的任意字符                     |
|`\w`   | 匹配数字、字母或下划线                         |
|`\W`   | 匹配除了数字、字母或下划线之外的任意字符       |
| `\s`   | 匹配空白字符（空格，回车符，换行符，制表符等） |
|`\S`   | 匹配非空白字符                                 |
| `\t`   | 匹配制表符                                     |
|`\n`  | 匹配换行符                                     |
|`\r`    | 匹配回车符                                     |