title: Yeoman安装.md
date: 2014-09-11 19:51:59
tags:
---
# 在 Windows 上安装 Yeoman #
	条件：注意先能够翻墙，因为下面要下载很多东西，如果是墙外的，可能会不成功。

## 什么场景下使用yeoman？

假设，接到一个项目：火车票订票系统，代码层面，前几天思考的问题如下：

	1.项目目录该如何规划？
	2.使用什么类库来支撑系统开发？
	3.生产环境如何搭建（比如很多前端的生产环境是基于php，也有基于NodeJs）
	4.编译环境如何搭建（编译环境其实应该归到生产环境中，但前端很多人使用coffeescript/less/sass等，所以需要编译环境）
	5.单元测试环境如何搭建？
	6.调试环境如何搭建（本地代理远程assets等）
	7.开发完毕后打包部署如何处理？

我相信多数前端在项目coding前肯定都会碰上类似的问题，你是花半天、1天、2天解决？
假如你是多人合作呢？问题更严重，如何保持团队环境和代码规范的一致性？教团队成员装依赖？配置工具？大费口舌告之规范？
没做一个项目，你都会遇到相同问题，再重复一遍？
亲累不？
用yeoman！1行命名，15秒进入coding状态！
想尝试下吗？往下看~

	YO：Yeoman核心工具，项目工程依赖目录和文件生成工具，项目生产环境和编译环境生成工具
	GRUNT：grunt去年很火，前端构建工具，jquery就是使用这个工具打包的
	BOWER：Web开发的包管理器，概念上类似npm，npm专注于nodeJs模块，而bower专注于CSS、JavaScript、图像等前端相关内容的管理

**Yeoman主要有三部分组成：yo（脚手架工具）、grunt（构建工具）、bower（包管理器）**。
这三个工具是分别独立开发的，但是需要配合使用，来实现我们高效的工作流模式。
闪电般的初始化：项目开始阶段，可以基于现有的模板框架（例如：HTML5 Bolierplate、Twitter Bootstrap）进行项目初始化的快速构建。
了不起的构建流程：不仅仅包括JS、CSS代码的压缩、合并，还可以对图片和HTML文件进行优化，同时对CoffeScript和Compass的文件进行编译。
自动编译CoffeScript和Compass：通过LiveReload进程可以对源文件发生的改动自动编译，完成后刷新浏览器。
自动Lint代码：对于JS代码会自动进行JSLint测试，确保代码符合最佳编程实践。
内置的预览服务器：不再需要自己配置服务器了，使用内置的就可以快速预览。
惊人的图片优化：通过使用OptiPNG和JPEGTran来优化图片，减少下载损耗。
杀手级包管理：通过bower search jQuery，可以快速安装和更新相关的文件，不再需要打开浏览器自己搜索了。
PhantomJS单元测试：可以非常方便的使用PhantomJS进行单元测试，一切在项目初始的时候都准备好了。


## 需要安装 ##

	ruby gem compass node npm mygit git python yeoman(yo grunt bower)

须先安装git，因为bower依赖与git下载东西

### 安装 Ruby：
注意看好自己的操作系统版本，比如我的是 Win7 64 位，选的就是 Ruby 2.0.0-p195 (x64) 。
http://rubyinstaller.org/downloads/
用户变量路径：
PATH：C:\Ruby200\bin;
系统变量：
PATH：C:\Ruby200\bin;

### gem compass
Compass 是一个用来开发 CSS 的工具，因为Yeoman 启动的时候需要依赖这个工具，所以是必须安装的。
gem update --system
gem install compass
参考：http://compass-style.org/install/

### 安裝 Git for Windows 指令列工具
安裝到 Adjusting your PATH environment 步驟時，選擇 Run Git from the Windows Command Prompt 的相容性比較高，問題也會少很多：
系统变量：
PATH：C:\Program Files\Git\cmd;C:\Program Files\TortoiseGit\bin;


