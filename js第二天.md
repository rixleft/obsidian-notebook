### 数据类型
- 基本数据类型
	- 字符串 数字（进制数 浮点数(小数) 科学计数法 NaN） 布尔值（true false）undefined null
- 复杂数据类型
	- 函数 对象 数组
- 如何判断数据类型
	- 通过typeof关键字 
	- 语法 typeof 你要判断的数据 或者  typeof （你要判断的数据）
	- 注意:typof 只能判断基本数据类型
	- 多次使用typeof的结果是string

### 转字符串
- 添加引号
- 与字符串做加法
```javascript
	<script>
	var str = "10";
	var str = "abc"
	var str = 10 + "";
	var str = null + "";
	var str = undefined + "";
	var str = "" + 10;
	var str = abc + ""; //会报错
	var str = "" + abc; //会报错
	console.log(typeof str)
	</script>
```
### 转数字
- Number 必须是纯数字或者null，true，false。首字母必须大写。
	- null 会被转换为0,
	- true 会被转换为1
	- false 会被转换为0
```javascript
	<script>
	var num = "10";
	var num = null;  //0
	var num = true;  //1
	var num = false;  //0
	var res = Number(num);
	var res = +str //类型转换为Number
	var res = str-0 //类型转换为Number
    var res = str*1 //类型转换为Number
    var res = str/1 //类型转换为Number
	console.log(res);
	</script>
```
如果加号放在后边 左右两边有一个是字符串就会做字符串的拼接。
```javascript
	<script>
	   console.log("1" + 1); //11
       console.log(+"1" + 1); //2
       console.log(1 + (+"1")); //2
       console.log(1 + true); //2
       console.log(1 + "true"); //1true
       console.log(1 + undefined); //NaN
       console.log(1 + undefined); //1undefined
       console.log(1 + NaN); //NaN
	</script>
```
- parseInt 严格区分大小写，将字符串转换为整数，小数点后会被省略。
```javascript
	<script>
	var num = "10"; //10
	var num = "10h";  //10
	var num = "10.9h";//10
	var num = "h10"; //NaN
	var num = unll; //NaN
	var res = parseInt(num);
	console.log(res);
	</script>
```
一个数代表将这个数转换成对应的数字类型，两个数时，第一个值代表要转换的数，第二个值代表要转换时使用的进制数。
```javascript
	<script>
        console.log(parseInt(9,10))  //十进制 0和10都可以表示十进制  值为9
        console.log(parseInt(11,8)) //八进制  值为9
        console.log(parseInt(11,16)) //八进制  值为17
        console.log(parseInt(11,36)) //八进制  值为37
        console.log(parseInt(11,37)) //八进制  值为NaN 
     </script>
```
- parseFloat
```javascript
	<script>
	var num = "10"; //10
	var num = "10h";  //10
	var num = "10.9h";//10.9
	var num = "h10"; //NaN
	var num = unll; //NaN
	var res = parseInt(num);
	console.log(res);
	</script>
```

### 隐式数据转换类型 [详情](https://www.jianshu.com/p/e4ac366ac2fd)
当运算符在运算时，如果两边数据类型不统一，CPU无法计算，这时编译器会自动将运算符两边的数据做一个数据类型转换，转换成一样的数据类型再进行运算，这种无需程序员手动转换，而由编译器自动转换的方式就称为隐式转换。
1.转为number类型：`+`  `-`   `*`  `/`  `++`  `--`（算数运算符） `>` `<` `>=` `<=` `==` `!=` `===` `!==`（比较运算符）；  
2.转为string类型：`+` 不仅是算术运算符，还可以做为字符串连接符把数据转换成string类型；  
3.转为boolean类型： `!`（逻辑非运算符）

#### 运算符的优先级
**另外需要补充的一点常用的几种运算符各运算符优先级：**  
算术运算符：`+` `-` `*` `/` `++` `--`  
比较运算符： `>` `<` `>=` `<=` `==` `!=` `===` `!==`  
逻辑运算符：`&&` `||` `!`  
赋值运算符：`=` `+=` `-=` `*=` `/=`

