<div style="color:#16b0ff;font-size:50px;font-weight: 900;text-shadow: 5px 5px 10px var(--theme-color);font-family: 'Comic Sans MS';">Others</div>

<span style="color:#16b0ff;font-size:20px;font-weight: 900;font-family: 'Comic Sans MS';">Author</span>：李茹钰（`echo`）

<span style="color:#16b0ff;font-size:20px;font-weight: 900;font-family: 'Comic Sans MS';">Introduction</span>：收纳其它相关的知识总结！

[TOC]

# 常用软件

## 画图工具

### draw.io

本地或在线画图地址：https://draw.io

![draw.io](images/Others/draw.io.jpeg)

### Excalidraw

在线画图地址：https://excalidraw.com

![Excalidraw](images/Others/Excalidraw.png)

### ProcessOn

在线画图地址：https://www.processon.com

![ProcessOn](images/Others/ProcessOn.png)

### Carbon

代码截图网址地址：https://carbon.now.sh

![Carbon](images/Others/Carbon.png)



## 数据抓包

### Fiddler

Fiddler是一个蛮好用的抓包工具，可以将网络传输发送与接受的数据包进行截获、重发、编辑、转存等操作。也可以用来检测网络安全。反正好处多多，举之不尽呀！当年学习的时候也蛮费劲，一些蛮实用隐藏的小功能用了之后就忘记了，每次去网站上找也很麻烦，所以搜集各大网络的资料，总结了一些常用的功能。

Fiddler 下载地址 ：https://www.telerik.com/download/fiddler

win8之后用“Fiddler for .NET4”而win8之前用“Fiidler for .NET2”比较好。

#### Fiddler抓包简介

##### 代理设置

Fiddler是通过改写HTTP代理，让数据从它那通过，来监控并且截取到数据。当然Fiddler很屌，在打开它的那一瞬间，它就已经设置好了浏览器的代理了。当你关闭的时候，它又帮你把代理还原了，是不是很贴心。

![Fiddler抓包简介](images/Others/Fiddler抓包简介.png)



##### Capture Traffic

Fiddler想要抓到数据包，要确保Capture Traffic是开启，在File –> Capture Traffic。开启后再左下角会有显示，当然也可以直接点击左下角的图标来关闭/开启抓包功能。

![Fiddler-CaptureTraffic](images/Others/Fiddler-CaptureTraffic.png)

Fiddler开始工作了，抓到的数据包就会显示在列表里面，下面总结了这些都是什么意思：

![Fiddler-CaptureTraffic-Debugger](images/Others/Fiddler-CaptureTraffic-Debugger.png)



##### Statistics请求的性能数据分析

随意点击一个请求，就可以看到Statistics关于HTTP请求的性能以及数据分析了。

![Fiddler-Statistics](images/Others/Fiddler-Statistics.png)



##### Inspectors查看数据内容

Inspectors是用于查看会话的内容，上半部分是请求的内容，下半部分是响应的内容：

![Fiddler-Inspectors](images/Others/Fiddler-Inspectors.png)



##### AutoResponder允许拦截指定规则的请求

AutoResponder允许你拦截指定规则的求情，并返回本地资源或Fiddler资源，从而代替服务器响应。看下图5步，我将“baidu”这个关键字与我电脑“f:\Users\YukiO\Pictures\boy.jpeg”这张图片绑定了，点击Save保存后勾选Enable rules，再访问baidu，就会被劫持。这个玩意有很多匹配规则，如：

1. 字符串匹配（默认）：只要包含指定字符串（不区分大小写），全部认为是匹配

| 字符串匹配（baidu）    | 是否匹配 |
| :--------------------- | :------- |
| http://www.baidu.com   | 匹配     |
| http://pan.baidu.com   | 匹配     |
| http://tieba.baidu.com | 匹配     |

2. 正则表达式匹配：以“regex:”开头，使用正则表达式来匹配，这个是区分大小写的

| 字符串匹配（regex:.+.(jpg \| gif \| bmp ) $） | 是否匹配 |
| :-------------------------------------------- | :------- |
| http://bbs.fishc.com/Path1/query=foo.bmp&bar  | 不匹配   |
| http://bbs.fishc.com/Path1/query=example.gif  | 匹配     |
| http://bbs.fishc.com/Path1/query=example.bmp  | 匹配     |
| http://bbs.fishc.com/Path1/query=example.Gif  | 不匹配   |



![Fiddler-AutoResponder-1](images/Others/Fiddler-AutoResponder-1.png)

![Fiddler-AutoResponder-2](images/Others/Fiddler-AutoResponder-2.png)



##### Composer自定义请求发送服务器

Composer允许自定义请求发送到服务器，可以手动创建一个新的请求，也可以在会话表中，拖拽一个现有的请求。Parsed模式下你只需要提供简单的URLS地址即可（如下图，也可以在RequestBody定制一些属性，如模拟浏览器User-Agent）。

![Fiddler-Composer](images/Others/Fiddler-Composer.png)



##### Filters请求过滤规则

Fiters是过滤请求用的，左边的窗口不断的更新，当你想看你系统的请求的时候，你刷新一下浏览器，一大片不知道哪来请求，看着碍眼，它还一直刷新你的屏幕。这个时候通过过滤规则来过滤掉那些不想看到的请求。

![Fiddler-Filters](images/Others/Fiddler-Filters.png)

勾选左上角的Use Filters开启过滤器，这里有两个最常用的过滤条件：Zone和Host

- Zone：指定只显示内网（Intranet）或互联网（Internet）的内容

  ![Fiddler-Filters-Zone](images/Others/Fiddler-Filters-Zone.png)

- Host：指定显示某个域名下的会话

  ![Fiddler-Filters-Host](images/Others/Fiddler-Filters-Host.png)

  如果框框为黄色（如图），表示修改未生效，点击红圈里的文字即可。



#### Fiddler设置解密HTTPS的网络数据

Fiddler可以通过伪造CA证书来欺骗浏览器和服务器。Fiddler是个很会装逼的好东西，大概原理就是在浏览器面前Fiddler伪装成一个HTTPS服务器，而在真正的HTTPS服务器面前Fiddler又装成浏览器，从而实现解密HTTPS数据包的目的。

解密HTTPS需要手动开启，依次点击：

1. Tools –> Fiddler Options –> HTTPS

![Fiddler-HTTPS-1](images/Others/Fiddler-HTTPS-1.png)

2. 勾选Decrypt HTTPS Traffic

![Fiddler-HTTPS-2](images/Others/Fiddler-HTTPS-2.png)

3. 点击OK

![Fiddler-HTTPS-3](images/Others/Fiddler-HTTPS-3.png)



#### Fiddler抓取IPhone/Android数据包

想要Fiddler抓取移动端设备的数据包，其实很简单，先来说说移动设备怎么去访问网络，看了下面这张图，就明白了。

![Fiddler抓取移动端-1](images/Others/Fiddler抓取移动端-1.png)

可以看得出，移动端的数据包，都是要走wifi出去，所以我们可以把自己的电脑开启热点，将手机连上电脑，Fiddler开启代理后，让这些数据通过Fiddler，Fiddler就可以抓到这些包，然后发给路由器（如图）：

![Fiddler抓取移动端-2](images/Others/Fiddler抓取移动端-2.png)

1. 打开Wifi热点，让手机连上（我这里用的360wifi，其实随意一个都行）

![Fiddler抓取移动端-3](images/Others/Fiddler抓取移动端-3.png)

2. 打开Fidder，点击菜单栏中的 [Tools] –> [Fiddler Options]

![Fiddler抓取移动端-4](images/Others/Fiddler抓取移动端-4.png)

