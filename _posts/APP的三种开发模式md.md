title: APP的三种开发模式.md
date: 2014-09-15 11:19:17
tags:
---
# APP的三种开发模式

开发者们都知道在高端智能手机系统中有两种应用程序：

1. 一种是基于本地（操作系统）运行的APP ---Native App；
2. 一种是基于高端机的浏览器运行的App ---WebApp
	因为这些高端智能手机（Iphone、Android）的内置浏览器都是基于webkit内核的，所以在开发WEBAPP时，多数都是使用HTML5和CSS3技术做UI布局。当使用HTML5和CSS3l做UI时，若还是遵循着一般web开发中使用HTML4和CSS2那样的开发方式的话，这也就失去了WEBAPP的本质意义了
3. 一种是基于上两种发展出来的产物 ---Hybrid App
    Hybrid App（混合模式移动应用）是指介于web-app、native-app这两者之间的app，兼具“Native App良好用户交互体验的优势”和“Web App跨平台开发的优势”。

移动产品的实现方式主要有三种：

1. Native App；
2. Web App；
3. Hybrid App

> 目前移动互联网基本采用了`NativeApp`、`WebApp`、`HybridApp`三种开发模式，很难说这三种模式那种更优越，目前的情况可以说是三分天下吧，不同的开发者可以根据自己的实际情况选择不同的开发模式。谈论那种模式最好实际上事非常无聊的事情。

### NativeApp指的是本地化应用，就是我们从应用商店下载安装的独立应用

1. 开发成本非常大。
	一般使用的开发语言为JAVA、C++、Objective-C。
2. 更新体验较差、同时也比较麻烦
	每一次发布新的版本，都需要做版本打包，且需要用户手动更新（有些应用程序即使不需要用户手动更新，但是也需要有一个恶心的提示）。
3. 非常酷
	因为native app可以调用IOS中的UI控件以UI方法，它可以实现WebApp无法实现的一些非常酷的交互效果
4. Native app是被Apple认可的
	Native app可以被Apple认可为一款可信任的独立软件，可以放在Apple Stroe出售，但是Web app却不行。

开发`成本过高`，`跨平台性不好`是开发者们选择放弃这种开发模式的重要原因。开发语音主要采用`Object-C、Java`等语言。由于我不是做`Native`端开发的，这里不多说了。

### WebApp通常是指触屏站，就是我们通过手机浏览器访问的Html5网站，Html5支持一些新标签和脚本，可以做出类原生应用的效果和动画

1. 开发成本较低
	使用web开发技术就可以轻松的完成web app的开发
2. 升级较简单
	升级不需要通知用户，在服务端更新文件即可，用户完全没有感觉
3. 维护比较轻松
	和一般的web一样，维护比较简单，它其实就是一个站点

Webapp说白了就是一个针对Iphone、Android优化后的web站点，它使用的技术无非就是HTML或HTML5、CSS3、JavaScript，服务端技术JAVA、PHP、ASP。

HTML5技术的兴起给Web App注入了新的生机。
Web App具有`开发成本低`、`周期短`、`使用方便`、`维护简单`等特点。
随着HTML5被过度热炒和实际开发中遇到的性能以及体验问题，WebApp逐渐势弱。
同样，以`AppStore为首的App分发平台当然是不希望webapp破坏自己建立的生态系统的`。html5迟迟没有得不到一个公认的标准，也阻碍着webapp的发展。但是这些都不足以阻碍webapp的发展。现在APP的数量已经达到数以百万计，实际上用户根本不需要这么多的App，很多App被用户下载后，一个月都不会被打开一次。
而webapp用户根本`不需要安装`，只需要`打开手机浏览器，输入网址或搜索目标`，点击即可到达想要的网页，`基本和PC互联网的思路是一致的`，这也说明百度同样在移动入口上有这很大的优势。在NativeApp上用户只有安装了App，才能浏览，而webapp是直接通过手机浏览器为入口，或者推送的信息为入口，这么看webapp在流量上是有很大的优势的。

