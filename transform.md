### skew（倾斜函数）
- `transform:skew(angle);`代表在水平方向上倾斜变换，相当于`transform:skewx(angle);`
- `transform:skew(x-angle,y-angle);`表示沿着x轴和y轴倾斜转换,相当于设置 `transform:skewx(角度);`h和 `transform:skewy(角度);`。

### scale（缩放函数）
**默认是以中心点为基点缩放，可以用`transform-origin:`属性更改缩放基点。该属性的属性值可以是具体的像素值，也可以是top,center,bottom,left,right等。**
例如：
	`transform-origin:left top;`
	`transform-origin:20px 30px;`
- `transform:scale(x-angle,y-angle);`宽度和高度的缩放
	- `transform:scale(2);`表示宽度和高度都变为原来的两倍。
	- `transform:scale(2,1);`表示宽度变为原来的两倍，高度不变。
	- `transform:scale(0);`会实现隐藏的效果
	- `transform:scale(-1);`会实现水平和垂直反转，宽度和高度不改变。
- `transform:scale3d(x-angle,y-angle,z-angle);` 复合写法
	- `transform:scalex(angle);`单独设置x轴的缩放，即宽度。
		- `transform:scalex(-1);`水平方向反转
	-  `transform:scaley(angle);`单独设置y轴的缩放，即高度。
		- `transform:scaley(-1);`垂直方向反转
	- `transform:scalez(angle);`单独设置z轴的缩放，即厚度。
  
### rotate（旋转函数）
**默认是二维平面以中心点为基点旋转，可以认为是该二维平面沿着三维空间的z轴进行旋转，可以用`transform-origin:`属性更改旋转基点。**
- `transform:rotate(angle);`只支持写一个值，正值会顺时针旋转，负值会逆时针旋转。
	- `transform:rotatex(angle);`视角在正上方，沿着二维平面的x轴旋转
	- `transform:rotatey(angle);`表示沿着二维平面的y轴旋转
### translate（偏移函数）
### perspective


