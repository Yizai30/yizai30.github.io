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

如果安装过程中遇到问题 `fatal: early EOF`，可能是仓库过大或负载过高，可以配置 git 解决：
```bash
git config --global http.postBuffer 524288000    # 500MB
git config --global http.maxRequestBuffer 100M
git config --global core.compression 0            # 临时禁用压缩减少负载
```
该问题在安装 Claude Code 的官方技能市场时遇到， `claude plugin marketplace add anthropics/skills` 。

我现在安装的 Claude Code 插件/辅助工具列表如下：
- openspec 规范化管理 AI 落地了哪些需求，直接在 changes 文件夹下有文件夹列表，每一个文件夹对应一个落地的需求，查阅很方便
- claude-mem 可视化项目列表、对话记录，方便地管理本地的所有项目
- anthropics/skills 官方的技能市场
- uipro-cli（或者使用 anthropics/skills 的官方技能 frontend-design） 让 AI 设计的网站少些 AI 味儿