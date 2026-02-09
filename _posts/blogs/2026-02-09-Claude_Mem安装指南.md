---
title: Claude-Mem 安装指南
tags: [claude code, claude mem]
categories: [vibe coding]
---

> Claude-Mem 在 Windows 操作系统安装出现路径错误，`C:\Users\Username\.claude\...` 被识别成 `C:\Users\Username.claude\...`。
{: .prompt-info }

解决方法是使用 claude 命令安装，而不是在 claude session 中安装。即，例如，原命令 `/plugin marketplace add thedotmack/claude-mem`，现使用 `claude plugin marketplace add thedotmack/claude-mem`。

```bash
HP@DESKTOP-THRS41I MINGW64 ~
$ claude plugin marketplace add thedotmack/claude-mem
Adding marketplace...
SSH not configured, cloning via HTTPS: https://github.com/thedotmack/claude-mem.git
Cloning repository: https://github.com/thedotmack/claude-mem.git
Clone complete, validating marketplace…
✔ Successfully added marketplace: thedotmack

HP@DESKTOP-THRS41I MINGW64 ~
$ claude plugin marketplace list
Configured marketplaces:

  ❯ claude-plugins-official
    Source: GitHub (anthropics/claude-plugins-official)

  ❯ thedotmack
    Source: GitHub (thedotmack/claude-mem)


HP@DESKTOP-THRS41I MINGW64 ~
$ claude plugin install claude-mem
Installing plugin "claude-mem"...
✔ Successfully installed plugin: claude-mem@thedotmack (scope: user)

HP@DESKTOP-THRS41I MINGW64 ~
$
```