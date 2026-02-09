---
title: 添加github的ssh_key
tags: [github, ssh]
categories: [git]
---
在 Windows 上配置 GitHub SSH 密钥的完整步骤如下。

### ✅ 步骤 1：确认已安装 OpenSSH 客户端
Windows 10/11 通常自带 OpenSSH，但需确认是否启用：

**方法 ：PowerShell 检查（管理员身份运行）**

```bash
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH.Client*'
```

如未安装，运行：

```bash
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
```

### 🔑 步骤 2：生成 SSH 密钥（PowerShell 或 Git Bash）

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

- 提示 `Enter file...` 直接回车（使用默认路径 `C:\Users\<你的用户名>\.ssh\id_ed25519`）
- 提示 `passphrase` 可直接回车跳过（或设置密码增强安全）

### 🧩 步骤 3：启动 ssh-agent 并添加密钥
Windows 的 ssh-agent 是系统服务，需先启动：

```bash
# 启动 ssh-agent 服务（管理员权限运行一次即可）
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent

# 添加私钥到 agent
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

### 📋 步骤 4：复制公钥到剪贴板
```bash
# PowerShell（Windows 10/11）
Get-Content "$env:USERPROFILE\.ssh\id_ed25519.pub" | Set-Clipboard
```


### 🌐 步骤 5：添加公钥到 GitHub
1. 访问 [https://github.com/settings/keys](https://github.com/settings/keys)
2. 点击 **New SSH key**
3. Title 填写设备名（如 `My Windows PC`）
4. Key 粘贴刚才复制的公钥内容
5. 点击 **Add SSH key**


### ✅ 步骤 6：测试连接
```bash
ssh -T git@github.com
```
成功时会看到：
```
Hi <你的用户名>! You've successfully authenticated...
```


