title: 无线页面的一点点小总结.md
date: 2014-09-28 19:18:36
tags:
---
#无线页面的一点点小总结

总结两个方面：
1. css3
1. js-iscroll

##css3
从几个代表的部分展开分析css3
- logo部分
- top布局部分
- 图标部分　@font-face

###logo部分
	先说一下`background-size`,随带说一下`background-clip`与`box-sizing`

> [示例demo](http://codepen.io/pleasureswx123/pen/vIeox) `background-size`,`background-clip`与`box-sizing`

	background-size: contain | cover | inherit

`contain` 等比，完全保留全部的底图，把完整的底图放进去展现出来，可能会留白，可能会铺不完全，以图为基准，只要把完整的图放进去目的就达到了
底图等比（放大或缩小）且完整的呈现在box中

![](http://i.imgur.com/CeKNORi.png)

`cover` 等比，填满，不留空白，超出的隐藏，把完整的框全部用底图铺满，不会留白，以框为基准，只要把框全部用图覆盖满了就行，不留空白死角
box会被底图全部填满，底图同样等比（放大或缩小），但底图超出的部分会被隐藏不显示。

![](http://i.imgur.com/I30XsEJ.png)

如果框的大小与底图的大小是等比例的，那么 `background-size: contain | cover | 100%` ;这时候这三者是一样的效果。

	background-clip: border-box | padding-box | content-box  //从什么位置（边缘）开始填充底图

`border-box` 　 从border的外界边缘开始填充底图

![](http://i.imgur.com/UeOUkVO.png)    ![](http://i.imgur.com/8d805bx.png)

`padding-box` 　从padding的外界边缘开始填充底图

![](http://i.imgur.com/lwEzRLA.png)    ![](http://i.imgur.com/gyn0Lfr.png)

`content-box` 　从content的外界边缘开始填充底图

![](http://i.imgur.com/4HGH6MH.png)    ![](http://i.imgur.com/Ez92Pi6.png)

	box-sizing: border-box | padding-box | content-box 盒子的大小，是包含padding呢，border呢，还是content呢

 `border-box` 意思是　width = contentWidth + padding + border;
![](http://i.imgur.com/y5VQdLD.png)   ![](http://i.imgur.com/HD8SJ2w.png)

 `padding-box` 意思是 width = contentWidth + padding;　　-webkit-box-sizing: padding-box; -webkit不支持padding-box;

![](http://i.imgur.com/87NkJDE.png)  chrome(-webkit) 版本 37.0.2062.120 暂时还不支持padding-box;

 `content-box` 意思是　width = contentWidth;

![](http://i.imgur.com/5YxLyek.png)   ![](http://i.imgur.com/JSazoay.png)


###top布局部分
	display: box; 	box-flex: 1;
	`box-orient` 	`box-direction` 	`box-pack` 	`box-align`

 [box && box-flex](http://codepen.io/pleasureswx123/pen/gvjhi) `box-orient` `box-direction` `box-align` `box-pack`

	`box-orient: horizontal | vertical`  轴，确定是到底哪个轴，是水平轴还是垂直轴

![](http://i.imgur.com/USCiFL2.png)

	`box-direction: normal | reverse`　轴的方向，是正向还是逆向

![](http://i.imgur.com/WAY6zo0.png)

	`box-pack: start | end| center | justify;` 轴上的位置，是居左居右居中还是两端对齐
box-pack的方向与box-orient的方向是相同的一致的

![](http://i.imgur.com/V0lFei8.png)

	`box-align: start | end | center | baseline | stretch;` 相反的轴上的位置，是居左居右居中还是两端对齐
box-align的方向与box-orient的方向是相反的不一致的

![](http://i.imgur.com/kKXURkH.png)

由box-pack与box-align实现居中会很容易，box-pack与box-align的方向受box-orient与box-direction的影响。

###图标部分　@font-face
- 自己绘制图标字体，参考　[自制矢量图标转换成字体](http://pleasureswx123.github.io/2014/09/04/fontfaceIcon/)　文章。
- 由其它网站（如：[icomoon](https://icomoon.io/)  [fortawesome](http://fortawesome.github.io/Font-Awesome/)）及其类似的网站，别人制好的库里筛选自己想的图标字体


	[class^="baikeicon-"], [class*=" baikeicon-"] {
		font-family: 'icomoon';
		speak: none;
		font-style: normal;
		font-weight: normal;
		font-variant: normal;
		text-transform: none;
		line-height: 1;

		/* Better Font Rendering =========== */
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}

	.baikeicon-home:before {
		content: "\e60c";
	}

添加class的值，通过伪类:before的content给标签加图标内容，标签对应的字符，如下图（下载下来的demo），可以自己去定义要用的字符。

![](http://i.imgur.com/c9eOSj0.png)



##iscroll
参考文档：　[iscroll4](http://www.gafish.net/api/iScroll.html)

结束
