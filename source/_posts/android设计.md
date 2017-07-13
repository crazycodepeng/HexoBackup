---
title: Material Design设计
date: 2017-07-12 11:19:20
tags: [android,Material]
---


1. 小屏幕优先
    1. > 小屏幕优先，虽然大屏幕会有大部分留白，但是不影响使用，
    可是如果大屏幕优先，小屏幕就可能无法使用。


2.  密度桶 ，以下是四种常用密度
   1. <img src="http://oqdxnp2lc.bkt.clouddn.com/dpi-buckets.png" width="80%" height="80%">

3.  drawable-nodpi文件夹-放入的是不会根据密度进行缩放的图片-比如背景图

4.  elevation -设置控件高度
   1. <img src="http://oqdxnp2lc.bkt.clouddn.com/QQ20170712-171104@2x.png" width="80%" height="80%">

5.  添加FAB按钮

    1. 首先讲下边这两行添加到你的build.grade文件中
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/buildgrade.png" width="80%" height="80%">
    2. 属性
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/fab.png" width="80%" height="80%">
        2. > fabSize - FAB的大小
        3. > elevation - FAB高度
        4. > pressedTranslationZ - 按下FAB，按钮变大的数值
    3. 针对老版本项目
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/appcompat.png" width="80%" height="80%">
6.  CoordinatorLayout 滚动的动态页面
    1. <img src="http://oqdxnp2lc.bkt.clouddn.com/coodinglayout.png" width="80%" height="80%">
    2. > 只有添加了 `nestedScrollingEnabled="true"` 才能实现工具栏联动
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/nestedScrolling.png" width="80%" height="80%">
