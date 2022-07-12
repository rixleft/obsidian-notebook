# JavaScript进阶 第三天


## 获取元素尺寸

**clientWidth / clientHeight :**

元素的可视区宽高尺寸 （如果有滚动条，不包括滚动条尺寸）

**offsetWidth / offsetHeight ：**

设置了宽高样式： width / height + padding + border

没有设置宽高样式： clientWidth / clientHeight + border + 滚动条尺寸

**clientLeft / clientTop ：**

元素的左边和上边边框宽度

**注意：** 只有支持宽高设置的元素，以上属性的取值才会准确。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
  <link rel="icon" href="data:image/x-icon;base64,=">  
  <style>  
    #div1 {  
      border: 10px solid #333;  
      width: 300px;  
      height: 200px;  
      background: pink;  
      padding: 20px;  
      margin: 30px;  
      /* overflow: hidden; */  
      overflow: auto;  
      /* display: none; */  
      /* visibility: hidden; */  
      /* display: inline; */  
      /* display: inline-block; */  
    }  
    /* webkit 内核浏览器 自定义滚动条的样式 */  
    /* ::-webkit-scrollbar {  
      width: 10px;  
      background-color: red;  
      height: 5px;  
    }  
    ::-webkit-scrollbar-button {  
      background-color: orange;  
    }  
    ::-webkit-scrollbar-corner {  
      background-color: green;  
    }  
    ::-webkit-scrollbar-thumb {  
      background: purple  
    } */  
    #div1 p {  
      width: 600px;  
    }  
  </style>  
</head>  
<body>  
    
  <div id="div1">  
    <p>乡传谷到弄得灰为着首五洪司易到等，尝你以不你葬保，不是马就不罪见圣母们姑过妄，么司而的孔反者办故才才在牛通，乌自学投也在落必措，而洪虽人，会国姑连也恩位给知他故将，定身求罪好向这，关李未当则人起于哥快乐，游他恨招身责原十认有和是的君地，思他秦过何么今，烦丰卅便何而实尝否自灰憾没为中报，不李绪已才思，连担骂怒骨仍恶打杀融土杂人读，我仆极自王劫文，人杀在一自谢善第了安了友虽为人国文是，领官的薪句救书，饮力身君台哥，而他下实文学其二力劝为瞠你圣在王氏，两洪一派互逃人受玉场秦领韩，大不大法死木白对笔人便大国找么他尝打谓，没叩判屯燕玉然仍妙下赐责前的是弟，洋得此大里司俭但罚水而人法光后作次，夹者故已皇，者的越同老道派归关，恨回欲慨仍临之而以，来后讨不不书夫你不的故，了有的罪子被我非非变有在恩，一妙光了心了首褒何人，后今虑总尺，策德收丈略才密血才而回那服属房今里，下是何母考人变领乐你郭后者己，畴盲虽互会中不若量骂着是一老马人月，下手洪子云挟何则这以大后，得是一才卑，风自平负中身训谢，出收历样中，上者是，国词使人，事的王啊韩脱谋皇的小，不揽受普王是杀情我中不其如只，了身乐脱着在打的曾婵向，母何夭乐千内，拢永妄先上仅如法，三法厄病才的答仓一文反处生，兄我谭让实着入卅上次我谢落饮胜疾，弟年到爱已徒文害入杨守之全留，知非我然一朗的洋洞着珍二嗣赠定主榜未量，第智我活韩和付将洪后话常君，修金司，尝的褒贤。</p>  
  </div>  
​  
  <script>  
    var div1 = document.getElementById('div1');  
​  
    // 可视区： 可以看到内容的区域 （不包括滚动条的尺寸）  
​  
    // clientWidth : 元素的可视区宽度  
    // clientHeight : 元素的可视区高度  
    console.log(div1.clientWidth, div1.clientHeight);  
​  
    // offsetWidth  
    // 设置了 width 样式： width + padding + border  
    // 没有设置 width 样式： clientWidth + 滚动条宽度 + border  
    // offsetHeight   
    // 设置了 height 样式： height + padding + border  
    // 没有设置 height 样式： clientHeight + 滚动条高度 + border  
    console.log(div1.offsetWidth, div1.offsetHeight);  
​  
    // 元素左边框和上边框的值  
    console.log(div1.clientLeft, div1.clientTop);  
