---
layout: post
title: Lenove产品Bios培训
categories: Lenovo
description: some word here
keywords: Bios， Lenovo， Case
---

感谢Ryuu的博文[Bios设置](https://kuroidark.github.io/posts/培训/BIOS设置.html) 

**BIOS**（Basic Input Output System），中文名称“基本输入输出系统”。是一组固化到计算机主板上一个ROM芯片上的程序，它保存着计算机最**重要的基本输入输出的程序、开机后自检程序和系统自启动程序**，它可从CMOS（Complementary Metal Oxide Semiconductor互补金属氧化物半导体 ）中读写系统设置的具体信息。 其主要功能是**为计算机提供最底层的、最直接的硬件设置和控制**。

#### 如何进入Bios

- （台式+一体机）**F1**

- （笔记本）**FN+F2/F2**

  ```win10在快速启动没关的情况下可能无法按F1进入Bios，解决方法为：*1、关闭快速启动/在当前系统下重启电脑 2、进入疑难解答界面（按Shift+重启/强制重启三次/设置界面-安全-恢复-重新启动）-UEFI固件设置```

#### 如何进入安全模式

安全模式是系统的**底层**

- [WIN7]（台式）**F8**  （笔记本）**FN+F8**/**F8**

- [WIN10]（台式+笔记本）**进入疑难界面-查看更多-启动设置**

  > 注：客户如果开机十分钟蓝屏或者关机，可以进入安全模式看系统底层有没有问题，如果没有问题，就有可能是最近安装的驱动有问题

  

### Main

---

**System Summary**「系统描述」→*可以查看电脑的主机配置和**硬盘***

System Serial Number「出厂编号」

Preinstalled OS License「预装正版操作系统」

```OKM激活（激活信息在主板内）、MAK key激活（零售商激活）、KMS服务批次激活（大公司多用）```

OA3 License Key ID「正版office等软件」

OA2.1 Make License「其他软件授权信息」

> Case：电脑时间异常
>
> Solution：1、时间过快或者过慢（大于10min） 故障件：**主板**
>
> ​                   2、时间总恢复到出厂值，由于CMOS电池无法存储信息 故障件：**主板**



### Devices

---

USB Setup「USB菜单」→USB Virtual KBC Support「虚拟USB键鼠」

**ATA Drive Setup**「ATA设备菜单」→Config SATA AS「硬盘模式」

```WIN XP 使用IDE模式、 WIN 7及以后使用AHCI模式```

Video Setup「显示菜单」

> Case：主机加电无显示
>
> Cause：配置独立显卡，默认情况自动屏蔽集成显卡

Audio Setup「音频菜单」

Network Setup「网络菜单」



**故障问题**

>Case：如何设置多屏输出
>
>Solution：1、XP系统最多支持双屏显示 2、Video Setup→Multl-Monltor Support设置为Enable（打开支持多屏输出） 3、六代前的主板只能支持集显或者独显单独工作，六代及以后可以同时工作

> Case：启动报错**DHCP**或者PXE-MOF:Exiting PXE ROM
>
> Solution：BIOS-Devices-Network Setup-**Boot Agent[Disable]**



### Advanced

---

CPU Setup「CPU菜单」→**Intel(R) Virtualization Technology/ VT-d/ txt**「Intel虚拟化技术」

Turbo Mode「睿频模式」

```通过降低其他核心的频率来提高一个主核的频率来增强性能```



### Power

---

After Power Loss「电源恢复后状态」

- Last Start「恢复到断电前的状态」
- Power Off「通电后不自启」
- Power On「通电自启

Automatic Power On「自动唤醒配置」

- Wake on Lan「网络唤醒」
- Wake from Serial Port Ring「串口唤醒」
- Wake Up on Alarm「时钟唤醒」—设置固定的时间启动



**故障问题**

> Case：计算机关机状态自动启动
>
> Solution：After Power Loss「Power Off」
>
> ​                  Automatic Power Power On→**所有的唤醒功能项都改为[Disable]**                  



### Security

---

Set Adminstrator Password「设置管理员密码」

Set Power-On Password「设置开机密码」

Allow Flashing Bios to a Previous Version「允许更新到低版本Bios」

Require Admin.Pass.when Flashing「当刷新Bios提示输入管理员密码」

Windows UEFI Firmware Update「Windows UEFI固件升级」

Require POP on System Boot 「启动时需要输入开机密码」

Require POP on Restart「重启时输入开机密码」

POP Changeable by USER「普通用户更改开机密码权限」

Require Admin, Pass, for F12 Boot「F12 调起启动菜单时输入 BIOS 密码」 

```通过开机F12可以看到硬盘是否被识别到```

**Smart USB Protection 「智能 USB 保护」**

```Disable 正常使用所有USB社保、Read Only 只读、No Access 只能使用键鼠无法使用U盘```

Hard Disk Password「硬盘密码」

```注意非损，清CMOS无法完全清楚硬盘密码```

Fingerprint Setup「指纹设置」

TCG Feature Setup「TCG安全芯片设置」

System Event Log「系统事件日志」 

Secure Boot「安全启动」 

```保护预装系统，该功能不关闭，重装系统会打不开。重装系统前注意数据备份```

Device Guard「设备保护」 

```导致有些功能无法使用```

Password Count Exceeded Error「密码输入超限错误」

```密码输入超过三次报错0199```



**故障问题**

> Case：0199报错是密码输入三次错误后的机器报警可能是开机密码错误和硬盘密码错误
>
> Solution：按F2会显示出设置密码类型1、输入正确的开机密码，可以正常启动计算机（应急方案为清         CMOS，但不推荐用户使用）2、输入正确的硬盘密码后即可正常启动系统（不要清CMOS，不然硬盘报废）



### Startup

---

Primary Boot Sequence「主要启动顺序」

```可以查看硬盘是否被识别到```

- Excluded from boot order「禁止启动」

   ```禁止后会导致按F12找不到引导盘```

CSM「兼容模块」

```WIN 7及以前开启```

- Boot Mode「启动方式」
- Boot Priority「启动方式优先级」
- Start Up Device Menu Prompt「F12启动菜单功能开关」



**WIN10换WIN7注意事项**

- 备份数据
- 重新分区
- 如果是预装了Win10系统，改Win7后会有激活问题，提醒用户
- NVme 的 SSD 需要加载NVme驱动
- 如果是6代CPU需要封装USB3驱动
- 100代之后的主板理论上不支持Win7，提醒用户

![微信截图_20190819014325](https://raw.githubusercontent.com/apolonmxl/apolonmxl.github.io/master/images/posts/2019-08-18/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20190819014325.png)![微信截图_20190819014308](https://raw.githubusercontent.com/apolonmxl/apolonmxl.github.io/master/images/posts/2019-08-18/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20190819014308.png)



### Exit

Save Changes and Exit「保存并退出，按F10」

Discard Changes and Exit「不保存并退出」

Load Optimal Defaults「加载默认设置，按F9」

**OS Optimized Defaults「优化OS初始值」**

- Win7及以前[Disabled]
- Win8及以后[Enable]
