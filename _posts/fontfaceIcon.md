title: fontfaceIcon
date: 2014-09-04 14:15:45
tags:
---
##简单说一下如何制作一个图标字体文件及css @fontface运用

主要有两个方面来进行简单的描述一下：

* fontface css
* fontface 图标 family 的制作生成

###fontface描述
> css属性 有几种不同的字体格式 每种相应的对应不同浏览器间的差异，详细了解：[font-face介绍](http://www.cn-sass.com/content/css3-font-face)
> 浏览器差异代码

    @font-face {
        font-family: 'YourWebFontName';
        src: url('YourWebFontName.eot'); /* IE9 Compat Modes */
        src: url('YourWebFontName.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
        url('YourWebFontName.woff') format('woff'), /* Modern Browsers */
        url('YourWebFontName.ttf')  format('truetype'), /* Safari, Android, iOS */
        url('YourWebFontName.svg#YourWebFontName') format('svg'); /* Legacy iOS */}

###fontface图标字体的制作与生成
> 用到的工具AI,fontforge

- 图标的制作
- 图标字体的生成

####图标的制作
用AI做一个大小512X512的黑白图标，格式svg

![Alt text](/img/fontfaceIcon/01.png)

####图标字体的生成
- 下载fontforge
- 打开fontforge.bat文件

![Alt text](/img/fontfaceIcon/02.png)

![Alt text](/img/fontfaceIcon/03.png)

![Alt text](/img/fontfaceIcon/04.png)

![Alt text](/img/fontfaceIcon/05.png)

![Alt text](/img/fontfaceIcon/06.png)

![Alt text](/img/fontfaceIcon/07.png)

![Alt text](/img/fontfaceIcon/08.png)

![Alt text](/img/fontfaceIcon/09.png)

![Alt text](/img/fontfaceIcon/10.png)

> 到此制作成了一个字体并且只包含一个图标的名称为addfont的字体，格式为ttf，通过webfont-generator将这个字体生成其它相关格式的字体。

![Alt text](/img/fontfaceIcon/11.png)

![Alt text](/img/fontfaceIcon/12.png)

![Alt text](/img/fontfaceIcon/13.png)

到此`@font-face`所需要的字体文件都有了
结束