​  
    /*   
    注意： 只有支持宽高设置的元素，以上属性的取值才会准确。  
​  
      当设置 display: none; 时：  
        clientWidth / clientHeight / offsetWidth / offsetHeight /  
        clientLeft / clientTop 的值都为 0  
​  
      当设置 display: inline 时：  
        clientWidth / clientHeight / clientLeft / clientTop 的值都为 0  
​  
        offsetWidth / offsetHeight 在不同浏览器中的值也不相同。  
    */  
  </script>  
</body>  
</html>
```


## 获取元素位置

**offsetParent:** 元素的最近的一个有定位属性的祖先元素。

1，如果所有元素都没有定位属性，默认为 body 元素。

2，body 元素没有 offsetParent。

3，在IE7及以下版本中，元素自身必须有定位属性，若自身没有定位属性： offsetParent === parentNode

**offsetLeft:** 元素的左外边框到定位父级的左内边框之间的距离

**offsetTop:** 元素的上外边框到定位父级的上内边框之间的距离

**注意：** ie6/7下 margin-top 与 padding-top 会重叠。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <!-- <meta http-equiv="X-UA-Compatible" content="IE=edge"> -->  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel='icon' href='data:image/x-icon;base64,='>  
  <title>Document</title>  
  <style>  
    div {  
      border: 10px solid #333;  
      padding: 20px;  
      margin: 30px;  
    }  
    /* html {  
      position: relative;  
    }  
    body {  
      position: relative;  
      position: absolute;  
    } */  
    #div1 {  
      width: 300px;  
      height: 300px;  
      background: pink;  
      position: relative;  
      /* position: absolute; */  
      /* position: fixed; */  
      /* position: sticky; */  
    }  
    #div2 {  
      width: 200px;  
      height: 200px;  
      background: orange;  
      /* position: relative; */  
    }  
    #div3 {  
      width: 100px;  
      height: 100px;  
      background: red;  
      position: relative;  
    }  
  </style>  
</head>  
<body>  
    
  <div id="div1">  
    <div id="div2">  
      <div id="div3"></div>  
    </div>  
  </div>  
​  
  <script>  
​  
    var div3 = document.getElementById('div3');  
​  
    /*   
      offsetParent:  元素的最近的一个有定位属性的祖先元素。  
​  
        1，如果所有元素都没有定位属性，默认为 body 元素。   
        2，在IE7及以下版本中，元素自身必须有定位属性，若自身没有定位属性： offsetParent === parentNode  
        3，body 元素没有 offsetParent。  
        4，在 标准浏览器和 IE11 以上浏览器中，如果元素因为 display: none; 属性被隐藏，则 offsetParent 为null。  
        5，webkit 内核和 ie7及以上版本IE浏览器中，offsetParent 为null。  
    */  
    // console.log(div3.offsetParent);  
    // console.log(div3.offsetParent.id);  
    // console.log(document.body.offsetParent);  
​  
    /*   
      offsetLeft: 元素的左外边框到定位父级的左内边框之间的距离  
      offsetTop: 元素的上外边框到定位父级的上内边框之间的距离  
​  
      注意： ie6/7下 margin-top 与 padding-top 会重叠。  
    */  
    console.log( div3.offsetLeft, div3.offsetTop);  
​  
  </script>  
</body>  
</html>
```


## 页面与元素的滚动尺寸

滚动尺寸： 指滚动条滚动的距离。

**页面滚动条：**

标准浏览器 window.scrollX / window.scrollY

标准和ie9以上浏览器 window.pageXoffset / window.pageYoffset

IE7、8 ： document.documentElement 的 scrollLeft / scrollTop

IE 6 : document.body 的 scrollLeft / scrollTop

**元素滚动条：**

元素.scrollLeft / 元素.scrollTop
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel='icon' href='data:image/x-icon;base64,='>  
  <title>Document</title>  
  <style>  
    body {  
      height: 3000px;  
      width: 2000px;  
    }  
    #div1 {  
      width: 300px;  
      height: 200px;  
      border: 10px solid #333;  
      background: pink;  
      overflow: auto;  
    }  
    #div1 p {  
      width: 400px;  
    }  
  </style>  
</head>  
<body>  
    
