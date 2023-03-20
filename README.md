# Hackintosh

## 目录

- [中文版](#工具)
  - 工具
  - 镜像1：E3v3 + RX570显卡ITX主机
    - 概述+硬件介绍
    - 更新记录
  - 参考
- [English](#Tools)
  - Tools
  - EFI1: E3v3 + RX570 itx build
  - References

---

## 工具

- [OpenCore](https://github.com/acidanthera/OpenCorePkg)
- [SSDTTime](https://github.com/corpnewt/SSDTTime)
- [USB mapping tools](https://github.com/USBToolBox/tool)
- [IASL] 

## E3v3的EFI

### 硬件配置介绍

| CPU      |          Xeon E3 1276v3 (核显Intel P4600)           |
| -------- | :-------------------------------------------------: |
| 主板     | 微星B85I (网卡型号瑞昱8111G Gigabit Lan controller) |
| 显卡     |          蓝宝石RX470D (刷蓝宝石570的bios)           |
| 内存     |                芝奇 DDR3 8G 1866MHz                 |
| 无线网卡 |                  博通 BCM94360HMB                   |
| 硬盘     |                    致钛 SC001 1T                    |

### 更新记录

#### 2023-03-20: 开始根据教程进行EFI配置

- 通过OpenCore下载适合的MacOS镜像
- 通过SSDTTime获取本机的`DSDT.asl`

#### 2023-03-21

- 从OpenCore指南里下载适配硬件的`kext`

## 参考资料

- [OpenCore 官方指南](https://dortania.github.io/OpenCore-Install-Guide)
- 司波图的视频：[b站](https://www.bilibili.com/video/BV1hA411t7dr/)，[YouTube](https://www.youtube.com/watch?v=Lu6Kmz5aDhY)
- 大头蔡Cass的视频：[b站](https://space.bilibili.com/16323318/channel/collectiondetail?sid=296068)，[YouTube](https://www.youtube.com/playlist?list=PLdKp3l7lXf-Ud-WGhrWn9cyPXpgcygUhd)

---

## Tools

- [OpenCore](https://github.com/acidanthera/OpenCorePkg)
- [SSDTTime](https://github.com/corpnewt/SSDTTime)
- [USB mapping tools](https://github.com/USBToolBox/tool)
- [IASL] 

## Intel Xeon E3 1276v3

### Hardwares

| CPU         | Intel Xeon E3 1276v3 (integrated graphics Intel P4600) |
| ----------- | :----------------------------------------------------: |
| Motherboard |    MSI B85I (Realtek 8111G Gigabit Lan controller)     |
| GPU         |         Sapphire RX470D (Sapphire RX570 bios)          |
| RAM         |                G-SKILL DDR3 8G 1866MHz                 |
| WLAN        |                  Broadcom BCM94360HMB                  |
| Drive       |                    Zhitai SC001 1T                     |

### Updates

#### 2023-03-20: Start to configure my EFI

- Download MacOS image using OpenCore
- Fetch `DSDT.asl` file using SSDTTime

#### 2023-03-21

- Download `kext` files from OpenCore guide

## Reference

- [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide)
- Videos by 司波图 on [bilibili](https://www.bilibili.com/video/BV1hA411t7dr/), and [Youtube](https://www.youtube.com/watch?v=Lu6Kmz5aDhY)
- Videos by 大头蔡Cass on [bilibili](https://space.bilibili.com/16323318/channel/collectiondetail?sid=296068), and [Youtube](https://www.youtube.com/playlist?list=PLdKp3l7lXf-Ud-WGhrWn9cyPXpgcygUhd)

