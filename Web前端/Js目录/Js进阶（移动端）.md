# JavaScript进阶 第五天


## touch 事件

触屏事件，只要是能与屏幕产生互动，就会产生触屏事件。

touchstart 触屏开始事件

touchend 触屏结束事件

touchmove 触屏并滑动时触发的事件

touchcancel 触屏事件被终止时触发的事件

移动端设备也会触发鼠标的 mousedown 、mouseup、click、dblclick 等事件，但会比触屏事件延迟300~500毫秒左右（参考值）执行。
```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
​  
  <h2>hello world</h2>  
  <p>前端开发</p>  
​  
<script>  
​  
// console.log(123);  
​  
  // 触屏事件  
  // 触屏开始事件 （手指点到屏幕就立即触发）  
  document.ontouchstart = function() {  
    console.log('ontouchstart');  
  }  
​  
  // 触屏结束事件 （手指离开屏幕就立即触发）  
  document.ontouchend = function() {  
    console.log('ontouchend');  
  }  
​  
  // 触屏移动事件  （手指在屏幕滑动时连续触发）   高频事件  
  document.ontouchmove = function() {  
    console.log('ontouchmove');  
  }  
​  
  // // 系统自动触发的事件  （当 touchstart  touchend 被中断时触发发，比如切换应用界面，来电话等）  
  // document.ontouchcancel = function() {  
  //   console.log('ontouchcancel');  
  // }  
​  
  // 鼠标事件      所有鼠标事件都会有 300~500 毫秒 左右的延迟， 这是特意设计成这样，并不是BUG  
​  
  // 手指点击到屏幕立即触发，但会在延迟300~500毫秒左右时间之后再调用事件处理函数  
  document.onclick = function() {  
    console.log('onclick');  
  };  
  document.onmousedown = function() {  
    console.log('onmousedown');  
  };  
  document.onmouseup = function() {  
    console.log('onmouseup');  
  };  
  document.ondblclick = function() {  
    console.log('ondblclick');  
  };  
​  
</script>  
</body>  
</html>
```

事件穿透：使用鼠标相关事件，有可能会产生事件穿透。为了避免事件穿透，不要将鼠标事件与触屏事件混用。
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
  <style>  
    .box1 {  
      width: 80%;  
      height: 150px;  
      background: red;  
    }  
    .box2 {  
      width: 200px;  
      height: 100px;  
      background: green;  
      position: absolute;  
      top: 50px;  
      left: 50px;  
    }  
  </style>  
</head>  
<body>  
    
  <div class="box1"></div>  
  <div class="box2"></div>  
​  
  <script>  
​  
    var box1 = document.querySelector('.box1');  
    var box2 = document.querySelector('.box2');  
​  
    // 移动端鼠标事件的事件穿透问题  
    // 原因在 移动端的鼠标事件有延迟  
    // 只能避免，不能修复 ，因为本身就不算BUG。  
    // 为避免出现事件穿透，当有元素重叠，并且都有绑定事件处理函数时，必须保证要么都用鼠标事件，要么都用touch事件，不要混用。  
    // box1.onclick = function() {  
    //   console.log('box1   onclick');  
    // }  
    box1.ontouchstart = function() {  
      console.log('box1   ontouchstart');  
    }  
​  
    box2.ontouchstart = function() {  
      console.log('box2   ontouchstart');  
      this.style.display = 'none';  
    }  
​  
    // box2.onclick = function() {  
    //   console.log('box2   onclick');  
    //   this.style.display = 'none';  
    // }  
​  
    /*   
      当两个元素重叠时，只有上一个元素使用 touch 事件， 下面的元素使用鼠标事件，才会有事件穿透问题。  
    */  
  </script>  