但是目前webapp得不到很好的发展主要有以下几个方面的原因：

1. 无有效且广泛的webapp发行渠道（NativeApp有AppStore等）；
2. webapp表现和体验不佳（这点算硬伤吧）；
3. 适配难度（一套web很难兼容所有的手机，特别是国内某些自以为很牛B的手机，大可乐算一个吧，哈哈）；
4. 配套的标准尚未成熟（主要指html5吧）。

网站移动化是必然的，目前知道webapp比较好的解决方案有如下几个：

1. 云适配  号称引入一段神奇的代码就能将PC网站移动化。陈本峰老师也是我学习的榜样，html5布道官。了解更多信息可以链接到http://www.yunshipei.com/
2. 百度site App  网址：http://siteapp.baidu.com/
3. 还知道个做微站的网站，号称把微信、微博入口都已打通，企业用户营销很好的平台：http://www.weizhan360.com/

### HybridApp是指混合模式应用，同时使用网页语言与程序语言编写，包含原生视图和Web视图两种方式，使用方式和Native App一致，而又继承了Web App实时更新开发成本低等优点。

汽车有混合动力Hybrid，移动应用同样也有混合模式。Hybrid App兼具“Native App良好用户交互体验的优势”和“Web App跨平台开发的优势”。很多人不知道市场上一些主流移动应用都是基于Hybrid App的方式开发，比如国外有Facebook、国内有百度搜索等。但究竟什么是Hybrid App？如何定义？


- mobile application：Hybrid App就是一个移动应用
- both browser-supported language and computer language：同时使用网页语言与程序语言编写
- available through application distribution platforms：通过应用商店进行分发
- a target device：区分目标平台
- install to run：用户需要安装使用

综合一下就是：“Hybrid App同时使用网页语言与程序语言开发，通过应用商店区分移动操作系统分发，用户需要安装使用的移动应用”。总体特性更接近Native App但是和Web App区别较大。只是因为同时使用了网页语言编码，所以开发成本和难度比Native App要小很多。因此说，Hybrid App兼具了Native App的所有优势，也兼具了Web App使用HTML5跨平台开发低成本的优势。

Hybrid App的兴起是现阶段移动互联网产业的一种偶然。移动互联网的热潮刮起后，众多公司前赴后继的进入。但是很快发现移动应用的开发人员太少，所以导致疯狂的人才争夺。市场机制下移动应用开发人才的待遇扶摇直上，最终变成众多企业无法负担养一个具备跨平台开发能力的专业移动应用开发团队。而HTML5的出现让Web App露出曙光，HTML5开发移动应用的跨平台和廉价优势让众多想进入移动互联网领域的公司开始心动。可是当下基于HTML5的Web App更是雾里看花，在用户入口习惯、分发渠道和应用体验这三个核心问题没解决之前，Web App也很难得以爆发。正是在这样是机缘巧合下，基于HTML5低成本跨平台开发优势又兼具Native App特质的Hybrid App技术杀入混战，并且很快吸引了众人的目光。大幅的降低了移动应用的开发成本，可以通过现有应用商店模式发行，在用户桌面形成独立入口等等这些，让Hybrid App成为解决移动应用开发困境不错的选择，也成为现阶段Web App的代言人。Hybrid App像刺客一样，在Native App和Web App混战之时，偶然间的在移动应用开发领域占有了一席之地。

Hybrid App，这种既有`跨平台开发周期短`、`成本低的基因`，又`能发挥Native App体验和性能`的优势，HybridApp混合式移动应用开发逐渐成为企业移动开发的首选。
Hybrid App通常是`基于第三方跨平台移动应用引擎框架`进行开发，
在国内开发者中比较知名的有`PhoneGap、Titanium和AppCan这些引擎框架`一般使用`HTML5和Javascript`作为编程语言，调用`引擎封装的底层功能如照相机、传感器、通讯录、二维码`等。`HTML5和Javascript只是作为一种解析语言，真正调用的都是NativeApp一样封装的底层功能，这是和Web App的最大区别和不同`。因为使用了`浏览器技术`，所以Hybrid App通常具有`跨平台的特性`，并且`开发成本和WebApp接近`，开发`效率也远高于Native App`。

