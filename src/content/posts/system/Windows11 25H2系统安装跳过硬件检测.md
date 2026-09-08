---
title: "Windows11 25H2系统安装跳过硬件检测"
published: 2026-09-08
description: "Windows11 25H2系统安装跳过硬件检测。"
tags: ["Win11", "跳过检测","系统安装"]
image: "./cover.png"
category: 系统运维
draft: false
---
## 1、下载Windows11系统镜像

下载地址：https://www.microsoft.com/zh-hk/software-download/windows11

![](./win11_01.png)

点击下载后会弹出下面这个选项。

![](./win11_02.png)

选择语言，确定。

![](./win11_03.png)

## 2、解压ISO镜像文件

将下载的Win11_25H2_Pro_Chinese_Simplified_x64.iso文件解压缩到文件夹。（注：不是加载或直接双击打开）

![](./win11_04.png)

将这段命令输入并回车。

```
setupprep.exe /product server
```

![](./win11_05.png)