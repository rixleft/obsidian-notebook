# for
- for(初始值;条件判断;循环变量的改变){循环语句}
	- 循环语句的条件  
        - 1：循环初始值
        - 2：循环条件判断
        - 3：循环语句
        - 4：循环变量的改变
==初始值可以拿到外部定义，但括号内的分号不能丢。==
循环嵌套时，外层循环控制行，内层循环控制列，内外循环的变量不要使用同一个。


```js
	<script>
	//九九乘法表
	for (var i = 1; i <= 9; i++) {
	    for (var j = 1; j <= i; j++) {
	        document.write(i + "*" + j + "=" + (i * j) + '&nbsp;&nbsp;');
        }
            document.write("<br/>")
    }
	</script>
```
# while
# do while
# for/in