说实在的，从表面上看的话，很难区分一个App到底是Native App还是Hybrid App，但实际上我们更多的是把`Hybrid App当做是Webapp的一部分`，因为他是一部分Native（比较少），绝大部分的web页面（html5页面）。

Hybrid App和Native App一样都是需要用户在各种App分发渠道上`下载并安装到手机上才能用的`。Hybrid App的体验当然是没话说，比较棒的，有这Native App的全部优点。html5很好的解决了跨平台性的问题，也解决了开发成本过高的问题。

One Web more  native 可以很好的形容Hybrid App这种开发模式。


Hybrid App是如何实现网页语言与程序语言的混合？谁占主体？

Hybrid App通常分为三种类型：`多View混合型，单View混合型，Web主体型`。

![](http://images.51cto.com/files/uploadimg/20120628/1602500.jpg)

> 从分析可见，Hybrid App中的Web主体型只要能够解决用户体验差的问题，就可以变成最佳Hybrid App解决方案类型。

Hybrid App的瓶颈与未来

国内外Hybrid App的开发框架众多。如何选择又成为一个难题。下面对开发者比较关心的集中知名跨平台开发移动应用中间件进行列表和对比，以便选择最适合您的移动应用中间件。

![](http://d.hiphotos.baidu.com/baike/c0%3Dbaike180%2C5%2C5%2C180%2C60%3Bt%3Dgif/sign=b8a433128c5494ee932f074b4c9c8b9b/d53f8794a4c27d1e996189691bd5ad6edcc438d3.jpg)

PhoneGap是相对比较早进入公众视线的一种选择。但是，开发者简单的基于PhoneGap来开发移动应用肯定会发现结果和Web App比较差的用户体验类似。这也是为什么基于PhoneGap有实用性的移动应用主要集中在iOS上。可是PhoneGap这种现状弱化了HTML5的跨平台价值。

AppCan在技术架构上和PhoneGap类似是Web主体型中间件，但是通过结合了一些原生交互效果能够达到iOS、Android平台都比较一致的用户体验。但是相比PhoneGap的开源，AppCan相对封闭的路线显得过于谨慎。

Titanium是一种基于翻译机制的跨平台中间件，能够开发出具有Native体验的移动应用，但是因为翻译机制的限制导致移动应用开发不能像真正的HTML5开发一样灵活。哪怕一个按钮也不能像普通HTML一样来编写，而必须按照Titanium约定的特定格式。

Hybrid App这个领域虽然还处于比较初期的阶段，但是已经有很多优秀的公司和技术团队在致力于跨平台开发移动应用中间件技术的研究，给了开发者众多选择。开发者可以根据实际的项目需求来选择中间件。Web App虽被浏览器厂商和搜索引擎公司所推崇，但存在用户体验差、盈利模式不明确等现阶段无法解决的问题，或最终夭折。Hybrid App正在被越来越多的公司和开发者所认同，势必会成为新世界的王。

Web App、Hybrid App、Native APP对比

| --- |Web App（网页应用）| Hybrid App（混合应用）| Native App（原生应用）|
|------|------|------|------|
|开发成本|低|中|高|
|维护更新|简单|简单|复杂|
|体验|差|优|优|
|Store或market认可|不认可|认可|认可|
|安装|不需要|需要|需要|
|跨平台|优|优|差|

    HybridApp开发，现阶段主流的平台包括PhoneGap（Cordova），AppCan，appMobi，Titanium等，它们基于webkit开源内核，使用HTML5 标准开发，适配机型简单，支持开发者自定义插件，并能很好的应用于商业，教育，娱乐等行业，成为移动开发者的首选开发平台。




