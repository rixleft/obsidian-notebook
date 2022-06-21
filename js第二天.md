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
	var str = "" + 10;
	var str = abc + ""; //会报错
	var str = "" + abc; //会报错
	</script>
```
### 转数字
- Number 必须是纯数字或者null，true，false。
	- null 会被转换为0,
	- true 会被转换为1
	- false 会被转换为0
```javascript
	<script>
	var num = "10";
	var res = Number(num);
	console.log(res);
	
	</script>
```
- parseInt
```javascript
	<script>
	
	</script>
```
- parseFloat
```javascript
	<script>
	
	</script>
```