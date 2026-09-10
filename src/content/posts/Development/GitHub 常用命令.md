---
title: "GitHub 常用命令"
published: 2026-09-08
description: "GitHub 常用命令。"
tags: ["GitHub","Git"]
image: "./cover.webp"
category: 开发技术
draft: false
---
## 确认 GitHub 身份信息

```
git config --global user.name
git config --global user.email
```

## 设置登录身份

```
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub邮箱"
```

## 查看远程仓库

执行：

```
git remote -v
```

正常应该看到：

```
origin  https://github.com/你的GitHub用户名/xxxx.git (fetch)
origin  https://github.com/你的GitHub用户名/xxxx.git (push)
```

## 测试 GitHub 登录状态

执行：

```
git pull
```

如果没有登录，通常会出现：

- 弹浏览器登录 GitHub
- 或提示：

```
Authentication failed
```

第一次登录成功后，Git Credential Manager 会保存。

## 上传到GitHub

## 1. `git add .`

意思：

> 把当前目录下所有修改过的文件加入 Git 的“准备提交列表”。

这里：

```
git add
```

表示：

添加文件。

后面的：

```
.
```

表示：

当前目录。

所以：

```
git add .
```

就是：

> 把当前项目里所有新增、修改、删除的文件全部放进下一次提交。

例如你修改了：

```
D:\fuwari

src/
 └── config.ts       修改
 └── content/
     └── posts/
         └── welcome/
             └── index.md   修改
```

执行：

```
git add .
```

Git 会记录：

```
准备提交：

M src/config.ts
M src/content/posts/welcome/index.md
```

------

注意：

`git add .` **不会上传 GitHub。**

它只是告诉 Git：

> “这些改动我准备保存。”

------

## 2. `git commit -m "update blog"`

意思：

> 给刚才准备好的修改创建一个版本记录。

拆开：

### commit

就是：

提交。

类似：

Word 文档：

```
版本1
版本2
版本3
```

Git 的 commit 就是保存一个版本节点。

------

### `-m`

表示：

message（提交说明）

后面：

```
"update blog"
```

就是备注。

例如：

```
git commit -m "修改首页标题"
```

以后你查看历史：

```
commit abc123

修改首页标题

commit def456

添加关于页面

commit xxx789

修改文章模板
```

------

所以：

```
git commit -m "update blog"
```

意思：

> 创建一个新的版本，并备注“更新博客”。

------

## 3. `git push`

意思：

> 把本地 Git 里的提交上传到 GitHub。

比如：

你的电脑：

```
D:\fuwari

commit A
commit B
commit C
```

GitHub：

```
commit A
```

执行：

```
git push
```

之后：

```
GitHub：

commit A
commit B
commit C
```