​  
  <div id="div1">  
    <p>支貂首失国久仆人派定，郭但力天设前他之侯哉陀，秦勇仅斯的自念将不我手事通要仄呼大如，送畴越在决大怎况，在讨见以太愿是而非秦为定系都啦交，生你德是性天作事么不，惊归善妙流竟临人起制匹化自郭，子必娘躲你才在呼时韩盲将让土韩君，娘皇作冇玉留，为举才当内同国已，自郭生上他才舟第愚韩法变尚永感负的，登后也善失韩山狂许徨圣，然感他与可，者国人有，娘派毒与生苟派到便投的尝到方张，令自于，千到力治偶乐说人你的场后别畴感当送的，郭仃不入土以有之智把会，把快因的不方否中作举大事为答，能定为洪决出君不们撒若惊在到日生长太，弟得生，吞我因是，已才磊畴太若讨平么孔五，王国办所远觉，天道卞何穿情为办互又定釜我未，爱你洪面明，对而陀徒十非，三关谭到其光范笔国对年出姑，郭定不案战谢憾五仃妙服怎穿是快韩，未才实没，骂太善家锐章的，得价那我动大洪，尚十谭招不派也呼承李这，下无为母明战兴的才回下极生官新保语书仄，乌斗老不位愿谷好杨倒才张骨艳怎前白韩介，德有法褒专肯，了入因就哥是子读司你即此皇到兼时己起，特训绪笔落有极，后气罪范那越时家苟别嗣否，五帮样求骨事同必落，尤答对是锐骨有帮可在通心是先，秦的下仃血其后揽专人君友，养。</p>  
  </div>  
​  
  <script>  
    var div1 = document.getElementById('div1');  
​  
    document.onclick = function() {  
​  
      // 浏览器窗口的滚动条尺寸获取   有兼容问题  
​  
      // IE7 以上和标准浏览器中通过 DOM 获取滚动尺寸  
      // console.log(document.documentElement.scrollTop);  
      // console.log(document.documentElement.scrollLeft);  
      // IE6以下的滚动条只能由子元素的内容撑起来  
​  
      // 标准浏览器中获取页面滚动距离 （IE浏览器不支持）  
      // console.log(window.scrollX, window.scrollY);  
      // 标准和IE9以上浏览器获取页面滚动距离（包括IE9）  
      // console.log(window.pageXOffset, window.pageYOffset);  
      // console.log(window.scrollLeft, window.scrollTop);  
​  
      // IE 6 以下通过 document.body 获取  
      // IE 7 8 可以通过 document.documentElment 获取  
​  
      // 兼容处理  
      var pageX = window.pageXOffset || document.documentElement.scrollLeft || document.body.scrollLeft;  
      var pageY = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;  
​  
      console.log(pageX, pageY);  
    };  
​  
    div1.onclick = function() {  
      // 元素的滚动条尺寸获取  没有兼容问题  
      // console.log(this.scrollLeft, this.scrollTop);  
    };  
​  
  </script>  
</body>  
</html>
```


## 页面滚动与缩放事件

**滚动事件：**

window.onscroll

**缩放事件：**

window.onresize

scroll 和 resize 都是高频触发事件。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel='icon' href='data:image/x-icon;base64,='>  
  <title>Document</title>  
  <style>  
    body,html {  
      height: 3000px;  
    }  
  </style>  
</head>  
<body>  
    
<script>  
  var count = 0;  
​  
  // window.onscroll = function() {  
  //   console.log("scroll", count ++);  
  // };  
​  
  // window.onresize = function() {  
  //   console.log("resize", count ++);  
  // };  
​  
  document.onscroll = function() {  
    // document 对象也可以触发 scroll 事件  
    console.log("scroll", count ++);  
  };  
​  
  document.onresize = function() {  
    // document 对象无法触发 resize 事件  
    console.log("resize", count ++);  
  };  
​  
  /*   
    1，这两个事件属于 BOM 事件.  
    2，在IE9以上和标准浏览器中，document对象也可以触发 scroll 事件。  
  */   
​  
</script>  
</body>  
</html>
```


## jQuery 的尺寸与位置方法

**width() ：** 计算后样式 width 的值 （getComputed().width）

**height() :** 计算后样式 height 的值 (getComputed().height)

**innerWidth() ：** 包含滚动条的 clientWidth 值

**innerHeight ():** 包含滚动条的 clientHeight 值

**outerWidth() :** 默认获取的是 innerWidth + 边框

outerWidth(true) 传递参数 true , 会额外加上margin的值

**outerHeight() :** 默认获取的是 innerHeight + 边框

outerHeight(true) 传递参数 true , 会额外加上margin的值

