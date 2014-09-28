title: linux文件结构.md
date: 2014-09-12 19:59:42
tags:
---

本文内容整理自网络，以作参考。

![文件结构](http://images.cnitblog.com/blog/80780/201306/28142420-0e319099f59243c4a98ca6805c3cbc26.jpg)


## 文件系统的类型
LINUX有四种基本文件系统类型：`普通文件、目录文件、连接文件和特别文件`，可用file命令来识别。

    普通文件：如文本文件、C语言元代码、SHELL脚本、二进制的可执行文件等，可用cat、less、more、vi、emacs来察看内容，用mv来改名。
    目录文件：包括文件名、子目录名及其指针。他是LINUX储存文件名的唯一地方，可用ls列出目录文件。
    连接文件：是指向同一索引节点的那些目录条目。用ls来查看是，连接文件的标志用l开头，而文件面后以"->"指向所连接的文件。
    特别文件：LINUX的一些设备如磁盘、终端、打印机等都在文件系统中表示出来，则一类文件就是特别文件，常放在/dev目录内。例如，软驱A称为/dev/fd0。LINUX无C：的概念，而是用/dev/had来自第一硬盘。

## 目录结构的周详解说  ##
	文件系统的组织结构分析，我们能分析什么呢？也就是当我们列/目录时，所看到的
	/usr、/etc ... ... /var
	等目录是做什么用的，这些目录是不是有些特定的用途。无论哪个哪个版本的Linux系统，都有这些目录，这些目录应该是标准的。当然各个Linux发行版
	本也会存在一些小小的差异，但总体来说，大体还是差不多。
	言归正传，下面飘扬将讲到本文最核心的部分：linux文件系统的目录结构。

| 目录 | 描述 |
| -----: | ----- |
|/  |bLinux文件系统的入口，也是处于最高一级的目录；|
|/bin       |系统所需要的那些命令位于此目录，比如 ls、cp、mkdir等命令；功能和/usr/bin类似，这个目录中的文件都是可执行的、普通用户都能使用的命令。作为基础系统所需要的最基础的命令就是放在这里。|
|/boot     |Linux的内核及引导系统程式所需要的文件目录，比如 vmlinuz initrd.img 文件都位于这个目录中。在一般情况下，GRUB或LILO系统引导管理器也位于这个目录；|
|/dev      |设备文件存储目录，比如声卡、磁盘... ...|
|/etc      | 系统设置文件的所在地，一些服务器的设置文件也在这里；比如用户帐号及密码设置文件；|
|/home  |普通用户家目录默认存放目录；|
|/lib       | 库文件存放目录|
|/lost+found |在ext2或ext3文件系统中，当系统意外崩溃或机器意外关机，而产生一些文件碎片放在这里。当系统启动的过程中fsck工具会检查这里，并修复已损坏的文件系统。 有时系统发生问题，有非常多的文件被移到这个目录中，可能会用手工的方式来修复，或移到文件到原来的位置上。|
|/mnt |这个目录一般是用于存放挂载储存设备的挂载目录的，比如有cdrom 等目录。能参看/etc/fstab的定义。有时我们能把让系统开机自动挂载文件系统，把挂载点放在这里也是能的。主要看/etc/fstab中怎么定义了；比如光驱能挂载到/mnt/cdrom 。|
|/opt |表示的是可选择的意思，有些软件包也会被安装在这里，也就是自定义软件包，比如在Fedora Core 5.0中，OpenOffice就是安装在这里。有些我们自己编译的软件包，就能安装在这个目录中；通过源码包安装的软件，能通过 ./configure --prefix=/opt/目录 。|
|/proc      |操作系统运行时，进程信息及内核信息（比如cpu、硬盘分区、内存信息等）存放在这里。/proc目录伪装的文件系统proc的挂载目录，proc并不是真正的文件系统，他的定义能参见 /etc/fstab 。|
|/root      | Linux终极权限用户root的家目录；|
|/sbin |大多是涉及系统管理的命令的存放，是终极权限用户root的可执行命令存放地，普通用户无权限执行这个目录下的命令，这个目录和/usr/sbin; /usr/X11R6/sbin或/usr/local/sbin目录是相似的；我们记住就行了，凡是目录sbin中包含的都是root权限才能执行的。|
|/tmp       |临时文件目录，有时用户运行程式的时候，会产生临时文件。/tmp就用来存放临时文件的。/var/tmp目录和这个目录相似。|
|/usr |这个是系统存放程式的目录，比如命令、帮助文件等。这个目录下有非常多的文件和目录。当我们安装一个Linux发行版官方提供的软件包时，大多安装在这里。 如果有涉及服务器设置文件的，会把设置文件安装在/etc目录中。/usr目录下包括涉及字体目录/usr/share/fonts ，帮助目录 /usr/share/man或/usr/share/doc，普通用户可执行文件目录/usr/bin 或/usr/local/bin 或/usr/X11R6/bin ，终极权限用户root的可执行命令存放目录，比如 /usr/sbin 或/usr/X11R6/sbin 或/usr/local/sbin 等；更有程式的头文件存放目录/usr/include。|
|/var |这个目录的内容是经常变动的，看名字就知道，我们能理解为vary的缩写，/var下有/var/log 这是用来存放系统日志的目录。/var/www目录是定义Apache服务器站点存放目录；/var/lib 用来存放一些库文件，比如MySQL的，及MySQL数据库的的存放地；|



## /dev目录

dev是设备(device)的英文缩写。/dev这个目录对所有的用户都十分重要。因为在这个目录中包含了所有Linux系统中使用的外部设备。但是这里并不是放的外部设备的驱动程序，这一点和windows,dos操作系统不一样。它实际上是一个访问这些外部设备的端口。我们可以非常方便地去访问这些外部设备，和访问一个文件，一个目录没有任何区别。

    Linux沿袭Unix的风格，将所有设备认成是一个文件。

设备文件分为两种：块设备文件(b)和字符设备文件(c)，`设备文件一般存放在/dev目录下`，对常见设备文件作如下说明：

| 目录 | 描述 |
|------:|------|
|/dev/hd[a-t]：|IDE设备 |
|/dev/sd[a-z]：|SCSI设备|
|/dev/fd[0-7]：|标准软驱|
|/dev/md[0-31]：|软raid设备|
|/dev/loop[0-7]：|本地回环设备|
|/dev/ram[0-15]：|内存|
|/dev/null：|无限数据接收设备,相当于黑洞|
|/dev/zero：|无限零资源|
|/dev/tty[0-63]：|虚拟终端|
|/dev/ttyS[0-3]：|串口|
|/dev/lp[0-3]：|并口|
|/dev/console：|控制台|
|/dev/fb[0-31]：|framebuffer|
|/dev/cdrom => |/dev/hdc|
|/dev/modem => |/dev/ttyS[0-9]|
|/dev/pilot =>| /dev/ttyS[0-9]|
|/dev/random：|随机数设备|
|/dev/urandom：|随机数设备|

## /etc目录

|目录|描述|
|-----:|-----|
|/etc/rc，/etc/rc.d，/etc/rc*.d |`启动、或改变运行级时运行的scripts或scripts的目录。`|
|/etc/passwd |`用户数据库，其中的域给出了用户名、真实姓名、家目录、加密的口令和用户的其他信息`。|
|/etc/fstab |启动时mount -a命令(在/etc/rc 或等效的启动文件中)自动mount的文件系统列表。Linux下，也包括用swapon -a启用的swap区的信息。|
|/etc/group |类似/etc/passwd ，但说明的不是用户而是`用户组`。|
|/etc/inittab |init 的配置文件，设定系统启动时init进程将把系统设置成什么样的runlevel 。|
|/etc/issue |getty 在登录提示符前的输出信息.通常包括系统的一段短说明或欢迎信息内容由系统管理员确定。|
|/etc/motd |Message Of The Day 成功登录后自动输出内容由系统管理员确定，经常用于通告信息，如计划关机时间的警告。|
|/etc/mtab |当前安装的文件系统列表.由scripts初始化，并由mount 命令自动更新，需要一个当前安装的文件系统的列表时使用，例如df 命令。|
|/etc/shadow |在安装了影子口令软件的系统上的影子口令文件.影子口令文件将/etc/passwd 文件中的加密口令移动到/etc/shadow 中，而后者只对root可读这使破译口令更困难.|
|/etc/login.defs login |命令的配置文件。|
|/etc/printcap 类似/etc/termcap |但针对打印机语法不同。|
|/etc/profile , /etc/csh.login , /etc/csh.cshrc |登录或启动时Bourne或C shells执行的文件，这允许系统管理员为所有用户建立全局缺省环境。|
|/etc/securetty |确认安全终端，即哪个终端允许root登录.一般只列出虚拟控制台，这样就不可能(至少很困难)通过modem或网络闯入系统并得到超级用户特权。|
|/etc/shells |列出可信任的shell.chsh 命令允许用户在本文件指定范围内改变登录shell.提供一台机器FTP服务的服务进程ftpd 检查用户shell是否列在 /etc/shells 文件中，如果不是将不允许该用户登录.|
|/etc/sysconfig |网络配置相关目录|
|/etc/DIR_COLORS |`设定颜色`|
|/etc/HOSTNAME |设定用户的节点名|
|/etc/NETWORKING |只有YES标明网络存在|
|/etc/host.conf |文件说明用户的系统如何查询节点名|
|/etc/hosts |设定用户自已的IP与名字的对应表|
|/etc/hosts.allow |设置允许使用inetd的机器使用|
|/etc/hosts.deny |设置不允许使用inetd的机器使用|
|/etc/hosts.equiv| 设置远端机不用密码|
|/etc/inetd.conf |设定系统网络守护进程inetd的配置|
|/etc/inetd.pid |inetd这个进程的进程id|
|/etc/hosts.lpd |设定远端有哪些节点可以使用本机的打印机|
|/etc/gateways |设定路由器|
|/etc/protocols |设定系统支持的协议|
|/etc/named.boot |设定本机为名字服务器的配置文件|
|/etc/named.pid |`本机上运行的名字服务器的进程id`|
|/etc/networks |设定网络的配置文件|
|/etc/resolv.conf |`设定系统的名字服务器`|
|/etc/services |设定系统的端品与协议类型和提供的服务|
|/etc/exports |`设定NFS系统用的`|
|/etc/NNTP_INEWS_DOMAIN |设置新闻服务器的配置文件|
|/etc/nntpserver |设置用户使用的新闻服务器的地址|
|/etc/XF86Config |X Window的配置文件|
|/etc/hostid |系统独有的一个硬件id|
|/etc/at.deny |设置哪些用户不能使用at命令|
|/etc/bootptab |给MAKEDEV程序设定各种不同的设备驱动文件的格式|
|/etc/makedev.cfg |同DEVINFO一样给MAKEDEV使用的设置文件|
|/etc/diphosts |设置拔号服务器的用户名和口令|
|/etc/slip.hosts,/etc/slip.login |设定SLIP的配置文件|
|/etc/fastboot |使用shutdown -f产生的，重启系统要查这个文件|
|/etc/fstab |`记录开机要mount的文件系统`|
|/etc/ftpaccess |`FTP服务器的一些配置`|
|/etc/ftpconversions |设定在FTP时使用的过滤器的位置|
|/etc/ftpusers |`设定不能使用FTP服务的用户`|
|/etc/ld.so.cache |查找系统动态链接库的缓存|
|/etc/ld.so.conf |系统动态链接库的路径|
|/etc/lilo.conf |lilo的配置文件|
|/etc/magic| 给file命令使用的|
|/etc/aliases |给sendmail使用的设置别名的文件|
|/etc/mail.rc, /etc/mailcap, /etc/sendmail.cf, /etc/sendmail.st  |设置sendmail的|
|/etc/motd |超级用户发布通知的地方|
|/etc/organization |存放用户的名字和组织|
|/etc/pnpdevices |列出支持的Plug&Play设备|
|/etc/snooptad |监控用户的屏幕，监听的终端列表|
|/etc/sudoers |`可以sudo命令的配置文件`|
|/etc/syslog.conf |系统记录程序syslogd的配置文件|
|/etc/utmp |目前在用系统的用户信息|
|/etc/wtmp |同utmp差不多，只是它累加|
|/etc/nologin |系统在shutdown时不希望用户登录就产生这个文件|
|/etc/termcap |设置系统终端信息的|
|/etc/ttys |设定系统的终端类型|
|/etc/gettydefs |getty_ps的定义文件|
|/etc/yp.conf | NIS的配置文件|
|/etc/mtools.conf |设定mtools程序的参数|
|/etc/fdprm |设定格式化软盘的参数|
|/etc/login.access |控制用户登录权限的文件|



## /proc目录


| 目录 | 描述 |
|------:|------|
|/proc/cmdline |加载 kernel 时所下达的相关参数，查阅此文件，可了解系统是如何启动。|
|/proc/cpuinfo |本机的 `CPU 的相关资讯，包含时脉、类型与运算功能等`|
|/proc/devices |这个文件记录了系统各个主要装置的主要装置代号，与 mknod 有关。|
|/proc/filesystems |目前系统已经加载的文件系统。|
|/proc/interrupts| 目前系统上面的 `IRQ 分配状态`|
|/proc/ioports |目前系统上面各个装置所配置的 `I/O 位址`。|
|/proc/kcore |这个就是内存的大小，但是不要读他。|
|/proc/loadavg |还记得 top 以及 uptime 吧？没错，上头的三个平均数值就是记录在此。|
|/proc/meminfo |使用 free 列出的内存资讯，在这里也能够查阅到。|
|/proc/modules |目前我们的 Linux 已经加载的模块列表，也可以想成是驱动程序。|
|/proc/mounts |系统已经挂载的数据，就是用 `mount` 这个命令呼叫出来的数据。|
|/proc/swaps |到底系统挂加载的内存在哪里？使用掉的 partition 就记录在此啦。|
|/proc/partitions |使用 `fdisk -l` 会出现目前所有的 partition 吧？在这个文件当中也有|
|/proc/pci |在 PCI 汇流排上面，每个装置的详细情况，可用 `lspci` 来查阅。|
|/proc/uptime |就是用 uptime 的时候，会出现的资讯。|
|/proc/version |核心的版本，就是用 `uname -a `显示的内容。|
|/proc/bus/* | 一些汇流排的装置，还有 U盘 的装置也记录在此。|

## /usr目录

| 目录 | 描述 |
|------:|------|
|/usr |最庞大的目录，因为`所有应用程序几乎都安装在这里`， `本地安装的程序和其他东西在/usr/local 下`。|
|/usr/etc |存放`配置文件`。|
|/usr/games |存放`游戏和教学`文件。|
|/usr/include | 开发和编译应用程序所需要的`头文件`。|
|/usr/share |存放结构独立的数据。|
|/usr/bin |几乎所有`用户命令`.有些命令在/bin 或/usr/local/bin 中。|
|/usr/sbin |根文件系统不必要的`系统管理命令`，例如多数服务程序。|
|/usr/share/man , /usr/share/info , /usr/share/doc |`手册页、GNU信息`文档和各种其他文档文件。|
|/usr/lib |程序或子系统的不变的数据文件，包括一些`site-wide配置文件`，名字lib来源于库(library)， 编程的原始库存在/usr/lib 里。|
|/usr/local |`本地安装的软件`和`其他文件放在这里`，`/usr/local/bin`存放本地增加的命令，`/usr/local/include`存放本地增加的库文件。|
|/usr/src |存放程序的源代码，`linux内核的源代码存放在/usr/src/kernels`。|


## /var目录

|目录|描述|
|------:|------|
|/var |包括系统一般运行时要改变的数据.每个系统是特定的，即不通过网络与其他计算机共享。|
|/var/catman |当要求格式化时的man页的cache.man页的源文件一般存在/usr/man/man* 中；有些man页可能有预格式化的版本，存在/usr/man/cat* 中.而其他的man页在第一次看时需要格式化，格式化完的版本存在/var/man 中，这样其他人再看相同的页时就无须等待格式化了. (/var/catman 经常被清除，就象清除临时目录一样.)|
|/var/lib |`系统正常运行时要改变的文件`。|
|/var/local，/usr/local |中安装的程序的可变数据(即系统管理员安装的程序).注意，如果必要，即使本地安装的程序也会使用其他/var 目录，例如/var/lock 。|
|/var/lock |锁定文件.许多程序遵循在/var/lock 中产生一个锁定文件的约定，以支持他们正在使用某个特定的设备或文件.其他程序注意到这个锁定文件，将不试图使用这个设备或文件。|
|/var/log |各种`程序的Log文件`，特别是login (/var/log/wtmp log所有到系统的登录和注销) 和syslog (/var/log/messages 里存储所有核心和系统程序信息. /var/log 里的文件经常不确定地增长，应该定期清除。|
|/var/run |保存到下次引导前有效的关于系统的信息文件.例如， `/var/run/utmp 包含当前登录的用户的信息`。|
|/var/spool，/var/mail, /var/news  |`打印队列和其他队列工作的目录`.每个不同的spool在/var/spool 下有自己的子目录，例如，用户的邮箱在/var/spool/mail 中。|
|/var/tmp |比/tmp `允许的大或需要存在较长时间的临时文件`。 (虽然系统管理员可能不允许/var/tmp 有很旧的文件.)|





## 比较重要的目录 ##

在 Linux 系统中，有几个目录是特别需要注意的，以下提供几个需要注意的目录，以及预设相关的用途：　

| 目录 | 描述 |
|------:|------|
|/etc： |这个目录相当重要，如前所述，你的开机与系统数据文件均在这个目录之下，因此当这个目录被破坏，那你的系统大概也就差不多该死掉了！而在往后的文件中，你会发现我们常常使用这个目录下的 /etc/rc.d/init.d 这个子目录，因为这个 init.d 子目录是开启一些 Linux 系统服务的 scripts （可以想成是批次檔 ）的地方。而在 /etc/rc.d/rc.local 这个文件是开机的执行档。　|
|/bin, /sbin, /usr/bin, /usr/sbin：| 这是系统预设的执行文件的放置目录，例如 root 常常使用的 userconf, netconf, perl, gcc, c++ 等等的数据都放在这几个目录中，所以如果你在提示字符下找不到某个执行档时，可以在这四个目录中查一查！其中， /bin, /usr/bin 是给系统使用者使用的指令，而 /sbin, /usr/sbin 则是给系统管理员使用的指令！  　|
|/usr/local： |这是系统预设的让你安装你后来升级的套件的目录。例如，当你发现有更新的 Web 套件（如 Apache ）可以安装，而你又不想以 rpm 的方式升级你的套件，则你可以将 apache 这个套件安装在 /usr/local 底下。安装在这里有个好处，因为目前大家的系统都是差不多的，所以如果你的系统要让别人接管的话，也比较容易上手呀！也比较容易找的到数据喔！因此，如果你有需要的话，通常我都会将 /usr/local/bin 这个路径加到我的 path 中。　|
|/home：| 这个是系统将有账号的人口的家目录设置的地方。    　|
|/var： |这个路径就重要了！不论是登入、各类服务的问题发生时的记录、以及常态性的服务记录等等的记录目录，所以当你的系统有问题时，就需要来这个目录记录的文件数据中察看问题的所在啰！而 mail 的预设放置也是在这里，所以他是很重要的    　|
|/usr/share/man, /usr/local/man： |这两个目录为放置各类套件说明档的地方，例如你如果执行 man man，则系统会自动去找这两个目录下的所有说明文件|


## 一些重要子目录的解说 ##

下面飘扬再补充几个比较常见且非常重要的目录。

| 目录 | 描述 |
| ------: | ------- |
|etc/init.d     |这个目录是用来存放系统或服务器以System V模式启动的脚本，这在以System V模式启动或初始化的系统中常见。比如Fedora/RedHat； |
|/etc/xinit.d    |如果服务器是通过xinetd模式运行的，他的脚本要放在这个目录下。有些系统没有这个目录， 比如Slackware，有些老的版本也没有。在Rehat/Fedora中比较新的版本中存在。 |
|/etc/rc.d        |这是Slackware发行版有的一个目录，是BSD方式启动脚本的存放地；比如定义网卡，服务器开启脚本等。 |
|/etc/X11  |这是X-视窗系统相关的设置文件存放地。 |
|/usr/bin |这个目录是可执行程式的目录，普通用户就有权限执行；当我们从系统自带的软件包安装一个程式时，他的可执行文件大多会放在这个目录。比如安装gaim软件包时。相似的目录是/usr/local/bin；有时/usr/bin中的文件是/usr/local/bin的链接文件；|
|/usr/sbin       |这个目录也是可执行程式的目录，但大多存放涉及系统管理的命令。只有root权限才能执行；相似目录是/sbin 或/usr/local/sbin或/usr/X11R6/sbin等； |
|/usr/local     |这个目录一般是用来存放用户自编译安装软件的存放目录；一般是通过源码包安装的软件，如果没有特别指定安装目录的话，一般是安装在这个目录中。这个目录下面有子目录。自己看看吧。 |
|/usr/share   |系统共用的东西存放地，比如 /usr/share/fonts 是字体目录，/usr/share/doc和/usr/share/man帮助文件。|
|/usr/src |是内核源码存放的目录，比如下面有内核源码目录，比如linux 、linux-2.xxx.xx目录等。有的系统也会把源码软件包安装在这里。比如Fedora/Redhat，当我们安装file.src.rpm的时候，这些软件包会安装在/usr/src/redhat相应的目录中。|
|/var/adm     |比如软件包安装信息、日志、管理信息等，在Slackware操作系统中是有这个目录的。在Fedora中好象没有；自己看看吧。 |
|/var/log       |系统日志存放，分析日志要看这个目录的东西； |
|/var/spool   |打印机、邮件、代理服务器等假脱机目录；|

## 目录结构的简明查阅手册 ##
### “/”根目录部分有以下子目录：

| 目录 | 描述 |
| ------: | ------- |
|  /usr            |  目录包含所有的命令、程式库、文件和其他文件。这些文件在正常操作中不会被改动的。这个目录也包含你的Linux发行版本的主要的应用程式，譬如，Netscape。  |
|  /var            |  目录包含在正常操作中被改动的文件：假脱机文件、记录文件、加锁文件、临时文件和页格式化文件等  |
|  /home           |  目录包含用户的文件：参数设置文件、个性化文件、文件、数据、EMAIL、缓存数据等。这个目录在系统省级时应该保留。  |
|  /proc           |  目录整个包含虚幻的文件。他们实际上并不存在磁盘上，也不占用所有空间。（用ls ?l 能显示他们的大小）当查看这些文件时，实际上是在访问存在内存中的信息，这些信息用于访问系统  |
|  /bin            |  系统启动时需要的执行文件（二进制），这些文件能被普通用户使用。  |
|  /sbin           |  系统执行文件（二进制），这些文件不打算被普通用户使用。（普通用户仍然能使用他们，但要指定目录。）  |
|  /etc            |  操作系统的设置文件目录。  |
|  /root           |  系统管理员（也叫终极用户或根用户）的Home目录。  |
|  /dev            |  设备文件目录。LINUX下设备被当成文件，这样一来硬件被抽象化，便于读写、网络共享及需要临时装载到文件系统中。正常情况下，设备会有一个独立的子目录。这些设备的内容会出目前独立的子目录下。LINUX没有所谓的驱动符。  |
|  /lib            |  根文件系统目录下程式和核心模块的共享库。  |
|  /boot           |  用于自举加载程式（LILO或GRUB）的文件。当计算机启动时（如果有多个操作系统，有可能允许你选择启动哪一个操作系统），这些文件首先被装载。这个目录也会包含LINUX核（压缩文件vmlinuz），但LINUX核也能存在别处，只要设置LILO并且LILO知道LINUX核在哪儿。  |
|  /opt            |  可选的应用程式，譬如，REDHAT 5.2下的KDE（REDHAT 6.0下，KDE放在其他的XWINDOWS应用程式中，主执行程式在/usr/bin目录下）  |
|  /tmp            |  临时文件。该目录会被自动清理干净。  |
|  /lost+found     |  在文件系统修复时恢复的文件  |


### “/usr”目录下比较重要的部分有：

| 目录 | 描述 |
| ------: | ------- |
|  /usr/X11R6             |  X-WINDOWS系统（version 11, release 6)  |
|  /usr/X11               |  同/usr/X11R6 （/usr/X11R6的符号连接）  |
|  /usr/X11R6/bin         |  大量的小X-WINDOWS应用程式（也可能是一些在其他子目录下大执行文件的符号连接）。  |
|  /usr/doc               |  LINUX的文件资料（在更新的系统中，这个目录移到/usr/share/doc）。  |
|  /usr/share             |  独立和你计算机结构的数据，譬如，字典中的词。  |
|  /usr/bin和/usr/sbin    |  类似和“/”根目录下对应的目录（/bin和/sbin），但不用于基本的启动（譬如，在紧急维护中）。大多数命令在这个目录下。  |
|  /usr/local             |  本地管理员安装的应用程式（也可能每个应用程式有独立的子目录）。在“main”安装后，这个目录可能是空的。这个目录下的内容在重安装或升级操作系统后应该存在。  |
|  /usr/local/bin         |  可能是用户安装的小的应用程式，和一些在/usr/local目录下大应用程式的符号连接。  |


### “/proc”目录的内容：

| 目录 | 描述 |
|------:|------|
|/proc/cpuinfo |关于处理器的信息，如类型、厂家、型号和性能等。|
|/proc/devices |当前运行内核所设置的所有设备清单。|
|/proc/dma |当前正在使用的DMA通道。/proc/filesystems 当前运行内核所设置的文件系统。|
|/proc/interrupts |正在使用的中断，和原来有多少个中断。|
|/proc/ioports |当前正在使用的I/O端口。|


## linux与windows的文件目录对比 ##

linux与windows的文件夹没有可对比之处，也没有对应的
不过非要说的话，按照软件安装时的行为，也可以有对应的

比如说，linux安装软件时一般会默认安装到`/usr/local`下，而windows下默认安装到`c:\program files`下，所以从这里看，它们两者对应

类似的，`/bin`  `/sbin`  `/usr/bin`  `/usr/sbin`  `/usr/local/xxx/bin`  和  `/usr/local/xxx/sbin` 这几个文件夹都相当于`c:\windows`,因为PATH变量会优先搜寻这几个目录，而windows的PATH一般会优先搜寻c:\windows

/etc  /usr/local/etc /usr/local/xxx/etc 这几个没有可对应的

`/（根目录）`，也没有可对应的,若非要说有，`c:\`免强说得过去

`~root/ 或~用户名/` , 就相当于`C:\Users\用户名(windows也可以用环境变量 %userprofile% 表示)` 表示)，`root对应于administrator`

/dev 没有可对应的

/usr/src 也没有可对应的（windows可不提供给你源码!)

`/home` 对应于`C:\Users`

`/tmp` 对应于 `%temp% 或 %tmp% (环境变量表示的路径)`

不错的网站（备用）：[鸟哥的私房菜](http://vbird.dic.ksu.edu.tw/linux_basic/linux_basic.php)