### 安装 NodeJS：
http://nodejs.org/download/
npm默认全局路径:
C:\Users\shangwenxue\AppData\Roaming\npm
C:\Users\shangwenxue\AppData\Roaming\npm\node_modules
npm默认的全局路径也可以设置：我建议使用默认的路径，只是知道有这么回事就行了
修改npm默认的全局路径:
npm config set prefix "C:\Program Files\nodejs\node_global" -g  对应默认的C:\Users\shangwenxue\AppData\Roaming\npm
npm config set cache "C:\Program Files\nodejs\node_cache" -g  对应默认的C:\Users\shangwenxue\AppData\Roaming\npm-cache

用户变量路径：
PATH：C:\Users\shangwenxue\AppData\Roaming\npm 对应npm的全局路径
系统变量：
PATH：C:\Program Files\nodejs\;
NODE_PATH：C:\Users\shangwenxue\AppData\Roaming\npm\node_modules  对应npm的全局路径下的node_modules

node/ node执行程序和npm模块

npm/ 默认的全局模块安装路径前缀

npm-cache/ npm安装模块的缓存目录，离线状态可以从这里读取方便安装

.npmrc 文本文件，存放npm的userconfig配置（后面会提到）
备注：我在安装时，在user/我/.npmrc  一开始存在.npmrc这文件一直安装不上去，后边删除就好了。


### 安装 python 环境：
安装教程：http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001374738150500472fd5785c194ebea336061163a8a974000
系统变量：
PATH：C:\Python34

##查看版本是否安装成功：

	ruby --version && gem --version && node --version && npm --version && git --version && python --version

###yeoman安装好后可查看：

	yo --version && bower --version && grunt --version



##安装 Yeoman：
首先安装 yo，这会自动安装 grunt, bower

	npm install -g yo
	npm install -g generator-webapp

	npm install -g yo grunt-cli bower

其中 -g 代表要把 yo , grunt-cli , bower 這三個套件安裝到全域 (global)
npm install -g yo（yo grunt-cli bower）
安裝 yo 相關的 程式碼產生器 (generator) 套件
因為 yo 這套工具主要就是用來自動產生 網站骨架 或 程式碼 ，在執行 yo 之前，你必須預先安裝好這些程式碼產生器範本，這些被稱為 YEOMAN GENERATORS ，你可以在 YEOMAN GENERATORS 找到許多現成的產生器範本，並且一樣透過 npm 進行安裝。

	npm install -g generator-mocha

例如你在 YEOMAN GENERATORS 頁面找到一個 webapp 產生器，那麼你可以用以下指令進行安裝：

	npm install -g generator-webapp

如果想安裝 angular 產生器，那麼你可以用以下指令進行安裝：

	npm install -g generator-angular

以此類推！


##创建工程:

	cd test

使用 yo 指令產生網站骨架，我們使用 webapp 這個 產生器 ( generator ) 來建立網站，指令如下：

	yo webapp

会询问我们是否使用Bootstrap和RequireJS及其它相关东西，我这里都选择了是。完成后一个Web应用的基础框架就建立好了。
添加JS库，这里添加 backbone，bower 会自动下载 underscore.

	bower install --save backbone

如果工程中需要其它类库，也可以使用命令方便的添加，例如添加 underscore：

	bower install --save underscore
	bower list(可以查看类库文件间的相互依赖关系)

	bower search jquery-ui
	bower uninstall jquery-ui

	bower install --save angular-ui-sortable
	bower install --save jquery-ui

其中 --save 选项帮助你更新 bower.jason,省却你以后手动更新的麻烦。

在app文件夹里如果总少一个bower_components 文件夹。应该是Git没装全。把Git装好后，重走一次前面的步骤，就会好了。所以，切记，先安装好Git，再装Yeoman。
初始化的WebApp目录结构如下，app目录是我们项目的主目录，test目录中对应的一些JS的单元测试文件。


##启动工程服务:

	grunt --help