3. 点击 [Connections] ，设置代理端口是8888， 勾选 Allow remote computers to connect， 点击OK

![Fiddler抓取移动端-5](images/Others/Fiddler抓取移动端-5.png)

4. 这时在 Fiddler 可以看到自己本机无线网卡的IP了（要是没有的话，重启Fiddler，或者可以在cmd中ipconfig找到自己的网卡IP）

![Fiddler抓取移动端-6](images/Others/Fiddler抓取移动端-6.png)

![Fiddler抓取移动端-7](images/Others/Fiddler抓取移动端-7.png)

5. 在手机端连接PC的wifi，并且设置代理IP与端口（代理IP就是上图的IP，端口是Fiddler的代理端口8888）

![Fiddler抓取移动端-8](images/Others/Fiddler抓取移动端-8.png)

6. 访问网页输入代理IP和端口，下载Fiddler的证书，点击下图FiddlerRoot certificate

![Fiddler抓取移动端-9](images/Others/Fiddler抓取移动端-9.png)

【注意】：如果打开浏览器碰到类似下面的报错，请打开Fiddler的证书解密模式（Fiddler 设置解密HTTPS的网络数据）

```
No root certificate was found. Have you enabled HTTPS traffic decryption in Fiddler yet?
```

![Fiddler抓取移动端-10](images/Others/Fiddler抓取移动端-10.png)![Fiddler抓取移动端-11](images/Others/Fiddler抓取移动端-11.png)

![Fiddler抓取移动端-12](images/Others/Fiddler抓取移动端-12.png)![Fiddler抓取移动端-13](images/Others/Fiddler抓取移动端-13.png)

7. 安装完了证书，可以用手机访问应用，就可以看到截取到的数据包了。（下图选中是布卡漫画的数据包，下面还有QQ邮箱的）

![Fiddler抓取移动端-14](images/Others/Fiddler抓取移动端-14.png)



#### Fiddler内置命令与断点

Fiddler还有一个藏的很深的命令框，就是眼前，我用了几年的Fiddler都没有发现它，偶尔在别人的文章发现还有这个小功能，还蛮好用的，整理下记录在这里。Fiddler断点功能就是将请求截获下来，但是不发送，这个时候你可以干很多事情，比如说，把包改了，再发送给服务器君。还有balabala一大堆的事情可以做，就不举例子了。

![Fiddler内置命令与断点](images/Others/Fiddler内置命令与断点.png)

| **命令** | **对应请求项** | **介绍**                                                     | **示例**       |
| :------- | :------------- | :----------------------------------------------------------- | :------------- |
| ?        | All            | 问号后边跟一个字符串，可以匹配出包含这个字符串的请求         | ?google        |
| >        | Body           | 大于号后面跟一个数字，可以匹配出请求大小，大于这个数字请求   | >1000          |
| <        | Body           | 小于号跟大于号相反，匹配出请求大小，小于这个数字的请求       | <100           |
| =        | Result         | 等于号后面跟数字，可以匹配HTTP返回码                         | =200           |
| @        | Host           | @后面跟Host，可以匹配域名                                    | @www.baidu.com |
| select   | Content-Type   | select后面跟响应类型，可以匹配到相关的类型                   | select image   |
| cls      | All            | 清空当前所有请求                                             | cls            |
| dump     | All            | 将所有请求打包成saz压缩包，保存到“我的文档\Fiddler2\Captures”目录下 | dump           |
| start    | All            | 开始监听请求                                                 | start          |
| stop     | All            | 停止监听请求                                                 | stop           |



| **断点命令** |          |                                                         |                                      |
| :----------: | -------- | ------------------------------------------------------- | ------------------------------------ |
|   bpafter    | All      | bpafter后边跟一个字符串，表示中断所有包含该字符串的请求 | bpafter baidu（输入bpafter解除断点） |
|     bpu      | All      | 跟bpafter差不多，只不过这个是收到请求了，中断响应       | bpu baidu（输入bpu解除断点）         |
|     bps      | Result   | 后面跟状态吗，表示中断所有是这个状态码的请求            | bps 200（输入bps解除断点）           |
|  bpv / bpm   | HTTP方法 | 只中断HTTP方法的命令，HTTP方法如POST、GET               | bpv get（输入bpv解除断点）           |
|    g / go    | All      | 放行所有中断下来的请求                                  | g                                    |



**断点命令**：断点可以直接点击Fiddler下图的图标位置，就可以设置全部请求的断点，断点的命令可以精确设置需要截获那些请求。如下示例：

![Fiddler-断点命令](images/Others/Fiddler-断点命令.png)



### Wireshark

### 科来网络分析系统



## SSH

### XShell/XFtp

https://www.netsarang.com/zh/free-for-home-school

![XShell](images/Others/XShell.png)

### SecureCRT

https://www.vandyke.com/cgi-bin/releases.php?product=securecrt

![SecureCRT](images/Others/SecureCRT.jpg)

### Terminal.icu

https://www.terminal.icu/

![Terminal.icu](images/Others/Terminal.icu.png)



## Chrome

### 谷歌访问助手

http://www.ggfwzs.com

### Postman

https://www.postman.com/downloads



## 代码对比

### WinMerge

![WinMerge](images/Others/WinMerge.png)

### Diffuse

![Diffuse](images/Others/Diffuse.png)

### Beyond Compare

![BeyondCompare](images/Others/BeyondCompare.png)

### Altova DiffDog

![AltovaDiffDog](images/Others/AltovaDiffDog.png)

### AptDiff

![AptDiff](images/Others/AptDiff.png)

### Code Compare

![CodeCompare](images/Others/CodeCompare.png)

### jq22

一款在线的文本比较工具，不想安装软件的直接用这个就好了！地址：http://www.jq22.com/textDifference

![jq22](images/Others/jq22.png)



## 其它软件

### 图壳

免费好用稳定的图床网站。https://imgkr.com/

![图壳](images/Others/图壳.gif)

### 小码短连接

简单易用的渠道短链接统计工具。https://xiaomark.com/

![小码短连接](images/Others/小码短连接.png)

非常好用的长链接转短链接工具，能够让链接看起来更简洁。并且，转换为短链接之后，还能在后台监测访问数据，如访问次数、访问人数。

### removebg

抠图神器。https://www.remove.bg/zh

![removebg](images/Others/removebg.png)

### 今日热榜

你关心的热点。今日热榜提供各站热榜聚合：微信、今日头条、百度、知乎、V2EX、微博、贴吧、豆瓣、天涯、虎扑、Github、抖音...。追踪全网热点、简单高效阅读。https://tophub.today

![今日热榜](images/Others/今日热榜.png)



# 开源工具

