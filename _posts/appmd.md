title: app.md
date: 2014-09-12 14:25:57
tags:
---
#制作APP过程
## 在node上安装cordova ##

	1 C:\>npm install -g cordova //安装
	2 $ cordova create hello com.example.hello HelloWorld //创建一个helloworld的APP
	3 $ cd hello //进入APP
	4 $ cordova platform add android  //添加android平台

就OK了,它自动生成的有很多文件,主要改底下有一个www目录下的文件，在前端的任何编辑下打开编辑就行了。

做好后，打包的话，先运行

	$ cordova build

这个命令行，是把你刚刚编辑的前端代码，自动编译成android语言，会自动替换到android目录，

再用usb把手机连接到电脑上，最后再运行

	$ cordova run android

然后手机上就会自动把这个应用安装到手机上了

