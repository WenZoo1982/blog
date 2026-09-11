---
title: "llama.cpp一键启动脚本"
published: 2026-09-11
description: "llama.cpp一键启动脚本。"
tags: ["脚本", "llama"]
category: 系统运维
draft: false
---

## llama.cpp一键启动脚本

#### 路径示例：

**llama.cpp所在路径：**

D:\AI\llama.cpp\build\bin\Release\llama-server.exe

**模型所在路径：**

D:\AI\models\Gemma 3 4B

D:\AI\models\Google_Gemma4-E2B

D:\AI\models\Qwen2.5-VL 7B

**脚本：**

````CMD
```bat
@echo off
chcp 65001 >nul
title llama.cpp 模型启动器
color 0B

:menu
cls

echo.
echo ============================================================
echo                    llama.cpp 模型启动器
echo ============================================================
echo.
echo   [1]  Gemma 3 4B
echo        文本对话
echo ------------------------------------------------------------
echo.
echo   [2]  Qwen2.5-VL 7B
echo        多模态 / 图片理解
echo ------------------------------------------------------------
echo.
echo   [3]  Gemma 4 E2B
echo        多模态 / 图片理解
echo ------------------------------------------------------------
echo.
echo   [0]  退出
echo.
echo ============================================================
echo.
set /p choice=  请输入数字 [0-4]：

if "%choice%"=="1" goto gemma
if "%choice%"=="2" goto qwen
if "%choice%"=="3" goto gemma4
if "%choice%"=="0" exit

echo.
echo   输入错误，请输入 0 - 3
timeout /t 2 /nobreak >nul
goto menu


:gemma
cls
echo.
echo ============================================================
echo                    Gemma 3 4B
echo ============================================================
echo.
echo   正在启动模型，请稍候...
echo.

start "llama.cpp - Gemma 3 4B" cmd /k ""D:\AI\llama.cpp\build\bin\Release\llama-server.exe" -m "D:\AI\models\Gemma 3 4B\google_gemma-3-4b-it-Q4_K_M.gguf" -ngl 999 -c 8192 --host 127.0.0.1 --port 8080"

goto browser


:qwen
cls
echo.
echo ============================================================
echo                  Qwen2.5-VL 7B
echo ============================================================
echo.
echo   类型：多模态 / 图片理解
echo.
echo   正在启动模型，请稍候...
echo.

start "llama.cpp - Qwen2.5-VL 7B" cmd /k ""D:\AI\llama.cpp\build\bin\Release\llama-server.exe" -m "D:\AI\models\Qwen2.5-VL 7B\Qwen2.5-VL-7B-Instruct-UD-IQ3_XXS.gguf" --mmproj "D:\AI\models\Qwen2.5-VL 7B\mmproj-BF16.gguf" -ngl 999 -c 4096 --host 127.0.0.1 --port 8080"

goto browser


:gemma4
cls
echo.
echo ============================================================
echo                    Gemma 4 E2B
echo ============================================================
echo.
echo   类型：多模态 / 图片理解
echo.
echo   主模型：Gemma 4 E2B Q4_K_M
echo   MMProj ：mmproj-BF16.gguf
echo.
echo   正在启动模型，请稍候...
echo.

start "llama.cpp - Gemma 4 E2B" cmd /k ""D:\AI\llama.cpp\build\bin\Release\llama-server.exe" -m "D:\AI\models\Google_Gemma4-E2B\gemma-4-E2B-it-Q4_K_M.gguf" --mmproj "D:\AI\models\Google_Gemma4-E2B\mmproj-BF16.gguf" -ngl 999 -c 8192 --host 127.0.0.1 --port 8080"

goto browser


:browser
echo.
echo   等待模型启动...
echo.

timeout /t 15 /nobreak >nul

echo   正在打开浏览器...
start "" "http://127.0.0.1:8080"

exit
```

````

根据自己文件所在目录自行修改即可。