**position() :** 元素的外边距到 offsetParent的内边距之间的距离 （{left: 0, top: 0}）

该方法对于 display: none; 和 position: fixed; 的元素计算不准确

**offset() :** 元素的外边距到整个文档的左边或顶边之间的距离 （{left: 0, top: 0}）

该方法对设置了 display: none; 的元素无效。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel='icon' href='data:image/x-icon;base64,='>  
  <title>Document</title>  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <style>  
    div {  
      border: 10px solid #333;  
      padding: 20px;  
      margin: 30px;  
    }  
    html {  
      position: relative;  
    }  
    body {  
      position: relative;  
      position: absolute;  
    }  
    #div1 {  
      width: 300px;  
      height: 300px;  
      background: pink;  
      position: relative;  
      /* position: absolute; */  
      /* position: fixed; */  
      /* position: sticky; */  
      /* display: none; */  
    }  
    #div2 {  
      width: 200px;  
      height: 200px;  
      background: orange;  
      position: relative;  
    }  
    #div3 {  
      width: 100px;  
      height: 100px;  
      background: red;  
      /* position: relative; */  
      /* display: none; */  
      /* position: fixed; */  
      /* visibility: hidden; */  
      overflow: auto;  
    }  
    #div3 p {  
      width: 600px;  
    }  
  </style>  
</head>  
<body>  
    
  <div id="div1">  
    <div id="div2">  
      <div id="div3">  
        <p>啊才服榜承而吾王，一对后久讨六，洪哉偶作者壬给何屯对唯无在陈老易保起，是设内手说衣德服大后孔感怒一，是娘千其常徒大国要这，训子了洪掸妄关不，视是也出们和不家法平易人秦事是谋持，勉是可动了才量生皇过心我君，老就畴斗感文举不洪天，年韩无郭洪他航才磊我对，仑马的新哉司原司鲜如听游不却少一份出，是才不可游了，说以釜力在她一哉性虑，重服保订盲方互壬山回言也杨爱为用，冇说弄认中王国，恨倒救罪间能，家愚尘吴，者死便是只将了国是为而音在马，这洪恶而让俭感十登必则程太之一游，非妙对看必价是略颜，司又高非，低土圣快是出光，今卡天九他在么措他帅竟六，得俭人情实锐，才修身了，仆对上，不完他甲负揽罪烦今韩郭活，说无人的同家了你，司死仍够生司己慨罚担人降哥尝可仍皇杂那，生给之德罚仑法遗这在倒答，的对下秦为开只专李尹沾绪弟保会中，变手爱其出，见道好样赏诗恨灰备措之，人连才赐人留是洞感得弟笔何落，十人惶打尤十，订连失略是磊君，的之尘的畴终书责，志国平狱赠我车事国气杨活，娇郭秦，子身国程，是不的以文完谢自是赠都卡故次，罪我千训薪足接韦知领说揽并屯融是可留，法令丑尘谋，救笔上胆杀，文生招向师畴小，自磊招友国郭评韩，故得一蒲绝，当文量会人了足弟责光那，送杨欲留弄王一，保言定虽的者光愚皇上自订光上着恼位九，到五洪连谓然，谓楚张我李只切感道，定血下了卞出四念使官，此只能有的得在人，名千新学仅土不匹冇的介的花，负送生认，不。</p>  
      </div>  
    </div>  
  </div>  
​  
  <script>  
    var $div1 = $('#div3');  
​  
    // console.log($div1.width());  
    // 包含滚动条的 clientWidth  
    // console.log($div1.innerWidth());  
    // console.log($div1[0].clientWidth);  
    // 默认获取的是 innerWidth + 边框  
    // console.log($div1.outerWidth());  
    // 传递参数 true , 会额外加上margin的值  
    // console.log($div1.outerWidth(true));  
​  
    // 元素到 offsetParent 之间的距离  
    // 该方法对于 display: none; 和 position: fixed; 的元素计算不准确   
    // （有这两种样式的元素本身就不应该使用这个方法）  
    // console.log($div1.position());  
​  
    // 元素到整个文档的左边或顶边之间的距离  
    // 该方法对设置了 display: none; 的元素无效。  
    console.log($div1.offset());  
​  
  </script>  
