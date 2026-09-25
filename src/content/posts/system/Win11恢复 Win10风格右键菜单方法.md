---
title: "Win11恢复Win10风格右键菜单方法"
published: 2026-09-25
description: "Win11恢复Win10风格右键菜单方法。"
tags: ["Win11", "修复","系统组件"]
category: 系统运维
draft: false
---
# Win11恢复Win10风格右键菜单方法

## 恢复 Win10 风格右键菜单

以管理员打开 **终端 / CMD**，执行：

```
reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
```

然后重启 Windows 资源管理器：

```
taskkill /f /im explorer.exe
start explorer.exe
```

之后右键菜单就会变成类似 Win10 的**完整经典菜单**。

------

## 恢复 Win11 原来的右键菜单

执行：

```
reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f
```

然后：

```
taskkill /f /im explorer.exe
start explorer.exe
```

恢复后就是 Win11 默认的右键菜单。