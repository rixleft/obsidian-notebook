## 数字方法 toFixed()

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

#### 范围获取类方法
所有字符串方法都会产生新的字符串，并不修改原来的字符串。

**slice(start, end)**

从字符串中获取指定范围的子字符串。

**参数：** start 开始位置 end 结束位置

**返回值：** 获取到的子字符串

1，start 值必须小于 end （start位置在end之前），否则返回空字符串

2，获取范围包括开始位置的字符，不包括结束位置的字符。

3，start, end 可以为负数，表示从后往前数位置（但必须保证start位置在end之前）

4，省略 end 表示从start开始提取后面所有字符，start,end 都省略会复制所有字符。

**substring(start, end)**

功能与 slice() 方法相同

**参数：** start 开始位置 end 结束位置

**返回值：** 获取到的子字符串

1，如果 start > end ，会交换两个参数位置再获取。

2，获取范围包括开始位置，不包括结束位置。

3，start, end 都必须 >=0 , 负数会自动转换为0。

4，省略 end 表示从start开始提取后面所有字符，start,end 都省略会复制所有字符。

**substr(start, length)**

从字符串中获取指定长度的子字符串。（非标准方法，不建议使用）

**参数：** start 表示开始获取位置 length 表示获取字符长度

**返回值：** 获取到的子字符串

1，第一个参数可以为负数，表示从后往前数位置

2，第二个参数表示要提取的字符个数，值为正整数，负数和0时，提取不到字符，返回空字符串.

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

  // var str = '北京前端开发有限公司';

  // 字符串的所有方法都不会修改原字符串的内容

  // slice()  从字符串中提取指定范围的子字符串
  // console.log( str.slice(2, 6) );
  // 开始位置必须小于结束位置
  // console.log( str.slice(6, 2) );
  // 只设置一个参数：  从参数指定的位置开始，提取后面所有的字符
  // console.log( str.slice(2) );
  // 不设置参数， 复制整个字符串
  // console.log( str.slice() );
  // 可以接收负数参数，表示从后往前数位置
  // console.log( str.slice(-8,-4) );
  // console.log( str.slice(-4) );

  // console.log(str);

  // substring(start, end)   与 slice() 方法功能相同
  // console.log( str.substring(2, 6) );
  // console.log( str.substring(2) );
  // console.log( str.substring() );
  // 与 slice() 方法的不同之处  1，不接收负数参数    2，提取前会比较两个参数的大小
  // 不接收负数参数，所有的负数参数自动转换成0
  // console.log( str.substring(-2, -6) );
  // console.log( str.substring(2, -6) ); // 实际提取的是 0~ 2 的字符
  // 在提取字符之前，会先比较两个参数的大小，如果第二个参数比第一个参数小，会先交换两个参数的位置，再提取
  // console.log( str.substring(6, 2) );

  var str = '北京前端开发有限公司';
  // substr(start, length)    不是标准方法，不推荐使用。
  // 注意 第一个参数表示位置，第二个参数表示要提取的字符个数。
  // console.log( str.substr(2, 4) );
  // console.log( str.substr(-8, 4) );

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
| `.`    | 匹配除 换行符(\n) 和 回车符(\r) 之外的所有字符 |
| `\d`   | 匹配 0~9 之间的任意数字                        |
| `\D`   | 匹配除了数字以外的任意字符                     |
| `\w`   | 匹配数字、字母或下划线                         |
| `\W`   | 匹配除了数字、字母或下划线之外的任意字符       |
| `\s`   | 匹配空白字符（空格，回车符，换行符，制表符等） |
| `\S`   | 匹配非空白字符                                 |
| `\t`   | 匹配制表符                                     |
| `\n`   | 匹配换行符                                     |
| `\r`   | 匹配回车符                                     |


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
  var str = 'abc123def456ghi789kl';
  var re = /./;

  // 元字符
  // .  匹配除换行(\n)和回车(\r) 之外的任意字符
  // console.log(/./.exec('abc')); // 'a'
  // console.log(/./.exec('#@!')); // '#'
  // console.log(/./.exec('()^')); // '('
  // console.log(/./.exec('\r')); // null
  // console.log(/./.exec('\n')); // null
  // console.log(/./.exec('\t')); // '\t'

  // \d   匹配数字 0~9
  // console.log(/\d/.exec('ab12')); // '1'
  // console.log(/\d/.exec('424')); // '4'

  // \D   匹配除数字 0~9 之外的其他任意字符
  // console.log(/\D/.exec('ab12')); // 'a'
  // console.log(/\D/.exec('424')); // null
  // console.log(/\D/.exec('@#!')); // '@'
  // console.log(/\D/.exec('\r')); // '\r'
  // console.log(/\D/.exec('\n')); // '\n'
  // console.log(/\D/.exec('\t')); // '\t'

  // \w   匹配数字、字母或下划线
  // console.log(/\w/.exec('abc123')); // 'a'
  // console.log(/\w/.exec('123')); // '1'
  // console.log(/\w/.exec('#!_42%')); // '_'
  // console.log(/\w/.exec('!@#-=')); // null

  // \W   匹配数字、字母或下划线之外的其他字符
  // console.log(/\W/.exec('abc123')); // null
  // console.log(/\W/.exec('123')); // null
  // console.log(/\W/.exec('#!_42%')); // '#'
  // console.log(/\W/.exec('!@#-=')); // '!'

  // \s   匹配空白字符  空格 制表符  换行符   回车符 等都是空白字符
  // console.log(/\s/.exec('af 1214')); // ' '
  // console.log(/\s/.exec('af\t1214')); // '\t'
  // console.log(/\s/.exec('af\r1214')); // '\r'
  // console.log(/\s/.exec('af\n1214')); // '\n'

   // \S   匹配除空白字符之外的任意字符
  var re = /\S/;
  console.log(re.exec(' a1214')); // 'a'
  console.log(re.exec('\tb1214')); // 'b'
  console.log(re.exec('\rc1214')); // 'c'
  console.log(re.exec('\nd1214')); // 'd'

  // \t   匹配制表符
  // \r   匹配回车符
    // 回车符：  回车符最早是用于打字机中的换行控制符号，现在用在一些特定的文件中用于换行
  // \n   匹配换行符
