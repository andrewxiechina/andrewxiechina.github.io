---
layout: post
title:  "［教程］使用React Native制作BBC网站"
categories: React
tags:  ReactNative JavaScript 教程 项目
author: Andrew Xie
---

* content
{:toc}

### 项目展示 
![Example Image](https://github.com/andrewxiechina/andrewxiechina.github.io/blob/master/img/bbc_news.png?raw=true)

### 开发环境
在进行开发前需要下载安装以下内容：
- [Node.js](https://nodejs.org/en/download/)
- [Expo.js](https://expo.io/)：是在React Native基础上开发的。React Native使开发者可以同时在iOS，Android，桌面等平台进行开发，并且可共享80%
以上的代码。与普通的hybrid技术不同，React Native开发的程序和原生程序的外观基本没有区别，但是却可以基本完全由javascript写成。使用Expo XDE使的创建React Native程序变得非常容易，并且可以随时使用手机端的Expo程序进行调试。Expo还加入了一些常用的库。

关于适用Expo创建新项目的方法请参见：

### 安装常用库
- [React Navigation](https://reactnavigation.org/docs/intro/):是React Native官方推荐的路由（navigation）解决方案。
- [React Native Elements](https://react-native-training.github.io/react-native-elements/)：该库里面有一系列的常用组件，可以进行快速原型设计，和bootstrap的功能相似，并且有一个Grid系统。


### 和后台进行通讯














### TODOS
 - 获取列表页，详细内容页信息
 - 做列表页到详细内容页的路由（router）
 - 呈现详细内容（html）
 - 呈现详细列表
 - 添加细节
 
 
### 完成后项目截图

Copy Right：[https://github.com/joeltrew/BBCNews-React-Native](https://github.com/joeltrew/BBCNews-React-Native)


## POKEMON
![](https://github.com/andrewxiechina/andrewxiechina.github.io/blob/master/img/pokemon_home.png?raw=true)

### 用到的第三方包
- Expo
- React Navigation (Stack Navigation)
- react-native-refreshable-listview
- react-native-video
- htmlparser
- moment

### TODOS
 - 获取列表页，详细内容页信息
 - 做列表页到详细内容页的路由（router）
 - 呈现详细内容（html）
 - 呈现详细列表
 - 添加细节
 
Copy Right：[https://github.com/VctrySam/Pokemon](https://github.com/VctrySam/Pokemon)

## 原理

众所周知 setTimeout 或者 setInterval 调用的时候会有微小的误差。有人做了一个 [demo](https://bl.ocks.org/kenpenn/raw/92ebaa71696b4c4c3acd672b1bb3f49a/) 来观察这个现象并对其做了修正。短时间的误差倒也可以接受，但是作为一个长时间的倒计时，误差累计就会导致倒计时不准确。

因此我们可以在获取剩余时间的时候，每次 new 一个设备时间，因为设备时间的流逝相对是准确的，并且如果设备打开了网络时间同步，也会解决这个问题。

但是，如果用户修改了设备时间，那么整个倒计时就没有意义了，用户只要将设备时间修改为倒计时的 endTime 就可以轻易看到倒计时结束是页面的变化。因此一开始获取服务端时间就是很重要的。

简单的说，一个简单的精确倒计时原理如下：

- 初始化时请求一次服务器时间 serverTime，再 new 一个设备时间 deviceTime
- deviceTime 与 serverTime 的差作为时间偏移修正
- 每次递归时 new 一个系统时间，解决 setTimeout 不准确的问题

## 代码

获取剩余时间的代码如下：

```js
/**
 * 获取剩余时间
 * @param  {Number} endTime    截止时间
 * @param  {Number} deviceTime 设备时间
 * @param  {Number} serverTime 服务端时间
 * @return {Object}            剩余时间对象
 */
let getRemainTime = (endTime, deviceTime, serverTime) => {
    let t = endTime - Date.parse(new Date()) - serverTime + deviceTime
    let seconds = Math.floor((t / 1000) % 60)
    let minutes = Math.floor((t / 1000 / 60) % 60)
    let hours = Math.floor((t / (1000 * 60 * 60)) % 24)
    let days = Math.floor(t / (1000 * 60 * 60 * 24))
    return {
        'total': t,
        'days': days,
        'hours': hours,
        'minutes': minutes,
        'seconds': seconds
    }
}
```

<del>获取服务器时间可以使用 mtop 接口 `mtop.common.getTimestamp` </del>

然后可以通过下面的方式来使用：

```js
// 获取服务端时间（获取服务端时间代码略）
getServerTime((serverTime) => {

    //设置定时器
    let intervalTimer = setInterval(() => {

        // 得到剩余时间
        let remainTime = getRemainTime(endTime, deviceTime, serverTime)

        // 倒计时到两个小时内
        if (remainTime.total <= 7200000 && remainTime.total > 0) {
            // do something

        //倒计时结束
        } else if (remainTime.total <= 0) {
            clearInterval(intervalTimer);
            // do something
        }
    }, 1000)
})
```

这样的的写法也可以做到准确倒计时，同时也比较简洁。不需要隔段时间再去同步一次服务端时间。

## 补充

在写倒计时的时候遇到了一个坑这里记录一下。

**千万别在倒计时结束的时候请求接口**。会让服务端瞬间 QPS 峰值达到非常高。

![](https://img.alicdn.com/tfs/TB1LBzjOpXXXXcnXpXXXXXXXXXX-154-71.png)

如果在倒计时结束的时候要使用新的数据渲染页面，正确的做法是：

在倒计时结束前的一段时间里，先请求好数据，倒计时结束后，再渲染页面。

关于倒计时，如果你有什么更好的解决方案，欢迎评论交流。
