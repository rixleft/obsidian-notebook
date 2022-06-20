## GFC（网格布局格式化上下文）

- `GFC(GridLayout Formatting Contexts)`直译为"**网格布局格式化上下文**"（是CSS3.0的新增布局：所以该属性的兼容性问题较大），当为一个元素设置`display`为`grid`的时候，此元素将会获得一个独立的渲染区域，即块级元素，当为一个元素设置`display`为`inline-grid`的时候，此元素将会获得一个行内块元素的渲染区域。

| 属性                    | 描述                                                           |
| ----------------------- | -------------------------------------------------------------- |
| `grid-template`         | 是复合写法                                       |
| `grid-auto-rows`        | 指定行的自动尺寸                                               |
| `grid-template-rows`    | 定义网格布局中的行的数量                                       |
| `grid-auto-columns`     | 指定列的自动尺寸                                               |
| `grid-template-columns` | 定义网格布局中的列的数量                                       |
| `grid-template-areas`   | 用于设置网格布局                                               |
| `grid-auto-flow`        | 指定自动布局怎么运作，精准指定在网格中被自动布局的元素怎么运作 |
| `grid-gap`              | 设置网格单元格之间的间隙，是行和列的复合写法，                                                               |
| `grid-row-gap`          | 设置网格列之间的间隙                                           |
| `grid-column-gap`       | 设置网格行之间的间隙                                           |

- `grid-template`是一种复合写法
	-   `grid-template-rows`定义容器的行属性
		- `grid-template-rows:1 / 3;`是指从盒子的左边的起始边线开始，指跨越了几条纵向边线。
			- `grid-column-start:`指盒子的边从第几条纵线开始计算，
				- `number;`可以为负值。
				- `span number;`也可以写跨越了几列，
			- `grid-column-end:number;`指盒子的边从第几条纵线开始计算，可以为负值。
		- `grid-template-rows：40px;`指每列的宽度为40px。
		- `grid-template-rows:40px 1fr;`指第一列的宽度为40px，其余每列占除去40px之外的空间，每列占据1份。
	-   `grid-template-columns`
	-  `grid-template-areas`