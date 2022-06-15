| 属性                        | 描述                             |
| --------------------------- | -------------------------------- |
| `animation`                 | 复合属性                         |
| `animation-name`            | 指定要绑定的选择器的关键帧的名称 |
| `animation-duration`        | 动画的持续时间                   |
| `animation-delay`           | 设置动画在启动前的延迟间隔时间   |
| `animation-timing-function` | 设置动画将何如完成一个周期       |
| `animation-iteration-count` | 设置动画的播放次数               |
| `animation-play-state`      | 指定动画是否正在运行或已停止     |
| `animation-fill-mode`       | 规定到动画不播放或已完成时的状态                                 |
| `animation-direction`       | 指定是否应该轮流反向播放动画                                 |


- `animation`
	- 复合写法对上述属性不都要求有顺序，但持续时间和延迟时间，总是持续时间在前，延迟时间在后，其余并无顺序。
- `animation-name`  
	- 制定了要绑定到选择器的关键帧的名称
- `animation-duration`
	- 指定了动画的持续时间，默认值为0，意味着无动画效果。
- `animation-delay` 
	- 定义了动画从多长时间内后开始执行，表示动画的延迟时间，它的值在复合属性写法下，默认是在持续时间之后。
- `animation-timing-function`
	- `linear`  动画从头到尾的速度都是相同的
	- `ease` 默认值， 动画以低速开始，然后加快，在结束前变慢。
	- `ease-in` 动画以低速开始。
	- `ease-out` 动画以低速结束
	- `ease-in-out` 
	- `steps(number,start|end)`