</body>  
</html>
```

## 封装 offset() 函数
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <!-- <meta http-equiv="X-UA-Compatible" content="IE=edge"> -->  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel='icon' href='data:image/x-icon;base64,='>  
  <title>Document</title>  
  <style>  
    body {margin: 0;}  
    div {  
      border: 10px solid #333;  
      padding: 20px;  
      margin: 30px;  
    }  
    #div1 {  
      width: 300px;  
      height: 300px;  
      background: pink;  
      position: relative;  
      /* position: absolute; */  
      /* position: fixed; */  
      /* position: sticky; */  
      /* display: none; */  
    }  
    #div2 {  
      width: 200px;  
      height: 200px;  
      background: orange;  
      position: relative;  
    }  
    #div3 {  
      width: 100px;  
      height: 100px;  
      background: red;  
      /* position: relative; */  
      /* display: none; */  
      /* position: fixed; */  
    }  
  </style>  
</head>  
<body>  
    
  <div id="div1">  
    <div id="div2">  
      <div id="div3"></div>  
    </div>  
  </div>  
  <script src="../js/jquery/jquery-1.12.4.js"></script>  
  <script>  
​  
    var div3 = document.getElementById('div3');  
​  
    console.log( getPos(div3) );  
​  
    // console.log(div3.getBoundingClientRect())  
​  
    console.log( $(div3).offset() );  
​  
    var docEle = document.documentElement;  
    // console.log(docEle.clientLeft);  
    console.log(getComputedStyle(document.body)['margin-top']);  
​  
    function getPos(obj) {  
      // 声明初始化对象  
      var pos = {top: 0, left: 0};  
​  
      if ( !obj || obj.nodeType !== 1 ) return null;  
      // 判断 obj 是否有 offsetParent   
      while (obj.offsetParent) {  
        // 先计算 obj 到 offsetParent 之间的距离  
        pos.left += obj.offsetLeft;  
        pos.top += obj.offsetTop;  
​  
        // 再计算父级的边框尺寸  
        // 这里是将 obj 重新赋值为自己的 offsetParent   
        // 目的是为了获取 offsetParent 的边框尺寸 （有点绕，需要多思考理解）   
        obj = obj.offsetParent;  
        pos.left += obj.clientLeft;  
        pos.top += obj.clientTop;  
      }  
​  
      // 返回计算结果  
      return pos;  
    }  
​  
  </script>  
</body>  
</html>
```

## 实例效果： 拖拽

拖拽的三个事件：

mousedown : 鼠标按下的时候开始准备拖拽

mousemove : 鼠标移动的时候，进行拖拽

mouseup : 鼠标抬起来的时候，终止拖拽

关键知识：

获取鼠标坐标：

clientX / clientY

计算鼠标点击位置与元素边框之间的距离：

ev.offsetX / ev.offsetY
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel='icon' href='data:image/x-icon;base64,='>  
  <title>Document</title>  
  <style>  
    #div1 {  
      width: 100px;  
      height: 100px;  
      background: red;  
      position: absolute;  
      left: 200px;  
      top: 150px;  
      border: 30px solid #333;  
    }  
  </style>  
</head>  
<body>  
​  
  <div id="div1"></div>  
​  
  <script>  
    var div1 = document.getElementById('div1');  
​  
    div1.onmousedown = function(ev) {  
      var ev = ev || event;  
​  
      // 拖拽元素的 left值： 鼠标到浏览器边缘的距离 - 鼠标到元素边缘的距离  
​  
      // 计算鼠标与元素外边框之间的距离   
      var offsetX = ev.offsetX + this.clientLeft;  
      var offsetY = ev.offsetY + this.clientTop;  
​  
      // 鼠标移动事件绑定在元素上，移动过快指针脱离元素范围会导致出BUG  
      // 绑定在 document 对象上，就不会有移动过快的BUG了  
      document.onmousemove = function(ev) {  
      // div1.onmousemove = function(ev) {  
        var ev = ev || event;  
​  
        // 计算元素的 left 与 top  
        var left = ev.clientX - offsetX;  
        var top = ev.clientY - offsetY;  
​  
        // 鼠标，实时更新div的left 与 top  
        div1.style.left = left + 'px';  
        div1.style.top = top + 'px';  
      };  
​  
      // 鼠标抬起时，注销掉移动事件，mouseup 事件本身就是为了注销移动事件，注销完移动事件之后，就没有作用了，所以也可以同时注销（不注销 mouseup 事件，对拖拽效果没有影响，但会有内存占用）。  
      // （mousemove事件会在下一次 mousedown 事件时重新绑定）  
      document.onmouseup = function() {  
        document.onmousemove = null;  
        document.onmouseup = null;  
      };  
​  
    };  
