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

- Opencore: https://github.com/acidanthera/OpenCorePkg
- SSDTTime: https://github.com/corpnewt/SSDTTime
- IASL: 

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
- 通过SSDTTime获取本机的DSDT.asl

## 参考资料

- OpenCore 官方指南 https://dortania.github.io/OpenCore-Install-Guide
- 司波图的视频 https://www.bilibili.com/video/BV1hA411t7dr/, https://www.youtube.com/watch?v=Lu6Kmz5aDhY
- 大头蔡Cass的视频 https://space.bilibili.com/16323318/channel/collectiondetail?sid=296068, https://www.youtube.com/playlist?list=PLdKp3l7lXf-Ud-WGhrWn9cyPXpgcygUhd

---

## Tools

- Opencore: https://github.com/acidanthera/OpenCorePkg
- SSDTTime: https://github.com/corpnewt/SSDTTime
- IASL: 

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
- Fetch DSDT.asl file using SSDTTime

## Reference

- OpenCore guide https://dortania.github.io/OpenCore-Install-Guide
- Videos by 司波图 https://www.bilibili.com/video/BV1hA411t7dr/, https://www.youtube.com/watch?v=Lu6Kmz5aDhY
- Videos by 大头蔡Cass https://space.bilibili.com/16323318/channel/collectiondetail?sid=296068, https://www.youtube.com/playlist?list=PLdKp3l7lXf-Ud-WGhrWn9cyPXpgcygUhd