​  
</body>  
</html>
```


## touch 事件对象中的属性

touches 包含所有触摸点信息的类数组对象

touchend 事件中的 touches 始终为空数组。

changedTouches包含所有变化的触摸点信息的类数组对象

touches 和 changedTouches类数组中保存的是每一个触摸点的信息：

clientX / clientY : 触点相对于可视区左上角的坐标

pageX / pageY : 触点相对于文档左上角的坐标

screenX / pageY : 触点相对于屏幕左上角的坐标
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
      
<h2>hello</h2>  
​  
<script>  
  document.ontouchstart = function(ev) {  
    // touch 事件中的事件对象也是事件处理函数中的第一个参数  
    // console.log(ev);  
​  
    // 包含触发事件时的所有触点（所有手指点的位置）相关信息的类数组对象  
    // console.log(ev.touches);  
​  
    // 包含所有在事件触发时新增或减少的触点的相关信息的类数组对象  
    // （如在事件触发前，有两个手指已经点击在屏幕上了，再使用另外两个手指点击到屏幕上时，changedTouches中保存的是新增的另外的两个手机触点的相关信息）  
    // 通常情况下，两个手指不太可能分毫不差地同时点击到屏幕，因此 changedTouches 对象中总是只会保存最近的一个新增或减少的触点信息  
    // console.log(ev.changedTouches);  
​  
    // 第一个触点的坐标信息  
    // console.log(ev.touches[0].clientX, ev.touches[0].clientY);  
​  
    // 最近新增的触点的坐标信息  
    // console.log(ev.changedTouches[0].clientX, ev.changedTouches[0].clientY);  
​  
  };  
​  
  document.ontouchend = function(ev) {  
    // touchend 事件中的 touches 没有触点信息  
    // console.log(ev.touches);  
    // console.log(ev.touches[0]);  
​  
    // changedTouches 中保存的一定是 触发 touchend 事件的那个触点信息  
    console.log(ev.changedTouches);  
    console.log(ev.changedTouches[0]);  
  }  
​  
</script>  
</body>  
</html>
```


## 过渡动画事件与关键帧动画事件

PC端 和 移动端 的过渡动画和关键帧动画都会触发事件。

**过渡动画事件：**

transitionstart 过渡动画开始时触发的事件

transitionend 过渡动画结束时触发的事件

**关键帧动画事件：**

animationstart 关键帧动画开始时触发的事件

animationend 关键帧动画结束时触发的事件
```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
  <style>  
    div {  
      width: 100px;  
      height: 100px;  
      background: red;  
      transition: all 5s;  
      animation: move .5s 5;  
    }  
​  
    @keyframes move {  
      from {  
        transform: translateY(0px);  
      }  
      50% {  
        transform: translateY(100px);  
      }  
      to {  
        transform: translateY(0px);  
      }  
    }  
  </style>  
</head>  
<body>  
    
  <div></div>  
​  
  <script>  
​  
    // 通过 getElementsByTagName() 方式获取，得到的是一个类数组对象  
    var div = document.getElementsByTagName('div')[0];  
​  
    div.onclick = function() {  
      // console.log(1111);  
      this.style.width = '500px';  
    };  
​  
    // 过渡动画开始执行立即触发的事件  
    // div.addEventListener('transitionstart', function() {  
    //   console.log('开始动起来了')  
    // });  
​  
    // 过渡动画执行结束立即触发的事件  
    // div.addEventListener('transitionend', function() {  
    //   console.log('到终止点啦')  
    // });  
​  
    // 关键帧开始执行时触发的事件  
    // div.addEventListener('animationstart', function() {  
    //   console.log('开始动起来了')  
    // });  
​  
    // 关键帧执行结束时触发的事件  （如果关键帧的动画次数设置为 Infinite ，将不会触发 animationend 事件）  
    // div.addEventListener('animationend', function() {  
    //   console.log('到终止点啦')  
    // });  
  </script>  
</body>  
</html>
```

## 移动端 JS 类库 -- zepto

zepto 是一个仿照 jquery 实现的一个移动端优先的JS类库，不兼容低版本IE。

