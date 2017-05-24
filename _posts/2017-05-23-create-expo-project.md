---
layout: post
title:  "［教程］使用Expo创建React Native项目"
categories: React
tags:  ReactNative JavaScript 教程 Expo.js
author: Andrew Xie
---

### Expo简介
Expo.js是在React Native基础上开发的。React Native使开发者可以同时在iOS，Android，桌面等平台进行开发，并且可共享80% 以上的代码。与普通的hybrid技术不同，React Native开发的程序和原生程序的外观基本没有区别，但是却可以基本完全由javascript写成。
使用Expo XDE使得创建React Native程序变得非常容易，并且可以随时使用手机端的Expo程序进行调试。Expo还加入了一些常用的库，例如图标等。Expo还将自动把图片、视频等上传到AWS上。

React Native使得软件升级变得更加容易，如果使用javascript外的语言写的原生组件不需要更新，则可以将所有的javascript代码更新到bundle.js中，然后由App进行下载，而无需重新由Apple官方进行审核，无需重新安装。而使用Expo则可使得这一工作流程变得更加容易。

不过使用Expo也有着明显的缺点。如果要使用Expo进行调试，则意味着整个程序中不能有原生组件。如果需要使用原生组件，则需要在使用时弃用Expo。所以在这类项目中，Expo可以作为初期创建项目和进行快速开发的平台。

### 创建项目
1. [下载Expo XDE](https://expo.io/)，如果需要使用手机进行调试，则还需要下载Expo的手机App。

2. 打开Expo XDE，注册进入主程序后选择Project -> New Project

3. 输入项目名称，选择存储位置，选择Blank模版，点击Create
![](https://github.com/andrewxiechina/andrewxiechina.github.io/blob/master/img/choose_template.png?raw=true)

4. 在项目创建完成并启动后，开启模拟器，点击右上角的`Device`，选择`Open on iOS Simulator` (选择Open on Android可以打开模拟器或手机进行开发，但必须曾经使用该机器进行Android开发。如不成功，则请参见文档）。
![](https://github.com/andrewxiechina/andrewxiechina.github.io/blob/master/img/expo/simple_app.png?raw=true)

5. 除模拟器外，还可以选择直接在手机上观察开发效果。点击右上角的`Share`，打开手机端的Expo APP并扫描二维码。

### 调试选项
在调试中，可以在模拟器上使用command＋D打开下图菜单，在手机上则可以摇动手机。其中`Show Perf Monitor`可以显示帧率和内存使用等数据，而`Toggle Element Inspector`则有和Chrome开发者工具类似的功能，可以通过点击组件，显示组件长宽等，在调试中非常重要。

![](https://github.com/andrewxiechina/andrewxiechina.github.io/blob/master/img/expo/menu_page.png?raw=true)