​  
  </script>  
</body>  
</html>
```

## 限制范围的拖拽

限制范围的原理：

让元素只能在定位父级的可视区域内拖拽。

主要知识点：

1，不限制范围的拖拽效果原理

2，获取限制父级的尺寸

3，获取滚动尺寸
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <link rel='icon' href='data:image/x-icon;base64,='>  
  <title>Document</title>  
  <style>  
    #div1 {  
      width: 100px;  
      height: 100px;  
      background: red;  
      position: absolute;  
      left: 200px;  
      top: 150px;  
    }  
    .box {  
      width: 500px;  
      height: 400px;  
      border: 10px solid #333;  
      margin: 100px;  
      position: relative;  
    }  
  </style>  
</head>  
<body>  
    
  <div class="box">  
    <div id="div1"></div>     
  </div>  
​  
​  
  <script>  
    var div1 = document.getElementById('div1');  
​  
    div1.onmousedown = function(ev) {  
      var ev = ev || event;  
​  
      var offsetX = ev.offsetX + this.clientLeft;  
      var offsetY = ev.offsetY + this.clientTop;  
​  
      // 获取定位父级的外边框到文档边缘之间的距离  
      var pos = getPos(this.offsetParent);  
      // 获取定位父级的边框宽度  
      pos.left += this.offsetParent.clientLeft;  
      pos.top += this.offsetParent.clientTop;  
​  
      document.onmousemove = function(ev) {  
        var ev = ev || event;  
        var docEle = document.documentElement,  
            body = document.body;  
          // 获取滚动宽度  
        var scrollX = window.pageXOffset || docEle.scrollLeft || body.scrollLeft;  
          // 获取滚动高度  
        var scrollY = window.pageYOffset || docEle.scrollLeft || body.scrollTop;  
          // 计算拖拽元素的 left 值  
        var left = ev.clientX + scrollX - pos.left - offsetX;  
          // 计算拖拽元素的 top 值  
        var top = ev.clientY + scrollY - pos.top - offsetY;  
          // 计算拖拽元素最大可以拖拽的移动宽度  
        var iWidth = div1.offsetParent.clientWidth - div1.offsetWidth;  
          // 计算拖拽元素最大可以拖拽的移动高度  
        var iHeight = div1.offsetParent.clientHeight - div1.offsetHeight;  
​  
        // 限制拖拽的允许范围  
        if (left < 0) {  
          left = 0;  
        }  
        if (top < 0) {  
          top = 0;  
        }  
​  
        if (left > iWidth) {  
          left = iWidth;  
        }  
​  
        if (top > iHeight) {  
          top = iHeight;  
        }  
​  
        div1.style.left = left + 'px';  
        div1.style.top = top + 'px';  
      };  
​  
      document.onmouseup = function() {  
        document.onmousemove = null;  
        document.onmouseup = null;  
      };  
​  
    };  
​  
    function getPos(obj) {  
      var pos = {top: 0, left: 0};  
​  
      if ( !obj || obj.nodeType !== 1 ) return null;  
​  
      while (obj.offsetParent) {  
        pos.left += obj.offsetLeft;  
        pos.top += obj.offsetTop;  
​  
        obj = obj.offsetParent;  
        pos.left += obj.clientLeft;  
        pos.top += obj.clientTop;  
      }  
      return pos;  
    }  
​  
  </script>  
</body>  
</html>
```

