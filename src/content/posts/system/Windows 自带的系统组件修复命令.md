---
title: "Windows 自带的系统组件修复命令"
published: 2026-09-19
description: "Windows 自带的系统组件修复命令。"
tags: ["Win11", "修复","系统组件"]
category: 系统运维
draft: false
---
`DISM /Online /Cleanup-Image /RestoreHealth` 是 **Windows 自带的系统组件修复命令**。

请用**管理员 PowerShell**运行：

```
DISM /Online /Cleanup-Image /RestoreHealth
```

它可能会在某个百分比停很久，例如 **20%、40%、60%**，不一定是卡死，先让它跑完。

简单理解就是：

> **检查 Windows 自己的“系统组件仓库”有没有损坏，如果发现损坏，就尝试从 Windows 的组件源恢复它。**

### 每一部分是什么意思

```
DISM /Online /Cleanup-Image /RestoreHealth
```

| 参数             | 含义                                 |
| ---------------- | ------------------------------------ |
| `DISM`           | Windows 的「部署映像服务和管理」工具 |
| `/Online`        | 检查**当前正在运行的 Windows**       |
| `/Cleanup-Image` | 对 Windows 系统映像/组件进行维护     |
| `/RestoreHealth` | 检查损坏并尝试修复                   |

这里的 **Image（映像）不是你的照片或硬盘镜像**，指的是 Windows 操作系统本身。

### 它会不会删除我的东西？

**正常情况下不会。**

它不会：

- ❌ 删除个人文件
- ❌ 删除软件
- ❌ 删除 Outlook 邮件
- ❌ 重装 Windows
- ❌ 修改你的用户账户

它主要处理 Windows 自己的系统组件。

`DISM /Online /Cleanup-Image /RestoreHealth` 的作用是修复 **Windows 系统组件存储（Component Store）**，不是扫描“已卸载应用”然后重新安装。

例如你之前卸载的：

- 某些微软商店应用
- Xbox
- Clipchamp
- OneDrive
- 其他 Windows AppX 应用

**不会因为运行 DISM 就自动恢复。**

### 需要区分两个东西

**DISM 修复的是：**

```
Windows 系统组件
系统文件
组件存储
系统运行库
```

**它不是：**

```
恢复已卸载的软件
恢复开始菜单应用
恢复 Microsoft Store 应用
恢复用户删除的 AppX
```

所以如果你比较在意自己已经精简/卸载掉的 Windows 应用，**可以放心运行 DISM**。

不过有一个细节：

> 如果你使用过非常激进的 Windows 精简工具，把 Windows 的某些系统组件本身删除了，DISM 可能会尝试恢复缺失的**系统组件**。