</script>
</body>
</html>
```

#### 修饰符

修饰符正则表达式的配置参数，是对正则规则的补充。

**语法：** 正则规则修饰符

| 修饰符 | 含义                                            |
| ------ | ----------------------------------------------- |
| g      | global 全局匹配， 匹配所有符合正则规则的字符串  |
| i      | ignoreCase 忽略大小写                           |
| m      | multiple 多行匹配，需要配合边界符号 ^ 或 $ 使用 |

**注意：** 修饰符必须使用小写，不能使用大写。

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
var str = 'abc123ABC4gHk';

// 修饰符
// g   全局修饰符    匹配所有符合要求的结果
// 匹配任意一个数字
var re1 = /\d/;
var re2 = /\d/g;

// exec() 方法 使用 g 和 不使用 g 修饰符的区别
// 不使用 g 修饰符，lastIndex 默认值为0，exec() 方法始终从0往查找第一个匹配的结果
// console.log(re1.exec(str)); // '1'   lastIndex 为 0
// console.log(re1.exec(str)); // '1'   lastIndex 为 0
// console.log(re1.exec(str)); // '1'   lastIndex 为 0
// console.log(re1.exec(str)); // '1'   lastIndex 为 0
// 使用 g 修饰符， lastIndex 默认值为0，每调用一次exec() ，都会将 lastIndex 重置为当前匹配的结果出现的位置值， 下一次调用 exec() 方法时，将从新的 lastIndex 位置开始往后匹配

// console.log(re2.exec(str)); // '1'  从0开始往后匹配  1 出现在3位置   lastIndex 被重置为 3
// console.log(re2.exec(str)); // '2'  从3开始往后匹配  2 出现在4位置   lastIndex 被重置为 4
// console.log(re2.exec(str)); // '3'  从4开始往后匹配  3 出现在5位置   lastIndex 被重置为 5
// console.log(re2.exec(str)); // '4'  从5开始往后匹配  4 出现在9位置   lastIndex 被重置为 9
// console.log(re2.exec(str)); // null  从9开始往后匹配，匹配不到数字了 lastIndex 被重置为 0
// console.log(re2.exec(str)); // '1'  从0开始往后匹配  1 出现在3位置   lastIndex 被重置为 3
//  ... 继续调用，会一直重复 1 2 3 4 null 1 2 3 4 null 1 2 ...

// test() 方法 使用g和不使用g 与 exec() 方法规则相同
// 不使用 g ， lastIndex 始终为0 重复调用不会更新 lastIndex
// console.log(re1.test(str));
// console.log(re1.test(str));
// console.log(re1.test(str));
// console.log(re1.test(str));
// 使用 g ， 每次调用 test() 都会更新 lastIndex 的值，循环重复
// console.log(re2.test(str)); // true 匹配到的是 1 的位置
// console.log(re2.test(str)); // true 匹配到的是 2 的位置
// console.log(re2.test(str)); // true 匹配到的是 3 的位置
// console.log(re2.test(str)); // true 匹配到的是 4 的位置
// console.log(re2.test(str)); // false 没有匹配到数字，lastIndex被重置为 0
// console.log(re2.test(str)); // true 从0开始重新匹配
//  ... 继续调用，会一直重复 true true true true false true true true true false ...


// i 忽略大小写
// 匹配字母a
var re3 = /A/;
var re4 = /A/i;

// 不使用 i 修饰符  匹配结果必须与正则表达式的大小写一致
// console.log(re3.exec(str)); // 'A'

// 使用 i 修饰符  匹配时忽略大小写
// console.log(re4.exec(str)); // 'a'


var str2 = 'abc123\nDEF456';
// \n 为换行符  str2 为两行文本
// console.log(str2);

// m 多行匹配
// 匹配开头位置的字母D
var re5 = /^D/;
var re6 = /D/m;
// 不使用m , 会将整个字符串都作为一行文本处理（忽略换行符）
console.log(re5.exec(str2)); // null
// 使用 m ， 每一个换行符表示一个新的行
console.log(re6.exec(str2)); // 'D'


// 修饰符只能是小写， 大写会抛出错误
// console.log(/\d/G.test(str));
</script>
</body>
</html>
```

