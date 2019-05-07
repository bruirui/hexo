---
title: css3动画
urlname: article10
date: 2018-08-29 16:50:46
tags: css
---

> animation
  transform
  transition

1. animation用法
设置动画属性，包含6个属性:
<font color="#9e845a">animation: name duration timing-function delay iteration-count direction paly-state fill-mode;</font>
		animation-name: 动画名称;
		animation-duration: 动画时长;
		animation-timing-function: 动画速度曲线(linear);
		animation-delay: 延迟时长;
		animation-iteration-count: 动画播放次数(infinite);
		animation-direction: 动画播放方向(normal | alternate轮流);
		animation-paly-state: 动画的播放状态(running继续 | paused暂停);
		animation-fill-mode: 动画结束后元素样式(none回到动画最开始状态 | forwards停留在动画结束状态 | backwards回到动画第一帧状态 | both根据direction轮流应用forward和backward规则)

2. transform用法
用于元素进行旋转，缩放，移动或倾斜:
<font color="#9e845a">transform: translate(x,y) scale(x[,y]?) rotate(angle) skew(angle) perspective(n);</font>
		translate：移动
		scale：缩放
		rotate：旋转
		skew：倾斜
		perspective：定义透视视图

3. transition用法
设置元素的样式过度:
<font color="#9e845a">transtion: property duration timing-function delay;</font>
		transtion-propery: 设置过度效果的css属性名称
		transtion-duration: 设置完成过度效果需要的时间
		transtion-timing-fucntion: 设置完成动画的速度曲线
		transtion-delay: 设置过度效果何时开始
