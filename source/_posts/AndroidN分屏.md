layout: multiwindow
title: Android多窗口支持
date: 2017-05-11 20:15:35
tags: [Google,Android7,多窗口支持]
---


 > Android N 添加了对同时显示多个应用窗口的支持。
 > 在手持设备上，两个应用可以在“分屏”模式中左右并排或上下并排显示。
 > 在电视设备上，应用可以使用“画中画”模式，在用户与另一个应用交互的同时继续播放视频。

 <img src="https://developer.android.com/images/android-7.0/mw-splitscreen_2x.png">

## 如何启动分屏

1.*第一种方式*

 按 Overview 按钮进入 Overview 界面，然后长按 activity 拖动到界面的提示区域(我的手机是顶部)。



<img src="http://oqdxnp2lc.bkt.clouddn.com/fenpingfs.gif" width="40%" height="40%">


2.*第二种方式*

 在 activity 界面长按 Overview 按钮，如果 activity 没有禁用分屏模式就可以进入分屏界面了。


## 解析官方Demo里的几种启动模式

1.*第一种启动方式-START BASIC，DEFAULT ACTIVITY(默认的启动方式)*

 这种启动方式并没有什么特别的，启动的 activity 如果没有设置其他属性，可正常进入分屏模式。

<img src="http://oqdxnp2lc.bkt.clouddn.com/basic.png" width="70%" height="70%">

2.*第二种启动方式-START UNRESIZEABLE ACTIVITY(禁用分屏模式)*

 这个模式中在 AndroidManifest 中加入了 `android:resizeableActivity=”false”` 将禁用分屏，
 如果不加这条属性，默认是 true，启用分屏模式。

<img src="http://oqdxnp2lc.bkt.clouddn.com/jyfpcode.png" width="70%" height="70%">

<img src="http://oqdxnp2lc.bkt.clouddn.com/jyfpfest.png" width="70%" height="70%">

 该模式下如果想启动分屏模式会提示`该应用不支持分屏`

<img src="http://oqdxnp2lc.bkt.clouddn.com/jyfp.png" width="40%" height="40%">

3.*第三种启动方式-START ACTIVITY ADJACENT(共享分屏模式)*

 如果处于分屏模式下，被启动 activity 直接占据屏幕另一半。否则这种启动方式并没有什么不同。
只需要在启动时加入`Intent.FLAG_ACTIVITY_LAUNCH_ADJACENT`即可。

 <img src="http://oqdxnp2lc.bkt.clouddn.com/fpcode.png" width="70%" height="70%">
 <img src="http://oqdxnp2lc.bkt.clouddn.com/fenping.gif" width="40%" height="40%">

4.*第四种启动方式-START ACTIVITY THAT HANDLES CONFIGURATIONCHANGES(加配置信息)*

 这种启动方式里在 AndroidManifest 的 configChanges 属性里加入了很多属性。比如禁用横竖屏切换之类的,
 如果想仔细了解这些配置可以看<a href=" https://developer.android.com/guide/topics/resources/runtime-changes.html">官方文档</a>，里面说的很详细，这里就不过多赘述了。

 <img src="http://oqdxnp2lc.bkt.clouddn.com/peizhi.png" width="70%" height="70%">


5.*第五种启动方式-START ACTIVITY WITH MINIMUM SIZE(Root权限下在AndroidManifest的一些属性配置)*

 对于 Android N，<layout> 清单元素支持以下几种属性，这些属性影响 Activity 在多窗口模式中的行为：

   + android:defaultWidth
    以自由形状模式启动时 Activity 的默认宽度。

   + android:defaultHeight
    以自由形状模式启动时 Activity 的默认高度。

   + android:gravity
    以自由形状模式启动时 Activity 的初始位置。请参阅 <a href="https://developer.android.com/reference/android/view/Gravity.html">Gravity</a> 参考资料，了解合适的值设置。

   + android:minimalHeight、android:minimalWidth
    分屏和自由形状模式中 Activity 的最小高度和最小宽度。 如果用户在分屏模式中移动分界线，使 Activity 尺寸低于指定的最小值，系统会将 Activity 裁剪为用户请求的尺寸。


 在以下节点显示了如何指定 Activity 在自由形状模式中显示时 Activity 的默认大小、位置和最小尺寸

 <img src="http://oqdxnp2lc.bkt.clouddn.com/rootfp.png" width="70%" height="70%">

6.*第六种启动方式-START ACTIVITY WITH MINIMUM SIZE(Root权限下在代码中的属性配置)*

 这个和第五种差不多，就是在代码中设置了

<img src="http://oqdxnp2lc.bkt.clouddn.com/codeset.png" width="70%" height="70%">


# 多窗口变更通知和查询

 <a href="https://developer.android.com/reference/android/app/Activity.html">Activity</a>类中添加了以下新方法，以支持多窗口显示。

  1. Activity.isInMultiWindowMode()
    调用该方法以确认 Activity 是否处于多窗口模式。

  2. Activity.isInPictureInPictureMode()
   调用该方法以确认 Activity 是否处于画中画模式。

       + 注：画中画模式是多窗口模式的特例。 如果 myActivity.isInPictureInPictureMode() 返回 true，则 myActivity.isInMultiWindowMode() 也返回 true。

  3. Activity.onMultiWindowModeChanged()
   Activity 进入或退出多窗口模式时系统将调用此方法。 在 Activity 进入多窗口模式时，系统向该方法传递 true 值，在退出多窗口模式时，则传递 false 值。

  4. Activity.onPictureInPictureModeChanged()
   Activity 进入或退出画中画模式时系统将调用此方法。 在 Activity 进入画中画模式时，系统向该方法传递 true 值，在退出画中画模式时，则传递 false 值。
---
  > 每个方法还有 Fragment 版本，例如 Fragment.isInMultiWindowMode()。

---
 > 关于更多关于Android<a href="https://developer.android.com/guide/topics/ui/multi-window.html">多窗口支持</a>的信息可点击链接查看

---
 > 最后附上我github稍微翻译了一下的<a href="https://github.com/crazycodepeng/android-multiwindowplayground">官方demo</a>