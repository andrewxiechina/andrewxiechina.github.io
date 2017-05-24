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

关于适用Expo创建新项目的方法请参见[https://andrewxiechina.github.io/2017/05/23/create-expo-project/](https://andrewxiechina.github.io/2017/05/23/create-expo-project/)。

### 安装常用库
- [React Navigation](https://reactnavigation.org/docs/intro/):是React Native官方推荐的路由（navigation）解决方案。
- [React Native Elements](https://react-native-training.github.io/react-native-elements/)：该库里面有一系列的常用组件，可以进行快速原型设计，和bootstrap的功能相似，并且有一个Grid系统。

安装代码如下：
```bash
npm install --save react-navigation
npm install --save react-native-elements
```
### 和后台进行通讯














### TODOS
 - 获取列表页，详细内容页信息
 - 做列表页到详细内容页的路由（router）
 - 呈现详细内容（html）
 - 呈现详细列表
 - 添加细节
 
 
### 完成后项目截图

Copy Right：[https://github.com/joeltrew/BBCNews-React-Native](https://github.com/joeltrew/BBCNews-React-Native)
