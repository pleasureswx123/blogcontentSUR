title: git在linux中的运用
date: 2014-08-29 17:40:42
categories: git
tags:
---
#### 新建 ssh-key 与 github.com 连接
- 生成key
- 连接github.com
- 设置github.com，clone 内容，服务器修改提交内容到github

####生成key
    cd ~
    ls -la
    git config --global user.name "pleasureswx123"
    git config --global user.email "pleasureswx123@163.com"
    cat .gitconfig
    cd .ssh
    ssh-keygen -C "pleasureswx123@163.com" -t rsa
    /*下几步后操作*/
    cat pleasureswx.pub

- cd ~   ##进入当前用户的根目录
- ls -la     ##查看所有文件 a 为查看隐藏的文件
> 可以 `.gitconfig` 文件夹
> 如果没有可能需要 进行如下设置：
>> git config --global user.name "`pleasureswx123`"
>> git config --global user.email "`pleasureswx123@163.com`"
>> "pleasureswx123"  为我的 github 的`用户名`
>> "pleasureswx123@163.com" 为设置我的 github 时的`邮箱`
- cat .gitconfig   ##查看你的github账号的配置信息
- cd .ssh  ##进入隐藏的.ssh文件
- ssh-keygen -C "pleasureswx123@163.com"  ##引号里的必须与user.email一致
- Enter file in which to save the key 输入要生成的key的`文件的名称`
- enter passphrash 输入你的密码可输入也可以不输入直接回车
- 再次输入密码
- 这时key已生成
- ls -la ##查看
- 找到你输入的key的文件名称，有两个，.pub后缀的为公开key，没有后缀的为私有key
- 一般情况下用公开的.pub
- cat pleasureswxssh.pub ##查看代码
- 复制到剪贴板
上面过程如下图所示：
下图中有一处错误：
ssh-keygen -C " pleasureswx123@163.com"
应为：
ssh-keygen -C " pleasureswx123@163.com" -t rsa
![Alt text](/img/gitlinux/01.png)
![Alt text](/img/gitlinux/02.png)


####连接github.com
- 进入github.com网站
![Alt text](/img/gitlinux/03.png)
此时上节生成的key与github.com不出问题的话，应该连接上了
查看是否连接上的命令：
`ssh -T git@github.com`
![Alt text](/img/gitlinux/04.png)
出现上图所示，即连接成功。

####github.com设置
![Alt text](/img/gitlinux/05.png)
- 点击如下红色框区域：
![Alt text](/img/gitlinux/06.png)
- 复制地址
- 下图中 `git clone` '粘贴复制的地址'
![Alt text](/img/gitlinux/07.png)

查看 是否有远端，`git remote`
![Alt text](/img/gitlinux/08.png)
如上图正确，如没有的话可通过
`git remote add origin git@github.com:pleasureswx123/myblog.git`
也可通过`git remote rm origin` 删除远端
![Alt text](/img/gitlinux/09.png)

![Alt text](/img/gitlinux/10.png)


####总结

对应window下的远端，仅供参考下图：
![Alt text](/img/gitlinux/11.png)

linux 配置主要分为两个部分：
- 一个为URL
- 一个为putty密钥