這裡就定義了四個自訂工作，分別是：
| `server`  | 這個工作會包含執行其他多項工作，並且依序執行，如 clean:server, concurrent:server, …|
| `test`    | 這裡會執行該網站的相關自動化測試工作，最後一項工作則是執行 mocha 工作 ( 註: mocha 是一套 JavaScript 測試框架 )。|
| `build`   | 用來執行一連串相關工作，主要目的是將網站建置為乾淨且可佈署的檔案，包含 css, js 檔案的最小化動作，並將所有需要部屬的檔案複製到 dist 目錄下。|
| `default` | 用來定義預設的工作，也就是單純執行 grunt 指令時要執行的工作項目。|

所以，如果我們想執行 build 工作，直接輸入 grunt build 即可：
Yeoman 内置 Node 服务。启动命令

	grunt server

服务启动后会自动打开浏览器访问http://localhost:9000/（端口号可以在 gruntfile.js 中配置）

	grunt build

生成dist文件夹

###小知识点：

npm清除缓存命令：

	npm cache clean


####nodejs npm目录配置方法：

	1.输入 npm config ls -l 可以查看当前的目录设置
	2. 针对某一项设置，可以通过
	npm config set 属性名 属性值
	的方式来进行配置。
	例如:
	npm config set prefix "C:\123\"
	3. 读取某一项配置
	npm config get prefix
	nodejs npm config

#####npm的常用命令：
代码如下:

	npm install xxx 安装模块
	npm install xxx@1.1.1   安装1.1.1版本的xxx
	npm install xxx -g 将模块安装到全局环境中。
	npm ls 查看安装的模块及依赖
	npm ls -g 查看全局安装的模块及依赖
	npm uninstall xxx  (-g) 卸载模块
	npm cache clean 清理缓存
	npm help xxx  查看帮助
	npm view moudlename dependencies  查看包的依赖关系
	npm view modulenames  查看node模块的package.json文件夹
	npm view modulename labelname  查看package.json文件夹下某个标签的内容
	npm view modulename repository.url  查看包的源文件地址
	npm view modulename engines   查看包所依赖的node的版本
	npm help folders   查看npm使用的所有文件夹
	npm rebuild modulename    用于更改包内容后进行重建
	npm outdated   检查包是否已经过时，此命令会列出所有已经过时的包，可以及时进行包的更新
	npm update modulename   更新node模块


参考：[http://www.tuicool.com/articles/ENbI7j3](http://www.tuicool.com/articles/ENbI7j3)
[http://chuo.me/2013/02/twitter-bower.html](http://chuo.me/2013/02/twitter-bower.html)
[http://www.36ria.com/6144](http://www.36ria.com/6144)
[http://yeoman.io/learning/](http://yeoman.io/learning/)
[http://blog.fens.me/series-nodejs/](http://blog.fens.me/series-nodejs/)
[http://yeoman.io/learning/resources.html](http://yeoman.io/learning/resources.html)


##运行过程的全部命令：

###1、运行start command prompt with ruby:

	gem update --system
	gem install compass

上面命令产生文件在 C:\Ruby200\bin 这个文件夹底下能够找到对应的


###2、运行node.js command prompt：

	ruby --version && gem --version && node --version && npm --version && git --version && python --version

	npm install -g yo grunt-cli bower
	npm install -g generator-webapp
	npm install -g generator-mocha
	npm install -g generator-angular

	yo --version && bower --version && grunt --version

上面命令产生文件在 C:\Users\shangwenxue\AppData\Roaming\npm 这个文件夹底下能够找到对应的

###3、运行node.js command prompt：

	cd test
	yo webapp
	bower install --save backbone
	bower install --save underscore
	bower install --save angular-ui-sortable
	bower install --save jquery-ui
	grunt --help
	grunt server
	grunt build

上面命令产生文件在 D:\test及D:\test\bower_components 这个文件夹底下能够找到对应的