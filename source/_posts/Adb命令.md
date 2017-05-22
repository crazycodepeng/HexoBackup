layout: android
title: Adb命令
date: 2017-05-17 14:21:55
tags: [Android,Adb]
---

# 常用Adb命令


### 1.安装应用 install后边直接拖apk进终端就好
 ``` bash
 $ adb install app.apk
 ```

 ---

### 2.当连接设备多个时怎么安装apk呢

#### 第一步
``` bash
$ adb devices
```
#### 第二步
``` bash
$ adb -s emulator-5553 install app.apk
```
#### 如下图

{% asset_img adbinstall.png 安装apk %}

---
### 3.获取自由模式-前提是手机有root权限

#### 第一步
``` bash
$ adb shell
```
#### 第二步 获得root操作权限
``` bash
# su
```

#### 第三步
``` bash
# settings put global enable_freeform_support 1
```
#### 重启模拟器或设备
``` bash
# reboot
```
---

