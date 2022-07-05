# JavaScript 第十天


## 认识jQuery

jQuery 是一个快速、小巧、功能丰富的JavaScript库。

jQuery 通过一个易于使用的、可跨多种浏览器工作的API，使HTML文档遍历和操作、事件处理、动画和Ajax请求等工作变得更加简单。

jQuery 结合了多功能性和可扩展性，改变了数百万人编写 JavaScript 的方式。

**jQuery 版本：**

jQuery 从2.0版本开始不再兼容IE8以下浏览器。

最后一个兼容IE8以下浏览器的版本为 1.12.4。

官网：[www.jquery.com](http://www.jquery.com/)

### 下载jQuery

**版本选择：**

jQuery 分为 开发版本 和 生产版本

**开发版本：**

开发时使用的版本，代码没有压缩，并且附带注释，方便开发人员研究学习。

**生产版本：**

项目上线之后使用的版本，代码进行了压缩，体积更小，加载速度更快。

**1.12.4 版本官方地址：**

开发版本：[https://code.jquery.com/jquery-1.12.4.js](https://code.jquery.com/jquery-1.12.4.js)

生产版本：[https://code.jquery.com/jquery-1.12.4.min.js](https://code.jquery.com/jquery-1.12.4.min.js)

### $() 函数介绍

$() 是 jQuery 的核心函数

**参数：** 两个

第一个： 用来获取指定元素的字符串选择器，支持所有的 css2.1 / css3 选择器。

第二个参数： （可选）指定获取元素的范围。

**返回值：**

经过 $() 函数包装的类数组对象，通常被称为 jQuery 对象。

1，无论是否成功获取到元素，$() 函数都始终返回 jQuery 对象。

2，可以通过 length 属性来判断 jQuery 是否获取到了元素。

**说明：**

1，$() 是 jQuery 库定义的一个 全局函数，函数名称为 $。

2，为防止 $ 名称被其它 js 类库占用，jQuery 同时提供了另一个函数名： jQuery。

3，$ 和 jQuery 指向的是同一个函数，功能完全相同。

```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel="icon" href="data:image/ico;base64,=">  
  <title>Document</title>  
</head>  
<body>  
    
  <h2>jquery学习</h2>  
​  
  <div id="div1">这是#div1</div>  
​  
  <ul>  
    <li>列表01</li>  
    <li class="active">列表02</li>  
    <li>列表03</li>  
    <li class="active">列表04</li>  
    <li>列表05</li>  
  </ul>  
​  
  <div class="main">  
    <h2>这是一个标题</h2>  
    <p>1111 2222 33333</p>  
    <p>aaaa bbbb ccccc</p>      
  </div>  
​  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
    // 通过 $() 获取元素  
    // $() jq 获取元素就像是 css 样式表中通过选择器选择元素。  
    // $() 的参数就是获取元素的选择器，支持所有的 css2.1 、 css3 选择器  
    // 获取 id 为 div1 的元素  
    console.log( $('#div1') );  
    // 获取标签名为 li 的元素  
    console.log( $('li') );  
    // 获取类名为 active 的元素  
    console.log( $('.active') )  
    // 获取类名为 main 的元素下面的第一个任意子元素  
    console.log( $('.main :nth-child(1)') );  
    // 获取类名为 main 的元素下面的第一个标签名为p的子元素  
    console.log( $('.main p:nth-child(1)') );  
​  
    //  $() 函数返回的始终是一个 jquery 自定义的类数组对象  
    // 即使是通过id方式获取，返回值同样也是一个类数组对象  
    console.log( $('#div1').length );  
    // 即使没有获取到任何值，返回值还是一个类数组对象（可以通过length属性来判断是否获取到了元素）  
    console.log( $('#div2') );  
​  
    // $() 可以指定第二个参数来限制获取元素的范围 （通常不需要）  
    // 获取所有 h2 标签  
    console.log( $('h2') );  
    // 获取 .main 下面的 h2 标签  
    console.log( $('h2', $('.main')) )  
    // 使用一个参数写法，效果与上一行完全相同  
    console.log( $('.main h2') );  
​  
    // $() 是 jquery 创建的一个全局函数，函数名称为 $。  
    console.log( $ );  
    console.log( typeof $ );  
​  
    // 为了防止 $ 被其他的类库占用导致无法使用， jquery 另外提供了函数名称 jQuery 作为 $ 的备用名。  
    // $ 与 jQuery 指向的是同一个函数  
    console.log( jQuery );  
  </script>  
​  
</body>  
</html>
```


### jQuery 对象常用方法

jQuery 的所有方法都必须是在 jQuery 对象上调用，无法在原生DOM对象上调用。

**size() ：** 返回 jQuery 对象的 length 值。

**样式获取与设置：**

**css() ：** 获取或者设置 jQuery 对象的样式。

获取样式： 无论 jQuery 对象中保存了多少个元素，都只会返回第一个元素的样式。

设置样式： 给 jQuery 对象中的所有元素设置样式。

**绑定事件函数：**

**on() ：** 绑定事件处理函数， 语法： on(事件名称, 事件处理函数)

事件名称不需要 'on' 前缀，如： $('#div1').on('click', function(){});

```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel="icon" href="data:image/ico;base64,=">  
  <title>Document</title>  
  <style>  
    #div1 { color: red; }  
  </style>  
</head>  
<body>  
    
  <h2>jquery学习</h2>  
​  
  <div id="div1">这是#div1</div>  
​  
  <ul>  
    <li style="color: green;">列表01</li>  
    <li class="active">列表02</li>  
    <li style="color: gray;">列表03</li>  
    <li class="active">列表04</li>  
    <li>列表05</li>  
  </ul>  
​  
  <div class="main">  
    <h2>这是一个标题</h2>  
    <p>1111 2222 33333</p>  
    <p>aaaa bbbb ccccc</p>      
  </div>  
​  
  <input type="button" value="按钮11">  
  <input type="button" value="按钮22">  
​  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
    // 查看获取到的html元素数量  
    console.log( $("#div1").size() );  
    console.log( $("li").size() );  
    // 也可以使用 length 属性查看，效果相同   
    console.log( $("#div1").length );  
    console.log( $("li").length );  
​  
    //  css() 方法 既可以获取样式，也可以设置样式，获取的样式为计算样式  
    // 获取color样式的值  
    console.log( $('#div1').css('color') );  
    // 将color 的值设置为 orange;  
    $('#div1').css('color', 'orange');  
    // 也可以使用对象形式设置样式  （jquery会根据参数个数和类型自动判断是获取样式，还是设置样式）  
    $('#div1').css({color: "blue", fontSize: 20});  
​  
    // 获取样式时，如果前面选择器选中的是多个元素，只会返回第一个元素的样式  
    console.log( $('li').css('color') );  
    // 设置样式时， 是给所有被选中的元素设置  
    $('li').css({border: "1px solid red"});  
​  
    // 通过 on 方法给元素添加事件处理函数  
    // 事件是添加给所有被选中的元素  
    // 支持所有的事件，注意事件名称需要 'on' 前缀  
    $('input').on('click', function() {  
      console.log('我被点击了！');  
    });  
        
    // 常用事件的快捷方法  
    // jquery 提供了常用事件的快捷方法，可以直接使用  
    $('input').click(function(){  
        console.log('点击事件快捷方法');  
    });  
    $('input').dblclick(function(){  
        console.log('双击事件快捷方法');  
    });  
    // 更多常用事件快捷方法：   
    // change() / focus() / mousedown() / mouseup  
    // mouseenter() / mouseleave() / keydown() / keyup()  
  </script>  
​  
</body>  
</html>
```


**简单动画**

**show() ：** 显示元素

**hide() ：** 隐藏元素

**toggle() ：** 在 show() 与 hide() 方法之间来回切换调用。

**slideDown()：** 下滑展开显示

**slideUp():** 上拉收缩隐藏

**slideToggle():** 切换调用 slideDown() 和 slideUp()

**fadeIn():** 淡入显示

**fadeOut():** 淡出隐藏

**fadeToggle():** 切换调用 fadeIn() 和 fadeOut()

**说明：** show() / hide() / toggle() 方法默认没有动画效果，可以传递时间参数来开启动画效果，单位为 ms。

```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel="icon" href="data:image/ico;base64,=">  
  <title>Document</title>  
  <style>  
    #div1 {  
      width: 200px;  
      height: 200px;  
      background: red;  
    }  
    #div2 {  
      width: 300px;  
      height: 100px;  
      background: pink;  
      font-size: 20px;  
      font-weight: bolder;  
    }  
  </style>  
</head>  
<body>  
    
  <h2>jquery学习</h2>  
​  
  <input type="button" class="btn1" value="显示">  
  <input type="button" class="btn2" value="隐藏">  
  <input type="button" class="btn3" value="切换">  
  <div id="div1"></div>  
​  
  <div id="div2">元素完全隐藏之后，不会再占页面空间</div>  
​  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
    // 需要重复使用时，可以将获取到的 jquery 对象存入变量中  
    // 为了与原生的DOM对象区别开，建议在变量名称的第一个字符为$。  
    // 原生DOM对象： 即使用 getElementById() / getElementsByTagName() / getElementsByClass() 等原生方式获取到的 DOM 对象  
    var $div1 = $('#div1');  
​  
      
  /*   
    // 显示隐藏  
    $('.btn1').on('click', function(){  
      // 如果元素已经是显示状态，则不会有任何效果  
      $div1.show();  
    });  
​  
    $('.btn2').on('click', function(){  
      // 如果元素已经是隐藏状态，则不会有任何效果  
      $div1.hide();  
    });  
​  
    $('.btn3').on('click', function(){  
      // 在显示与隐藏之间切换：原来是隐藏，点击就显示；原来是显示，点击就隐藏。  
      $div1.toggle();  
    });  
     */  
​  
    /*   
    // 下滑显示与收缩隐藏  
    $('.btn1').on('click', function(){  
      // 如果元素已经是显示状态，则不会有任何效果  
      $div1.slideDown();  
    });  
​  
    $('.btn2').on('click', function(){  
      // 如果元素已经是隐藏状态，则不会有任何效果  
      $div1.slideUp();  
    });  
​  
    $('.btn3').on('click', function(){  
      // 在显示与隐藏之间切换：原来是隐藏，点击就显示；原来是显示，点击就隐藏。  
      $div1.slideToggle();  
    });   
    */  
​  
/*     // 淡入显示与淡出隐藏  
    $('.btn1').on('click', function(){  
      // 如果元素已经是显示状态，则不会有任何效果  
      $div1.fadeIn();  
    });  
​  
    $('.btn2').on('click', function(){  
      // 如果元素已经是隐藏状态，则不会有任何效果  
      $div1.fadeOut();  
    });  
​  
    $('.btn3').on('click', function(){  
      // 在显示与隐藏之间切换：原来是隐藏，点击就显示；原来是显示，点击就隐藏。  
      $div1.fadeToggle();  
    });  
 */  
    
    // 显示隐藏默认没有动画，可以通过传递参数来开启动画，单位 ms  
    $('.btn1').on('click', function(){  
      // 如果元素已经是显示状态，则不会有任何效果  
      $div1.show(600);  
    });  
​  
    $('.btn2').on('click', function(){  
      // 如果元素已经是隐藏状态，则不会有任何效果  
      $div1.hide(600);  
    });  
​  
    $('.btn3').on('click', function(){  
      // 在显示与隐藏之间切换：原来是隐藏，点击就显示；原来是显示，点击就隐藏。  
      $div1.toggle(600);  
    });  
      
  </script>  
​  
</body>  
</html>
```


**内容获取与设置**

**html() :** 获取第一个普通元素的内容，或者修改所有普通元素的内容。

**val() :** 获取第一表单元素的内容，或者修改所有表单元素的内容。

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
  <div id="div1">这是div1标签</div>  
​  
  <ul>  
    <li>列表001</li>  
    <li>列表002</li>  
    <li>列表003</li>  
    <li>列表004</li>  
    <li>列表005</li>  
  </ul>  
​  
  <input type="text" value="这是第一个文本输入框">  
  <input type="text" value="这是第二个文本输入框">  
​  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
  // console.log($);  
​  
  // html() 方法  
  // 不传递参数为 获取元素的 innerHTML   
  // console.log( $('#div1').html() );  
  // 如果 jq 对象中包含多个html元素，只会返回第一个元素的 内容  
  // console.log( $('li').html() );  
  // 传递参数， 表示修改元素的 innerHTML   
  // $('#div1').html('hello world');  
  // 如果 jq 对象中包含多个html元素，所有元素的内容都会被修改  
  // $('li').html('修改多个元素的内容');  
  $('li').html(function(index, html) {  
    // html() 方法默认会覆盖元素原来的 innerHTML  
    // 可以使用函数作为参数，来修改指定元素的内容  
    // 函数自动接收两个参数： index  元素的索引   html  元素原来的 innerHTML  
    //  返回值将是元素的新内容，没有return， 元素的内容不会被修改   
    // 在指定元素后面添加新内容（保留原来的内容）  
    if ( index == 2 ) {  
      return html + ' 这是新添加的内容';  
    }  
  });  
​  
  // val() 方法  
  // 不传递参数为获取 value ，传递为设置或修改value  
  // 获取表单元素的 value  
  console.log( $('input').val() );  
  // 设置表单元素的 value  
  // $('input').val('修改表单内容')  
  // 通过回调函数修改指定表单元素内容  
  $('input').val(function(index, val) {  
    if (index == 1) {  
      return val + ' 新增的内容';  
    }  
    // 与 html() 方法不同的是: html() 回调函数没有return，默认不修改，使用原来的内容； val() 回调函数没有return，会清空表单里的内容。  
    return val;  
  })  
​  
  </script>  
​  
</body>  
</html>
```


**属性操作**

**addClass() :** 给所有元素添加className。

**removeClass() :** 移除所有元素的className，不传递参数会清空所有class。

**hasClass() :** 所有元素都没有指定class，返回 false, 否则返回 true。

**toggleClass() :** 切换执行 addClass() 和 removeClass()。

**attr() :** 获取第一个元素的指定属性的值，或修改所有元素的指定属性值。

attr() 获取和设置的是字符串值， 布尔类型的值使用 prop() 方法。

**removeAttr() :** 删除元素的指定属性，不指定参数则不执行该方法（不用处理关键字）。

由 prop() 方法添加的属性，建议使用 removeProp() 方法删除。

```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
  <style>  
    #div1 {  
      width: 300px;  
      height: 150px;  
      background: pink;  
      text-align: center;  
      line-height: 150px;  
    }  
    .normal {  
      font-size: 30px;  
      color: white;  
    }  
    .active {  
      font-size: 50px;  
      color: green;  
      font-weight: bold;  
    }  
  </style>  
</head>  
<body>  
​  
​  
  <input type="button" value="添加class">  
  <input type="button" value="移除class">  
  <input type="button" value="切换class">  
  <br/>  
  <input type="text" >  
  <input type="button" value="判断class">  
  <span></span>  
​  
  <div id="div1" class="normal" title="这是提示文字">前端开发</div>  
​  
  <!-- <input type="checkbox"> -->  
  <input type="checkbox" checked>  
​  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
    var $div1 = $('#div1');  
    var $btns = $('input[type=button]');  
    var $text = $('input[type=text]');  
    var $span = $('span');  
​  
    // console.log( $btns.length );  
​  
    // class 相关操作  
    $btns.eq(0).click(function() {  
      // 添加指定class （追加效果，不会覆盖原来的class）  
      $div1.addClass('active');  
    });  
    $btns.eq(1).click(function() {  
      // 传递参数： 删除指定class  
      // $div1.removeClass('active');  
      // 可以同时删除多个class，中间使用空格分隔  
      // $div1.removeClass('active normal');  
      // 不传递参数： 删除所有class  
      $div1.removeClass();  
    });  
    $btns.eq(2).click(function() {  
      // 切换指定class   元素身上如果没有指定class，就添加，有指定class，就删除   
      $div1.toggleClass('active');  
    });  
    $btns.eq(3).click(function() {  
      $span.html( $div1.hasClass( $text.val() ) ? 'true' : 'false' );  
    });  
​  
    // 属性操作  
    // 获取 title 属性的值  
    // console.log( $div1.attr('title') );  
    // 修改 title 属性的值  
    // $div1.attr('title', '修改后的提示文字');  
​  
    // 布尔值类型的属性，使用 attr() 方法不会返回布尔值  
    // console.log( $('input:checkbox').attr('checked') );  
    // 需要返回布尔值，应该使用 prop() 方法  
    // console.log( $('input:checkbox').prop('checked') );  
    // 使用 attr() 方法设置布尔类型的值  
    // $('input:checkbox').attr('checked', 'checked');  
    // $('input:checkbox').prop('checked', true);  
​  
    // 删除属性  
    // 删除 div1 的 title 属性  
    // $div1.removeAttr('title');  
    // 同时删除 title 和 class 属性 （删除多个属性，中间要使用空格分隔）  
    // $div1.removeAttr('title class');  
    // 布尔值类型的属性，使用 removeAttr() 和 removeProp() 都可以，效果一样  
    // $('input:checkbox').removeAttr('checked');  
    // $('input:checkbox').removeProp('checked');  
​  
  </script>  
    
</body>  
</html>
```


### 节点操作

**$(this) :** 将原生 this 对象 包装成 jQuery 对象。

**parent() :** 获取已选中的所有元素的直接父节点，可以传递参数来筛选父节点。

**children() :** 获取已选中的所有元素的直接子节点，可以传递参数来筛选子节点。

**siblings() :** 获取已选中的所有元素的所有同级兄弟节点，可以传递参数来筛选兄弟节点。

**next() :** 获取与已选中的所有元素的相邻的下一个兄弟节点，可以传递参数来筛选兄弟节点。

**nextAll() :** 获取已选中的所有元素后面的所有兄弟节点，可以传递参数来筛选兄弟节点。

**prev() :** 获取与已选中的所有元素的相邻的上一个兄弟节点，可以传递参数来筛选兄弟节点。

**prevAll() :** 获取已选中的所有元素前面的所有兄弟节点，可以传递参数来筛选兄弟节点。

**parents() :** 获取已选中的所有元素的所有祖先节点，可以传递参数来筛选祖先节点。

**find() :** 获取已选中的所有元素的指定后代节点，不传递参数将不会选中任何后代节点。

**说明：** 以上所有方法都支持链式操作，并且可以使用 end() 方法回退链式操作。

**end() ：** 回退到上一个链式操作的节点操作，如果end() 前面没有链式操作，返回空的 jquery 对象。

```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel="icon" href="data:image/ico;base64,=">  
  <title>Document</title>  
  <style>  
    h2,p,ul {margin: 0; padding: 0;}  
    li { list-style: none; }  
    ul {  
      width: 400px;  
      padding: 20px;  
    }  
    ul li {  
      padding: 10px 0;  
      /* background: orange; */  
      margin: 5px 0;  
      border: 2px solid #333  
    }  
    ul li li {  
      background: orchid;  
      /* background: orangered; */  
    }  
  </style>  
</head>  
<body>  
    
​  
  <ul class="list">  
    <li>li</li>  
    <li>li</li>  
    <li>li</li>  
    <li>li</li>  
    <li>li</li>  
    <li>li</li>  
    <li>li</li>  
    <li>li</li>  
    <li>  
      <ul>  
        <li></li>  
        <li class="abc"></li>  
        <li></li>  
        <li class="abc"></li>  
        <li></li>  
      </ul>  
    </li>  
  </ul>  
​  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
      
    $('.list > li').click(function() {  
      // 当前被点击的元素  
      $(this).css({background: 'green'});  
​  
​  
      // $(this).parent().css({background: 'pink'});  
        
      // 当前元素的所有兄弟节点（同级的其他元素，不包括自身）  
      // $(this).siblings().css({background: 'blue'});  
​  
      // 当前元素的下一个兄弟节点  
      // $(this).next().css({background: 'gold'});  
​  
      // 当前元素后面的所有兄弟节点  
      // $(this).nextAll().css({background: 'purple'});  
​  
      // 当前元素的上一个兄弟节点  
      // $(this).prev().css({background: 'burlywood'});  
​  
      // 当前元素前面的所有兄弟节点  
      // $(this).prevAll().css({background: 'goldenrod'});  
​  
      // 当前元素的所有祖先节点  
      // $(this).parents().css({border: '5px solid red'});  
    });  
​  
    // 给 .list 元素设置边框  
    $('.list').css({border: '5px solid darkblue'});  
​  
    // 在 .list 元素的后代元素中查找所有 ul 元素，然后设置样式  
    // $('.list').find('ul').css({border: "5px solid red"});  
​  
    // 在 .list 元素的后面元素中查找所有class名称为 abc 的元素，然后设置样式  
    $('.list').find('.abc').css({border: "5px solid red", background: 'gold'});  
​  
     
    // $('.list').children() // 获取 .list 的子节点（第一层子元素）  
    // $('.list').children().eq(-1)  // .list的子节点中的最后一个节点  
    // $('.list').children().eq(-1).find('ul')  // 查找 .list的子节点中的最后一个节点下面的 ul 元素  
    // $('.list').children().eq(-1).find('ul').find('.abc') // // 在.list的子节点中的最后一个节点下面的 ul 元素中查找 class 为 .abc 的后代节点  
    // 链式操作  
    // $('.list').children().eq(-1).find('ul').find('.abc').css({background: "#333"});  
​  
    // end() 返回链式操作的上一层 （必须在链式操作中使用）  
    // 相当于 $('.list').children().eq(-1).find('ul').css({background: "#333"});  
    // $('.list').children().eq(-1).find('ul').find('.abc').end().css({background: "#333"});  
    // 相当于 $('.list').children().eq(-1).css({background: "#333"});  
    // $('.list').children().eq(-1).find('ul').find('.abc').end().end().css({background: "#333"});  
    // 相当于 $('.list').children().css({background: "#333"});  
    // $('.list').children().eq(-1).find('ul').find('.abc').end().end().end().css({background: "#333"});  
    // 相当于 $('.list').css({background: "#333"});  
    // $('.list').children().eq(-1).find('ul').find('.abc').end().end().end().end().css({background: "#333"});  
    // $('.list') 已经是链式操作的最顶层，再使用 end() 不会有任何效果  
    // $('.list').children().eq(-1).find('ul').find('.abc').end().end().end().end().end().css({background: "#333"});  
​  
  </script>  
​  
</body>  
</html>
```


### 精确选择 与 元素遍历

**精确选择：**

**eq(index) :** 从 jQuery 对象中选中指定的元素。

index : 要选中的元素的位置，正数表示从前往后查找，负数表示从后往前查找。

**first() :** 返回 jQuery 对象中的第一个元素 （jQuery对象）。

**last() :** 返回 jQuery 对象中的最后一个元素 （jQuery对象）。

**get(index) :** 返回指定jQuery对象的原生DOM对象，不指定参数则返回所有原生DOM对象。

**元素遍历：**

**each(fn) :** 遍历已选中的所有 jQuery 对象。

参数： fn 遍历时自动调用的函数。

each() 方法会自动传递两个参数给 fn 函数：

第一个参数： 当前遍历元素的索引

第二个参数： 当前遍历元素的原生 dom 对象。

```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel="icon" href="data:image/ico;base64,=">  
  <title>Document</title>  
</head>  
<body>  
    
  <ul>  
    <li>无序列表01</li>  
    <li>无序列表02</li>  
    <li>无序列表03</li>  
    <li>无序列表04</li>  
    <li>无序列表05</li>  
  </ul>  
​  
  <ol>  
    <li>有序列表01</li>  
    <li>有序列表02</li>  
    <li>有序列表03</li>  
    <li>有序列表04</li>  
    <li>有序列表05</li>  
  </ol>  
​  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
      
    // 给所有li都设置边框  
    // $('li').css({border: "2px solid red"})  
​  
    // 给所有li中的第三个li设置边框  
    // $('li').eq(2).css({border: "2px solid orange"});  
​  
    // 给所有li中的倒数第二个li设置边框  
    // $('li').eq(-2).css({border: "2px solid blue"});  
​  
    // 给所有li中的第一个li设置边框  
    // $('li').first().css({border: "2px solid green"});  
​  
    // 给所有li中的最后一个li设置边框  
    // $('li').last().css({border: "2px solid purple"});  
​  
    // 获取 Jq对象中的第四个原生DOM对象，并设置背景颜色  
    // $('li').get(3).style.background = 'pink';  
    // 原生DOM对象不能使用 jquery 的方法  
    // $('li').get(4).css({background: 'red'});  
    // 不传递参数，会返回包含 jq对象 中的所有原生对象的数组。  
    // console.log( $('li').get() );  
​  
    // 元素遍历  
    // 遍历 jq对象 中的所有li元素  
    $('li').each(function(index, element) {  
      // this 就是每次循环的当前 li, 是原生的 this 对象  
      // console.log(this);  
      // 要使用jquery方法，需要使用 $() 函数将 this 包装成 jq对象  
      // 输出每一个li的innerHTML  
      // console.log( $(this).html() );  
      // 回调函数默认接收两个参数，这两个参数是 each 方法每次遍历时自动传进来的  
      // 第一个参数 index  每个 li 的下标  
      // 第二个参数 element 每个 li 元素  
      // console.log(index, element);  
    });  
  </script>  
​  
</body>  
</html>
```

**元素索引 index()**

index() 方法返回指定元素的相对于兄弟节点的下标，如果没有匹配的元素，则返回 -1。

该方法接收一个参数，也可以不传递参数。

**不传递参数：**返回第一个 jq 对象在它的所有兄弟节点中的位置。

**传递参数：** 返回 第一个 jq 对象在所有具有参数指定的选择器的兄弟节点中的位置。

```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel="icon" href="data:image/ico;base64,=">  
  <title>Document</title>  
</head>  
<body>  
​  
  <ul>  
    <li>列表01</li>  
    <li class="active">列表02</li>  
    <li>列表03</li>  
    <li class="active focus">列表04</li>  
    <li class="active focus">列表05</li>  
    <li class="focus">列表06</li>  
  </ul>  
    
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
    $('li').click(function() {  
      // console.log(this);  
      // 获取当前元素在所有兄弟元素中的索引值   
      // console.log( $(this).index() );  
      // 获取当前元素在所有兄弟元素中的有className为 active 的元素中的索引值, 如果当前元素自身不包含 active 类，则返回 -1  
      // console.log( $(this).index('.active') );  
      // 获取当前元素在所有兄弟元素中的有className为 focus 的元素中的索引值, 如果当前元素自身不包含 focus 类，则返回 -1  
      console.log( $(this).index('.focus') );  
    })  
​  
  </script>  
</body>  
</html>
```


### 自定义动画 animate()

animate() 方法可以创建自定义动画效果。

**参数：**animate(css, speed, easing, fn);

css : 要执行动画的css样式对象

speed : 动画速度，可以使用"slow","normal", "fast" 或 毫秒数值。

easing : 动画效果，可选值为"linear" 和 "swing（默认）"，可以通过插件扩展。

fn : 动画结束之后的回调函数（每个元素的动画结束都会执行一次）。

**执行顺序：**

同一元素的不同animate，会按照顺序执行

不同元素的animate，会同时执行

**说明：** jq 的所有动画效果都有回调函数。 （show, hide, slideDown, slideUp, fadeIn, fadeOut 等）

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    #div1,#div2 {
      width: 100px;
      height: 100px;
      background: red;
    }
    #div2 {
      background: blue;
    }
  </style>
</head>
<body>
  
  <input type="button" value="开始">
  <div id="div1"></div>
  <div id="div2"></div>

  <script src="../js/jquery/jquery-1.12.4.js"></script>
  <script>

    var $btn = $('input');
    var $div1 = $('#div1');
    var $div2 = $('#div2');

    $btn.click(function() {

      // 动画效果设置
      // 相对于 show() / hide() / slideDown() / fadeInt() ... 等简单动画，animate() 更灵活
      // 设置宽高动画，动画默认时间为 400ms 完成
      // $div.animate({width: 400, height: 400});
      // 设置宽高动画，动画时长设置为 2000ms 内完成
      // $div.animate({width: 400, height: 400}, 2000);
      // 使用字符串参数设置动画速度，可选值  'slow'   'normal'  'fast'
      // $div.animate({width: 400, height: 400}, 'normal');
      // 设置动画形式，可选值  'linear'  'swing'   可使用插件扩展更多效果
      // $div.animate({width: 400, height: 400}, 'normal', 'linear');

      // 同一个元素，多次调用 animate() 方法，会按顺序执行动画
      // $div1.animate({width: 400});
      // $div1.animate({height: 400});

      // 不同元素调用 animate() 方法，所有元素动画同时执行
      // $div1.animate({width: 400});
      // $div2.animate({height: 400});

      // 动画的回调函数： 动画执行完成之后自动调用的函数
      // $div.animate({width: 400, height: 400}, function() {
      //   console.log('动画执行结束啦~~');
      // });
      
      // 简单动画函数也都有回调函数
      // $div.hide(450, function() {
      //   console.log('元素被隐藏起来啦~~');
      // });

    })

  </script>

</body>
</html>
```


### 动画的延迟与终止

**delay() :** 在动画方法前面调用，延迟动画执行的开始时间。

参数： 表示延迟时长的毫秒数值

所有动画方法都支持 delay()。

**stop() :** 提前终止动画执行。

**参数：** 两个

第一个参数 ： 是否清空动画队列， true 清空 false 不清空

第二个参数 ： 是否让当前正在执行的动画立即完成。

true : 立即让动画跑到终点（不会有动画效果）

false: 直接结束动画 （动画执行到哪，就停止在哪）

**参数组合：**

stop(false, false)： 等价于 stop() ，停止当前动画，继续执行后续的动画。

stop(false,true)： 直接让当前动画执行到终点，继续执行后续的动画。

stop(true, true)： 清空当前动画队列， 并让当前动画直接跑到终点。

stop(ture, false)：等价于stop(true) ， 清空当前动画队列，并立即停止当前动画

```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    #div1 {
      width: 100px;
      height: 100px;
      background: red;
    }
  </style>
</head>
<body>
  
  <input type="button" value="开始">
  <input type="button" value="停止">
  <div id="div1"></div>

  <script src="../js/jquery/jquery-1.12.4.js"></script>
  <script>

    var $start = $('input:first');
    var $stop = $('input:last');
    var $div = $('#div1');

    // console.log($start, $stop);

    $start.click(function() {

      // 延迟 1000毫秒 之后再执行动画 参数为延迟的时间，单位为毫秒
      // 所有简单动画也都支持 .delay() 方法
      // $div.delay(1000).animate({width: 400});

      $div.animate({width: 400}, 1500);
      $div.animate({height: 400}, 1500);

    });

    $stop.click(function() {

      // stop()  停止动画执行
      // stop() 有两个参数：  第一个参数  是否清空动画队列   第二个参数   是否立即完成动画
      // 动画队列： 是指同一个元素多次调用  animate() 方法 ， jquery 会按动画设置顺序进行排序，然后依次执行动画。这多个动画称为动画队列。

      // 不清空动画队列，停止当前动画，继续执行后续动画，可以省略参数 即  $div.stop()
      // $div.stop(false, false);
      
      // 不清空动画队列，立即完成当前动画，继续执行后续动画
      // $div.stop(false, true);

      // 清空队列，并停止当前动画，可以简写成 $div.stop(true)
      // $div.stop(true, false);

      // 清空队列，并立即完成当前动画
      $div.stop(true, true);
    });

  </script>
</body>
</html>
```


### 动画累积

动画累积又叫动画堆叠，是指在动画还未执行完成之前，频繁触发相同动画效果产生的现象。

动画累积影响用户体验，可以通过以下两种方式优化：

1，终止旧的动画任务，开启新的动画任务

使用 stop(true) 来终止旧的动画。

2，判断动画执行的状态，如果旧动画还在执行，则不执行新的动画。

使用 :animated 状态伪类检测 （length值不为0表示动画正在执行）。

:animated 状态伪类：

jquery 会自动给正在执行动画效果的元素添加 :animated 伪类，表示该元素正在执行动画，当动画 执行结束，会自动取消 :animated 伪类。该伪类可以作为选择器来选择元素。


```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="data:image/ico;base64,=">
  <title>Document</title>
  <style>
    #div1 {
      width: 300px;
      height: 300px;
      background: red;
    }
  </style>
</head>
<body>
  
  <input type="button" value="开始">
  <div id="div1"></div>

  <script src="../js/jquery/jquery-1.12.4.js"></script>
  <script>

    var $btn = $('input:first');
    var $div = $('#div1');

    $btn.click(function() {

      // 快速连续点击，会产生动画累积，用户体验不好。
      // $div.toggle(1000);

      // 解决动画累积
      // 方式一： 先清空之前的动画队伍，并停止之前的动画，开始执行当前点击的动画
      // $div.stop(true).toggle(1000);

      // 方式二： 在动画结束之前，禁止执行新的动画
      // 使用 is() 方法 检测 $div 是否有 :animated 状态伪类
      // :animated : 当 animate() 动画在执行过程中，jquery 会自动给动画的元素添加 :animated 状态伪类，表示动画正在执行，动画结束之后，会自动移除该伪类。
      if ( $div.is(':animated') ) {
        console.log('还有动画没有执行完成，请稍等。。。');
      } else {
        $div.toggle(1000);
      }

    });

  </script>
</body>
</html>
```

# 本节练习

使用 jquery 实现完整版淘宝轮播图