## 支持正则的字符串方法

**split()**

使用与正则匹配的子字符串作为分割符。

**match()**

查找与正则匹配的子字符串，如果查找成功，返回包含匹配结果的数组；查找失败返回 null;

**参数：** 字符串或正则表达式

成功匹配的结果受 g 修饰符影响：

1，如果没有指定 g 修饰符， 数组的第0个值为第一次成功匹配的结果，从第1个值开始后面的值均为捕获分组；同时有三个额外属性（与不带g修饰符的正则方法 exec() 的结果相同）：

index: 匹配结果在字符串中第一次出现的位置

input: 进行正则匹配的字符串

groups: 如果有命名捕获组，值为包含所有命名捕获组的对象；如果没有命名捕获组，值为 undefined.

2，如果指定了 g 修饰符，数组包含所有匹配到的结果，没有其他额外信息。

**search()**

查找字符串与正则匹配的子字符串.

1，如果成功，返回匹配结果第一次出现的位置，如果失败返回 -1.

2，不支持 g 修饰符。

**replace()**

将匹配结果替换为指定的子字符串。

**参数：** 两个

**第一个参数:** 指定匹配字符串的正则 或 要替换的子字符串

**第二个参数:** 用来替换的值

**说明：**

1，当第一个参数为字符串时，只会替换第一个符合的子字符串。

2，当第一个参数为正则时，不指定g只替换一次，指定g则替换所有匹配结果。

3，第二个参数可以是一个字符串值，也可以是一个有返回值的函数。

当第一个参数为正则，并且第二个参数为字符串时，第二个参数中可以使用以下特殊字符：

```js

$$ 插入一个 $ 字符

$& 插入匹配的结果

$` 插入匹配结果左边部分的内容

$' 插入匹配结果右边部分的内容

$n 插入第n个捕获分组的内容（n为分组序号）

