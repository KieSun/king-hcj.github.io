---
layout: post
title: GIF 若死，谁才是未来？
categories: JavaScript
description: 你不知道的 GIF
keywords: JS, 前端, JavaScript, 浏览器, GIF, Apng
---

<!--
前端解析、生成Excel
你不知道的 GIF，压缩算法
-->

## 你不知道的 GIF

&emsp;&emsp;GIF 文件带给了我们很多欢乐，君不见每天微博上搞笑的图片大多数都是 GIF 格式的。那么 GIF 这种神奇的图片格式究竟是怎么来的呢？GIF(Graphics Interchange Format)的原义是“图像互换格式”。本片是 SmartWater 工作室为首届 GIF 动画节 Moving the Still 所做，精致的粘土定格动画给我们讲述了 GIF 这三十年的历史，还给我们展示了为什么 GIF 文件能给我们带来无穷的欢乐。A Short History of the Gif GIF25 岁生日快乐！

> [科普小知识：GIF 的简短历史](https://v.qq.com/x/cover/p0164wh13yx/p0164wh13yx.html){:target='\_blank'}

&emsp;&emsp;动图，顾名思义就是动态图片，亦称 GIF 图片。官方解释：它是一个可以将多幅图像数据存于一起，并逐帧显示到屏幕上，形成简单动画的图像文件。

&emsp;&emsp;gif 的全称是 Graphics Interchange Format（ 图形交换格式 ），诞生于 1987 年，最初是为了填补跨平台图像格式的空白，用人话来说就是填补了静态图片和视频之间的空隙。gif 最初由一家叫做 CompuServe 的公司搞出来，这也是美国最早的一家信息服务公司。gif 到了 1995 年才能循环起来，这已经是 gif 诞生 8 年之后了。之所以 gif 能在 1995 年开始循环播放，其实要靠一个叫做网景 （ Netscape ） 的浏览器。

&emsp;&emsp;gif 之所以能够在有限的大小实现了动态画面，是因为它采用了 LZW（ Lempel-Zev-Welch ）压缩算法。LZW 算法也叫做 “ 串表压缩算法 ”，这种算法会用数字来表示文件中第一次出现的串，然后再放进串表中。而压缩文件只存储数字，不存储串符，这样压缩效率就会得到提高。

&emsp;&emsp;2004 年，一种叫做 apng 的动图格式诞生于火狐浏览器所在的公司，它和 gif 类似，但是它是以一帧帧 png 组成的。再结合优异的压缩算法， apng 在文件大小和 gif 相似的情况下，图片质量要更高，而且即使不加载整个动图也能预览第一张。直到 2017 年才只有 Safari 和火狐浏览器支持，2019 年 Chrome 才跟上。

&emsp;&emsp;到了 5G 时代，就连短视频都能够轻松地用手机观看和制作，动图更是小事一桩的事情。从简单的像素动画到现在的全民表情包，gif 似乎就是为互联网而生的。几十年过去了，gif 仍然宝刀不老，也许在几年之后，apng 就会取代它，但 gif 应该永远不会被遗忘。其实啊，无论是什么格式，这一张张动图既是互联网时代的缩影，也默默记录着每个网上冲浪的人的喜怒哀乐。

&emsp;&emsp;动图是一个多幅图像数据文件，其中应至少包含两幅图片。当图像越多时，动画就越细腻（文件也越大）。当每秒超过 24 帧，即单帧时间低于 0.04 秒，这些连续播放的图片就会连成视频。

- **[APNG 与 GIF](https://lxb.wiki/941edb97/){:target='\_blank'}**

- **[移动端图片格式调研](https://blog.ibireme.com/2015/11/02/mobile_image_benchmark/){:target='\_blank'}**

- [为什么 30 多年过去了，GIF 还没有被淘汰](https://zhuanlan.zhihu.com/p/396618872){:target='\_blank'}
- [谈谈 GIF 格式](https://zhuanlan.zhihu.com/p/22590949){:target='\_blank'}
- [GIF 动图发展史上的 11 个重要时刻](https://zhuanlan.zhihu.com/p/28466822){:target='\_blank'}

- [PNG 图片压缩原理解析--屌丝的眼泪](https://zhuanlan.zhihu.com/p/59608343){:target='\_blank'}
- [apng、webp 适用性调研与兼容性方案](https://lizheguang.github.io/zhaiGuang/2020/10/10/gitwebp/){:target='\_blank'}

- [FLIF, the new lossless image format that outperforms PNG, WebP and BPG](https://cloudinary.com/blog/flif_the_new_lossless_image_format_that_outperforms_png_webp_and_bpg){:target='\_blank'}

- [The GIF is 30 years old. It didn't just shape the internet — it grew up with the internet.](https://www.vox.com/culture/2017/6/15/15802136/gif-turns-30-evolution-internet-history){:target='\_blank'}
- [A Brief History of the GIF, From Early Internet Innovation to Ubiquitous Relic](https://www.smithsonianmag.com/history/brief-history-gif-early-internet-innovation-ubiquitous-relic-180963543/){:target='\_blank'}
- [A brief history of the GIF](https://journals.sagepub.com/doi/pdf/10.1177/1470412914553365){:target='\_blank'}
- [GIF vs APNG vs WebP](https://www.jayxon.com/gif-apng-webp/){:target='\_blank'}

- [GIF vs APNG vs WebP](http://littlesvr.ca/apng/gif_apng_webp.html){:target='\_blank'}
- [Animated PNG VS. Animated Webp VS. GIF battle Royale!](https://corydowdy.com/blog/apng-vs-webp-vs-gif){:target='\_blank'}
- [WHY WEBP IS THE ROCKSTAR OF IMAGE FORMATS FOR WEB DESIGNERS](https://insanelab.com/blog/web-development/webp-web-design-vs-jpeg-gif-png/){:target='\_blank'}

- [Web 端 APNG 播放实现原理](https://www.h5w3.com/47911.html){:target='\_blank'}
- [File Format](https://docs.fileformat.com/){:target='\_blank'}
- [FLIF](http://flif.info/index.html){:target='\_blank'}
- [FLIF 自由的无损图像格式](https://www.oschina.net/p/flif){:target='\_blank'}
- [一种新型免费无损图片格式 FLIF](https://blog.csdn.net/ybhuangfugui/article/details/104528840){:target='\_blank'}
- [A new image format for the Web](https://developers.google.com/speed/webp/){:target='\_blank'}
