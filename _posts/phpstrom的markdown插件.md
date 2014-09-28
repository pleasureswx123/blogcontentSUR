title: phpstrom的markdown插件
date: 2014-08-29 17:39:12
categories: phpstrom
tags:
---
###PhpStorm 安装插件有两种方式：

- 使用 PhpStorm 自带的 plugin repository 进行安装，安装方式较简单，推荐
- 先下载插件安装包，使用 PhpStorm 加载本地安装包的方式，进行安装，适用于安装插件库中没有的插件

####使用Browse repositories安装 Markdown 插件
PhpStorm plugin repository 字面上很容易理解，主要用于管理 PhpStorm 插件：禁用，下载和安装。
进入 PhpStorm 插件库：

    菜单栏 `File` -> `Setting` -> `Plugins` -> `Browse repositories...`

我们先搜索一下是否有 markdown 插件：

    在右边搜索框中输入：`markdown`
    结果列表中显示 Markdown v.0.9.1
    右键点击 Download and install

接下来我们就可以关闭设置窗口，等待自动下载安装完成吧。

安装完成后编辑器底部会出现类似：

    Plugin 'Markdown v.0.9.1' was successfully installed: Restart JetBrains PhpStorm to activate changes in plugins? // Restart... (2 minutes ago)

以下是以加载本地安装包的方式进行安装：
####使用Install plugin from disk安装 Markdown 插件
#####下载 Markdown 插件
到 [JetBrains 插件库](http://plugins.jetbrains.com/plugin?pluginId=5970) 下载最新 Markdown 插件版本 0.9.1
#####安装 Markdown 插件
按照以下步骤点击进行安装：

    菜单栏 File
    Setting (弹出设置窗口)
    Plugins (左边菜单栏，可直接在上边的输入框搜索 Plugins 关键字)
    Install plugin from disk… (弹出文件选择窗口)
    选择刚下载的 idea-markdown.zip 文件
    点击 OK 按钮
    点击 Apply 按钮 (弹出是否重启生效提示框)
    Restart

###验证是否安装成功
再次进入设置窗口，会发现左边的菜单栏多了 Markdown 一项，如果左边菜单栏有markdown说明安装成功了。





