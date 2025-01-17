---
layout: post
title: 前端装逼技巧 108 式（五）—— 前端工具人
categories: JavaScript
description: 前端装逼技巧 108 式，助你更懂JS原理
keywords: JS, 前端, JavaScript
---

> 春风好媒妁，说动一树榴红。偶来雨多，茅屋又新破，且戴一笠，借故去访邻居家老叟。  循着江岸梅林，一颗颗睡饱了的梅子，正是青里一抹红透，得着此刻无人，且摘它个两袖清风、一袋新酒。世间的功名不能裱壁，就向天地讨一笔闲钱糊口。   正算计着老叟家的那只古瓮，怎么着，一匹快马驰过，溅得我一身泥泞，定睛一探，可不是城里那位篡了功名的新进？  且拼春风一叹，还好，近日雨多。

## 第七十三式：JSON.parse('null') === null

```js
JSON.parse('{}');              // {}
JSON.parse('true');            // true
JSON.parse('"foo"');           // "foo"
JSON.parse('[1, 5, "false"]'); // [1, 5, "false"]
JSON.parse('null');            // null
```

- [为什么JSON.parse与空字符串失败？](http://www.djcxy.com/p/8003.html){:target='_blank'}

## 第七十四式：尾调用优化，尾调用为什么能优化？

- [尾调用优化](http://www.ruanyifeng.com/blog/2015/04/tail-call.html){:target='_blank'}

## 七十五：JS实现页面全屏功能（模拟F11）

```js
function toggleFullScreen() {
  if (!document.fullscreenElement) {
      document.documentElement.requestFullscreen();
      // document.body.requestFullscreen()
      // 层级太低可能影响交互
  } else {
    if (document.exitFullscreen) {
      document.exitFullscreen();
    }
  }
}
```

<!-- 可以对页面的任何区域进行全屏 -->
- [MDN - 全屏 API](https://developer.mozilla.org/zh-CN/docs/Web/API/Fullscreen_API){:target='_blank'}
- [JS实现页面全屏功能](https://blog.csdn.net/qiao_1017/article/details/80421631){:target='_blank'}
- [js实现f11的全屏效果](https://blog.csdn.net/qq_36698956/article/details/82697938){:target='_blank'}

## 第七十六式：程序员必备网站

- [程序员必备网站](https://www.zhihu.com/column/GHDaily){:target='_blank'}
  - [程序员必备网站之一：VisuAlgo](https://zhuanlan.zhihu.com/p/166642871){:target='_blank'}
  - [程序员必备网站之一：Wolfram Alpha](https://zhuanlan.zhihu.com/p/165093450){:target='_blank'}
  - [程序员必备网站之一：i Hate Regex](https://zhuanlan.zhihu.com/p/151775461){:target='_blank'}
  - [程序员必备网站之一：No Design](https://zhuanlan.zhihu.com/p/147631925){:target='_blank'}
  - [程序员必备网站之一：API Coding](https://zhuanlan.zhihu.com/p/145137377){:target='_blank'}

1. 大厂越来越重算法？VisuAlgo 你值得拥有

我们都知道，在人体的直接感官体验上，动画与图形相对于文字代码往往能带来更有冲击感的视觉效果，也更容易加深大脑对某项事物的认知程度。

而像算法这类，拥有完整逻辑推理计算链条的知识，用动画来展示是再好不过了。

说到这里，便不得不提到那个非常经典的算法可视化网站：VisuAlgo。

- [VisuAlgo](https://visualgo.net/zh){:target='_blank'}
- [程序员必备网站之一：VisuAlgo](https://zhuanlan.zhihu.com/p/166642871){:target='_blank'}

## 第七十七式：前端水印生成方案

- [前端水印生成方案(网页水印+图片水印)](https://juejin.cn/post/6844903645155164174){:target='_blank'}
- [不能说的秘密——前端也能玩的图片隐写术](http://www.alloyteam.com/2016/03/image-steganography/){:target='_blank'}

## 第七十八式：百度搜索你不知道的几点技巧，让你的搜索更加高效（单篇文章？）
<!-- 面向百度/浏览器编程工程师 -->
- [这几个百度搜索技巧，太好用了](https://zhuanlan.zhihu.com/p/92562328){:target='_blank'}
- [百度搜索技巧](http://d.baidu.com/search/skill.html){:target='_blank'}
- [百度搜索你不知道的几点技巧，让你的搜索更加准确，绝对值得收藏](https://baijiahao.baidu.com/s?id=1588667642036316564){:target='_blank'}
- [百度高级搜索技巧](https://blog.csdn.net/cx243698/article/details/80625384){:target='_blank'}
- [【译】像大佬一样使用 Google](https://mp.weixin.qq.com/s/SLxQ8eBGZQwrChZjo9brSQ){:target='_blank'}

## 第七十九式：JavaScript中的void 0

> void其实是javascript中的一个函数，接受一个参数，返回值永远是undefined。可以说，使用void目的就是为了得到javascript中的undefined。

undefined是JS语言中的7大基本类型之一，表示未定义，它的值只有一个，就是undefined。任何变量在赋值前都是undefined。

```js
    console.log(void ("hello"))  // undefined
    console.log(void (0))  // undefined
    console.log(void 0)  // undefine
```

1. undefined是可变的？

在ES5的全局环境中，undefined是只读的。而在局部作用域中，undefined是可变的。这个是JS语言公认的设计失误之一。

2. 什么是void？
void是一元运算符，出现在操作数的左边，操作数可以是任意类型的值，void右边的表达式可以是带括号形式（例如：void(0)），也可以是不带括号的形式（例如：void 0）。 

3. 使用void 0代替undefined的原因是？

　　① 使用void 0比使用undefined能够减少3个字节
```js
"undefined".length; // 9
"void 0".length; // 6
```
　　② undefined并不是javascript中的保留字，我们可以使用undefined作为变量名字，然后给它赋值。void 0输出唯一的结果undefined，保证了不变性。

4. undefined与null的区别？

null代表空值，代表“定义了但是为空”。而undefined的代表未定义。

- 为什么不直接使用undefined呢？
  - 使用void 0比使用undefined能够减少3个字节。虽然这是个优势，个人但感觉意义不大，牺牲了可读性和简单性
  - undefined并不是javascript中的保留字，我们可以使用undefined作为变量名字，然后给它赋值,, 但在chrome 中打印出来的是 undefined
  ```js
  let undefined = 1; // undefined
  let for = 1; // Uncaught SyntaxError: Unexpected token 'for'
  let break = 2; // Uncaught SyntaxError: Unexpected token 'break'
  ```
> [【JS基础】JavaScript中的void 0](https://www.cnblogs.com/sophierabbit/p/11452205.html)
[javascript:void(0)的含义](https://www.cnblogs.com/duxiu-fang/p/11104735.html)
[“javascript：void（0）”是什么意思？](http://www.djcxy.com/p/8001.html){:target='_blank'}

## 第八十式：CSS3动画 - 酷炫的扑克牌展开

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        body {
            /*background-color: #eee;*/
        }

        .box {

            width: 300px;
            height: 440px;
            margin: 100px auto;
            position: relative;
        }

        img {
            width: 100%;
            transition: all 1.5s;
            position: absolute;     /* 既然扑克牌是叠在一起的，那就都用绝对定位 */
            left: 0;
            top: 0;

            transform-origin: center bottom; /*旋转时，以盒子底部的中心为坐标原点*/
            box-shadow: 0 0 3px 0 #666;
        }

        .box:hover img:nth-child(6) {
            transform: rotate(-10deg);
        }

        .box:hover img:nth-child(5) {
            transform: rotate(-20deg);
        }

        .box:hover img:nth-child(4) {
            transform: rotate(-30deg);
        }

        .box:hover img:nth-child(3) {
            transform: rotate(-40deg);
        }

        .box:hover img:nth-child(2) {
            transform: rotate(-50deg);
        }

        .box:hover img:nth-child(1) {
            transform: rotate(-60deg);
        }

        .box:hover img:nth-child(8) {
            transform: rotate(10deg);
        }

        .box:hover img:nth-child(9) {
            transform: rotate(20deg);
        }

        .box:hover img:nth-child(10) {
            transform: rotate(30deg);
        }

        .box:hover img:nth-child(11) {
            transform: rotate(40deg);
        }

        .box:hover img:nth-child(12) {
            transform: rotate(50deg);
        }

        .box:hover img:nth-child(13) {
            transform: rotate(60deg);
        }

    </style>
</head>
<body>
<div class="box">
    <img src="images/pk1.jpg"/>
    <img src="images/pk2.jpg"/>
    <img src="images/pk1.jpg"/>
    <img src="images/pk2.jpg"/>
    <img src="images/pk1.jpg"/>
    <img src="images/pk2.jpg"/>
    <img src="images/pk1.jpg"/>
    <img src="images/pk2.jpg"/>
    <img src="images/pk1.jpg"/>
    <img src="images/pk2.jpg"/>
    <img src="images/pk1.jpg"/>
    <img src="images/pk2.jpg"/>
    <img src="images/pk1.jpg"/>
</div>
</body>
</html>
```

- [CSS3动画详解（图文教程）](https://www.cnblogs.com/qianguyihao/p/8435182.html)

## 第八十一式：屏幕录制工具

- [推荐几款屏幕录制工具（可录制GIF）](https://www.cnblogs.com/libin-1/p/6424368.html){:target='_blank'}
- [screentogif](https://www.screentogif.com/){:target='_blank'}
- [mac用什么软件制作GIF方便？](https://www.zhihu.com/question/21773876){:target='_blank'}

## 第八十二式：How To Force The Browser To Reload Cached .JS, .CSS Files To Reflect The Latest Changes To Those Files

[How To Force The Browser To Reload Cached .JS, .CSS Files To Reflect The Latest Changes To Those Files](https://www.c-sharpcorner.com/article/how-to-force-the-browser-to-reload-cached-js-css-files-to-reflect-latest-chan/)
[What’s the difference between F5, Ctrl+R, Ctrl+Shift+R, Ctrl+F5 and Shift+F5 in Google Chrome browser?](https://www.saicharanreddy.com/whats-the-difference-between-f5-ctrlr-ctrlshiftr-ctrlf5-and-shiftf5-in-google-chrome-browser/)
[详解谷歌Chrome浏览器中的各种刷新姿势（点击链接，在地址栏回车，F5，Ctrl + F5，Shift + F5，Ctrl + R，Ctrl + Shift + R）](https://blog.csdn.net/u012107143/article/details/100735550)

JS 模拟浏览器强刷：
    ```js
    useEffect(() => {
      const oaStorage = localStorage.getItem('UCloud_OA_SupplierInfoList');
      const curTime = new Date().getTime();
      // 没有缓存或者缓存已经超过8个小时
      if (!oaStorage || (oaStorage &&  curTime - Number(oaStorage) > 28800000)) {
        localStorage.setItem('UCloud_OA_SupplierInfoList', curTime);
        window.location.href = window.location.href.split('?')[0] + `?time=${curTime}`;
        // location.search += (location.search ? '&time=' : '?time=') +  new Date().getTime()
      }
    }, []);
    ```

## 第八十三式：Status Code:200 OK (from disk cache)和304的区别，以及怎么禁止缓存

[Status Code:200 OK (from disk cache)和304的区别，以及怎么禁止缓存](https://blog.csdn.net/u014452812/article/details/79131676)
[status code: 200 OK (FROM CACHE) 与 304 NOT MODIFIED](https://blog.csdn.net/m0_37205611/article/details/82751811)
[浏览器缓存(一)：强缓存 MEMORY CACHE 和 DISK CACHE](http://www.wewyy.com/archives/444)
[from disk/memory cache详解](https://blog.csdn.net/franknotbad/article/details/79400105)
[Nginx下关于缓存控制字段cache-control的配置说明 - 运维小结](https://www.cnblogs.com/kevingrace/p/10459429.html)
[浏览器缓存详解:expires,cache-control,last-modified,etag详细说明](https://blog.csdn.net/eroswang/article/details/8302191)

- 200 from memory cache
不访问服务器，一般已经加载过该资源且缓存在了内存当中，直接从内存中读取缓存。浏览器关闭后，数据将不存在（资源被释放掉了），再次打开相同的页面时，不会出现from memory cache。
- 200 from disk cache
不访问服务器，已经在之前的某个时间加载过该资源，直接从硬盘中读取缓存，关闭浏览器后，数据依然存在，此资源不会随着该页面的关闭而释放掉下次打开仍然会是from disk cache。
- 304 Not Modified
访问服务器，发现数据没有更新，服务器返回此状态码。然后从缓存中读取数据。
- ETag 还有“强”“弱”之分。
  - 强ETag值：无论资源发生多么细微的变化都会改变。一般是以"xxx"的形式。
  - 弱ETag值：只有在资源发生了根本性改变，才会改变。一般是以W/"xxx"形式。
  - 常规（强）ETag和弱ETag之间的区别在于，匹配的强ETag保证文件字节对字节相同，而匹配的弱ETag表示内容在语义上是相同的。因此，如果文件的内容发生更改，则弱ETag也应更改。

![fromdiskcache](https://king-hcj.github.io/images/posts/arts/fromdiskcache.png?raw=true)

## 第八十四式：`will-change`是如何优化性能的？

&emsp;&emsp;CSS 属性 `will-change` 为 web 开发者提供了一种告知浏览器该元素会有哪些变化的方法，这样浏览器可以在元素属性真正发生变化之前提前做好对应的优化准备工作。这种优化可以将一部分复杂的计算工作提前准备好，使页面的反应更为快速灵敏。

- [will-change](https://developer.mozilla.org/zh-CN/docs/Web/CSS/will-change){:target='\_blank'}
- [说一说 will-change](https://mp.weixin.qq.com/s/rbDZntqZd8VcbDjQFER2Yw){:target='\_blank'}
- [CSS 页面渲染优化属性 will-change](https://www.cnblogs.com/xiaohuochai/p/6321790.html){:target='\_blank'}
- [极客 2](https://time.geekbang.org/column/article/141842){:target='\_blank'}
- [仅使用CSS就可以提高页面渲染速度的4个技巧](https://segmentfault.com/a/1190000038810622)

## 第八十五式：`String.replace()`第二个参数可以是个函数？

<!-- 那些不为人知的第二个参数 -->

- 特殊符号`$`
- [JavaScript replace() 方法](https://www.w3school.com.cn/jsref/jsref_replace.asp){:target='\_blank'}
- [js字符串方法replace()的第二个参数为函数讲解](https://blog.csdn.net/JCY1009015337/article/details/45220431){:target='_blank'}
- [String.prototype.replace()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace){:target='_blank'}

```js
// 下划线转换驼峰
function toHump(name) {
    return name.replace(/\_(\w)/g, function(all, letter){
        return letter.toUpperCase();
    });
}
// 驼峰转换下划线
function toLine(name) {
  return name.replace(/([A-Z])/g,"_$1").toLowerCase();
}
 
 
// 测试
let a = 'a_b2_345_c2345';
console.log(toHump(a));
 
let b = 'aBdaNf';
console.log(toLine(b));
```

实用封装：
```js
// 下划线转换驼峰
function toHumpObj (data) {
    if (typeof data == 'object') {
      for (const key in data) {
        if (data.hasOwnProperty(key)) {
          let eleValue = data[key];
          typeof eleValue == 'object' && toHumpObj(eleValue);
          delete data[key];
          let newKey = key.replace(/\_(\w)/g, function (all, letter) {
            return letter.toUpperCase();
          });
          data[newKey] =
            newKey == 'CompanyId' || newKey == 'State' ? +eleValue : eleValue;
        }
      }
    }
    return data;
  }
  // 驼峰转换下划线
  function toLineObj (data) {
    if (typeof data == 'object') {
      for (const key in data) {
        if (data.hasOwnProperty(key)) {
          let eleValue = data[key];
          typeof eleValue == 'object' && toLineObj(eleValue);
          delete data[key];
          let newKey = (key[0].toLowerCase() + key.slice(1)).replace(/([A-Z])/g, "_$1").toLowerCase();
          data[newKey] =
            newKey == 'CompanyId' || newKey == 'State' ? +eleValue : eleValue;
        }
      }
    }
    return data;
  }
```

## 第八十六式：如何通过脚本来新建文件，提高开发效率？

- 抛砖引玉，你一定会探究出更高级的用法

- 接口

## 第八十七式：跨域请求都会有option 请求吗？Http option 请求是怎么回事

- [Http option 请求是怎么回事](https://www.cnblogs.com/bradwarden/p/11505999.html){:target='_blank'}：跨域的复杂请求需要preflight request（预检）
- [http跨域时的options请求](https://www.jianshu.com/p/5cf82f092201){:target='_blank'}

## 第八十八式：window.getSelection()

谈过了禁止复制，那，复制是如何实现的呢？

- [clipboard.js 的源码分析](https://mp.weixin.qq.com/s/nsEmDprpeICz_wC3Xu9cPQ){:target='_blank'}
- [Window.getSelection](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/getSelection){:target='_blank'}
- https://developer.mozilla.org/zh-CN/docs/Web/API/Selection

## 第八十九式：函数参数传递，到底传递了什么——你应该知道的那些区别

- 箭头函数和普通函数
- 基本类型和引用类型

```js
var obj1 = {
  value: '111',
};

var obj2 = {
  value: '222',
};

function changeStuff(obj) {
  obj.value = '333';
  obj = obj2;
  return obj.value;
}

var foo = changeStuff(obj1);

console.log(foo); // '222' 参数obj指向了新的对象obj2
console.log(obj1.value); //'333'
```

**函数的参数传递，传递的都是值，参数是 Object 类型的也一样，也是值，只不过这个值是地址值。**

- [Is JavaScript a pass-by-reference or pass-by-value language?](https://stackoverflow.com/questions/518000/is-javascript-a-pass-by-reference-or-pass-by-value-language?lq=1){:target='\_blank'}
- [javascript 传递参数如果是 object 的话，是按值传递还是按引用传递？](https://www.zhihu.com/question/27114726/answer/35481766){:target='\_blank'}
- [JavaScript 中函数都是值传递吗？](https://www.zhihu.com/question/51018162/answer/123779633){:target='\_blank'}
- [箭头函数和普通函数的区别](https://segmentfault.com/a/1190000021380336){:target='\_blank'}
- [08 | x => x：函数式语言的核心抽象：函数与表达式的同一性](https://time.geekbang.org/column/article/171617){:target='\_blank'}
- [为什么函数赋值为null后,后续还会执行?](https://segmentfault.com/q/1010000040298121){:target='_blank'}

## 第九十式：web Storage事件机制 - 实现浏览器内多个标签页之间的通信

- 标签是当前页面打开的：可直接操作
- postMessage
- BroadCast Channel
    BroadcastChannel，叫做“广播频道”，官方文档说，该API是用于同源不同页面之间完成通信的功能。

    与window.postMessage的区别：BroadcastChannel只能用于同源的页面之间进行通信，而window.postMessage却可以用于任何的页面之间，

    基于BroadcastChannel的同源策略，它无法完成跨域的数据传输，跨域的情况，我们还是使用window.postMessage来处理

    使用起来很简单：

    发送消息：

    var bc = new BroadcastChannel(‘test_channel’);

    bc.postMessage(‘hello world’);

    接收消息:

    bc.onmessage = function(msg){
        console.log(msg);
    }
- localStorage
- cookie+setInterval()
- 使用websocket协议
- 使用html5浏览器的新特性SharedWorker。

大家一般都只知道localStorage.setItem(key,value)、localStorage.getItem(key)以及localStorage.removeItem(key)，一般却不会监听localStorage变化。
```js
window.onstorage = (e) => {console.log(e)}
// 或者这样
window.addEventListener('storage', (e) => console.log(e))
```
- [JavaScript之web Storage事件机制](https://blog.csdn.net/weixin_43772533/article/details/107166033)
- [如何实现浏览器内多个标签页之间的通信？](https://blog.csdn.net/meijory/article/details/76358570)
- [实现多个标签页之间通信的几种方法(sharedworker)](https://www.jianshu.com/p/31facd4934d7)
- [实现浏览器内多个标签页之间的通信](https://segmentfault.com/a/1190000018354650)
- [面试官：前端跨页面通信，你知道哪些方法？](https://juejin.cn/post/6844903811232825357){:target='_blank'}
- [【3分钟速览】前端广播式通信：Broadcast Channel](https://juejin.cn/post/6844903811228663815){:target='_blank'}


