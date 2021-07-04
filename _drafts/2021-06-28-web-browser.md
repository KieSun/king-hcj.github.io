---
layout: post
title: Web浏览器面面观
categories: Chrome
description: Web 浏览器面面观
keywords: Chrome, Chrome V8, JavaScriptCore, JS, 前端, JavaScript
---

&emsp;&emsp;浏览器的主要功能就是向服务器发出请求，在浏览器窗口中展示HTML文档、PDF、图片、视频等网络内容。这些网络资源的位置由用户使用 URI（统一资源标示符）来指定指定。

&emsp;&emsp;获取在大多数人眼中，浏览器是这样的：

![大多数人眼中的浏览器](https://king-hcj.github.io/images/browser/black-box.png?raw=true)

&emsp;&emsp;一个展示前端，一个未知的中间层连接着网络世界；甚至，网络世界也可以省略：一台显示器，一个神秘的幕后黑盒。

&emsp;&emsp;如果你是一个前端开发者，甚至每天浏览器陪伴你度过的时光比女朋友陪伴你的都要久，想想那每一个令人“不是那么期待”的早晨，每一个争分夺秒完成任务的黄昏，只有浏览器和编辑器一直是你忠实的伙伴。而就连你一直离不开的VS Code编辑器，甚至也与浏览器有着莫大的渊源。
&emsp;&emsp;屏幕前的朋友，你熟悉自己身边的那些人吗，熟悉那些与你朝夕相伴的朋友吗？也许熟悉，也许补，那么，你是否愿意花些时间来熟悉一下这个在大量时间里与你有着莫大交集的浏览器的内心世界呢？

&emsp;&emsp;今天，我们就来一探究竟，走进这个我们与网络连接最紧密的中间地带。

## 浏览器发展简史

### 浏览器的诞生与发展

&emsp;&emsp;第一款浏览器诞生于1990年，但是现代浏览器的雏形却出现在1980s年代。

&emsp;&emsp;一位名叫蒂姆·伯纳斯-李的英国科学家在 1980 年代初期创建了一个名为 Inquire 的计算机程序，当时他在总部位于瑞士的欧洲核研究组织（CERN，以其法文字母表示）工作。该计划旨在使在 CERN 工作的许多不同个人更容易共享信息。

&emsp;&emsp;1990年，第一款浏览器问世于Tim Berners-Lee 在 CERN 工作期间。您可能想知道 Web 浏览器到底是什么，简而言之，它是一个计算机程序，其目的是显示和检索数据。使用分配给存储在网络服务器上的每个数据集（网页）的 URL，它可以做到这一点。所以这意味着当您在浏览器中输入内容时，您实际上是在输入地址，浏览器将使用该地址来获取您想要查看的信息。浏览器的另一个关键功能是以易于理解的方式向您解释和呈现计算机代码。

&emsp;&emsp;浏览器简史：

![Timeline_of_the_Web_Browsers](https://king-hcj.github.io/images/browser/Timeline_of_the_Web_Browsers.jpg?raw=true)

&emsp;&emsp;早期的浏览器：

![The-Early-Browsers](https://king-hcj.github.io/images/browser/The-Early-Browsers.jpeg?raw=true)

&emsp;&emsp;浏览器诞生之后的故事，想必您已经早有耳闻：

- NCSA Mosaic，或简称Mosaic，是互联网历史上第一个获普遍使用和能够显示图片的网页浏览器。它是由伊利诺伊大学厄巴纳-香槟分校的NCSA组织在1993年所发表，并于1997年1月7日正式终止开发和支持。在当时人气爆发的大受欢迎。Mosaic的出现，算是点燃了后期互联网热潮的火种之一。后来网景导航者浏览器的开发工作，聘用了许多原有的Mosaic浏览器工程师，但是没有采用Mosaic网页浏览器的任何代码。传承网景浏览器代码的后裔为Firefox浏览器。

- Marc Andreesen 与同事 Jim Clark 于 1994 年成立了一家公司，当时 Mosaic 还是最流行的浏览器，它们计划打造出一个比 Mosaic 更好的浏览器，占领市场，让他们变得富有，并改变历史。他们的第一个浏览器被称为 Mosaic Netscape 0.9，不久更名 Netscape。得益于 JavaScript 和“partial-screen loading”（即使页面未完全加载，用户也可以开始阅读页面上的详细信息，这一个新概念极大地丰富了在线体验）等功能，它很快成为市场领导者，占据了浏览器市场上一半的份额，Netscape 的 IPO 也助长了日益增长的网络泡沫。

- Netscape 最初的成功向那些在计算机和互联网领域工作的人证明了时代已经永远改变了，这让当时业内最强大的参与者感到震惊。一家名为 Microsoft 的西雅图公司就是这样一家公司。Netscape 对微软来说是一个挑战，微软在 1990 年代后期创建了自己的浏览器 Internet Explorer，但它通常被视为劣质产品。由于其跨平台特性，人们可以在 Windows PC 或 Mac 或任何其他系统上使用 Netscape，这导致许多人猜测**操作系统的时代已经结束**。计算机将通过浏览器运行，浏览器可以在任何机器上运行，从而使软件行业民主化并降低其相当大的进入壁垒。**微软已经建立了销售其专有操作系统 Windows 的帝国**，因此将这种由 Netscape 等公司带头的发展视为一种威胁。微软通过对其产品的大量投资，成功地迅速扭转了浏览器行业的局面，使其与 Netscape 一样好。Windows 计算机在发布时已经安装了 Internet Explorer（Microsoft 的浏览器），这使其能够在市场上占据一席之地并不断发展壮大，最终在浏览器领域取得了胜利。

![Market_Share_During_the_Browser_Wars](https://king-hcj.github.io/images/browser/Market_Share_During_the_Browser_Wars.jpg?raw=true)

&emsp;&emsp;市场份额的快速下滑导致 Netscape 在 2000 年卖给了 AOL，2008 年Netscape最终灭绝。
&emsp;&emsp;到 2003 年，微软的 Internet Explorer 控制了 92% 以上的市场，完全扭转了 1995 年的局面。然而，虽然微软在不到十年的时间里成功地完全接管了浏览器市场，但很快就会出现其他竞争，再次重塑网络浏览器的历史。

- 在微软在 1990 年代后期崛起并让 Netscape 等公司屈服之后，浏览器的历史似乎已经走到了尽头。然而，正如最初发布后的情况一样，Internet Explorer 正在成为劣质产品。谷歌于 2008 年推出了其专有浏览器——Chrome。到 2012 年底，即推出仅四年后，谷歌 Chrome 浏览器凭借其易用性、跨平台功能、速度以及与标签和书签相关的特殊功能，取代 Internet Explorer 成为最受欢迎的浏览器。

- 在 2000 年代初期，可能是在微软将浏览器附加到其操作系统之后，Apple 发布了 Safari，一种专为 Mac 设计的浏览器，并成为目前市场上第二大浏览器。

- Internet Explorer 的流行度在 2000 年代后期逐渐减少，主要是因为它变得缓慢和过时，而 Microsoft 发现自己现在似乎已经是在外面观察浏览器世界。该公司不想继续错过，于是着手解决这个问题，但发现一个关键问题是“Internet Explorer”这个名字已经成为劣质浏览器的同义词。因此，为了尝试重新进入游戏，微软不得不重新命名，它通过发布 Edge 来实现，这是微软浏览器的最新版本，它收到了很多好评，但对于 Microsoft 来说，作为 Edge 可能为时已晚。

- IE浏览器终成时代之泪，Microsoft Edge成为Windows 11的默认浏览器。这是Windows系统更新20年来，IE的首次缺席，也是最后一次。早在Win10更新时微软就表示，将放弃更新IE转向开发新的浏览器Microsoft Edge。如今是彻底要和桌面上的IE说再见了。 —— IE 浏览器将在 2022 年安息，它也将从 Windows 11 中消失。

### 浏览器市场份额

&emsp;&emsp;截止2021年7月初，浏览器市场份额如下：

&emsp;&emsp;近年来浏览器使用趋势变化：

![Web_Browser_Usage_Trends](https://king-hcj.github.io/images/browser/Web_Browser_Usage_Trends.png?raw=true)

&emsp;&emsp;浏览器市场份额：

![Web_Browser_Market_Share](https://king-hcj.github.io/images/browser/Web_Browser_Market_Share.png?raw=true)


&emsp;&emsp;国内浏览器市场份额：

![Web_Browser_Market_Share_CHN](https://king-hcj.github.io/images/browser/Web_Browser_Market_Share_CHN.png?raw=true)

如何查看浏览器市场份额：

- 国内浏览器市场份额
  - [浏览器市场份额](https://tongji.baidu.com/research/site){:target='\_blank'}
- 全球浏览器市场份额
  - [全球浏览器市场份额](https://gs.statcounter.com/){:target='\_blank'}
  - [w3counter](https://www.w3counter.com/globalstats.php){:target='\_blank'}


### 参考资料

- [The Story of the Web: A History Of Internet Browsers](https://www.internetadvisor.com/the-story-of-the-web-a-history-of-internet-browsers){:target='_blank'}
- [THE HISTORY OF THE WEB BROWSER](https://minimalistwpthemes.com/history-of-the-web-browser/){:target='_blank'}
- [浏览器简史](http://www.cnw.com.cn/zhuanti/2009-ie/){:target='_blank'}

## 浏览器架构

### 计算机的核心

#### CPU

&emsp;&emsp;中央处理器（Central Processing Unit），或简称为 CPU。CPU 可以看作是计算机的大脑。**一个 CPU 核心如图中的办公人员，可以逐一解决很多不同任务**。它可以在解决从数学到艺术一切任务的同时还知道如何响应客户要求。过去 CPU 大多是单芯片的，一个核心就像存在于同芯片的另一个 CPU。随着现代硬件发展，你经常会有不止一个内核，为你的手机和笔记本电脑提供更多的计算能力。

&emsp;&emsp;4 个 CPU 核心作为办公人员，坐在办公桌前处理各自的工作：

![CPU](https://king-hcj.github.io/images/browser/CPU.png?raw=true)

#### GPU

&emsp;&emsp;图形处理器（Graphics Processing Unit，简称为 GPU）是计算机的另一部件。与 CPU 不同，GPU 擅长同时处理跨内核的简单任务。顾名思义，**它最初是为解决图形而开发的**。这就是为什么在图形环境中“使用 GPU” 或 “GPU 支持”都与快速渲染和顺滑交互有关。近年来随着 GPU 加速计算的普及，仅靠 GPU 一己之力也使得越来越多的计算成为可能。

&emsp;&emsp;许多带特定扳手的 GPU 内核意味着它们只能处理有限任务

![GPU](https://king-hcj.github.io/images/browser/GPU.png?raw=true)

&emsp;&emsp;当你在电脑或手机上启动应用时，是 **CPU 和 GPU 为应用供能**。通常情况下应用是通过操作系统提供的机制在 CPU 和 GPU 上运行。

&emsp;&emsp;三层计算机体系结构，底部是机器硬件，中间是操作系统，顶部是应用程序。

![hw-os-app](https://king-hcj.github.io/images/browser/hw-os-app.png?raw=true)


#### 进程与线程

&emsp;&emsp;进程可以被描述为是一个应用的执行程序。线程是位于进程内部并执行其进程程序的任意部分。

&emsp;&emsp;启动应用时会创建一个进程。程序也许会创建一个或多个线程来帮助它工作，这是可选的。操作系统为进程提供了一个可以使用的“一块”内存，所有应用程序状态都保存在该私有内存空间中。关闭应用程序时，相应的进程也会消失，操作系统会释放内存。

![memory](https://king-hcj.github.io/images/browser/memory.svg?raw=true)

&emsp;&emsp;进程可以请求操作系统启动另一个进程来执行不同的任务。此时，内存中的不同部分会分给新进程。如果两个进程需要对话，他们可以通过**进程间通信（IPC）**来进行。许多应用都是这样设计的，所以如果一个工作进程失去响应，该进程就可以在不停止应用程序不同部分的其他进程运行的情况下重新启动。

![workerprocess](https://king-hcj.github.io/images/browser/workerprocess.svg?raw=true)

### 浏览器的进程/线程架构模型

&emsp;&emsp;关于如何构建 web 浏览器并不存在标准规范，一个浏览器的构建方法可能与另一个迥然不同。不同浏览器架构的进程/线程一般由下图几部分：

![browser-arch](https://king-hcj.github.io/images/browser/browser-arch.png?raw=true)

&emsp;&emsp;而当下“浏览器世界的王者” Chrome 架构如下图所示，渲染进程下显示了多个层，表明 Chrome 为每个标签页运行多个渲染进程。

![browser-arch-chrome](https://king-hcj.github.io/images/browser/browser-arch-chrome.png?raw=true)

&emsp;&emsp;顶部是浏览器进程，它与处理应用其它模块任务的进程进行协调。对于渲染进程来说，创建了多个渲染进程并分配给了每个标签页。直到最近，Chrome 在可能的情况下给每个标签页分配一个进程。而现在它试图给每个站点分配一个进程，包括 iframe。

- 浏览器进程：控制应用中的 “Chrome” 部分，包括地址栏，书签，回退与前进按钮。以及处理 web 浏览器不可见的特权部分，如网络请求与文件访问。
- 渲染进程：控制标签页内网站展示。
- 插件进程：控制站点使用的任意插件，如 Flash。
- GPU进程：处理独立于其它进程的 GPU 任务。GPU 被分成不同进程，因为 GPU 处理来自多个不同应用的请求并绘制在相同表面。

&emsp;&emsp;不同进程指向浏览器 UI 的不同部分：

![browserui](https://king-hcj.github.io/images/browser/browserui.png?raw=true)


&emsp;&emsp;更多进程信息，可通过在浏览器顶栏右键，任务管理器查看。或者可以点击右上角的选项菜单图标，选择更多工具，然后选择任务管理器。在任务管理器面板会列出当前正在运行的进程以及它们当前的 CPU/内存使用量。

![task](https://king-hcj.github.io/images/browser/task.png?raw=true)

&emsp;&emsp;前文中提到了 Chrome 使用多个渲染进程，那他有什么优势呢？

- 稳定：最简单的情况下，你可以想象每个标签页都有自己的渲染进程。假设你打开了三个标签页，每个标签页都拥有自己独立的渲染进程。如果某个标签页失去响应，你可以关掉这个标签页，此时其它标签页依然运行着，可以正常使用。如果所有标签页都运行在同一进程上，那么当某个失去响应，所有标签页都会失去响应，显然这样的体验会很糟糕，下面是对比动图，供你参考。

![tabs](https://king-hcj.github.io/images/browser/tabs.svg?raw=true)

- 安全性与沙箱化：把浏览器工作分成多个进程的另一好处是安全性与沙箱化。由于操作系统提供了限制进程权限的方法，浏览器就可以用沙箱保护某些特定功能的进程。例如，Chrome 浏览器限制处理任意用户输入的进程(如渲染器进程)对任意文件的访问。

- 共享拷贝：由于进程有自己的私有内存空间，所以它们通常包含公共基础设施的拷贝(如 V8，它是 Chrome 的 JavaScript 引擎)。这意味着使用了更多的内存，如果它们是同一进程中的线程，就无法共享这些拷贝。为了节省内存，Chrome 对可启动的进程数量有所限制。具体限制数值依设备可提供的内存与 CPU 能力而定，但是**当 Chrome 运行时达到限制时，会开始在同一站点的不同标签页上运行同一进程**。

&emsp;&emsp;Chrome 正在经历架构变革，它转变为将浏览器程序的每一模块作为一个服务来运行，从而可以轻松实现进程的拆解或聚合。具体表现是，当 Chrome 运行在**强力硬件**上时，它会将每个服务分解到不同进程中，从而**提升稳定性**，但是如果 Chrome 运行在资源有限的设备上时，它会将服务聚合到一个进程中从而**节省了内存占用**。在这一架构变革实现前，类似的整合进程以减少内存使用的方法已经在 Android 类平台上使用。

![servicfication](https://king-hcj.github.io/images/browser/servicfication.svg?raw=true)

&emsp;&emsp;Chrome 67 版本后，桌面版 Chrome 都默认开启了站点隔离，每个标签页的 iframe 都有一个单独的渲染进程。启用站点隔离是多年来工程人员努力的结果。站点隔离并不只是分配不同的渲染进程这么简单。它从根本上改变了 iframe 的通信方式。在一个页面上打开开发者工具，让 iframe 在不同的进程上运行，这意味着开发者工具必须在幕后工作，以使它看起来无缝。即使运行一个简单的 Ctrl + F 来查找页面中的一个单词，也意味着在不同的渲染器进程中进行搜索。你可以看到为什么浏览器工程师把发布站点隔离功能作为一个重要里程碑！

![isolation](https://king-hcj.github.io/images/browser/isolation.png?raw=true)

- [Chrome 为什么多进程而不是多线程？](https://www.zhihu.com/question/368712837){:target='_blank'}

### 浏览器整体架构

&emsp;&emsp;如果您是一名前端工程师，那么，面试时你大概率会被问到：从 URL 输入到页面展现到底发生了什么？，如果您对这一过程不太熟悉，建议看看下面两篇文章，再次不过多赘述：

  - [经典面试题：从 URL 输入到页面展现到底发生什么？](https://zhuanlan.zhihu.com/p/57895541){:target='_blank'}
  - [在浏览器输入 URL 回车之后发生了什么（超详细版）](https://zhuanlan.zhihu.com/p/80551769){:target='_blank'}

&emsp;&emsp;浏览器的主要任务之一就是渲染展示页面，不同的浏览器内核，渲染过程也不完全相同，但大致流程都差不多，下面这张图片是火狐浏览器（Firefox）开发文档中的一张图片。

![浏览器架构](https://king-hcj.github.io/images/browser/browser-diagram-full.png?raw=true)

&emsp;&emsp;上面这张图片大体揭示了浏览器的渲染展示流程，但是从浏览器的整体架构上来说，上面的图片展示的也许只是浏览器体系中的冰山一角。

&emsp;&emsp;通常意义下，浏览器架构是如下图这样的：

![浏览器架构](https://king-hcj.github.io/images/browser/BROWSER_ARCHITECTURE.png?raw=true)

#### 用户界面

&emsp;&emsp;包括地址栏、前进/后退按钮、书签菜单等。除了浏览器主窗口显示的您请求的页面外，其他显示的各个部分都属于用户界面。

#### 浏览器引擎

&emsp;&emsp;用户界面和渲染引擎的桥梁，在用户界面和渲染引擎之间传送指令。浏览器引擎提供了开始加载URL资源 和一些其他高级操作方法，比如：重新加载、前进、后退动作，错误信息、加载进度等。

#### 渲染引擎

&emsp;&emsp;负责显示请求的内容。如果请求的内容是 HTML，它就负责解析 HTML 和 CSS 内容，并将解析后的内容显示在屏幕上。

&emsp;&emsp;所谓浏览器内核就是指浏览器最重要或者说核心的部分"Rendering Engine"，译为"渲染引擎"。负责对网页语法的解析，比如HTML、JavaScript，并渲染到网页上。所以浏览器内核也就是浏览器所采用的渲染引擎，渲染引擎决定这浏览器如何显示页面的内容和页面的格式信息。不同的浏览器内核对语法的解释也不相同，因此同一的网页在不同内核的浏览器显示的效果也会有差异。这也就是网页编写者在不同内核的浏览器中测试网页显示效果的原因。

![RENDERING ENGINE](https://king-hcj.github.io/images/browser/browser_inner.png?raw=true)

&emsp;&emsp;浏览器内核主要包括以下三个技术分支：排版渲染引擎、 JavaScript引擎，以及其他。

&emsp;&emsp;排版引擎：

- KHTML：KHTML，是HTML网页排版引擎之一，由KDE所开发。KHTML拥有速度快捷的优点，但对错误语法的容忍度则比Mozilla产品所使用的Gecko引擎小。苹果电脑于2002年采纳了KHTML，作为开发Safari浏览器之用，并发布所修改的最新及过去版本源代码。后来发表了开放源代码的WebCore及WebKit引擎，它们均是KHTML的衍生产品。
- WebCore：WebCore是苹果公司开发的排版引擎，它是在另外一个排版引擎“KHTML”的基础上而来的。使用WebCore的主要有Safari浏览器。

&emsp;&emsp;浏览器的内核引擎，基本上是四分天下：

- Trident: IE 以Trident 作为内核引擎;
- Gecko: Firefox 是基于 Gecko 开发;
- WebKit: 开源引擎，Safari, Google Chrome,傲游3,猎豹浏览器,百度浏览器 opera浏览器 基于 Webkit 开发。
- Presto: Opera的内核，但由于市场选择问题，主要应用在手机平台--Opera mini。（2013年2月Opera宣布转向WebKit引擎，2013年4月Opera宣布放弃WEBKIT，跟随GOOGLE的新开发的blink引擎。）

![WebKit](https://king-hcj.github.io/images/browser/WebKit.png?raw=true)

&emsp;&emsp;WebKit就是一个页面渲染以及逻辑处理引擎，前端工程师把HTML、JavaScript、CSS这“三驾马车”作为输入，经过WebKit的处理，就输出成了我们能看到以及操作的Web页面。从上图我们可以看出来，WebKit由图中框住的四个部分组成。而其中最主要的就是WebCore和JSCore（或者是其它JS引擎）。除此之外，WebKit Embedding API是负责浏览器UI与WebKit进行交互的部分，而WebKit Ports则是让Webkit更加方便的移植到各个操作系统、平台上，提供的一些调用Native Library的接口，比如在渲染层面，在iOS系统中，Safari是交给CoreGraphics处理，而在Android系统中，Webkit则是交给Skia。

&emsp;&emsp;WebKit的渲染流程：

![WebKit-Rendering](https://king-hcj.github.io/images/browser/WebKit-Rendering.png?raw=true)

&emsp;&emsp;首先浏览器通过URL定位到了一堆由HTML、CSS、JS组成的资源文件，通过加载器（这个加载器的实现也很复杂，在此不多赘述）把资源文件给WebCore。之后HTML Parser会把HTML解析成DOM树，CSS Parser会把CSS解析成CSSOM树。最后把这两棵树合并，生成最终需要的渲染树，再经过布局，与具体WebKit Ports的渲染接口，把渲染树渲染输出到屏幕上，成为了最终呈现在用户面前的Web页面。

&emsp;&emsp;需要略作补充的是，我们经常还会听到Chromium、Webkit2、Blink这些引擎。

- Chromium：基于webkit，08年开始作为Chrome的引擎，Chromium浏览器是Chrome的实验版，实验新特性。可以简单地理解为：Chromium为实验版，具有众多新特性；Chrome为稳定版。

![chromium 架构](https://king-hcj.github.io/images/browser/chromium.jpeg?raw=true)

> 图片来源：[万字详文：深入理解浏览器原理](https://zhuanlan.zhihu.com/p/96986818){:target='_blank'}

- Webkit2：2010年随OS X Lion一起面世。WebCore层面实现进程隔离与Google的沙箱设计存在冲突。
- Blink：基于Webkit2分支，是WebKit中WebCore组件的一个分支，13年谷歌开始作为Chrome 28的引擎集成在Chromium浏览器里。Android的WebView同样基于Webkit2。Opera（15及往后版本）和Yandex浏览器中也在使用。

![khtml](https://king-hcj.github.io/images/browser/khtml.png?raw=true)

#### 网络

&emsp;&emsp;用于网络调用，比如 HTTP 请求。其接口与平台无关，并为所有平台提供底层实现，负责网络通信和安全。

#### JavaScript 解释器

&emsp;&emsp;用于解析和执行 JavaScript 代码，执行结果将传递给渲染引擎来展示。

#### 用户界面后端

&emsp;&emsp;用于绘制基本的窗口小部件，比如组合框和窗口。其公开了与平台无关的通用接口，而在底层使用操作系统的用户界面方法。

#### 数据存储

&emsp;&emsp;这是持久层。浏览器需要在硬盘上保存各种数据，例如 Cookie。新的 HTML 规范 (HTML5) 定义了“网络数据库”，这是一个完整（但是轻便）的浏览器内数据库。

### 求同存异的浏览器架构

&emsp;&emsp;FIREFOX架构：

![FIREFOX架构](https://king-hcj.github.io/images/browser/FIREFOX_ARCHITECTURE.png?raw=true)

&emsp;&emsp;CHROME架构：

![CHROME架构](https://king-hcj.github.io/images/browser/CHROME_ARCHITECTURE.png?raw=true)

&emsp;&emsp;IE架构：

![IE架构](https://king-hcj.github.io/images/browser/IE_ARCHITECTURE.png?raw=true)

> 参考资料：[Internet Explorer Architecture](https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa741312(v=vs.85)){:target='_blank'}

### 参考资料

- [PPT - Browser Architecture](https://sangbui.com/sb-files/BrowserArchitecture_ClientSide.pdf){:target='_blank'}
- [Inside look at modern web browser (part 1)](https://developers.google.com/web/updates/2018/09/inside-browser-part1){:target='_blank'}

## 浏览器基本原理

- [Design Documents](https://www.chromium.org/developers/design-documents){:target='_blank'}
- [浏览器运行原理】全程高能动画解析浏览器运行机制！](https://www.zhihu.com/zvideo/1318938663649800192){:target='_blank'}
  - https://www.zhihu.com/people/li-ming-44-11/zvideos
  - [Chromium_doc_zh](https://ahangchen.gitbooks.io/chromium_doc_zh/content/zh/){:target='_blank'}
- [万字详文：深入理解浏览器原理](https://zhuanlan.zhihu.com/p/96986818){:target='_blank'}

### Chrome V8

&emsp;&emsp;关于Chrome V8，笔者曾有一篇笔记做了比较详细的介绍，全文脉络如下，感兴趣可以[参考阅读](https://segmentfault.com/a/1190000037435824){:target='_blank'}。

![Chrome-V8](https://king-hcj.github.io/images/posts/arts/Chrome-V8.png?raw=true)

&emsp;&emsp;V8 是一个非常复杂的项目，有超过 100 万行 C++代码。它由许多子模块构成，其中这 4 个模块是最重要的：

- [Parser](https://v8.dev/blog/scanner){:target='\_blank'}：负责将 JavaScript 源码转换为 Abstract Syntax Tree (AST)
  > 确切的说，在“Parser”将 JavaScript 源码转换为 AST前，还有一个叫”Scanner“的过程，具体流程如下：
  ![Scanner](https://king-hcj.github.io/images/posts/arts/overview.png?raw=true)

- [Ignition](https://v8.dev/docs/ignition){:target='\_blank'}：interpreter，即解释器，负责将 AST 转换为 Bytecode，解释执行 Bytecode；同时收集 TurboFan 优化编译所需的信息，比如函数参数的类型；解释器执行时主要有四个模块，内存中的字节码、寄存器、栈、堆。

- [TurboFan](https://v8.dev/docs/turbofan){:target='\_blank'}：compiler，即编译器，利用 Ignition 所收集的类型信息，将 Bytecode 转换为优化的汇编代码；
- [Orinoco](https://v8.dev/blog/trash-talk){:target='\_blank'}：garbage collector，垃圾回收模块，负责将程序不再需要的内存空间回收。

&emsp;&emsp;其中，Parser，Ignition 以及 TurboFan 可以将 JS 源码编译为汇编代码，其流程图如下：

![V8流程](https://king-hcj.github.io/images/posts/arts/ignition-turbofan-pipeline.jpeg?raw=true)

&emsp;&emsp;简单地说，Parser 将 JS 源码转换为 AST，然后 Ignition 将 AST 转换为 Bytecode，最后 TurboFan 将 Bytecode 转换为经过优化的 Machine Code(实际上是汇编代码)。

- 如果函数没有被调用，则 V8 不会去编译它。
- 如果函数只被调用 1 次，则 Ignition 将其编译 Bytecode 就直接解释执行了。TurboFan 不会进行优化编译，因为它需要 Ignition 收集函数执行时的类型信息。这就要求函数至少需要执行 1 次，TurboFan 才有可能进行优化编译。
- 如果函数被调用多次，则它有可能会被识别为**热点函数**，且 Ignition 收集的类型信息证明可以进行优化编译的话，这时 TurboFan 则会将 Bytecode 编译为 Optimized Machine Code（已优化的机器码），以提高代码的执行性能。

&emsp;&emsp;图片中的红色虚线是逆向的，也就是说 Optimized Machine Code 会被还原为 Bytecode，这个过程叫做 **Deoptimization**。这是因为 Ignition 收集的信息可能是错误的，比如 add 函数的参数之前是整数，后来又变成了字符串。生成的 Optimized Machine Code 已经假定 add 函数的参数是整数，那当然是错误的，于是需要进行 Deoptimization。

```js
function add(x, y) {
  return x + y;
}

add(1, 2);
add('1', '2');
```

&emsp;&emsp;在运行 C、C++以及 Java 等程序之前，需要进行编译，不能直接执行源码；但对于 JavaScript 来说，我们可以直接执行源码(比如：node test.js)，它是在运行的时候先编译再执行，这种方式被称为**即时编译(Just-in-time compilation)**，简称为 JIT。因此，V8 也属于 **JIT 编译器**。

### JavaScriptCore

&emsp;&emsp;JSCore是WebKit默认内嵌的JS引擎，之所以说是默认内嵌，是因为很多基于WebKit分支开发的浏览器引擎都开发了自家的JS引擎，其中最出名的就是Chrome的V8。这些JS引擎的使命都相同，那就是解释执行JS脚本。而从上面的渲染流程图我们可以看到，JS和DOM树之间存在着互相关联，这是因为浏览器中的JS脚本最主要的功能就是操作DOM树，并与之交互。我们也通过一张图看下它的工作流程:

![JavaScriptCore](https://king-hcj.github.io/images/browser/jsCore.png?raw=true)

&emsp;&emsp;可以看到，相比静态编译语言生成语法树之后，还需要进行链接，装载生成可执行文件等操作，解释型语言在流程上要简化很多。这张流程图右边画框的部分就是JSCore的组成部分：Lexer、Parser、LLInt以及JIT的部分（之所以JIT的部分是用橙色标注，是因为并不是所有的JSCore中都有JIT部分）。接下来我们就搭配整个工作流程介绍每一部分，它主要分为以下三个部分：词法分析、语法分析以及解释执行。

> PS：严格的讲，语言本身并不存在编译型或者是解释型，因为语言只是一些抽象的定义与约束，并不要求具体的实现，执行方式。这里讲JS是一门“解释型语言”只是JS一般是被JS引擎动态解释执行，而并不是语言本身的属性。

<!-- - [深入剖析 JavaScriptCore](https://ming1016.github.io/2018/04/21/deeply-analyse-javascriptcore/){:target='\_blank'} -->
- [深入理解 JSCore](https://tech.meituan.com/2018/08/23/deep-understanding-of-jscore.html){:target='\_blank'}【关注一下参考资料】
- [JavaScriptCore 全面解析](https://juejin.cn/post/6844903765582053384){:target='\_blank'}
- [深入浅出 JavaScriptCore](https://www.jianshu.com/p/ac534f508fb0){:target='\_blank'}

### 浏览器与JavaScript

- 在 **V8 出现之前，所有的 JavaScript 虚拟机所采用的都是解释执行的方式，这是 JavaScript 执行速度过慢的一个主要原因**。而 V8 率先引入了**即时编译（JIT）**的**双轮驱动**的设计（混合使用编译器和解释器的技术），这是一种权衡策略，**混合编译执行和解释执行这两种手段**，给 JavaScript 的执行速度带来了极大的提升。V8 出现之后，各大厂商也都在自己的 JavaScript 虚拟机中引入了 JIT 机制，所以目前市面上 JavaScript 虚拟机都有着类似的架构。另外，**V8 也是早于其他虚拟机引入了惰性编译、内联缓存、隐藏类等机制，进一步优化了 JavaScript 代码的编译执行效率**。
- V8 执行一段 JavaScript 的流程图：

  ![V8执行一段JavaScript流程图](https://king-hcj.github.io/images/posts/arts/v8.jpg?raw=true)

- **V8 本质上是一个虚拟机**，因为计算机只能识别二进制指令，所以要让计算机执行一段高级语言通常有两种手段：
  - 第一种是将高级代码转换为二进制代码，再让计算机去执行；
  - 另外一种方式是在计算机安装一个解释器，并由解释器来解释执行。
- 解释执行和编译执行都有各自的优缺点，**解释执行启动速度快，但是执行时速度慢，而编译执行启动速度慢，但是执行速度快**。为了充分地利用解释执行和编译执行的优点，规避其缺点，**V8 采用了一种权衡策略，在启动过程中采用了解释执行的策略，但是如果某段代码的执行频率超过一个值，那么 V8 就会采用优化编译器将其编译成执行效率更加高效的机器代码**。
- 总结：

  **V8 执行一段 JavaScript 代码所经历的主要流程**包括：

  - 初始化基础环境；
  - 解析源码生成 AST 和作用域；
  - 依据 AST 和作用域生成字节码；
  - 解释执行字节码；
  - 监听热点代码；
  - 优化热点代码为二进制的机器代码；
  - 反优化生成的二进制机器代码。

&emsp;&emsp;Chrome V8 的事件机制：

![v8-ui](https://king-hcj.github.io/images/posts/arts/v8-ui.jpg?raw=true)

- [JavaScript 引擎 V8 执行流程概述](http://blog.itpub.net/69912579/viewspace-2668277/){:target='_blank'}【图更好一点】
- [V8 Ignition：JS 引擎与字节码的不解之缘](https://cnodejs.org/topic/59084a9cbbaf2f3f569be482){:target='_blank'}
- [认识 V8 引擎](https://zhuanlan.zhihu.com/p/27628685){:target='_blank'}
- [V8引擎详解（一）——概述](https://juejin.cn/post/6844904137792962567){:target='_blank'}

## 浏览器的不同形态
### WebView

&emsp;&emsp;WebView 是一种嵌入式浏览器，原生应用可以用它来展示网络内容。WebView 只是一个可视化的组件/控件/微件等。

&emsp;&emsp;运行在你的 WebView 中的 JavaScript 有能力调用原生的系统 API。这意味着你不必受到 Web 代码通常必须遵守的传统浏览器安全沙箱的限制。下图解释了使这样成为可能的架构差异：

![webview and webapp](https://king-hcj.github.io/images/browser/webview_webapp.png?raw=true)

&emsp;&emsp;WebView 非常棒。虽然看起来它们看起来像是完全特殊和独特的野兽，记住，它们只不过是一个在应用中设置好位置和大小的浏览器，而且不会放置任何花哨的 UI。其实还有更多东西，但这是它的精髓。在大多数情况下，除非你要调用原生 API，否则不必在 WebView 中专门测试 Web 应用。除此以外，你在 WebView 中看到的内容与你在浏览器中看到的内容相同，尤其是使用同一渲染引擎时：

- 在 iOS 上，Web 渲染引擎始终是 WebKit，与 Safari 和 Chrome 相同。是的，你没看错。iOS 上的 Chrome 实际上使用了 WebKit。
- 在 Android 上的渲染引擎通常是 Blink，与 Chrome 相同。
- 在 Windows，Linux 和 macOS 上，由于这些是更宽松的桌面平台，因此在选择 WebView 风格和渲染引擎时会有很大的灵活性。你看到的流行渲染引擎将是 Blink（Chrome）和 Trident（Internet Explorer），但是没有一个引擎可以依赖。这完全取决于应用以及它正在使用的 WebView 引擎。

- [理解 WebView](https://github.com/xitu/gold-miner/blob/ec8862f2993f7eea977af6929d0b0785a86fd4e3/TODO1/understanding-webviews.md){:target='_blank'}

<!-- - [Android WebView基本使用](https://blog.csdn.net/lowprofile_coding/article/details/77928614){:target='_blank'}
- [7.5.1 WebView(网页视图)基本用法](https://www.runoob.com/w3cnote/android-tutorial-webview.html){:target='_blank'}
- [你真的了解webview么？](https://zhuanlan.zhihu.com/p/58691238){:target='_blank'}
- [Android：这是一份全面 & 详细的Webview使用攻略](https://www.jianshu.com/p/3c94ae673e2a/){:target='_blank'}
- [WebView你真的熟悉吗？看了才知道](https://www.jianshu.com/p/d2f5ae6b4927){:target='_blank'}
- [WebView](http://www.androidchina.net/tag/webview){:target='_blank'} -->

### Headless browser

- [什么是「无头浏览器」 （Headless browser），它有什么应用场景？](https://www.zhihu.com/question/314668782/answer/620975831){:target='_blank'}
- [啥是无头浏览器，都能干啥？一文说清楚](https://zhuanlan.zhihu.com/p/137843898){:target='_blank'}
- [Headless Chrome architecture](https://www.cnblogs.com/bigben0123/p/13880254.html){:target='_blank'}
- [What is a Headless Browser?](https://oxylabs.io/blog/what-is-headless-browser){:target='_blank'}
- [6 Popular Headless Browsers for Web Testing](https://www.keycdn.com/blog/headless-browsers){:target='_blank'}

- [Headless Chrome architecture](https://www.google.com.hk/search?q=Headless+Chrome+architecture&newwindow=1&safe=strict&tbm=isch&source=iu&ictx=1&fir=W9qdIOjuXPFz5M%252C1zvWEtXccmOnlM%252C_&vet=1&usg=AI4_-kRn8Gc3dK1IDfgodMG38_HcVuPoeQ&sa=X&ved=2ahUKEwiTvdzvuMPxAhW583MBHZnTA7wQ9QF6BAgiEAE#imgrc=W9qdIOjuXPFz5M){:target='_blank'}

&emsp;&emsp;Puppeteer 是一个 node 库，他提供了一组用来操纵 Chrome 的 API, 通俗来说就是一个 headless chrome 浏览器 (当然你也可以配置成有 UI 的，默认是没有的)。既然是浏览器，那么我们手工可以在浏览器上做的事情 Puppeteer 都能胜任, 另外，Puppeteer 翻译成中文是”木偶”意思，所以听名字就知道，操纵起来很方便，你可以很方便的操纵她去实现：

1） 生成网页截图或者 PDF
2） 高级爬虫，可以爬取大量异步渲染内容的网页
3） 模拟键盘输入、表单自动提交、登录网页等，实现 UI 自动化测试
4） 捕获站点的时间线，以便追踪你的网站，帮助分析网站性能问题

&emsp;&emsp;Puppeteer 跟 webdriver 以及 PhantomJS 最大的 的不同就是它是站在用户浏览的角度，而 webdriver 和 PhantomJS 最初设计就是用来做自动化测试的，所以它是站在机器浏览的角度来设计的，所以它们 使用的是不同的设计哲学。

- [puppeteer](https://github.com/puppeteer/puppeteer/){:target='\_blank'}
- [Puppeteer 入门教程](https://www.r9it.com/20171106/puppeteer.html){:target='\_blank'}
- [API 文档](https://github.com/puppeteer/puppeteer/blob/main/docs/api.md){:target='\_blank'}

- [网站性能测试利器:Puppeteer](https://cloud.tencent.com/developer/article/1086109){:target='\_blank'}
- [结合项目来谈谈 Puppeteer](https://zhuanlan.zhihu.com/p/76237595){:target='\_blank'}

### Electron

## 浏览器代码兼容性

- [caniuse](https://www.caniuse.com/){:target='_blank'}
- [browseemall](https://www.browseemall.com/Resources){:target='_blank'}
- [html5test](https://html5test.com/){:target='_blank'}

## 相伴日久 —— 浏览器

&emsp;&emsp;作为一名前端开发人员，学习浏览器的内部工作原理将有助于我们在开发中作出更明智的决策，并理解那些最佳开发实践的个中缘由。在前端面试中，也有一道经典的面试题 ——【从您在地址栏输入 google.com 直到您在浏览器屏幕上看到 Google 首页的整个过程中都发生了些什么】。

- [浏览器是如何工作的：Chrome V8 让你更懂 JavaScript](https://segmentfault.com/a/1190000037435824){:target='\_blank'}
- [浏览器的工作原理：新式网络浏览器幕后揭秘](https://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/){:target='\_blank'}
- [从浏览器多进程到 JS 单线程，JS 运行机制最全面的一次梳理](https://segmentfault.com/a/1190000012925872){:target='\_blank'}
- [🤔 移动端 JS 引擎哪家强？美国硅谷找......](https://mp.weixin.qq.com/s/cV3RH72YKd6jRYBFhjJ-5w){:target='\_blank'}
- [Page Lifecycle API](https://developers.google.com/web/updates/2018/07/page-lifecycle-api#overview_of_page_lifecycle_states_and_events){:target='\_blank'}
- [从 V8 角度揭秘你不知道的面试八股文](https://mp.weixin.qq.com/s/NkaGseRlLKcERx6rpouCFA){:target='_blank'}
- [高性能 JavaScript 引擎 V8 - 垃圾回收](https://mp.weixin.qq.com/s/TnaQRMpJaxxIUIZS2MK9-g){:target='_blank'}

- [自主研发一款浏览器内核的难度到底有多大？](https://www.zhihu.com/question/290564335/answer/474202037){:target='\_blank'}


- [QQ浏览器是基于chrome内核开发的吗？](https://zhidao.baidu.com/question/2058022048028049667.html){:target='_blank'}
- [新版Microsoft Edge（Chromium内核）介绍](https://baijiahao.baidu.com/s?id=1654951353372013675){:target='_blank'}
  - Microsoft Edge (EdgeHTML)
  - Chromium

### Chrome 

- [Chrome 浏览器架构](https://xie.infoq.cn/article/5d36d123bfd1c56688e125ad3){:target='_blank'}
  - [Inside look at modern web browser (part 1)](https://developers.google.com/web/updates/2018/09/inside-browser-part1){:target='_blank'}
  - [Inside look at modern web browser (part 2)](https://developers.google.com/web/updates/2018/09/inside-browser-part2){:target='_blank'}
  - [Inside look at modern web browser (part 3)](https://developers.google.com/web/updates/2018/09/inside-browser-part3){:target='_blank'}
  - [Inside look at modern web browser (part 4)](https://developers.google.com/web/updates/2018/09/inside-browser-part4){:target='_blank'}
  - [图解浏览器的基本工作原理](https://zhuanlan.zhihu.com/p/47407398){:target='\_blank'}
  - [现代浏览器内部揭秘（第一部分）](https://github.com/xitu/gold-miner/blob/master/TODO1/inside-look-at-modern-web-browser-part1.md){:target='_blank'}
- [一文看透浏览器架构](https://segmentfault.com/a/1190000018277184){:target='_blank'}

- [现代浏览器工作原理（一）](http://chuquan.me/2018/01/21/browser-architecture-overview/){:target='_blank'}
- [Web 浏览器相关的一些概念](https://keqingrong.cn/blog/2019-11-24-concepts-related-to-web-browsers){:target='_blank'}

- [THE BASIC FLOW OF RENDERING ENGINE](https://www.google.com.hk/search?newwindow=1&safe=strict&source=univ&tbm=isch&q=THE+BASIC+FLOW+OF+RENDERING+ENGINE&sa=X&ved=2ahUKEwjNopKj2b7xAhXP7XMBHcUyCs8Q7Al6BAgnEFM&biw=1536&bih=694&dpr=2#imgrc=BOuUFmUelYNhYM){:target='_blank'}

图片很精美：
- [Quantum Up Close: What is a browser engine?](https://hacks.mozilla.org/2017/05/quantum-up-close-what-is-a-browser-engine/){:target='_blank'}
  - [解密 Quantum：现代浏览器引擎的构建之道](https://github.com/xitu/gold-miner/blob/master/TODO/quantum-up-close-what-is-a-browser-engine.md){:target='_blank'}

- [掘金翻译计划](https://github.com/xitu/gold-miner/search?q=web+browser){:target='_blank'}


- [浏览器市场占有率分析](https://zhuanlan.zhihu.com/p/187066428){:target='\_blank'}
