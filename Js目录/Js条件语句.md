#### 三元运算
- 三元运算符又称为三目运算符。      
	 - 语法格式   (条件表达式)?表达式1：表达式2；
	 - 如果条件为true，运算后的结果是表达式1；
	 - 如果条件为false，运算后的结果是表达式2；

```js
	<script>
	(关系表达式) ? 表达式1 : 表达式2;
	int x = 10;
	int y = 5;
	int z;
	如果x大于y 则是true，将x赋值给z；
	如果x不大于y 则是false，将y赋值给z；
	z = (x > y) ? x : y;
	System.out.println("x = " + x);

	获取三个整数中的最大值
	int a = 10;
	int b = 20;
	int c = 30;
	先比较任意两个数的值，找出这两个数中的最大值
	int temp = (a > b) ? a : b;
	用前两个数的最大值与第三个数比较，获取最大值
	int max = (temp > c) ? temp : c;
	System.out.println("max = " + max);

	</script>
```


#### if语句
- 语法一：if(条件) {执行语句}
当条件成立执行 不成立不执行
- 语法二：if(条件) {执行语句} else {执行语句} （可以使用三元运算符代替）
当条件成立之后条件后边的{}不成立，执行else。
- 语法三：if(条件) {执行语句} else if（条件）{执行语句} 。。。
只要有一个条件符合就会执行对应条件后边的语句，如果条件都不符合，不执行。
注意：条件从大向小写
- 语法三：if(条件) {执行语句} else if（条件）{执行语句} 。。。else {执行语句}
只要有一个条件符合就会执行对应条件后边的语句   如果条件都不符合 执行else

注意：如果{}里只有一条执行语句 可以省略{} （不建议）







#### switch
- switch(变量) {
	case 条件1：执行语句;break;
	case 条件2： 执行语句;break;}
- 条件必须是全等，不论是数值还是数据类型。
- 如果没有break关键词，代码会继续向下穿透，直到遇到break或者switch语句结束才能停止。
- 适用于写具体的数值的情况。
```js
<script type="text/javascript">
        var now = new Date();    //获取当天系统日期
        var day = now.getDay();   //获取当天是星期几
        var week;
        switch(day)//可以内写表达式
        {
            case 1:
                week = "星期一"; break;
            case 2:
                week = "星期二"; break;
            case 3:
                week = "星期三"; break;
            case 4:
                week = "星期四"; break;
            case 5:
                week = "星期五"; break;
            case 6:
                week = "星期六"; break;
            default:
                week = "星期日";
        }
        document.write("今天是"+week);    //输出今天是星期几
    </script>
```