```

当第一个参数为正则，并且第二个参数为函数时，每次调用函数时，会依次传入以下参数：

第一个参数为当前匹配结果，接着是捕获分组结果，然后是匹配结果的索引，然后是被匹配的字符串
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

var str = 'a1b2c3d4e5f6g';

// split()   分割字符串
// 使用普通字符串作为分割符
// console.log( str.split('1') ); // ['a', 'b2c3d4e5f6g']
// 使用正则作为分割符
// console.log( str.split(/\d/) ); // ['a', 'b', 'c', 'd', 'e', 'f', 'g']

// match()  查找匹配的子字符串，匹配成功 返回保存结果的数字，匹配失败 返回 null
// 不使用g修饰符 只会匹配一次，数组保存第一个匹配到的结果，并额外提供  index , input , groups 三个属性
// console.log(str.match(/\d/));
// 使用g修饰符  匹配所有结果，数组保存所有匹配的结果， 没有额外属性
// console.log(str.match(/\d/g));
// 匹配失败，返回 null
// console.log(str.match(/xyz/));

// search()    匹配成功 返回匹配结果第一次出现的位置， 匹配失败 返回 -1
// search() 方法 不支持 g 修饰符
// console.log( str.search(/\d/g) )
// console.log( str.search(/\d/g) )
// console.log( str.search(/x/g) )


var str2 = 'abc123DEF';
// replace()   将匹配结果替换成指定的子字符串
// 将123替换成一二三
// console.log( str2.replace('123', '一二三') );
// 将所有数字都替换成 *
// console.log( str2.replace(/\d/g, '*') );
// 将每个数字都复制一次
// console.log( str2.replace(/\d/g, '$&$&') );
// 用匹配结果左边的内容替换匹配结果 （匹配结果为123，左边的内容为abc）
// console.log( str2.replace(/123/g, '$`') );
// 用匹配结果右边的内容替换匹配结果 （匹配结果为123，右边的内容为DEF）
// console.log( str2.replace(/123/g, "$'") );
console.log( str2.replace(/123/, function(a, b, c, d){
  // 查看 replace 自动传入的参数  正则规则不同，参数含义不同
  console.log(a, b, c, d);
  // 函数返回值为替换内容
  return '哈喽';
}) );
</script>

</body>
</html>
```

## 字符集合

字符集合指定正则表达式的匹配范围，字符集合使用 [] 表示。

**字符集合分类：**

**列表字符集合：**匹配列表中指定的字符中的任意一个字符。

如： `/a[bdf]c/` 表示匹配 abc , adc 或 afc。

**范围字符集合：**匹配指定范围中的字符。

`[0-9]` 匹配任意一个数字 [a-z] 匹配任意一个小写字母

`[A-Z]` 匹配任意一个大写字母 [A-z] 匹配任意大小写字母和 []^_` （注意大小写不能反）

`[\u4e00-\u9fa5]` 匹配任意一个中文字符

**范围组合集合：**范围字符的组合匹配，如：

`[0-9a-z]` 匹配任意数字和小写字母 [0-9A-Z] 匹配任意数字和大写字母

