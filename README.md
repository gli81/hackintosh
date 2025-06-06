# Hackintosh

## 目录

- [中文版](#工具)
  - 工具
  - 镜像1：E3v3 + RX570显卡ITX主机
    - 概述+硬件介绍
    - 更新记录
    - 测试
    - 问题
  - 参考
- [English](#Tools)
  - Tools
  - EFI1: E3v3 + RX570 itx build
    - Intro
    - Updates
    - Tests
    - Problems
  - References

---

## 工具

- [OpenCore](https://github.com/acidanthera/OpenCorePkg)
- [SSDTTime](https://github.com/corpnewt/SSDTTime)
- [USB mapping tools](https://github.com/USBToolBox/tool)
- [ProperTree](https://github.com/corpnewt/ProperTree)
- [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)
- [balenaEtcher](https://www.balena.io/etcher)
- [OpenCore Scanity Checker](https://opencore.slowgeek.com/)
- [OpenCore Auxilliary Tool](https://github.com/ic005k/OCAuxiliaryTools)
- [DiskGenius](https://www.diskgenius.cn/)
- [sysin](https://sysin.org/)
- [IASL](https://acpica.org/)

## E3v3的EFI

### 硬件配置介绍

| CPU      |              Xeon E3 1276v3 (核显Intel P4400)               |
| -------- | :---------------------------------------------------------: |
| 主板     |     微星B85I (网卡型号瑞昱8111G Gigabit Lan controller)     |
| 显卡     | <del>蓝宝石RX470D (刷蓝宝石570的bios)</del>华擎RX6600XT ITX |
| 内存     |                    芝奇 DDR3 8G 1866MHz                     |
| 无线网卡 |                      博通 BCM94360HMB                       |
| 硬盘     |                        致钛 SC001 1T                        |

### 步骤

1. 根据OpenCore Debug版`OC`文件夹创建EFI目录
2. 使用`USB mapping tools`获取USB map
3. 使用`SSDTTime`获取`DSDT`和`SSDT-EC`, `SSDT-HEPT`, `SSDT-PLUGIN`
4. 配置`Drivers`目录
5. 配置`Kexts`目录
6. 配置`config.plist`
7. 安装
8. 安装成功后检查声卡（并调整）
9. 使用`Hackintool`完善USB定制
10. 选择一个Picker或自定义一组Picker
11. 定制编译`SSDT`
12. 原生电源管理
13. 换到OpenCore Release版

### 测试

- 网卡 - 11✅12✅13✅
- 无线网卡
  - wifi - 11✅12✅13✅
  - AirDrop - 11❌12✅13✅
  - 接力 - 11❌12✅13✅
- 声卡 - 11✅12✅13✅
- 睡眠 - 11✅12❓13❌

### 问题

- ~~2023-03-22 - 桌面左上角出现一小块显示问题~~`换个桌面背景解决，原图片还是不能正常显示`
- ~~2023-03-22 - 为了解决上面的问题，直接重启了，于是会被直接引导到Windows（因为没有用OC引导替换原来的引导）~~`通过OpenCore Configurator将u盘efi分区覆盖硬盘efi分区，拔掉u盘后也能正常引导OC`
- ~~2023-03-22 - 拔掉u盘后进入OC，但OC不能引导Windows~~<del>`通过Windows镜像把Windows引导恢复了，又不能进入Mac啦，需要解决OC不能引导Windows的问题`</del>
- ~~2023-03-22 - OC不能引导Windows~~`使用EasyUEFI在Windows引导分区创建OC引导项，可以从硬盘引导OC再引导Windows和MacOS了，暂时不确定有没有更好的方法`
- ~~2023-03-22 - 声卡暂时不能驱动~~`可以驱动`
- 2023-03-22 - 有时拖动窗口时会导致死机重启
- 2023-03-22 - 视频播放偶尔卡顿
- 2023-03-22 - 副屏连接核显输出，系统加载前和刚关机时会大花屏；副屏最高选择60Hz刷新率
- <del>2023-03-22 - USB定制可能还不完善 2023-07-30 - 需要参考大头蔡的视频完善USB定制</del>
- ~~2023-03-22 - 但👴只想摆烂，过几天再修😝~~
- ~~2023-07-30 - 需要测试睡眠功能~~ `可以正常睡眠唤醒`
- 2024-07-28 - 自定义picker不能使用
- <del>2024-07-28 - 不确定是否需要`SSDT-HEPT`，根据OpenCore Guide， Haswell平台是不需要解决IRQ冲突问题的</del>2025-05-21`目前没问题`
- <del>2024-07-28 - `AppleALCU.kext`为`AppleALC.kext`的精简版，可以移除</del> `2025-05-21已移除`
- <del>2025-05-21 - 核显在`Monterey`中没有被正确驱动</del>`2025-05-24核显可以被正确识别为P4600，但不能VDA解码`
- <del>2025-05-24 - 核显不能在`Monterey`中硬解</del>`2025-05-25大概率Monterey是不能支持的`
- <del>2025-05-21 - 忘记删除Tools了</del> `2025-05-22 已移除`
- 2025-05-21 - 不确定`Misc>Debug`中未按照OC Official Guide设置的三项有没有问题

### 更新记录

#### 2023-03-20: 开始根据教程进行EFI配置

- 通过OpenCore下载适合的MacOS镜像
- 通过SSDTTime获取本机的`DSDT.aml`

#### 2023-03-21

- 从OpenCore指南里下载适配硬件的`kext`
- 使用USB mapping tool创建本机的USB映射，生成`UTBMap.kext`，并用ProperTree检查单个控制器是否超过15条通道
- 使用`SSDTTime`生成`SSDT-EC.aml`和`SSDT-PLUG.aml`
- 使用`ProperTree`调整`config.plist`
  - 
- 根据OpenCore指南将`Monterey 12.6.3 (21G419)`的`BaseSystem.dmg`和`BaseSystem.chunklist`放到u盘根目录中的`com.apple.recovery.boot`路径下，引导程序找不到镜像
- 使用`Etcher`烧录`Monterey 12.6.3 (21G419)`镜像到u盘，在`config.plist`中将机型设置为`iMac17,1`；用`DiskGenius`将efi拷贝到u盘efi分区；尝试安装`Monterey`，跑码一会后失败，进入Windows
- 使用Etcher烧录`Big Sur 11.7.3 (20G1116)`镜像到u盘，没有efi分区:D

#### 2023-03-22

- 从`sysin.org`下载`Big Sur 11.7.3 (20G1116)`镜像并使用Etcher烧录到u盘，用DiskGenius拷贝efi到efi文件夹下，成功安装![About this Mac](./resources/e3rx570.png)

#### 2023-07-27~2023-07-30

- 从`sysin.org`下载的`Big Sur 11.7.8 (20G1351)`iso镜像不能通过Etcher烧录到u盘，通过Mac系统App Store下载镜像并使用`sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`命令制作了`Big Sur 11.7.9 (20G1426)`的安装u盘
- 安装`Big Sur 11.7.9 (20G1426)`
- 使用`EasyUEFI`设置从硬盘双系统启动，教程参见[bilibili wxlei_雷 的视频](https://www.bilibili.com/video/BV1QV4y1K7WC)

#### 2024-07-26~2024-07-28

- 重复USB Mapping，获取`DSDT`和`SSDT`，配置EFI的过程，选择SMBIOS`iMacPro1,1`
- 通过Mac系统App Store下载`Ventura 13.6.7 (22G720)` iso 镜像，烧录u盘并安装

#### 2025-05-20~2025-05-23

- 通过Mac系统App Store下载`Monterey 12.7.4 (21h1123)`  iso镜像，烧录u盘并安装
- 更换显卡为AsRock RX6600XT
- 更换SMBIOS为`Macmini7,1`，该机型可以在`Monterey`驱动Haswell核显，且可以安装更新的OS
- 根据OpenCore Official Guide设置`config.plist`开机后黑屏，设置`Misc > Debug`中 `AppleDebug=False`, `ApplePanic=False`, `Target=0`可以解决，参照[这篇文章](https://www.sleepycow.cc/amd-navi-gpu-random-black-screen-dp.html#anchor-7)
- 安装`Monterey 12.7.4 (21H1123)`
- OTA更新至`Monterey 12.7.6 (21H1320)`
- 使用`EasyUEFI`设置从硬盘双系统启动，教程参见[bilibili wxlei_雷 的视频](https://www.bilibili.com/video/BV1QV4y1K7WC)

#### 2025-05-24

- 打开BIOS中的`IGD Multi Monitor`以启动核显，仿冒的P4600核显可以被识别但不能VDA解码

- 更换SMBIOS为`iMac17,1`，该机型不是Haswell原生支持的SMBIOS，但原生包含核显和独显，但仿冒的P4600核显可以被识别但不能VDA解码

#### 2025-05-25~2025-05-26

- 更换SMBIOS为`iMacPro1,1`并安装`Ventura 13.7.6 (22H625)`，计划未来更换SMBIOS为`iMac15,1`并安装`Big Sur`
- 重新定制USB映射，添加`-btlfxnvramcheck`到`boot-args`，重置nvram以解决蓝牙不能驱动的问题，其中一种方法解决了问题

## 参考资料

- [OpenCore 官方指南](https://dortania.github.io/OpenCore-Install-Guide)
- 司波图的视频：[b站](https://www.bilibili.com/video/BV1hA411t7dr/)，[YouTube](https://www.youtube.com/watch?v=Lu6Kmz5aDhY)
- 大头蔡Cass的视频：[b站](https://space.bilibili.com/16323318/channel/collectiondetail?sid=296068)，[YouTube](https://www.youtube.com/playlist?list=PLdKp3l7lXf-Ud-WGhrWn9cyPXpgcygUhd)

---

## Tools

- [OpenCore](https://github.com/acidanthera/OpenCorePkg)
- [SSDTTime](https://github.com/corpnewt/SSDTTime)
- [USB mapping tools](https://github.com/USBToolBox/tool)
- [ProperTree](https://github.com/corpnewt/ProperTree)
- [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) - generates fake Mac serial number
- [balenaEtcher](https://www.balena.io/etcher) - moves MacOS image to USB stick
- [OpenCore Scanity Checker](https://opencore.slowgeek.com/) - checks your mental health status
- [OpenCore Auxilliary Tool](https://github.com/ic005k/OCAuxiliaryTools) - does ProperTree and GenSMBIOS things, with a better GUI
- [DiskGenius](https://www.diskgenius.cn/) - moves your finished files to the efi sector in the USB stick
- [sysin](https://sysin.org/) - provides MacOS images
- [IASL](https://acpica.org/) - decompiles `.aml` file

## Intel Xeon E3 1276v3

### Hardwares

| CPU         |    Intel Xeon E3 1276v3 (integrated graphics Intel P4400)    |
| ----------- | :----------------------------------------------------------: |
| Motherboard |       MSI B85I (Realtek 8111G Gigabit Lan controller)        |
| GPU         | <del>Sapphire RX470D (Sapphire RX570 bios)</del>AsRock RX6600XT ITX |
| RAM         |                   G-SKILL DDR3 8G 1866MHz                    |
| WLAN        |                     Broadcom BCM94360HMB                     |
| Drive       |                       Zhitai SC001 1T                        |

### Updates

#### 2023-03-20: Start to configure my EFI

- Download MacOS image using OpenCore
- Fetch `DSDT.aml` file using SSDTTime

#### 2023-03-21

- Download `kext` files from OpenCore guide
- Create USB mapping `UTBMap.kext` using USB mapping tool, and check if each USB controller has more than 15 lanes? using ProperTree
- Fetch `SSDT-EC.aml` and `SSDT-PLUG.aml` using SSDTTime
- Configure `config.plist`
- 

#### Tests

- Ethernet - ✅
- WLAN - wifi works, bt doesn't
  - WiFi - ✅
  - AirDrop - ❌
  - Handoff - ❌
- Audio - ✅
- Hibernate - ✅

### 

## Reference

- [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide)
- Videos by 司波图 on [bilibili](https://www.bilibili.com/video/BV1hA411t7dr/), and [Youtube](https://www.youtube.com/watch?v=Lu6Kmz5aDhY)
- Videos by 大头蔡Cass on [bilibili](https://space.bilibili.com/16323318/channel/collectiondetail?sid=296068), and [Youtube](https://www.youtube.com/playlist?list=PLdKp3l7lXf-Ud-WGhrWn9cyPXpgcygUhd)