**算术运算符 > 比较运算符 > 逻辑运算符 > 赋值运算符**
  
```javascript
    console.log(1 + true);      //2
    console.log(1 + "true");        //"1true"
    console.log(1 + undefined);     //NaN
    console.log(1 + null);      //1
```
- `+` 两边有一边是字符串，那这个`+`就是字符串连接符，它会把其他数据类型调用`String()`方法转成字符串然后拼接；  
- `+` 做为算术运算符会把其他数据类型调用`Number()`转成数字然后做加法运算;  
	- 布尔值`true`会被转换数字 `1`，  
	- `undefined`会被转换为 `NaN`，  
	- `null`会转换为数字 `0`

比较运算符会把其他数据类型转换成number数据类型后再比较。
```javascript
    console.log("2" > 10);      //false
    console.log("a" > 10);      //false
    console.log(10 > "a");      //false
    console.log(Number("a"));      //NaN
    console.log("2" > "10");        //true    '
    console.log(false == 0);        //true
    console.log(false == "");       //true
    console.log(Number(false));       //0
    console.log(NaN == NaN);        //false
    console.log(undefined == null);     //true
    console.log(Number(NaN));       //NaN
    console.log(Number(undefined));     //NaN
    console.log(Number(null))       //0
```
- 比较运算符的一边是字符串的时候，会调用 `Number()` 方法把字符串转换成数字在进行比较；  
- 当关系运算符两边都是字符串的时候，此时同时转成number然后比较关系。
	- 重点：此时并不是按照Number()的形式转成数字，而是按照字符串对应的unicode编码来转成数字，使用 `字符串.charCodeAt(字符下标，默认为0)` 方法可以查看字符的unicode编码。  
- 布尔值和数字比较时，会把布尔值通过 `Number()` 转成数字再进行比较，`true`转成 `1`，`false` 转成 `0`；  
- 字符串和布尔值比较时，会把字符串和布尔值都通过 `Number()` 转成数字再进行比较  
- **在javascript中有两种特殊情况无视规则：1. `null == undefined`； 2. `NaN`和谁都不相等，包括他自己。**

  
### Math方法
- 1.random：随机数的值0~1之间，不包含1
- 2.sqrt 开平方根
- 3.pow 次幂数
- 4.PI  π
#### Math对象属性
| 属性    | 描述                            |
| ------- | ------------------------------- |
| E       | 返回算术常量e，即自然对数的底数 |
| LN2     | 返回 2 的自然对数               |
| LN10    | 返回 10 的自然对数              |
| LOG2E   | 返回以2 为底的e的对数           |
| LOG10E  | 返回以10 为底的e的对数          |
| PI      | 返回圆周率                      |
| SQRT1_2 | 返回2的平方根的倒数                                |
| SQRT2   | 返回2的平凡根                                |
#### Math对象方法
| 方法             | 描述                                          |
| ---------------- | --------------------------------------------- |
| random()         | 返回0~1之间的随机数                           |
| abs(x)           | 返回x的绝对值                                 |
| sqrt(x)          | 返回数的平方根                               |
| round(x)         | 四舍五入                                      |
| pow(x,y)         | 返回x的y次幂                                  |
| exp(x)           | 返回e的x次方                                  |
| ceil(x)          | 对x向上取整                                   |
| floor(x)         | 对x向下取整                                   |
| max(x,y,z.....n) | 返回最大值                                    |
| min(x,y,z.....n) | 返回最小值                                    |
| log(x)           | 返回数的自然对数(底为e)                       |
| sin(x)           | 返回数的正弦值                                              |
| cos(x)           | 返回数的余弦值                                  |
| tan(x)           | 返回数的正切值                                              |
| asin(x)          | 返回x的反正弦值                               |
| acos(x)          | 返回x的反余弦值                               |
| atan(x)          | 以介于-π/2与π/2之间的数值返回x的反正切值      |
| atan2(y,x)       | 返回从x轴到点(x,y)的角度（介于-π/2与π/2之间） |
