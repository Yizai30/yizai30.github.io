---
title: spritedoc.com域名注册
tags: [domain]
categories: [Game]
---

本意是方便独立游戏开发，萌生了做一个素材生成网站的想法，但其实素材生成，对于独立游戏还是团队开发，都可以帮助快速验证想法，减轻负荷。

问了问 Claude Code 帮我选择注册商，推荐 Claudeflare。

📊 成本对比总结（By Claude Code）
│   注册商   │ 5年总成本 │ 10年总成本 │    推荐    │
|------------|----------|-----------|------------|
│ Cloudflare │ $48.85    │ $97.70     │ ⭐⭐⭐⭐⭐ │
│ Namecheap  │ $68.31    │ $136.62    │ ⭐⭐⭐⭐   │
│ GoDaddy    │ $99.95    │ $199.90    │ ⭐⭐       │

现在网站托管在了 Vercel 上，不知道会不会收集到什么反馈。

在 vercel 上托管网站时，如果直接从文件导入环境变量，Application Preset 可能会清空，尤其注意，需要再次设置一下，保证其不为空，否则网站可能 404。

![注意设置 Application Preset](assets/img/2026-02-09-spritedoc.com域名注册/image.png)
_注意设置 Application Preset_

域名需要配置 DNS，Vercel 可以自动帮你配置，如图。

![自动配置 DNS](assets/img/2026-02-09-spritedoc.com域名注册/image2.png)
_自动配置 DNS_

网站 URL：https://www.spritedoc.com/ 。