## 放大镜效果
```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel='icon' href='data:image/x-icon;base64,='>
  <title>Document</title>
  <style>
    body {margin: 0;}
    #div1 {
      width: 200px;
      height: 200px;
      background: red;
      position: absolute;
      left: 200px;
      top: 150px;
      opacity: .5;
      display: none;
    }
    .box {
      width: 450px;
      height: 450px;
      border: 10px solid #333;
      margin: 100px;
      position: relative;
      background-image: url(images/thumb.jpg.avif);
    }
    .zoom {
      width: 550px;
      height: 550px;
      border: 1px solid #ccc;
      position: absolute;
      display: none;
      background-image: url(images/zoom.jpg.avif);
    }
  </style>
</head>
<body>
  
  <div class="box">
    <div id="div1"></div>

  </div>
  <div class="zoom"></div>

  <script>
    var div1 = document.getElementById('div1');
    var box = document.getElementsByClassName('box')[0];
    var zoom = document.getElementsByClassName('zoom')[0];
    var imgSize = {
      width: 800,
      height: 800
    };

    box.onmouseenter = function(ev) {
      var ev = ev || event;
      
      div1.style.display = 'block';
      div1.style.cursor = 'move';

      var disX = ev.clientX;
      var disY = ev.clientY;

      var pos = getPos(div1.offsetParent);
      pos.left += div1.offsetParent.clientLeft;
      pos.top += div1.offsetParent.clientTop;

      // 初始化并显示大框架的位置
      zoom.style.left = box.offsetLeft + box.offsetWidth + 'px'; 
      zoom.style.top = box.offsetTop + 'px'; 
      zoom.style.display = 'block';

      box.onmousemove = function(ev) {
        var ev = ev || event;
        // 浮动小方块的坐标
        var left = ev.clientX - pos.left - div1.offsetWidth / 2;
        var top = ev.clientY - pos.left - div1.offsetHeight / 2;
        // 浮动小方块可以活动的最大范围
        var iWidth = div1.offsetParent.clientWidth - div1.offsetWidth;
        var iHeight = div1.offsetParent.clientHeight - div1.offsetHeight;

        if (left < 0) { left = 0; }
        if (top < 0) { top = 0; }

        if (left > iWidth) { left = iWidth; }
        if (top > iHeight) { top = iHeight; }

        div1.style.left = left + 'px';
        div1.style.top = top + 'px';

        // 大图可以活动的范围
        var iW = imgSize.width - zoom.clientWidth;
        var iH = imgSize.height - zoom.clientHeight;

        // 小方块活动范围 与  大图活动范围的比例关系 
        // 横向 （小方块当前的 left / 最大活动范围 iWidth == 大图当前的背景位置x / 大图的活动范围 iW ）
        // 纵向同理
        var scaleX = iWidth / iW;
        var scaleY = iHeight / iH;

        // 使用比例关系来计算大图的背景定位位置
        zoom.style.backgroundPositionX = -left * scaleX + 'px';
        zoom.style.backgroundPositionY = -top * scaleY + 'px';
      };

      box.onmouseleave = function() {
        div1.style.display = 'none';
        zoom.style.display = 'none';
        document.onmousemove = null;
        box.onmouseleave = null;
      };

    };

    function getPos(obj) {
      var pos = {top: 0, left: 0};

      if ( !obj || obj.nodeType !== 1 ) return null;

      while (obj.offsetParent) {
        pos.left += obj.offsetLeft;
        pos.top += obj.offsetTop;

        obj = obj.offsetParent;
        pos.left += obj.clientLeft;
        pos.top += obj.clientTop;
      }
      return pos;
    }

  </script>

</body>
</html>
```

## 返回顶部

效果：

当滚动高度达到一顶距离时，显示按钮

比如 scrollY > 300 时

动画：

使用 jquery 实现动画效果

防抖：

使用延迟定时器解决防抖问题
```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    body {
      height: 7000px;
    }
    #box {
      width: 100px;
      height: 100px;
      font-size: 40px;
      background: red;
      text-align: center;
      line-height: 1.2;
      color: #fff;
      position: fixed;
      right: 50px;
      bottom: 50px;
      display: none;
    }
  </style>
</head>
<body>
  
  <div id="box">返回顶部</div>

  <script src="../js/jquery/jquery-1.12.4.js"></script>
  <script>
    var box = document.getElementById('box');
    var timer = null;

    window.onscroll = function() {
      var pageY = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
console.log( $(window).scrollTop() )

      // if (pageY > 300) {
      //   // box.style.display = 'block';
      // } else {
      //   box.style.display = 'none';
      // }

      // 防抖一
      // if ( !$(box).is(':animated') ) {
        
      //   if ( $(window).scrollTop() > 300) {
      //     $(box).stop(true).fadeIn();
      //   } else {
      //     $(box).stop(true).fadeOut();
      //   }          
      // }

      // 防抖二
      clearTimeout(timer);
      timer = setTimeout(() => {
        if ( $(window).scrollTop() > 300) {
          $(box).stop(true).fadeIn();
        } else {
          $(box).stop(true).fadeOut();
        }        
      }, 300);

    }

    box.onclick = function() {
      // 没有动画效果
      // window.scroll(0,0);

      // 添加动画效果
      $(document.documentElement).animate({scrollTop: 0}, 1500);
    };

  </script>
</body>
</html>
```