[**Swagger**](https://swagger.io/): API Documentation & Design Tools for Teams

[**jvm-sandbox**](https://github.com/alibaba/jvm-sandbox)：Real - time non-invasive AOP framework container based on JVM

**[JimuReport](https://github.com/zhangdaiscott/JimuReport)**：这是一款免费的数据可视化工具，报表与大屏设计！类似于excel操作风格，在线拖拽完成报表设计！功能涵盖: 报表设计、图形报表、打印设计、大屏设计等，永久免费！

**[sa-token](https://github.com/dromara/sa-token)**：这可能是史上功能最全的Java权限认证框架！目前已集成——登录认证、权限认证、分布式Session会话、微服务网关鉴权、单点登录、OAuth2.0、踢人下线、Redis集成、前后台分离、记住我模式、模拟他人账号、临时身份切换、账号封禁、多账号认证体系、注解式鉴权、路由拦截式鉴权、花式token生成、自动续签、同端互斥登录、会话治理、密码加密、jwt集成、Spring集成、WebFlux集成...

**[soul](https://github.com/dromara/soul)**：应用于所有微服务场景的，可扩展、高性能、响应式的 API 网关解决方案。

**[arthas](https://github.com/alibaba/arthas)**：Arthas旨在帮助开发人员解决Java应用程序的生产问题，无需修改代码或重新启动服务器。有了Arthas，你就可以在不重新启动JVM或需要额外的代码更改的情况下实时地对问题进行故障排除。

**[miaosha](https://github.com/qiurunze123/miaosha)**：该项目是对高并发大流量如何进行秒杀架构，而做的一个系统整理，如果你完全没接触过 MQ、SpringBoot、Redis、Dubbo、ZK 、Maven,lua等，那么我建议你可以先在网上搜一下每一块知识的快速入门。

[**Guava**](https://github.com/google/guava)：Google core libraries for Java

[**TransmittableThreadLocal**](https://github.com/alibaba/transmittable-thread-local)：The missing Java™ std lib(simple & 0-dependency) for framework/middleware, provide an enhanced InheritableThreadLocal that transmits ThreadLocal values between threads even using thread pooling components.

[**FastJSON**](https://github.com/alibaba/fastjson)：A fast JSON parser/generator for Java.

[**Druid**](https://github.com/alibaba/druid)：阿里巴巴计算平台事业部出品，为监控而生的数据库连接池

[**JetCache**](https://github.com/alibaba/jetcache)：JetCache is a Java cache framework.

[**Metrics**](https://github.com/alibaba/metrics)：The metrics library for Apache Dubbo and any frameworks or systems.



# IDEA

**JetBrains 破解许可服务器**：https://www.licensez.com

## 常见设置

### 显示工具条

**效果图**
![显示工具条](images/Others/显示工具条.png)
**设置方法**

- 标注1：View–>Toolbar
- 标注2：View–>Tool Buttons



### 设置鼠标悬浮提示

**效果图**
![设置鼠标悬浮提示](images/Others/设置鼠标悬浮提示.png)

**设置方法**
File–>settings–>Editor–>General–>勾选Show quick documentation…
![在这里插入图片描述](images/Others/20181030154227362.png)



### 显示方法分隔符

**效果图**
![在这里插入图片描述](images/Others/20181030154728569.png)
**设置方法**

File–>settings–>Editor–>Appearance–>勾选

![在这里插入图片描述](images/Others/2018103015481187.png)



### 忽略大小写提示

**效果图**
备注：idea的默认设置是严格区分大小写提示的，例如输入string不会提示String，不方便编码
![在这里插入图片描述](images/Others/20181030155133360.png)
**设置方法**
File–>settings–>Editor–>General -->Code Completion -->
![在这里插入图片描述](images/Others/20181030155413727.png)



### 主题设置

**效果图**
备注：有黑白两种风格
![在这里插入图片描述](images/Others/20181030155545483.png)
![在这里插入图片描述](images/Others/20181030155612301.png)
**设置方法**
File–>settings–>Appearance & Behavior–>Appearance–>
![在这里插入图片描述](images/Others/2018103015572874.png)



### 护眼主题设置

**效果图**
![在这里插入图片描述](images/Others/20190110100508868.png)
**设置方法**

如果想将编辑页面变换主题，可以去设置里面调节背景颜色
![在这里插入图片描述](images/Others/20190110100622631.png)

如果需要很好看的编码风格，这里有很多主题
http://color-themes.com/?view=index&layout=Generic&order=popular&search=&page=1
点击相应主题，往下滑点击按钮
![在这里插入图片描述](images/Others/20190110100734530.png)
下载下来有很多Jar包
![在这里插入图片描述](images/Others/2019011010115881.png)
![在这里插入图片描述](images/Others/2019011010123767.png)

在上面的位置选择导入jar包，然后重启idea生效，重启之后去设置

![在这里插入图片描述](images/Others/20190110101907801.png)



### 自动导入包
**效果图**
备注：默认情况是需要手动导入包的，比如我们需要导入Map类，那么需要手动导入，如果不需要使用了，删除了Map的实例，导入的包也需要手动删除，设置了这个功能这个就不需要手动了，自动帮你实现自动导入包和去包，不方便截图，效果请亲测~
**设置方法**
File–>settings–>Editor–>general–>Auto Import–>

![在这里插入图片描述](images/Others/2018103015593523.png)



### 单行显示多个Tabs

**效果图**
默认是显示单排的Tabs:
![在这里插入图片描述](images/Others/20181030160351154.png)
单行显示多个Tabs:

![在这里插入图片描述](images/Others/20181030160604417.png)
**设置方法**
File–>settings–>Editor–>General -->Editor Tabs–>去掉√
![在这里插入图片描述](images/Others/20181030160533499.png)



### 设置字体

**效果图**
备注：默认安装启动Idea字体很小，看着不习惯，需要调整字体大小与字体（有需要可以调整）
**设置方法**
File–>settings–>Editor–>Font–>
![在这里插入图片描述](images/Others/20181030161017921.png)



### 配置类文档注释信息和方法注释模版

**效果图**
备注：团队开发时方便追究责任与管理查看
![在这里插入图片描述](images/Others/20181030161142910.png)
![在这里插入图片描述](images/Others/20181030161254216.png)
**设置方法**
https://blog.csdn.net/zeal9s/article/details/83514565



### 水平或者垂直显示代码

**效果图**
备注：Eclipse如果需要对比代码，只需要拖动Tabs即可，但是idea要设置
![在这里插入图片描述](images/Others/20181030162041400.png)
**设置方法**
鼠标右击Tabs
![在这里插入图片描述](images/Others/20181030161922248.png)



### 更换快捷键

**效果图**
备注：从Eclipse移植到idea编码，好多快捷键不一致，导致编写效率降低，现在我们来更换一下快捷键
**设置方法**

- 方法一：

File–>Setting–>
![在这里插入图片描述](images/Others/20181030165223996.png)

例如设置成Eclipse的，设置好了之后可以ctrl+d删除单行代码（idea是ctrl+y）

- 方法二：设置模板
- File–>Setting–>
  ![在这里插入图片描述](images/Others/20181030165549295.png)
- 方法三：

![在这里插入图片描述](images/Others/20181030165842703.png)
以ctrl+o重写方法为例

![在这里插入图片描述](images/Others/20181030170008544.png)



### 注释去掉斜体

**效果图**
![在这里插入图片描述](images/Others/20181031135509461.png)
**设置方法**
File–>settings–>Editor–>
![在这里插入图片描述](images/Others/20181031135416445.png)

![在这里插入图片描述](images/Others/20181031135540101.png)



### 代码检测警告提示等级设置

![在这里插入图片描述](images/Others/20190316140152621.png)
强烈建议，不要给关掉，不要嫌弃麻烦，他的提示都是对你好，帮助你提高你的代码质量，很有帮助的。



### 项目目录相关–折叠空包

![在这里插入图片描述](images/Others/20190316140238852.png)



### 窗口复位

![在这里插入图片描述](images/Others/20190316140505814.png)
这个就是当你把窗口忽然间搞得乱七八糟的时候，还可以挽回，就是直接restore一下，就好啦。



### 查看本地代码历史

![在这里插入图片描述](images/Others/20190316140617590.png)



## 常用插件

### .ignore

生成各种ignore文件，一键创建git ignore文件的模板，免得自己去写，如下图。

地址：https://plugins.jetbrains.com/plugin/7495--ignore

![ignore](images/Others/ignore.gif)



### Lombok

支持lombok的各种注解，从此不用写getter setter这些 可以把注解还原为原本的java代码 非常方便。

地址：https://plugins.jetbrains.com/plugin/6317-lombok-plugin

![Lombok](images/Others/Lombok.gif)



### GsonFormat

一键根据json文本生成java类  非常方便。

地址：https://plugins.jetbrains.com/plugin/7654-gsonformat

![GsonFormat](images/Others/GsonFormat.gif)



### GenerateAllSetter

一键调用一个对象的所有set方法并且赋予默认值 在对象字段多的时候非常方便。

地址：https://plugins.jetbrains.com/plugin/9360-generateallsetter

![GenerateAllSetter](images/Others/GenerateAllSetter.gif)



### GenerateSerialVersionUID

`Alt + Insert` 生成`serialVersionUID`

![GenerateSerialVersionUID](images/Others/GenerateSerialVersionUID.gif)



### MyBatisCodeHelper-Pro

MybatisCodeHelperPro 是一款IDEA下全方位支持Mybatis的插件 大部分功能是免费的。

① 接口与xml 互相跳转 高清图标 更改图标 使用快捷键跳转

![MyBatisCodeHelper-Pro](images/Others/MyBatisCodeHelper-Pro.gif)

② 一键添加param注解

![addParamAnnotation](images/Others/addParamAnnotation.gif)



### Maven Helper

一键查看maven依赖，查看冲突的依赖，一键进行exclude依赖，对于大型项目 非常方便。

地址：https://plugins.jetbrains.com/plugin/7179-maven-helper

![Maven-Helper](images/Others/Maven-Helper.gif)



### Rainbow Brackets

代码作色工具（Rainbow Brackets）插件可以实现配对括号相同颜色，并且实现选中区域代码高亮的功能。

- 高亮效果快捷键
  - mac: command+鼠标右键单击
  - windows: ctrl+鼠标右键单击

- 选中部分外暗淡效果快捷键：alt+鼠标右键单击

地址：https://plugins.jetbrains.com/plugin/10080-rainbow-brackets

![Rainbow-Brackets](images/Others/Rainbow-Brackets.gif)

事实上，代码作色之后，可以非常方便我们阅读。类似的工具还有：Grep Console 来自定义设置控制台输出颜色等。



### HighlightBracketPair

自动化高亮显示光标所在代码块对应的括号，可以定制颜色和形状。

![HighlightBracketPair](images/Others/HighlightBracketPair.gif)
![HighlightBracketPair-set](images/Others/HighlightBracketPair-set.jpg)



### CodeGlance

在编辑区的右侧显示的代码地图。

![CodeGlance](images/Others/CodeGlance.png)



### Alibaba Java Coding Guidelines

阿里巴巴出品的java代码规范插件（p3c）。可以扫描整个项目找到不规范的地方 并且大部分可以自动修复。Alibaba Java Code Guidelines 插件实现了开发手册中的的 53 条规则，大部分基于 PMD 实现，其中有 4 条规则基于 IDEA 实现，并且基于 IDEA Inspection 实现了实时检测功能。部分规则实现了 Quick Fix 功能。目前，插件检测有两种模式：实时检测、手动触发。

地址：https://plugins.jetbrains.com/plugin/10046-alibaba-java-coding-guidelines



### Key promoter X

Key Promoter X 是一个**快捷键提示插件**，如果鼠标操作是能够用快捷键替代，Key Promoter X 会提示可以用什么快捷键替代。详细使用文档。

地址：https://plugins.jetbrains.com/plugin/9792-key-promoter-x

![key-promoter-x](images/Others/key-promoter-x.gif)


### Translation

最好用的翻译插件，功能很强大，界面很漂亮。

地址：https://plugins.jetbrains.com/plugin/8579-translation

![Translation](images/Others/Translation.gif)



### SequenceDiagram

时序图生成工具。有时我们需要梳理业务逻辑或者阅读源码。从中，我们需要了解整个调用链路，反向生成 UML 的时序图是强需求。其中，SequenceDiagram 插件是一个非常棒的插件。

地址：https://plugins.jetbrains.com/plugin/8286-sequencediagram

![SequenceDiagram](images/Others/SequenceDiagram.gif)



### CamelCase

命名风格转换插件，可以在 kebab-case，SNAKE_CASE，PascalCase，camelCase，snake_case 和 空格风格之间切换。快捷键苹果为 **⇧+⌥+ U** ，windows 下为 **Shift + Alt +U**。

![CamelCase](images/Others/CamelCase.gif)



###  MybatisX

**Mybatis-plus** 团队为 **Mybatis** 开发的插件，提供了 **Mapper** 接口和 **XML**之间的跳转和自动生成模版的功能。另外这个名字是我起的，嘿嘿！

![MybatisX](images/Others/MybatisX.gif)





### Git Commit Template

老是有人吐槽你提交的 **Git** 不规范？你可以试试这个插件。它提供了很好的 **Git** 格式化模版，你可以按照实际情况格式化你的提交信息。

![Git-Commit-Template](images/Others/Git-Commit-Template.jpg)



### Extra Icons

最后是一个美化插件，为一些文件类型提供官方没有的图标。来看看效果吧。

![Extra-Icons](images/Others/Extra-Icons.jpg)



### RestfulToolkit

开发时经常会根据 URI 的部分信息来查找对应的Controller 中方法，RestfulToolkit提供了一套 RESTful 服务开发辅助工具集。

地址：https://plugins.jetbrains.com/plugin/10292-restfultoolkit

![RestfulToolkit](images/Others/iuYryuy.jpg)

### Grep Console

### EasyCode

### CheckStyle

### Java Stream Debugger

https://www.e-learn.cn/topic/3624009

## 功能插件

### FindBugs-IDEA

检测代码中可能的bug及不规范的位置，检测的模式相比p3c更多，写完代码后检测下 避免低级bug，强烈建议用一下，一不小心就发现很多老代码的bug。

地址：https://plugins.jetbrains.com/plugin/3847-findbugs-idea

![img](images/Others/1697faf5f3381462)



### VisualVM Launcher

运行java程序的时候启动visualvm，方便查看jvm的情况 比如堆内存大小的分配，某个对象占用了多大的内存，jvm调优必备工具。

地址：https://plugins.jetbrains.com/plugin/7115-visualvm-launcher

![img](images/Others/1697faf61a88910f)





### MyBatis Log Plugin

Mybatis现在是java中操作数据库的首选，在开发的时候，我们都会把Mybatis的脚本直接输出在console中，但是默认的情况下，输出的脚本不是一个可以直接执行的。如果我们想直接执行，还需要在手动转化一下。MyBatis Log Plugin 这款插件是直接将Mybatis执行的sql脚本显示出来，无需处理，可以直接复制出来执行的，如图：

![img](images/Others/v2-2e63a1d6ddf2782ab8a0cda4d3e41502_hd.jpg)



### Activate-Power-Mode

根据Atom的插件activate-power-mode（或Power mode II）的效果移植到IDEA上。

![8](images/Others/intellij-idea-zhuangbi-top-5-5.gif)



### Background Image Plus

可设置idea背景图片的插件，不但可以设置固体的图片，还可以设置一段时间后随机变化背景图片，以及设置图片的透明度等等。

![img](images/Others/772743-20181027200424736-854569575.png)

 

### Material Theme UI

这是一款主题插件，可以让你的ide的图标变漂亮，配色搭配的很到位，还可以切换不同的颜色，甚至可以自定义颜色。默认的配色就很漂亮了，如果需要修改配色，可以在工具栏中Tools->Material Theme然后修改配色等。

![tools](images/Others/material-theme-ui-tools.png)

![](images/Others/oceanic.png)



## 集成插件

### 集成JIRA

Jira是一个广泛使用的项目与事务跟踪工具，被广泛应用于缺陷跟踪、客户服务、需求收集、流程审批、任务跟踪、项目跟踪和敏捷管理等工作领域。idea可以很好的跟它集成，参考下图：

File -> Settings ->Task -> Servers 点击右侧上面的+号，选择JIRA，然后输入JIRA的Server地址，用户名、密码即可

![IDEA-JIRA-1](images/Others/IDEA-JIRA-1.png)

然后打开Open Task界面

![IDEA-JIRA-2](images/Others/IDEA-JIRA-2.png)

如果JIRA中有分配给你的Task，idea能自动列出来

![IDEA-JIRA-3](images/Others/IDEA-JIRA-3.png)

代码修改后，向svn提交时，会自动与该任务关联

![IDEA-JIRA-4](images/Others/IDEA-JIRA-4.png)

将每次提交的代码修改与JIRA上的TASK关联后，有什么好处呢？我们每天可能要写很多代码，修复若干bug，日子久了以后，谁也不记得当初为了修复某个bug做了哪些修改，只要你按上面的操作正确提交，idea都会帮你记着这些细节：

![IDEA-JIRA-5](images/Others/IDEA-JIRA-5.png)

如上图，选择最近提交的TASK列表，选择Switch to，idea就会自动打开该TASK关联的源代码，并定位到修改过的代码行。当然如果该TASK已经Close了，也可以选择Remove将其清空。



### UML类图插件

idea已经集成了该功能，只是默认没打开，仍然打开Settings界面，定位到Plugins，输入UML，参考下图：

![img](images/Others/IDEA-UML-1.png)

 确认UML 这个勾已经勾上了，然后点击Apply，重启idea，然后仍然找一个java类文件，右击Diagram

![img](images/Others/IDEA-UML-2.png)

然后，就自个儿爽去吧

![img](images/Others/IDEA-UML-3.png)



### 集成SSH

java项目经常会在linux上部署，每次要切换到SecureCRT这类终端工具未免太麻烦，idea也想到了这一点:

![img](images/Others/IDEA-SSH-1.png)

然后填入IP、用户名、密码啥的

![img](images/Others/IDEA-SSH-2.png)

点击OK，就能连接上linux了

![img](images/Others/IDEA-SSH-3.png)

注：如果有中文乱码问题，可以在Settings里调整编码为utf-8

![img](images/Others/IDEA-SSH-4.png)

 

### 集成FTP

![img](images/Others/IDEA-FTP-1.png)

点击上图中的...，添加一个Remote Host

![img](images/Others/IDEA-FTP-2.png)

填写ftp的IP、用户名、密码，根路径啥的，然后点击Test FTP Connection，正常的话，应该能连接，如果连接不通，点击Advanced Options，参考下图调整下连接选项

![img](images/Others/IDEA-FTP-3.png)

配置了FTP连接后，在提交代码时，可以选择提交完成后将代码自动上传到ftp服务器

![img](images/Others/IDEA-FTP-4.png)

 

### Database管理工具

先看效果吧：

![img](images/Others/IDEA-Database-1.png)

有了这个，再也不羡慕vs.net的db管理功能了。配置也很简单，就是点击+号，增加一个Data Source即可

![img](images/Others/IDEA-Database-2.png)

唯一要注意的是，intellij idea不带数据库驱动，所以在上图中，要手动指定db driver的jar包路径。



## Debug

### 弹框/显示

勾选Show debug window on breakpoint，则请求进入到断点后自动激活Debug窗口：

![img](images/Others/856154-20170905111655647-1134637623.png)

如果IDEA底部没有显示工具栏或状态栏，可以在View里打开，显示出工具栏会方便我们使用：

　　![img](images/Others/856154-20170905112617351-1554043487.png)



### 快捷键

在菜单栏Run里有调试对应的功能，同时可以查看对应的快捷键：　　![img](images/Others/856154-20170905124338444-556465721.png)

 首先说第一组按钮，共8个按钮，从左到右依次如下：

　　　　![img](images/Others/856154-20170905134837851-1615718043.png)

- **Show Execution Point (Alt + F10)**：如果你的光标在其它行或其它页面，点击这个按钮可跳转到当前代码执行的行
- **Step Over (F8)**：步过，一行一行地往下走，如果这一行上有方法不会进入方法
- **Step Into (F7)**：步入，如果当前行有方法，可以进入方法内部，一般用于进入自定义方法内
- **Force Step Into (Alt + Shift + F7)**：强制步入，能进入任何方法，查看底层源码的时候可以用这个进入官方类库的方法
- **Step Out (Shift + F8)**：步出，从步入的方法内退出到方法调用处，此时方法已执行完毕，只是还没有完成赋值
- **Drop Frame (默认无)**：回退断点，后面章节详细说明
- **Run to Cursor (Alt + F9)**：运行到光标处，你可以将光标定位到你需要查看的那一行，然后使用这个功能，代码会运行至光标行，而不需要打断点
- **Evaluate Expression (Alt + F8)**：计算表达式，后面章节详细说明

第二组按钮，共7个按钮，从上到下依次如下：

 　　　　![img](images/Others/856154-20170905134011101-1824595229.png) 

- **Rerun 'xxxx'**：重新运行程序，会关闭服务后重新启动程序

- **Update 'tech' application (Ctrl + F5)**：更新程序，一般在你的代码有改动后可执行这个功能
- **Resume Program (F9)**：恢复程序，比如，你在第20行和25行有两个断点，当前运行至第20行，按F9，则运行到下一个断点(即第25行)，再按F9，则运行完整个流程，因为后面已经没有断点了
- **Pause Program**：暂停程序，启用Debug。目前没发现具体用法
- **Stop 'xxx' (Ctrl + F2)**：连续按两下，关闭程序。有时候你会发现关闭服务再启动时，报端口被占用，这是因为没完全关闭服务的原因，你就需要查杀所有JVM进程了
- **View Breakpoints (Ctrl + Shift + F8)**：查看所有断点，后面章节会涉及到
- **Mute Breakpoints**：哑的断点，选择这个后，所有断点变为灰色，断点失效，按F9则可以直接运行完程序。再次点击，断点变为红色，有效


### 变量查看

在IDEA中，参数所在行后面会显示当前变量的值：　　![img](images/Others/856154-20170905154209179-9123997.png) 

光标悬停到参数上，显示当前变量信息：

　　![img](images/Others/856154-20170905154425772-770303651.png)

![img](images/Others/856154-20170905154724866-160919363.png) 

在Variables里查看，这里显示当前方法里的所有变量：

 　　![img](images/Others/856154-20170905155339491-1166069157.png)

在Watches里，点击New Watch，输入需要查看的变量。或者可以从Variables里拖到Watche里查看：

　　![img](images/Others/856154-20170905160057038-750351531.png)

如果你发现你没有Watches，可能在下图所在的地方：

　　![img](images/Others/856154-20170905160433710-2004658473.png)

![img](images/Others/856154-20170905160515538-1647769062.png) 



### 计算表达式

　　![img](images/Others/856154-20170905160826444-1625048711.png)

![img](images/Others/856154-20170905161614694-93470669.png) 

设置变量，在计算表达式的框里，可以改变变量的值，这样有时候就能很方便我们去调试各种值的情况了不是：

![img](images/Others/856154-20170905162404288-824548249.png) 



### 智能步入

一行代码里有好几个方法，怎么只选择某一个方法进入。之前提到过使用Step Into (Alt + F7) 或者 Force Step Into (Alt + Shift + F7)进入到方法内部，但这两个操作会根据方法调用顺序依次进入，这比较麻烦。

　　那么智能步入就很方便了，智能步入，这个功能在Run里可以看到，Smart Step Into (Shift + F7)：

　　![img](images/Others/856154-20170905152523304-803289488.png)

　　按Shift + F7，会自动定位到当前断点行，并列出需要进入的方法，如图5.2，点击方法进入方法内部。

　如果只有一个方法，则直接进入，类似Force Step Into。

　　![img](images/Others/856154-20170905163730929-1374653206.png) [图5.2]



### 断点条件设置

通过设置断点条件，在满足条件时，才停在断点处，否则直接运行：

　　![img](images/Others/856154-20170905165253944-1162138475.png)  [图6.1]

点击View Breakpoints (Ctrl + Shift + F8)，查看所有断点。Java Line Breakpoints 显示了所有的断点，在右边勾选Condition，设置断点的条件。

- 勾选Log message to console，则会将当前断点行输出到控制台
- 勾选Evaluate and log，可以在执行这行代码是计算表达式的值，并将结果输出到控制台

![img](images/Others/856154-20170905170655163-1805982960.png)

　　![img](images/Others/856154-20170905170947257-1667065155.png)



### 异常断点

通过设置异常断点，在程序中出现需要拦截的异常时，会自动定位到异常行。点击+号添加Java Exception Breakpoints，添加异常断点。然后输入需要断点的异常类，如图6.7，之后可以在Java Exception Breakpoints里看到添加的异常断点。我这里添加了一个NullPointerException异常断点，出现空指针异常后，自动定位在空指针异常行：

　　![img](images/Others/856154-20170905200131851-150143203.png)

![img](images/Others/856154-20170905200305147-527881101.png) 　![img](images/Others/856154-20170905200726069-688175303.png) 



### 多线程调试

　　一般情况下我们调试的时候是在一个线程中的，一步一步往下走。但有时候你会发现在Debug的时候，想发起另外一个请求都无法进行了？那是因为IDEA在Debug时默认阻塞级别是ALL，会阻塞其它线程，只有在当前调试线程走完时才会走其它线程。可以在View Breakpoints里选择Thread，如图下图，然后点击Make Default设置为默认选项：

![img](images/Others/856154-20170905204329757-1196950664.png) 

　　切换线程，在下图中Frames的下拉列表里，可以切换当前的线程，如下我这里有两个Debug的线程，切换另外一个则进入另一个Debug的线程：![img](images/Others/856154-20170905205012663-56609868.png) 



### 回退断点

在调试的时候，想要重新走一下流程而不用再次发起一个请求？

所谓的断点回退，其实就是回退到上一个方法调用的开始处，在IDEA里测试无法一行一行地回退或回到到上一个断点处，而是回到上一个方法。回退的方式有两种：

​	方法一：是Drop Frame按钮，按调用的方法逐步回退，包括三方类库的其它方法(取消Show All Frames按钮会显示三方类库的方法，如图8.3)。

![img](images/Others/856154-20170905211428554-1617570377.png)

　　方法二：在调用栈方法上选择要回退的方法，右键选择Drop Frame(图8.4)，回退到该方法的上一个方法调用处，此时再按F9(Resume Program)，可以看到程序进入到该方法的断点处了。

　　![img](images/Others/856154-20170905212138101-113776159.png)

但有一点需要注意，断点回退只能重新走一下流程，之前的某些参数/数据的状态已经改变了的是无法回退到之前的状态的，如对象、集合、更新了数据库数据等等。



### 中断Debug

想要在Debug的时候，中断请求，不要再走剩余的流程了？

　　![img](images/Others/856154-20170905213656241-1998475384.png)

 

## 常用设置


### UID

快捷键：`ALT` + `INS`

### 折叠空包

![clipboard.png](images/Others/bV13Sa)

![clipboard.png](images/Others/bV13RH)



### 显示边沟图标

Editor→General→Gutter Icons

### 设置自动import包

可选，对于不能import \*的要求的，建议不要用这个：

[![img](images/Others/417876-20171119103804546-819180423.png)](https://images2017.cnblogs.com/blog/417876/201711/417876-20171119103804546-819180423.png)

如果非要用这个自动导入却不想导入\*的，可以通过配置这个来解决：

**![img](images/Others/417876-20171128105146972-1080966086.png)**

调整import包导入的顺序，保持和Eclipse一致：![img](images/Others/417876-20171129081632175-614878351.png)



### 右下角显示内存

[![img](images/Others/417876-20171119103943062-564729605.png)](https://images2017.cnblogs.com/blog/417876/201711/417876-20171119103943062-564729605.png)

点击右下角可以回收内存。



### 自定义Javadoc注释

@date可能不是标准的Javadoc，但是在业界标准来说，这个已经成为Javadoc必备的注释，因为大多数人都用这个来标注日期。建议：注释不要太个性，比如自定义类说明，日期时间字段等等；尽量保持统一的代码风格，建议参考阿里巴巴Java开发手册：

[![img](images/Others/417876-20171119150102656-1550889934.png)](https://images2017.cnblogs.com/blog/417876/201711/417876-20171119150102656-1550889934.png)



### 鼠标放上去自动显示文档

![设置功能](images/Others/201705221495449669133450.jpg)

![演示效果](images/Others/201705221495449833127277.png)



## 快捷键

Mac 键盘符号和修饰键说明

- `⌘` ——> `Command`
- `⇧` ——> `Shift`
- `⌥` ——> `Option`
- `⌃` ——> `Control`
- `↩︎` ——> `Return/Enter`
- `⌫` ——> `Delete`
- `⌦` ——> `向前删除键(Fn + Delete)`
- `↑` ——> `上箭头`
- `↓` ——> `下箭头`
- `←` ——> `左箭头`
- `→` ——> `右箭头`
- `⇞` ——> `Page Up(Fn + ↑)`
- `⇟` ——> `Page Down(Fn + ↓)`
- `⇥` ——> `右制表符(Tab键)`
- `⇤` ——> `左制表符(Shift + Tab)`
- `⎋` ——> `Escape(Esc)`
- `End` ——> `Fn + →`
- `Home` ——> `Fn + ←`

### Editing(编辑)

| 快捷键                                          | 作用                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| `Control + Space`                               | 基本的代码补全（补全任何类、方法、变量）                     |
| `Control + Shift + Space`                       | 智能代码补全（过滤器方法列表和变量的预期类型）               |
| `Command + Shift + Enter`                       | 自动结束代码，行末自动添加分号                               |
| `Command + P`                                   | 显示方法的参数信息                                           |
| `Control + J`                                   | 快速查看文档                                                 |
| `Shift + F1`                                    | 查看外部文档（在某些代码上会触发打开浏览器显示相关文档）     |
| `Command` + 鼠标放在代码上                      | 显示代码简要信息                                             |
| `Command + F1`                                  | 在错误或警告处显示具体描述信息                               |
| `Command + N`, `Control + Enter`, `Control + N` | 生成代码（`getter`、`setter`、`hashCode`、`equals`、`toString`、构造函数等） |
| `Control + O`                                   | 覆盖方法（重写父类方法）                                     |
| `Control + I`                                   | 实现方法（实现接口中的方法）                                 |
| `Command + Option + T`                          | 包围代码（使用`if...else`、`try...catch`、`for`、`synchronized`等包围选中的代码） |
| `Command + /`                                   | 注释 / 取消注释与行注释                                      |
| `Command + Option + /`                          | 注释 / 取消注释与块注释                                      |
| `Option` + 方向键上                             | 连续选中代码块                                               |
| `Option` + 方向键下                             | 减少当前选中的代码块                                         |
| `Control + Shift + Q`                           | 显示上下文信息                                               |
| `Option + Enter`                                | 显示意向动作和快速修复代码                                   |
| `Command + Option + L`                          | 格式化代码                                                   |
| `Control + Option + O`                          | 优化 import                                                  |
| `Control + Option + I`                          | 自动缩进线                                                   |
| `Tab / Shift + Tab`                             | 缩进代码 / 反缩进代码                                        |
| `Command + X`                                   | 剪切当前行或选定的块到剪贴板                                 |
| `Command + C`                                   | 复制当前行或选定的块到剪贴板                                 |
| `Command + V`                                   | 从剪贴板粘贴                                                 |
| `Command + Shift + V`                           | 从最近的缓冲区粘贴                                           |
| `Command + D`                                   | 复制当前行或选定的块                                         |
| `Command + Delete`                              | 删除当前行或选定的块的行                                     |
| `Control + Shift + J`                           | 智能的将代码拼接成一行                                       |
| `Command + Enter`                               | 智能的拆分拼接的行                                           |
| `Shift + Enter`                                 | 开始新的一行                                                 |
| `Command + Shift + U`                           | 大小写切换                                                   |
| `Command + Shift + ]` / `Command + Shift + [`   | 选择直到代码块结束 / 开始                                    |
| `Option + Fn + Delete`                          | 删除到单词的末尾                                             |
| `Option + Delete`                               | 删除到单词的开头                                             |
| `Command` + 加号 / `Command` + 减号             | 展开 / 折叠代码块                                            |
| `Command + Shift` + 加号                        | 展开所以代码块                                               |
| `Command + Shift` + 减号                        | 折叠所有代码块                                               |
| `Command + W`                                   | 关闭活动的编辑器选项卡                                       |



### Search/Replace(查询/替换)

| 快捷键                | 作用                                                      |
| --------------------- | --------------------------------------------------------- |
| `Double Shift`        | 查询任何东西                                              |
| `Command + F`         | 文件内查找                                                |
| `Command + G`         | 查找模式下，向下查找                                      |
| `Command + Shift + G` | 查找模式下，向上查找                                      |
| `Command + R`         | 文件内替换                                                |
| `Command + Shift + F` | 全局查找（根据路径）                                      |
| `Command + Shift + R` | 全局替换（根据路径）                                      |
| `Command + Shift + S` | 查询结构（Ultimate Edition 版专用，需要在 Keymap 中设置） |
| `Command + Shift + M` | 替换结构（Ultimate Edition 版专用，需要在 Keymap 中设置） |



### Usage Search(使用查询)

| 快捷键                         | 作用                              |
| ------------------------------ | --------------------------------- |
| `Option + F7` / `Command + F7` | 在文件中查找用法 / 在类中查找用法 |
| `Command + Shift + F7`         | 在文件中突出显示的用法            |
| `Command + Option + F7`        | 显示用法                          |



### Compile and Run(编译和运行)

| 快捷键                                       | 作用                       |
| -------------------------------------------- | -------------------------- |
| `Command + F9`                               | 编译 Project               |
| `Command + Shift + F9`                       | 编译选择的文件、包或模块   |
| `Control + Option + R`                       | 弹出 Run 的可选择菜单      |
| `Control + Option + D`                       | 弹出 Debug 的可选择菜单    |
| `Control + R`                                | 运行                       |
| `Control + D`                                | 调试                       |
| `Control + Shift + R`, `Control + Shift + D` | 从编辑器运行上下文环境配置 |



### Debugging(调试)

| 快捷键                 | 作用                                                         |
| ---------------------- | ------------------------------------------------------------ |
| `F8`                   | 进入下一步，如果当前行断点是一个方法，则不进入当前方法体内   |
| `F7`                   | 进入下一步，如果当前行断点是一个方法，则进入当前方法体内，如果该方法体还有方法，则不会进入该内嵌的方法中 |
| `Shift + F7`           | 智能步入，断点所在行上有多个方法调用，会弹出进入哪个方法     |
| `Shift + F8`           | 跳出                                                         |
| `Option + F9`          | 运行到光标处，如果光标前有其他断点会进入到该断点             |
| `Option + F8`          | 计算表达式（可以更改变量值使其生效）                         |
| `Command + Option + R` | 恢复程序运行，如果该断点下面代码还有断点则停在下一个断点上   |
| `Command + F8`         | 切换断点（若光标当前行有断点则取消断点，没有则加上断点）     |
| `Command + Shift + F8` | 查看断点信息                                                 |



### Navigation（导航）

| 快捷键                                                       | 作用                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Command + O`                                                | 查找类文件                                                   |
| `Command + Shift + O`                                        | 查找所有类型文件、打开文件、打开目录，打开目录需要在输入的内容前面或后面加一个反斜杠`/` |
| `Command + Option + O`                                       | 前往指定的变量 / 方法                                        |
| `Control` + 方向键左 / `Control` + 方向键右                  | 左右切换打开的编辑 tab 页                                    |
| `F12`                                                        | 返回到前一个工具窗口                                         |
| `Esc`                                                        | 从工具窗口进入代码文件窗口                                   |
| `Shift + Esc`                                                | 隐藏当前或最后一个活动的窗口，且光标进入代码文件窗口         |
| `Command + Shift + F4`                                       | 关闭活动 `run/messages/find/... tab`                         |
| `Command + L`                                                | 在当前文件跳转到某一行的指定处                               |
| `Command + E`                                                | 显示最近打开的文件记录列表                                   |
| `Option` + 方向键左 / `Option` + 方向键右                    | 光标跳转到当前单词 / 中文句的左 / 右侧开头位置               |
| `Command + Option` + 方向键左 / `Command + Option` + 方向键右 | 退回 / 前进到上一个操作的地方                                |
| `Command + Shift + Delete`                                   | 跳转到最后一个编辑的地方                                     |
| `Option + F1`                                                | 显示当前文件选择目标弹出层，弹出层中有很多目标可以进行选择(如在代码编辑窗口可以选择显示该文件的 Finder) |
| `Command + B` / `Command` + 鼠标点击                         | 进入光标所在的方法/变量的接口或是定义处                      |
| `Command + Option + B`                                       | 跳转到实现处，在某个调用的方法名上使用会跳到具体的实现处，可以跳过接口 |
| `Option + Space`, `Command + Y`                              | 快速打开光标所在方法、类的定义                               |
| `Control + Shift + B`                                        | 跳转到类型声明处                                             |
| `Command + U`                                                | 前往当前光标所在方法的父类的方法 / 接口定义                  |
| `Control` + 方向键下 / `Control` + 方向键上                  | 当前光标跳转到当前文件的前一个 / 后一个方法名位置            |
| `Command + ]` / `Command + [`                                | 移动光标到当前所在代码的花括号开始 / 结束位置                |
| `Command + F12`                                              | 弹出当前文件结构层，可以在弹出的层上直接输入进行筛选（可用于搜索类中的方法） |
| `Control + H`                                                | 显示当前类的层次结构                                         |
| `Command + Shift + H`                                        | 显示方法层次结构                                             |
| `Control + Option + H`                                       | 显示调用层次结构                                             |
| `F2` / `Shift + F2`                                          | 跳转到下一个 / 上一个突出错误或警告的位置                    |
| `F4` / `Command` + 方向键下                                  | 编辑 / 查看代码源                                            |
| `Option + Home`                                              | 显示到当前文件的导航条                                       |
| `F3`                                                         | 选中文件 / 文件夹 / 代码行，添加 / 取消书签                  |
| `Option + F3`                                                | 选中文件 / 文件夹/代码行，使用助记符添加 / 取消书签          |
| `Control + 0`…`Control + 9`                                  | 定位到对应数值的书签位置                                     |
| `Command + F3`                                               | 显示所有书签                                                 |



### Refactoring（重构）

| 快捷键                 | 作用                               |
| ---------------------- | ---------------------------------- |
| `F5`                   | 复制文件到指定目录                 |
| `F6`                   | 移动文件到指定目录                 |
| `Command + Delete`     | 在文件上为安全删除文件，弹出确认框 |
| `Shift + F6`           | 重命名文件                         |
| `Command + F6`         | 更改签名                           |
| `Command + Option + N` | 一致性                             |
| `Command + Option + M` | 将选中的代码提取为方法             |
| `Command + Option + V` | 提取变量                           |
| `Command + Option + F` | 提取字段                           |
| `Command + Option + C` | 提取常量                           |
| `Command + Option + P` | 提取参数                           |



### VCS / Local History（版本控制 / 本地历史记录）

| 快捷键               | 作用                       |
| -------------------- | -------------------------- |
| `Command + K`        | 提交代码到版本控制器       |
| `Command + T`        | 从版本控制器更新代码       |
| `Option + Shift + C` | 查看最近的变更记录         |
| `Control + C`        | 快速弹出版本控制器操作面板 |



### Live Templates（动态代码模板）

| 快捷键                 | 作用                                           |
| ---------------------- | ---------------------------------------------- |
| `Command + Option + J` | 弹出模板选择窗口，将选定的代码使用动态模板包住 |
| `Command + J`          | 插入自定义动态代码模板                         |



### General（通用）

| 快捷键                      | 作用                                                         |
| --------------------------- | ------------------------------------------------------------ |
| `Command + 1`…`Command + 9` | 打开相应编号的工具窗口                                       |
| `Command + S`               | 保存所有                                                     |
| `Command + Option + Y`      | 同步、刷新                                                   |
| `Control + Command + F`     | 切换全屏模式                                                 |
| `Command + Shift + F12`     | 切换最大化编辑器                                             |
| `Option + Shift + F`        | 添加到收藏夹                                                 |
| `Option + Shift + I`        | 检查当前文件与当前的配置文件                                 |
| Control + `                 | 快速切换当前的 scheme（切换主题、代码样式等）                |
| `Command + ,`               | 打开 IDEA 系统设置                                           |
| `Command + ;`               | 打开项目结构对话框                                           |
| `Shift + Command + A`       | 查找动作（可设置相关选项）                                   |
| `Control + Shift + Tab`     | 编辑窗口标签和工具窗口之间切换（如果在切换的过程加按上 delete，则是关闭对应选中的窗口） |



# Product

## Axure RP

提供快速原型设计工具。



## 蓝湖

提供产品设计。

地址：https://lanhuapp



## 墨刀

地址：https://modao.cc/feature/flowchart

提供原型、流程图、设计图、思维导图等功能。



#  Manger

## 时间管理

### 四象限法则

使用四象限法则来确定需要做的事情的优先级。

![时间管理-四象限法则](images/Others/时间管理-四象限法则.png)

### 番茄工作法

![番茄工作法](images/Others/番茄工作法.jpeg)

**番茄工作法优点**

- 减轻对时间的焦虑
- 提高工作效率、集中力、注意力，减少工作中断
- 增强决策意识
- 激励效果唤醒持久工作奖励
- 巩固达成工作目标的决心
- 完善工作任务预估流程，精确任务时间和质量
- 优化工作、学习的流程，提高时间效率
- 锻炼工作时间把控与高效时间管理能力



**番茄工作法原则**

- 每一个番茄时间约为25分钟，每完成一个番茄时间休息5分钟
- 在每一个番茄时间里，如遇突发事件被迫打断，该番茄时间作废
- 非必需马山待办事项应安排到下一个番茄时间处理，并记录到敬业签
- 每连续完成4个番茄时间后，建议休息时间增加到25分钟作为奖励



### PDCA循环管理

PDCA是最早由美国质量统计控制之父Shewhat（休哈特)提出的PDS（Plan Do See）演化而来，由美国质量管理专家戴明改进成为PDCA模式，所以又称为“戴明环”;它是全面质量管理所应遵循的科学程序。全面质量管理活动的全部过程，就是质量计划的制订和组织实现的过程，这个过程就是按照PDCA循环，不停顿地周而复始地运转的。

![pdca](images/Others/pdca.png)

- **P——Plan（计划）**
  包括方针和目标的确定，以及活动规划的制定。
- **D——Do（执行）**
  根据已知的信息，设计具体的方法、方案和计划布局；再根据设计和布局，进行具体运作，实现计划中的内容。
- **C——Check（检查）**
  总结执行计划的结果，分清哪些对了，哪些错了，明确效果，找出问题。
- **A——Action（处理）**
  对总结检查的结果进行处理，对成功的经验加以肯定，并予以标准化；对于失败的教训也要总结，引起重视。对于没有解决的问题，应提交给下一个PDCA循环中去解决。

每件事情，通常我们会先做计划（P），计划完了以后去实施（D），实施的过程中进行检查（C），检查执行结果是否达到了预期，分析影响的因素、出现问题的原因，并提出解决的措施，然后再把检查的结果进行改进、实施、改善（A）。



**适应范围**

PDCA循环工作方法无论是在解决生产质量问题上还是在解决企业管理问题以及完善人生目标方面，都不愧为一个好的、有益的工作方法。 　



**现代观点**

- **P(Planning)**：计划，包括三小部分：目标（goal）、实施计划（plan）、收支预算（budget）
- **D(design)**：设计方案和布局
- **C(4C)**：4C管理，Check（检查）、Communicate（沟通）、Clean （清理）、Control（控制）
- **A(2A)**：Act（执行，对总结检查的结果进行处理）、Aim（按照目标要求行事，如改善、提高）



## 项目管理



## 团队管理

### 离职退群方式

- 大群悄悄退，无伤大碍
- 小群知会领导，正式退场
- 关系好的同事群，发个红包再退群
- 同事微信别删，都是日后资源



## 知识卡片

https://www.yinxiang.com/everhub/

### 多维度思考

![独立思考的三条法则](images/Others/独立思考的三条法则.jpg)

![坚持健康思考的3条法则](images/Others/坚持健康思考的3条法则.jpg)

![创造性思考的3条法则](images/Others/创造性思考的3条法则.jpg)

![合作性思考的3条法则](images/Others/合作性思考的3条法则.jpg)



## 演讲能力

### PPT演讲力

#### 定位PPT演讲主题

![定位PPT演讲主题](images/Others/定位PPT演讲主题.jpg)



#### PPT演讲创新思维

![PPT演讲创新思维](images/Others/PPT演讲创新思维.jpg)



#### PPT演讲的逻辑结构

![PPT演讲的逻辑结构](images/Others/PPT演讲的逻辑结构.jpg)



#### 讲出好故事的HIT大法

![讲出好故事的HIT大发](images/Others/讲出好故事的HIT大发.jpg)



#### 自我介绍公式MTV

![自我介绍公式MTV](images/Others/自我介绍公式MTV.jpg)



#### 打造个人品牌营销

![打造个人品牌营销](images/Others/打造个人品牌营销.jpg)



#### 顶级演讲者的素养

![顶级演讲者的素养](images/Others/顶级演讲者的素养.jpg)



#### 六步准备高光演讲

![六步准备高光演讲](images/Others/六步准备高光演讲.jpg)



#### PPT演讲大树模型

![PPT演讲大树模型](images/Others/PPT演讲大树模型.jpeg)



### 即兴演讲

![即兴交流的7种力量](images/Others/即兴交流的7种力量.jpg)



### 精简发言

![精简发言的3个重点](images/Others/精简发言的3个重点.jpg)

