---
title: spritedoc.com域名注册
tags: [domain]
categories: [Game]
---

本意是方便独立游戏开发，萌生了做一个素材生成网站的想法，但其实素材生成，对于独立游戏还是团队开发，都可以帮助快速验证想法，减轻负荷。

问了问 Claude Code 帮我选择注册商，推荐通过 Claudeflare 注册域名。现在网站的 URL 是：[https://www.spritedoc.com/](https://www.spritedoc.com/) 。

📊 成本对比总结（By Claude Code）

|   注册商   | 5年总成本 | 10年总成本 |    推荐    |
|------------|----------|-----------|------------|
| Cloudflare | $48.85   | $97.70    | ⭐⭐⭐⭐⭐ |
| Namecheap  | $68.31   | $136.62   | ⭐⭐⭐⭐   |
| GoDaddy    | $99.95   | $199.90   | ⭐⭐       |

之前网站托管在了 Vercel 上，目的是收集反馈，但是 Vercel 免费版仅支持非商业目的的网站部署，而 Cloudflare 支持所有用户部署商业目的的网站，于是将网站迁移到了 Cloudflare 平台上托管，迁移过程中遇到问题就多问问 claude code。

![Vercel 免费版仅支持非商业目的的网站部署](assets/img/2026-02-09-spritedoc.com域名注册/image5.png)
_Vercel 免费版仅支持非商业目的的网站部署_

![Cloudflare 免费计划也可以用于商业用途](assets/img/2026-02-09-spritedoc.com域名注册/image7.png)
_Cloudflare 免费计划也可以用于商业用途_


---

下面是在 Vercel 平台上托管个人网站时可能遇到的坑，和经验。

在 Vercel 上托管网站时，如果直接从文件导入环境变量，Application Preset 可能会清空，尤其注意，需要再次设置一下，保证其不为空，否则网站会 404。

![注意设置 Application Preset](assets/img/2026-02-09-spritedoc.com域名注册/image.png)
_注意设置 Application Preset_

域名需要配置 DNS，Vercel 可以自动帮你配置，如图。

![自动配置 DNS](assets/img/2026-02-09-spritedoc.com域名注册/image2.png)
_自动配置 DNS_