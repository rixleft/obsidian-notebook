## 组成
- ECMA  js的语法规则,描述了语言的及基本语法（var、for、if、array等和数据类型(数字、字符串、布尔、函数、对象(obj、`[]`、{}、null)、未定义)。
- DOM   文档对象模型  一整套控制元素（标签）的方式方法。DOM 通过创建树来表示文档，从而使开发者对文档的内容和结构具有空前的控制力。用 DOM API 可以轻松地删除、添加和替换节点（getElementById、childNodes、appendChild、 innerHTML）。
- BOM   浏览器对象模型 一整套控制浏览器的方式方法，对浏览器窗口进行访问和操作。例如弹出新的浏览器窗口，移动、改变和关闭浏览器窗口，提供详细的网络浏览器信息（navigator object），详细的页面信息（location object），详细的用户屏幕分辨率的信息（screen object），对cookies的支持等等。

## 注释
```
	单行注释  ctrl+/   //
	多行注释   alt+shift+a    /**/
```

## 输出语句
- 1：alert(你要输出的内容)  弹出的形式输出
- 2：console.log(你要输出的内容) 在浏览器的控制台输出  排错常用方式
- 3：document.write(你要输出的内容)  在浏览器的页面中输出，可以将html的标签按照html进行解析
- 注意：你要输出的内容如果是纯数字的可以不用添加引号 非纯数字必须添加引号，如果不加引号代表的是变量，变量没有定义就会报错
```javascript
	<script>
        // alert("avbc")
        // alert(abc)
        // alert(123)
        alert("<h1>标题</h1>")
        // console.log(123)
        // console.log("abc")
        // console.log(abc)
        console.log("<h1>标题</h1>")
        // document.write(123)
        // document.write("abc")
        // document.write(abc)
        document.write("<h1>标题</h1>")
     </script>
```

## 字面量
- 字面量：一种表示固定值的方式方法，还可以叫做常量 固定值，所见即所得。
- 字符串字面量：一切写在引号（单双引号都可以）里面的都是字符串字面量。字符串不能换行书写，可以通过转义字符。
- 数字字面量：整数 ，小数（浮点数）。
```javascript
            \n 换行
            \t  制表符
            \' 转义单引号
            \" 转义双引号
            \\ 转义反斜杠
        注意：单双引号不能单独出现 必须是成对出现  
```

## 方式
### 1.行内式

1.行内式：
方式一：
```javascript
<button οnclick="alert('今天天气很好！');">今天天气?</button>
 
 虽然可以写在标签的属性中，但是结构与行为耦合，不方便维护，不推荐使用。
```
 方式二：
```javascript
<a href="javascript:alert('你点疼我了！！');">点我</a>
```

2.页内式(内联式)

```javascript
<body>   
	<script  type="text/text/javascript">  
           alert('我出现了')  
    </script>  
</body>
```

 **注意事项：`<script></script>`标签中的js代码一版写在文档的尾部；网页是从上而下加载的，而js代码通常是给标签添加交互（操作元素），所以需要先加载html，否则如果执行js代码时html还没有被加载，那么js代码将无法添加交互（操作元素）

**html页面中出现`<script>`标签后，就会让页面暂停等待脚本的解析和执行，无论当前脚本时内嵌式还是外链式，页面的下载和渲染都必须停下来等待脚本的执行完成才能继续。**

**所以如果把js代码写在head中，那么js代码执行完毕之前后续页面无法被加载。**

3、外链式
```javascript

<script type="text/javascript" src="01-js书写格式.js"></script>  
 注意事项  
     外链式的script代码块中不能编写js代码, 即便写了也不会执行  
     
     <script type="text/javascript" src="index.js">  
       alert("今天天气很好！"); // 不会被执行  
 </script>

```
由于每次加载外链式的js文件都会发送一次请求, 这样非常消耗性能, 所以在企业开发中推荐将多个JS文件打包成为一个JS文件,以提升网页的性能和加载速度。

### 2.JS输出方式

```javascript
	alert("Hello, World!");  
         控制浏览器弹出一个警告框  
     document.write("Hello World!");  
         可以向body中输出一个内容  
     console.log("Hello World!");  
         向控制台输出一个内容  
          console.warn("警告输出！");  
          console.error("错误输出！");  
     prompt("Hello, World！");  
         在网页中弹出输入框，一般用于接收用户输入的信息  
         comfirm("Hello，JavaScript！");  
         在网页中弹出提示框，显示信息，该方法一般与if判断语句结合使用
```

### 3.JS严格区分大小写

```javascript
comfirm("Hello，JavaScript！");   // 正确  
COMFIRM("Hello，JavaScript！");   // 错误
```

### 4.JS标识符

```javascript
 命名规则  
     1. 标识符中可以含有字母、数字、_、$  
     2. 标识符不能以数字开头  
     3. 标识符不能是ES中的关键字或保留字  
     4. 标识符一般都采用驼峰命名法  
         首字母小写，每个单词的开头字母大写，其余字母小写  
         比如: myName, yourName, itLike, ....  
     5. 在JS底层保存的标识符采用的是Unicode编码，所以UTF-8中所有的字符都可以作为标识符
```
### 5.JS的进制表示
在JS中可以表示不同进制的数字  
16进制的数字，则需要以0x开头  0x17=16+7=23
8进制的数字，则需要以0开头      0
2进制的数字，则需要以0b开头  
得看浏览器支持  
使用  
十六进制  
num = 0x18;  
num = 0xcf;  
num = 0xAacf;  
八进制数字  
num = 016;  
二进制数字  
num = 0b1010;  
注意  
"010"这种[字符串](https://so.csdn.net/so/search?q=%E5%AD%97%E7%AC%A6%E4%B8%B2&spm=1001.2101.3001.7020)，有些浏览器会当成8进制解析，有些会当成10进制解析  
可以在parseInt()或parseFloat中传递一个第二个参数，来指定数字的进制

>     str = "070";  
> // str= parseInt(str,10);  
> str = Number(str);  
>               
> console.log(typeof str);  
> console.log(str);