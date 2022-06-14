### skew（倾斜函数）
- `skew(angle)`代表在水平方向上倾斜变换，相当于`skewx(angle)`
- `skew(x-angle,y-angle)`表示沿着x轴和y轴倾斜转换,相当于设置 `skewx(角度)`h和 `skewy(角度)`。

### scale（缩放函数）
**默认是以中心点为基点缩放，可以用`transform-origin`属性更改缩放基点。**
- `scale(x-angle,y-angle)`宽度和高度的缩放
	- `scale(2)`表示宽度和高度都变为原来的两倍。
	- `scale(2,1）`表示宽度变为原来的两倍，高度不变。
	- `scale(0)`会实现隐藏的效果
	- `scale(-1)`会实现水平和垂直反转，宽度和高度不改变。
- `scale3d(x-angle,y-angle,z-angle)` 复合写法
	- `scalex(angle)`单独设置x轴的缩放，即宽度。
	-  `scaley(angle)`单独设置y轴的缩放，即高度。
	- `scalez(angle)`单独设置z轴的缩放，即厚度。
  
### rotate（旋转函数）
**默认是以中心点为旋转缩放，可以用`transform-origin`属性更改缩放基点。**
- `rotate`只支持写一个值，正值顺时针，负值逆时针
### translate（偏移函数）
### perspective