`[a-zA-Z]` 匹配任意大小写字母 [A-z0-9] 匹配任意数字、大小写字母和 []^_`

**反向字符集合：**在上面三种集合里的最前面添加^，表示匹配除指定范围的字符之外的其他任意字符， 如

`[^abc]` 匹配除 abc 之外的任意字符

如： `/a[^bd]c/` 可以匹配 afc ，但不能匹配 abc、adc

**注意：** ^ 符号 必须紧贴` [ `符号右边，才表示反向字符集合。

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

// 列表字符集合
// [bdf]  匹配 b d f 三个字符中的任意一个
// 不论[]集合里有多少个字符，都只会匹配其中的一个字符
// console.log( 'abcadcafcaecagc'.match(/a[bdf]c/g) ); // ['abc', 'adc', 'afc']

// 范围字符集合
// [3-5]  匹配 3~5 之间的任意一个数字
// console.log( '0123456789'.match(/[3-5]/g) ); // ['3', '4', '5']
// [c-g]  匹配 c~g 之间的任意一个字母
// console.log( 'abcdefghijklmn'.match(/[c-g]/g) ); // ['c', 'd', 'e', 'f', 'g']
// [\u4e00-\u9fa5]  匹配任意一个汉字
// console.log( '123你好abc'.match(/[\u4e00-\u9fa5]/g) ); // ['你', '好']

// 范围组合集合
// [0-9a-z] 	匹配任意数字和小写字母  
// [0-9A-Z]   匹配任意数字和大写字母
// [a-zA-Z] 	匹配任意大小写字母  
// [A-z0-9]   匹配任意数字、大小写字母和 [\]^_`

// 反向字符集合   匹配不在列表中的字符
// [^bdf]  匹配除了 b d f 之外的其他字符
console.log( 'abcadcafcaecagc'.match(/a[^bdf]c/g) ); // ['aec', 'agc']
// 匹配除数字之外的其他任意字符
console.log( '1a#@$_-=哈234('.match(/[^0-9]/g) ); // ['a', '#', '@', '$', '_', '-', '=', '哈', '(']

</script>

</body>
</html>
```

## 量词

量词写在匹配字符的右边，表示匹配字符的数量。

| 量词                    | 含义                        |
| ----------------------- | --------------------------- |
| {n}                     | 必须是 n 个                 |
| {n,m}                   | 最少n个，最多m个            |
| {n,}                    | 最少n个，最多不限           |
| +                       | 一个到任意多个，相当于 {1,} |
| *                       | 0个到任意多个，相当于{0,}   |
| ?|0个或1个，相当于 {0,1} |                             |

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
var str = '123abc456def7890';

// 量词： 表示匹配的数量
// 匹配一个任意的两位数 
// console.log( str.match(/\d{2}/g) ); // ['12', '45', '78', '90']
// 匹配任意一个1~3位的数字
// console.log( str.match(/\d{1,3}/g) ); // ['123', '456', '789', '0']
// 匹配一个至少两位到任意多位的数字
// console.log( str.match(/\d{2,}/g) ); // ['123', '456', '7890']
// 匹配任意一个至少一位，最多不限位数的数字，相当于 {1,}
// console.log( str.match(/\d+/g) ); // ['123', '456', '7890']
// 匹配任意一个0到多位的数字，相当于 {0,}
// console.log( str.match(/\d*/g) ); // ['123', '', '', '', '456', '', '', '', '7890', '']
// 匹配一个 字母+一个可选数字（可以有数字，也可以没有数字）的字符串
// console.log( str.match(/[a-z]\d?/g) ); // ['a', 'b', 'c4', 'd', 'e', 'f7']
</script>

</body>
</html>
```


## 边界

边界匹配的是字符串中的一个位置，不表示具体的字符，不占用字符长度。

**`^`** 匹配字符串的开始位置，开始位置指每行字符串的第一个字符左边的位置

**`$`** 匹配字符串的结束位置，结束位置指每行字符串的最后一个字符右边的位置

**`\b`** 匹配单词边界，单词边界指的是单词的左边或者右边

Js正则中的单词是指由数字、字母下划线组成的字符串，比如:

'abc' 'a_c' 都为一个单词

'adce;fbad' 'wew a123' 'qw&fda' 都为两个单词

**`\B`** 匹配非单词边界，表示一个不是单词边界的位置

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

var str = '123abc456def789';

// ^ 表示开头位置   $ 表示结尾位置
// 匹配开头位置的数字
// console.log(str.match(/^\d+/g));
// 匹配结束位置的数字
// console.log(str.match(/\d+$/g));

// \b 单词边界   \B 非单词边界
// 边界是指单词第一个字符的左边，或最后一个字符的右边
// JS中的单词是指由 数字、字母和下划线组成的字符串，并不是英语单词

var str2 = 'act react action react-native';
// 匹配所有的 act 子字符串 act react action  react-native 都包含有 act 
// console.log( str2.match(/act/g) ); // ['act', 'act', 'act', 'act']
// 匹配左边是边界的子字符串 act action 左边是边界 react react-native 中的 act 左边还有字符，不匹配
// console.log( str2.match(/\bact/g) ); // ['act', 'act']
// 匹配左右两边都是边界的子字符串  只有 act 匹配，其他单词左边或右边有字符
// console.log( str2.match(/\bact\b/g) ); // ['act']
// 匹配左边是边界，右边不是边界的子字符串， 只有 action 匹配
// console.log( str2.match(/\bact\B/g) ); // ['act']

</script>

</body>
</html>
```

## 捕获分组

捕获分组 是将正则表达式匹配规则使用 () 进行分组，并捕获分组信息。

分组有序号，分组序号是按左括号的顺序从1开始的有序整数。

**正则内部：**

后面可以使用 \n（n为大于0的数字，表示捕获的分组，也就是小括号的内容，第一个小括号的索引为1，第二个为2） 的方式引用前面分组的匹配结果，称为反向引用。
（\n的匹配结果与分组结果完全相同）。

**正则外部：**

在 replace() 方法中

当第二个参数为字符串时，可以使用 $ + 序号 的方式引用指定分组。如 ： $1, $2

当第二个参数为函数时，replace方法会自动将分组作为参数依次传入。

**例：** 编写正则，将 '-' 写法 转成 驼峰式命名

如： 'font-size' fontSize

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

// 内部的分组反向引用
var str1 = 'aaa123bcd444eee567fg';
// 匹配所有字母组合
 console.log(str1.match(/[a-z]+/g));  // ['aaa', 'bcd', 'eee', 'fg']
// 匹配所有重复字母组合 比如 aaa
 console.log(str1.match(/([a-z])\1+/g));  // ['aaa', 'eee']

var str = '1122 3434 5566 7879 9887';
//匹配连续四个数字，第一和第二数字相同，第三和第四数字相同
var res = str.match(/(\d)\1(\d)\2/g);
console.log(res);
//匹配连续四个数字，第一和第三数字相同，第二和第四数字相同
var res = str.match(/(\d)(\d)\1\2/g);
console.log(res);
//匹配连续四个数字，第一和第三数字相同
var res = str.match(/(\d)\d\1\d/g);
console.log(res);
//匹配连续四个数字，第一和第二数字相同，第三和第四数字相同，并将相同的数字只保留一个
var res = str.replace(/(\d)\1(\d)\2/g, '$1$2');
console.log(res);

// 外部引用分组
// 案例： 将 - 左右两边的单词位置互换
var str2 = 'hello-world';
// 分组是按左小括号( 的出现顺序进行编号的
// console.log( str2.replace(/(\w+)-(\w+)/, '$2-$1') );

// 第二个参数为函数
// var str3 = 'font-size';
var str3 = 'border-left-top';
// 将 - 改写为 驼峰式命名
console.log( str3.replace(/-(\w)(\w+)/g, function(a, b, c){
  console.log(a, b, c);
  // return b.charAt().toUpperCase() + b.slice(1);
  return b.toUpperCase() + c;
}) );
</script>
</body>
</html>
```

## 非捕获分组

非捕获分组 是作为条件使用，用于限制或筛选匹配结果。

非捕获分组不作为匹配结果输出，也不参与分组排序（即不计算分组序号），也无法被引用。

非捕获分组也称 断言（或者零宽断言）。

**ECMAScript 3中的断言：**

x(?=y) 向前肯定断言，x后面必须有y（y不会作为匹配结果返回）。

x(?!y) 向前否定断言，x后面不能有y

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

  var str = "abcadcafcaecagc";

  // console.log(str);

  // ES3中支持的断言
  // 匹配一个以a开头中间为b或d的三个字符的子字符串
  // console.log(str.match(/a[bd][a-z]/g)); // 写法一
  // console.log(str.match(/a(?=[bd])[a-z]{2}/g)); // 写法二
  // 匹配一个以a开头中间除了b和d之外的三个字符的子字符串
  // console.log(str.match(/a[^bd][a-z]/g)); // 写法一
  // console.log(str.match(/a(?![bd])[a-z]{2}/g)); // 写法二

</script>
  
</body>
</html>
```

**ECMAScript2018中新增了两个断言：**

(?<=y)x 向后肯定断言，x前面必须有y（y不会作为匹配结果返回）。

(?<!y)x 向后否定断言，x前面不能有y

## 或操作符 |

或操作符 表示匹配符合 | 符号左边或者右边的正则表达式的子字符串。

**不使用分组小括号：** 表示全局或操作

如： /abc|adc|afc/ abc adc afc 是三个独立的正则。

**使用分组小括号：** 表示局部或操作

如： `/a(b|d|f)c/ 相当于 /a[bdf]c/`

**或操作符 与 字符集合 的区别：**

字符集合只能表示一个字符， 或操作符可以表示任意多个字符。

比如： 匹配后缀为 .jpg / .png / .gif 三种后缀格式的图片

/.(jpg|png|gif)$/