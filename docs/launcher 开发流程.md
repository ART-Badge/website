# Launcher 开发流程

## 设计器导入 Launcher 工程

打开 `PersimStudio` 设计器，在设计器中打开 Launcher 工程进行修改二次开发即可，`ART-BadgeV2.0_launcher` 文件夹里的就是 Launcher 的源码。

![导入工程](img\导入工程.png)

* 打开后便会显示 launcher 的工程界面

![launcher工程](img\launcher工程.png)

## 打包 Launcher 为 prc 文件

* 点击左下角的 `打包项目` 后，右下角会提示打包成功

![打包项目](img\打包项目.png)

* 打开文件 `\ART-BadgeV2.0_launcher\dist` ，其中 app.prc 为已经打包好的 .prc 文件

  ![](img\prc.png)

## 根文件系统打包

`ART-Badge ` 的文件系统是以 `ROMFS` 的方式挂载到了 `SPI Nor Flash` 上，所以我们需要将 `rootfs` 文件夹打包，生成 root.bin 文件。

生成 root.bin 文件需要使用一个脚本工具 `persim_mkromfs_script.zip`，该工具需要依赖 Python 3，故请到Python 官网下载：https://www.python.org/downloads/ 。安装 Python 3 的时候需要特别注意，需将其添加到 Windows 的环境变量中来，如下图所示。若安装时忘记勾选，请自行百度安装后添加环境变量的方法。

![](C:\Users\RTT\Desktop\ART-Badge 二次开发文档\img\python3.png)

解压 `persim_mkromfs_script.zip`，把 `root.zip` 根文件解压在 `...\persim_mkromfs_script` 文件夹里面，`root` 的文件夹解构如下：

```makefile
root
├───system                 #系统目录
│   ├───apps               #系统小程序存放目录
│   │   ├───launcher       #launcher 程序存放目录
│   ├───fonts              #公共字体目录
│   ├───icons              #公共图标目录
│   ├───lib                #公共系统模块
│   │   ├───js             #JS 模块库
├───user                   #用户目录
│   ├───apps               #用户小程序存放目录
```

将刚刚设计器中生成的 `app.prc` 文件拷贝到 `Persim_Tools\persim_mkromfs_script\root\system\apps\launcher` 路径下，返回到 `...\persim_mkromfs_script`，双击 `mkromfs.bat` 运行，与其同级目录下可见生成了 `root.bin`。

![mkromfs](img\mkromfs.png)

`persim_mkromfs_script` 可以在SDK包的 `firmware`目录下的 `tools`下获得

得到 `root.bin`后，使用Jlink连接到 `SPI Nor Flash`上，通过 `MPTool`工具烧写到 `SPI Nor Flash` 上。烧写完成后重新启动即可看到运行效果。



![root.bin](img\root.png)

## 添加默认应用（可省略）

以下三个步骤就能添加一个出厂默认应用:

1. 打开程序打包目录，查看 `app.json` 文件，并记下 `id` 字段的值。

![小程序id](img\小程序id.png)

2. 在 `system/apps` 目录下新建一个跟 `id` 字段同名的文件夹。

![\新建id文档](img\新建id文档.png)

3. 拷贝 `app.prc`、`app.json` 及相应的图标文件到新建的目录下。

![dist目录](img\dist目录.png)

![id目录](img\id目录.png)

## 下载 Launcher 固件

> 下载 Launcher 后想立马运行起来看到效果，需要保证板子已经烧录过出厂固件（默认）

1. 下载 Launcher 固件需要使用 MPTool 工具。

2. 使用之前需要先注册，在 `..\Bee2MPTool_kits_v1.0.4.0\Registry Set` 里找到 `RegistrySet.exe`，双击执行即可（不会有任何提示，双击就可以了）；如果提示错误，请阅读该目录下的 `ReadMe.txt` 文档解决。

3. 打开 MPTool 工具之后，需切换到 `调试` 模式，见下图指示。

![](img\调试.png)

4. 先将 `Image Files` 取消勾选，然后勾选上 `User Data` ，点击 `User Data` 按键选择之前生成的 `root.bin` 固件，见下图指示。

![](img\userdata1.png)

* 选择打包好的 `root.bin`  ，并修改烧录目标地址为 `0x00C00000`

![选择bin](img\userdata2.png)

* ART-Badge 使用 USB线 与电脑连接，先按下内键（即 `LOG_UART_TX` 键）不放，然后按一下外键（即 `RESET` 键）复位 MCU，最后松开内键即可。

![内外键](img\内外键.png)

* 使用 MPTool 工具中点一下 `Detect` 和 `Open`，会看到有一个 COM 口显示 OK。如下图所示：

![detect](img\detect.png)



点击下载，下载成功之后，开机会显示 `湃心 OS PersimWear` LOGO ↓↓，并进入 Launcher 界面，至此说明你的 Launcher 开发成功了。

![](img\成功.png)
