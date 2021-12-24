# BSP 开发流程

> 该教程适用于需要自行开发 胸牌底层 C 代码的同学，通过该教程便可以掌握对胸牌的 BSP开发。

## 焊接 SWD 排针接口

* 如下图所示，请自行焊接胸牌的 SWD 排针接口。

![](img\排针.png)

* 然后使用杜邦线连接好 stlink/jlink 至胸牌，选择下载算法，进行 bsp 源码的烧录。
* 注意：下载算法若第一次配置需要将 `flashalgo` 下的两个文件复制到 安装 mdk 的目录下的  `..\ ARM\Flash ` 中。

![下载算法的选择](img\下载算法.png)

## 烧录 BSP 程序

* 点击 mdk 左上角的下载按钮，进行代码的烧录。

![下载按钮](img\下载.png)

> 新版本胸牌支持使用 env 工具对 RT-Thread 源码、软件包进行配置，env 的使用教程请自行百度 RT-Thread env 学习。



## 老版本硬件胸牌注意

> 以下修改仅适用 2020 款电子胸牌，2021 款可以跳过

### 1. 修改 drv.touchpad.c 文件

![](img\修改引脚.png)

* 将按键引脚替换为下面的引脚即可

```c
#ifndef PIN_KEY_UP
	#define PIN_KEY_UP      P2_4
#endif

#ifndef PIN_KEY_DOWN
	#define PIN_KEY_DOWN    P2_5
#endif

#ifndef PIN_KEY_LEFT
	#define PIN_KEY_LEFT    P2_6
#endif

#ifndef PIN_KEY_RIGHT
	#define PIN_KEY_RIGHT   P2_7
#endif
```



