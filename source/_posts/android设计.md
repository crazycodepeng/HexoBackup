---
title: Material Design设计
date: 2017-07-12 11:19:20
tags: [android,Material]
---


1. 小屏幕优先
    1. > 小屏幕优先，虽然大屏幕会有大部分留白，但是不影响使用，
    可是如果大屏幕优先，小屏幕就可能无法使用。

2. 密度桶 ，以下是四种常用密度
   1. <img src="http://oqdxnp2lc.bkt.clouddn.com/dpi-buckets.png" width="80%" height="80%">

3. drawable-nodpi文件夹-放入的是不会根据密度进行缩放的图片-比如背景图

4. elevation -设置控件高度
   1. <img src="http://oqdxnp2lc.bkt.clouddn.com/QQ20170712-171104@2x.png" width="80%" height="80%">

5. 添加FAB按钮

    1. 首先讲下边这两行添加到你的build.grade文件中
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/buildgrade.png" width="80%" height="80%">
    2. 属性
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/fab.png" width="80%" height="80%">
        2. > fabSize - FAB的大小
        3. > elevation - FAB高度
        4. > pressedTranslationZ - 按下FAB，按钮变大的数值
    3. 针对老版本项目
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/appcompat.png" width="80%" height="80%">
6. CoordinatorLayout 滚动的动态页面
    1. <img src="http://oqdxnp2lc.bkt.clouddn.com/coodinglayout.png" width="80%" height="80%">
    2. > 只有添加了 `nestedScrollingEnabled="true"` 才能实现工具栏联动
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/nestedScrolling.png" width="80%" height="80%">
7. 添加自定义字体
    1. > 将下载的字体放入assets下
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/ziti.png" width="80%" height="80%">
    2. > 在`onAttach` 方法中实例化字体类型
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/onattact.png" width="80%" height="80%">
    3. > 然后在 `onCreate` 方法中将字体类型设置给`TextView`
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/oncreateview.png" width="80%" height="80%">

8. 圆形图像的处理方法
    1. <img src="http://oqdxnp2lc.bkt.clouddn.com/yuanxingtouxiang.png" width="80%" height="80%">

9. 固定宽高比图像
    1. 自定义ImageView
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/zidingyiimage.png" width="80%" height="80%">
    2. 重写onMeasure方法
        1. 设置宽高比例
        2. 将设置好的数值传递给超类
        3. <img src="http://oqdxnp2lc.bkt.clouddn.com/onmeasure.png" width="80%" height="80%">
    3. xml中使用，控件高度使用0dp,会根据权重去自动计算控件高度
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/imagexml.png" width="80%" height="80%">

10. 背景保护 - 文字、图标和背景色一样导致看不到问题
    1. <img src="http://oqdxnp2lc.bkt.clouddn.com/titlemeile.png" width="80%" height="80%">
    2. 创建一个带透明度的渐变色
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/jianbianse.png" width="80%" height="80%">
    3. 用FrameLayout来堆叠视图
        1. <img src="http://oqdxnp2lc.bkt.clouddn.com/frameduidie.png" width="80%" height="80%">
11. 动画设置
    1. 动画时长一般在～300ms
    2. 要根据尺寸和移动距离来确定动画时长
    3. 对于穿过屏幕的动画，可以使用快出慢进的过渡
    4. 动画可指导用户动作
    5. 动画不要重叠，这样会感觉很乱
    6. AnimatedVectorDrawables   VectorDravable   矢量图动画 4-19（回顾）
12. 自适应
    1. 文本边缘要比行间距大，行间距要适中。
    2. 单行文本不易过长，不易阅读。
    3. 图片尽量不要裁剪，保持宽高比，保证图片清晰度。
    4. 详细信息少的，尽量用dialog形式展示
    5. 设计时要均衡空间，不要有太多留白。
    6. 整体设计不要参差不齐
    7. 通过layout-w600dp和include来为大尺寸屏幕重新设计排版
