title: 在github上用hexo搭建博客
date: 2014-08-29 17:41:41
categories: hexo
tags:
---
##搭建hexo博客

- 安装Git
- 安装Node.js
- 安装hexo
- 创建hexo文件夹
- 安装依赖包
- 到此安装完成，本成看效果
- 注册Github账号
- 创建repository，查看github page页面
- 部署 将hexo与github page关联，并替换github page效果
- 完成部署

###安装Git
下载 [msysgit](http://msysgit.github.io/) 并执行即可完成安装。

###安装Node.js
在 Windows 环境下安装 [Node.js](http://nodejs.org/) 非常简单，仅须下载安装文件并执行即可完成安装。

###安装hexo
新建文件夹（如：myblog），在文件夹里点击右键－选择git bash，如下图：
![Alt text](/img/hexoblog/01.png)
执行下面命令，通过npm的install命令在全局系统下安装hexo，参数 -g 即为在全局安装

    npm install -g hexo

###创建hexo文件
在文件夹myblog里，执行

    hexo init

此时myblog文件夹里就自动生成了一些文件，如下图：
![Alt text](/img/hexoblog/02.png)

###安装依赖包
执行以下命令：

    npm install

此时hexo的依赖文件也安装上去了，如下图：
![Alt text](/img/hexoblog/03.png)

###到此安装完成，本成看效果
现在我们已经搭建起本地的hexo博客了，执行以下命令：

    hexo generate
    hexo server

然后到浏览器输入localhost:4000看看效果，效果如下图：
![Alt text](/img/hexoblog/04.png)

好了，至此，本地博客已经搭建起来了，只是本地哦，别人看不到的。下面，我们要部署到Github。

###注册Github账号
已有账号可以跳过，没有的，请[在此](https://github.com/)进行注册，很简单的，这里就不介绍了。

###创建repository，查看github page页面
在自己Github主页右下方，创建一个新的repository。
![Alt text](/img/hexoblog/05.png)
![Alt text](/img/hexoblog/06.png)
![Alt text](/img/hexoblog/07.png)
![Alt text](/img/hexoblog/08.png)
![Alt text](/img/hexoblog/09.png)
![Alt text](/img/hexoblog/10.png)
查看github page页面 http:// `username` .github.io/，如下图我的效果
![Alt text](/img/hexoblog/11.png)

###部署 将hexo与github page关联，并替换github page效果
编辑_config.yml文件

    deploy:
    type: github
    repository: 地址
    branch: master

repository 地址在，看下图：
![Alt text](/img/hexoblog/12.png)

编辑如下图：
![Alt text](/img/hexoblog/13.png)

###完成部署
执行下列指令即可完成部署，

    hexo generate
    hexo deploy

到此全部完成。

注意：以下所有命令行的操作都在 myblog文件夹内执行如：
![Alt text](/img/hexoblog/14.png)

###tips

hexo现在支持更加简单的命令格式了，比如：

hexo g == hexo generate
hexo d == hexo deploy
hexo s == hexo server
hexo n == hexo new

###特别提醒
更换主题的时候，在_config.yml里设置主题的名字是有大小写之分的,
当你对所用主题做了修改时，应进行如下操作以便能看到你想要的结果

    rm -rf public
    hexo clean  ##这条命令找到半天，费了不少劲

然后再

    hexo g
    hexo s  或 hexo d

_config.yml

    # Hexo Configuration
    ## Docs: http://hexo.io/docs/configuration.html
    ## Source: https://github.com/tommy351/hexo/

    # Site #整站的基本信息
    title: 1000 words a Day #网站标题
    subtitle: Writing 1000 Words a Day Changes My Life #网站副标题
    description: 学习总结 思考感悟 知识管理 #网站描述
    author:  cnFeat #网站作者，在下方显示
    email: cnFeat@gmail.com #联系邮箱
    language: zh-CN

    # URL
    ## If your site is put in a subdirectory
    url: http://www.cnfeat.com #你的域名
    root: /
    permalink: :year/:month/:day/:title/
    tag_dir: tags
    archive_dir: archives
    category_dir: categories
    code_dir: downloads/code

    # Directory
    source_dir: source
    public_dir: public

    # Writing
    new_post_name: :title.md # File name of new posts
    default_layout: post
    auto_spacing: false # Add spaces between asian characters and western characters
    titlecase: false # Transform title into titlecase
    external_link: true # Open external links in new tab
    max_open_file: 100
    multi_thread: true
    filename_case: 0
    render_drafts: false
    post_asset_folder: false
    highlight:
      enable: true
      line_number: true
      tab_replace:

    # Category & Tag
    default_category: uncategorized
    category_map:
    tag_map:

    # Archives
    ## 2: Enable pagination
    ## 1: Disable pagination
    ## 0: Fully Disable
    archive: 2
    category: 2
    tag: 2

    # Server
    ## Hexo uses Connect as a server
    ## You can customize the logger format as defined in
    ## http://www.senchalabs.org/connect/logger.html
    port: 4000
    server_ip: 0.0.0.0
    logger: false
    logger_format:

    # Date / Time format
    ## Hexo uses Moment.js to parse and display date
    ## You can customize the date format as defined in
    ## http://momentjs.com/docs/#/displaying/format/
    date_format: YYYY-MM-DD
    time_format: H:mm:ss

    # Pagination
    ## Set per_page to 0 to disable pagination
    per_page: 15 #每页15篇文章
    pagination_dir: page

    # Disqus #社会化评论disqus，我使用多说，在主题中配置
    disqus_shortname:

    # Extensions
    ## Plugins: https://github.com/tommy351/hexo/wiki/Plugins
    ## Themes: https://github.com/tommy351/hexo/wiki/Themes
    theme: jacman
    exclude_generator:
    Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap

    #sitemap
    sitemap:
      path: sitemap.xml

    #Feed Atom
    feed:
      type: atom
      path: atom.xml
      limit: 20

    # Markdown
    ## https://github.com/chjj/marked
    markdown:
      gfm: true
      pedantic: false
      sanitize: false
      tables: true
      breaks: true
      smartLists: true
      smartypants: true

    # Stylus
    stylus:
      compress: false

    # Deployment
    ## Docs: http://hexo.io/docs/deployment.html
    deploy:
      type: github
      repository: https://github.com/cnfeat/cnfeat.github.io.git
      branch: master

页面展现的全部逻辑都在每个主题中控制，源代码在hexo\themes\主题\中

    .
    ├── languages  #多语言
    |   ├── default.yml#默认语言
    |   └── zh-CN.yml  #中文语言
    ├── layout #布局，根目录下的*.ejs文件是对主页，分页，存档等的控制
    |   ├── _partial   #局部的布局，此目录下的*.ejs是对头尾等局部的控制
    |   └── _widget#小挂件的布局，页面下方小挂件的控制
    ├── source #源码
    |   ├── css#css源码
    |   |   ├── _base  #*.styl基础css
    |   |   ├── _partial   #*.styl局部css
    |   |   ├── fonts  #字体
    |   |   ├── images #图片
    |   |   └── style.styl #*.styl引入需要的css源码
    |   ├── fancybox   #fancybox效果源码
    |   └── js #javascript源代码
    ├── _config.yml#主题配置文件
    └── README.md  #用GitHub的都知道

用hexo发表新文章

    $ hexo n #写文章

###Hexo命令

常用命令：

    hexo new "postName" #新建文章
    hexo new page "pageName" #新建页面
    hexo generate #生成静态页面至public目录
    hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
    hexo deploy #将.deploy目录部署到GitHub

常用复合命令：

    hexo d -g #生成加部署
    hexo s -g #预览加部署
简写：

    hexo n == hexo new
    hexo g == hexo generate
    hexo s == hexo server
    hexo d == hexo deploy

安装插件
添加sitemap和feed插件

    $ npm install hexo-generator-sitemap
    $ npm install hexo-generator-feed

修改_config.yml，增加以下内容

    # Extensions
    Plugins:
    - hexo-generator-feed
    - hexo-generator-sitemap

    #Feed Atom
    feed:
      type: atom
      path: atom.xml
      limit: 20

    #sitemap
    sitemap:
      path: sitemap.xml

Hexo上传README文件
Github的版本库通常建议同时附上README.md说明文件，但是hexo默认情况下会把所有md文件解析成html文件，所以即使你在线生成了README.md，它也会在你下一次部署时被删去。怎么解决呢？

在执行hexo deploy前把在本地写好的README.md文件复制到.deploy文件夹中，再去执行hexo deploy。

###参考
[如何搭建一个独立博客——简明Github Pages与Hexo教程](http://jianshu.io/p/05289a4bc8b2?comment=24686)
[hexo系列教程](http://zipperary.com/2013/06/02/hexo-guide-5/)
[Hexo在github上构建免费的Web应用](http://blog.fens.me/hexo-blog-github/)

常见问题1：出现问题时，先把gitbash关闭掉，然后重新找开试试，可能就好了。
常见问题2：[更换主题常见的问题](http://www.huangyunkun.com/2014/07/31/hexo-update-error-with-yaml-parser/)
常见问题3：`hexo deploy`没反应，有可能问题出在config.yml的deploy配置上。注意`缩进`，同时注意冒号后面要有`一个空格`。


结束！