GitHub 地址： [https://github.com/madrobby](https://github.com/madrobby/zepto)[/](https://github.com/madrobby/zepto)[zepto](https://github.com/madrobby/zepto)

zepto 将不同功能模块单独封装，需要时才引用，可以减少文件总体积大小，加速访问。

**常用事件：**

**tap**：触碰 **singleTap**: 单击 **longTap**: 长按

**doubleTap**: 双击 **swipe**: 滑动 **swipeLeft**: 左滑动

**swipeRight:** 右滑动 **swipeUp:** 上滑动 **swipeDown:** 下滑动

跟jquery 一样，事件可以通过 .on(type) 或 .type() 方式绑定
```js
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
  <style>  
    div {  
      width: 300px;  
      height: 300px;  
      background: red;  
    }  
  </style>  
</head>  
<body>  
​  
  <div></div>  
​  
  <!-- 要注意模块的引入顺序，核心模块必须最先引入 -->  
  <!-- 引入核心模块 -->  
  <script src="js/zepto.js"></script>  
  <!-- 引入事件模块 -->  
  <script src="js/event.js"></script>  
  <!-- 引入触屏模块 -->  
  <script src="js/touch.js"></script>  
  <script>  
​  
    // 因为 jquery 和 Zepto 都使用 $() 函数， 所以如果同一个页面同时使用 jquery 和 zepto 那么引入时，先引入的将不能使用  $() 函数名称   
    // jquery 先引入，需要使用 jQuery 作为函数名称调用  如： jQuery('#div1');   
    // Zepto 先引入，需要使用 Zepto 作为函数名称调用  如： Zepto('#div1');   
​  
    // Zepto 跟 jquery 一样，也使用 $() 来获取元素并返回类数组对象  
    // console.log( $('div') );  
​  
    // $('div').css({  
    //   backgroundColor: 'pink'  
    // });  
​  
    // 使用 .on() 方式绑定事件  
​  
    // $('div').on('click', function() {  
    //   console.log('click');  
    // });  
​  
    // $('div').on('touchstart', function() {  
    //   console.log('touchstart');  
    // });  
​  
    // 使用快捷方式绑定事件  
​  
    // $('div').on('tap', function() {  
    //   console.log('tap');  
    // });  
​  
    // $('div').tap(function() {  
    //   console.log('tap');  
    // });  
​  
    // 滑动事件     只要滑动就会触发  
    $('div').swipe(function() {  
      console.log('swipeRight');  
    });  
​  
    // 右滑事件     只有往右滑动才会触发  
    $('div').swipeRight(function() {  
      console.log('swipeRight');  
    });  
​  
    // 其他事件同理，  如  swipeLeft() 只有往左滑动才会触发    
​  
  </script>  
</body>  
</html>
```

## 面向对象介绍

面向对象是一种编程思想，与之相对的是面向过程。

与模块化思想类似，面向对象也是将所有公共的方法提前封装，目的在于提高代码的开发效率，降低维护成本。

面向对象是以对象形式将所有的属性和方法都封装到一个对象中。

**例：**

var person = {

name: "小明",

age: 18,

say: function() {

console.log("我叫" + this.name + "，今年" + this.age + "岁");

}

}
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
<script>  
​  
  // 普通方式保存数据  
  // var name = '小明';  
  // var age = 18;  
  // var say = function() {  
  //   console.log('我叫' + name + ', 今年' + age + '岁了。');  
  // };  
​  
  // console.log(name);  
  // console.log(age);  
  // say();  
​  
  // 对象形式保存数据  
  var person = {  
    name: "小明",  
    age: 18,  
    say: function() {  
      console.log('我叫' + this.name + ', 今年' + this.age + '岁了。');  
    }  
  };  
​  
  console.log( person.name );  
  console.log( person.age );  
  person.say();  
​  
  // 面向对象 是一种开发思想。 是将所有数据都保存到一个特定对象中，以对象形式开发的一种开发模式。  
</script>  
​  
</body>  
</html>
```

## 构造函数

构造函数是指专门用来创建对象实例的函数。

为了区别普通函数，构造函数的首字母都约定为大写。

**定义：**

构造函数的定义与普通函数相同，只是函数名称首字母要大写

**调用：**

构造函数使用 new 关键字调用 ，具体格式 new 构造函数名称();
```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
    
<script>  
​  
// 创建普通对象    
// var person = {  
//   name: "小明",  
//   age: 18,  
//   say: function() {  
//     console.log('我叫' + this.name + ', 今年' + this.age + '岁了。');  
//   }  
// };  
​  
// 普通对象不够灵活，如果需要创建多个结构相同的对象，需要重复编写相同代码  
​  
​  
// 普通函数方式创建对象  
// function createPerson(name, age) {  
//   var person = {  
//     name: name,  
//     age: age,  
//     say: function() {  
//       console.log('我叫' + this.name + ', 今年' + this.age + '岁了。');  
//     }  
//   };  
​  
//   return person;  
// }  
​  
// 普通函数方式创建对象并没有什么问题， 以普通函数方式创建对象，是以面向过程的思维方式开发。  
​  
// 构造函数方式创建对象，是以面向对象的思维方式开发。  
​  
// var xiaoming = createPerson('小明', 18);  
// var xiaohong = createPerson('小红', 16);  
// console.log(xiaoming, xiaohong);  
​  
// 构造函数的方式创建对象  
function CreatePerson(name, age) {  
  this.name = name;  
  this.age = age;  
  this.say = function() {  
    console.log('我叫' + this.name + ', 今年' + this.age + '岁了。');  
  };  
​  
  // console.log(this.name);  
}  
​  
// 普通方式调用函数， 函数内部的 this 指向window对象  
// window.name = '小明'  
// var xm = CreatePerson('小明', 18);  
// window.name = '小红'  
// var xh = CreatePerson('小红', 16);  
​  
// console.log(xm.name);  
// xm.say();  
// console.log(this.name)  
​  
// 通过 new 关键字调用  
// var xm = new CreatePerson('小明', 18);  
// var xh = new CreatePerson('小红', 16);  
​  
// console.log(xm.name);  
// xm.say();  
</script>  
</body>  
</html>
```


## new 关键字

new 关键字用来调用执行构造函数，在执行构造函数时，new 会执行以下操作：

1，创建一个空对象

2，将函数内部的 this 指向这个空对象。

3，执行构造函数中的代码。

4，将 this 作为 return 的默认值返回。

使用 new 关键字调用构造函数时， return 关键字不能再返回简单数据类型的值，所有简单数据类型的值都会被直接忽略。
```js
<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
  <meta charset="UTF-8">  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Document</title>  
</head>  
<body>  
    
<script>  
​  
// 函数内部的注释表示 使用 new 关键字调用函数时，new 的执行过程，并不是实际开发时需要编写的代码。  
function CreatePerson(name, age) {  
  // 1, new 在函数内部创建了一个空对象  
  // var obj = {};  
​  
  // 2， new 会将 this 指向创建的 空对象 （将this由window改成了空对象）  
  // this = obj;  
​  
  // 3，执行代码，将所有属性和方法添加到 this 对象上 （等同于添加到空对象中）。  
  this.name = name;  
  this.age = age;  
  this.say = function() {  
    console.log('我叫' + this.name + ', 今年' + this.age + '岁了。');  
  };  
  // 4, new 会自动将 this 为作返回值返回 (等同于 return obj)。  
  // return this;  
}  
​  
// 普通的直接使用 () 调用  
// 普通方式调用函数， 函数内部的 this 指向 window ，如果函数内部使用 this 添加数据，只有最后一次调用的数据会被最终保存。  
// var xm = CreatePerson('小明', 18);  
// var xh = CreatePerson('小红', 16);  
​  
// 通过 new 关键字调用  
// new 关键字调用函数，因为每次 new 都会创建一个新的对象，所以每次调用的数据都能被保存起来。  
var xm = new CreatePerson('小明', 18);  
var xh = new CreatePerson('小红', 16);  
​  
// console.log()  
// console.log(xm);  
// console.log(xh);  
​  
// 构造函数必须通过 new 关键字调用。  
console.log(xm.name);  
console.log(xh.age);  
xm.say();  
xh.say();  
</script>  
​  
</body>  
</html>
```


## 构造函数中的 return

如果一个函数是通过 new 关键字调用的，那么这个函数就是一个构造函数，与函数的首字母是否大写无关。

构造函数中的 return ，如果返回简单数据类型的值，会被直接忽略，如果返回的是复杂数据类型的值，会替换 由 new 创建的对象，作为函数的返回值。
```js
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  
<script>

// 一个函数是不是构造函数，不取决于函数名称的首字母是否大写，而是取决于是否通过 new 关键字调用。
// 函数名称首字母大写只是开发人员之间的一种约定。

function CreatePerson(name, age) {
  this.name = name;
  this.age = age;
  this.say = function() {
    console.log('我叫' + this.name + ', 今年' + this.age + '岁了。');
  };
  // 使用 new 关键字调用函数，函数内部的return 不能再返回简单数据类型的值。
  // return 123;
  // return 'abc';

  // 一般不会修改 构造函数的 return ，因为有可能导致构造函数的功能失效。
  // 可以返回复杂数据类型的值
  // return {a: 123, b: 456};
  // return function() { console.log(123) };
}

// 不使用 new 关键字调用 ， 就是一个普通函数调用， this 是 window 对象。
// var xm = CreatePerson('小明', 18);
// var xh = CreatePerson('小红', 16);

// 通过 new 关键字调用 ， 是一个构造函数， this 是由 new 创建的对象。
var xm = new CreatePerson('小明', 18);
var xh = new CreatePerson('小红', 16);


console.log(xm);
console.log(xh);

// console.log(xm.name);
// console.log(xh.age);
// xm.say();
// xh.say();
</script>
</body>
</html>
```

