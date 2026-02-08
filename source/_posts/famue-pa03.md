---
title: 拯救电子垃圾之梵沐 PA03
date: 2026-02-08 18:58:25
tags: # 标签列表
    - Android
    - Magisk
    - MTK
    - 电子垃圾
categories: # 分类列表
    - 折腾
excerpt: 折腾垃圾电子设备梵沐 PA03，允许为其安装第三方应用程序，获取 ROOT 权限。
---
## 前传

某同学无意中知悉，自己全款购入的 MP3 居然是**不能安装第三方软件的 Android**，遂心生歹意，希望解除其对安装第三方软件的限制。

## 历程

### 基本了解

晚自习他就迫不及待地把设备借给我，因此我们可以先对它进行一个非正式的把玩。在对其外观进行一个粗略观察后，我们可以得到如下信息：

{% notel purple 设备信息 %}
<strong>品牌：</strong>梵沐 Famue
<strong>型号：</strong>PA03
{% endnotel %}

{% note gray %}
*我没见过的品牌一律当作杂牌处理（bushi*
{% endnote %}

根据一点微薄的经验，我们可以知道，这种电子垃圾**有很大概率是联发科 SoC**，它和 **MTK Client** 也许能帮助我们给折腾降低不少难度。

由于暂时没有其他设备，因此我们只能先试试，找到系统内常规的突破点。

经过一些杂乱且毫无头绪的翻找，我们可以毫不费力地发现如下可能有用的信息：

{% notel purple 设备信息 %}
<strong>操作系统：</strong>Android 6.0（甚至彩蛋都完整保留了，可惜一分都得不了，悲）
<strong>可能的突破点：</strong>允许未知应用安装（默认打开）、开发者模式 & OEM 解锁 / USB 调试（可以打开）
{% endnotel %}

### ADB

我们万分欣喜，于是尝试直接使用 ADB 安装 **[MT 管理器](https://mt2.cn/)**，非常幸运地成功了。

我们以为已经大功告成了，可是尝试使用系统内方法（不用 ADB）安装 APK 时，居然遇到了另外的障碍：

{% notel red 设备反骨 %}
障碍：初步猜测<strong>软件包安装程序被篡改</strong>，可能只允许来自特定包名的调用。
现象：系统自带的假应用市场可以调用软件包安装程序安装预置的软件包，卸载软件时软件包安装程序也会弹出，但使用系统自带的文件管理器打开会提示<strong>不受支持的格式</strong>，使用 MT 管理器打开会导致<strong>软件包安装程序闪退</strong>。
{% endnotel %}

其实也有解决办法，就是用 InstallerX 之类的 ADB 安装器，通过 Shizuku / Sui 等 <strong>授予 ADB 权限</strong>来安装 APK。但这样并不优雅稳定。于是我开始考虑 ROOT。

### ROOT

#### 前置准备

首先让我们使用 ADB 查询一些必要的信息，这有助于我们选择合适的方法。

```yaml
# 产品型号
ro.product.model = PA03
# MTK 的占位品牌，没有被厂商修改，可能是工程机等非正常版本，或者厂商太懒了
ro.product.brand = alps
# 主板代号/内部代号，似乎是工厂测试版
ro.product.device = y9be_v5_m_factory
# 制造商名称，怎么值还是型号？草台
ro.product.manufacturer = PA03
# 联发科内部固件版本，似乎是骗人的，因为标注了 3500 万像素相机但实际并没有镜头…
ro.mediatek.version.release = B01_PA03_35mp_KG_1.5_16_2.8inch_202308182018
# SoC，似乎是联发科某四核低端平台，28 nm，Cortex-A53 1.0~1.3GHz
ro.board.platform = mt6735m
# 指令集，纯 32 位
ro.product.cpu.abilist = armeabi-v7a,armeabi
```

非常垃圾啊，非常垃圾。

我们发现设备的 SoC 是 **MT6735M**，联发科。这就很好办了，我们可以直接使用 MTK Client 在启动早期（Boot ROM 左右吧，我忘了）读取和篡改分区。

{% notel purple 操作细节 %}
<strong>方法：</strong>完全关机，断开 USB，按住上下音量键，连接 USB，松开音量键，马上执行 `sudo mtk payload`，跑日志不报错就大概率正常。如果不正常就听它的话做吧，它让你干什么你就干什么。
{% endnotel %}

进入 DA 模式后，执行 `sudo mtk rl . --skip=userdata` 全盘备份。用户数据就不管了，没什么用还占空间。全盘备份的文件我放在[这里](https://t.me/RyansDoorstep/512)了。

#### 解锁

然后尝试解锁。

```zsh
➜  ~ sudo mtk da seccfg unlock
Main - Handling da commands ...
DaHandler
DaHandler - [LIB]: Unknown lockstate or no lockstate
```

似乎提示无锁？让我们读取 `seccfg` 分区简单验证下。

```zsh
➜  ~ sudo mtk r seccfg ./seccfg.bin
➜  ~ hexdump -C ./seccfg.bin | head -20
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00080000
```

大面积 `0`，果然没有锁，那我们再尝试进入 bootloader。

于是我们发现了一个非常奇怪的事情，虽然可以正常进入 bootloader，但是它仍然**固执地认为自己有锁**。

考虑到这种设备安全等级非常低，我们可以尝试不管 bootloader 的锁状态，直接使用 MTK Client 刷写分区，应该也是可以启动的。~~大不了再刷回来嘛。~~

#### 选择方案

这种老设备可能还是 [Magisk](https://github.com/topjohnwu/Magisk) 最保险，[KernelSU](https://github.com/tiann/KernelSU) 和 [APatch](https://github.com/bmax121/APatch) 似乎并不支持 Android 6.x。

于是我们从 Magisk [`20.4`](https://github.com/topjohnwu/Magisk/releases/tag/v20.4) 开始试起，很多版本都有或多或少的问题，比如有的版本无法选择镜像，有的版本在修补时闪退。诸如此类等等等等。

试到 [`23.0`](https://github.com/topjohnwu/Magisk/releases/tag/v23.0) 时，终于一切正常，于是就可以走常规流程，修补然后刷入了。

#### 执行方案

我们使用简单的 ADB 安装 Magisk `23.0`，将之前备份中的 `boot` 分区推入设备，修补，拉取，重启进入 DA 模式，执行 `sudo mtk w boot ./boot_patched.img`，等待进度条跑完就刷好了。

#### 检验结果

重启设备，打开 Magisk Manager，我们不难发现设备**已经成功 ROOT**，MT 管理器也可以请求权限了。虽然启动时提示检测到不属于 Magisk 的 su 文件，不过**应该无伤大雅**。反正我是没遇到什么问题，**又不是不能用.webp**。

于是就可以愉快地玩耍啦～

## 番外

在折腾完成后第二天，我们有了一个**惊世骇俗**的**超级无敌大发现**。

我们似乎可以通过直接在系统计算器中输入 `.202188=` 来选择允许安装第三方软件。

也就是说我白折腾了？

**不管。**

反正就要 ROOT，**又不难。**

**略略略。**