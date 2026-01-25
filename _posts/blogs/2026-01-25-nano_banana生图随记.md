---
title：Nano_Banana生图随记
tags: [Game, Nano_Banana]
categories: [Game]
---

开始游戏的界面需要是连续的。手动“复制→拼接→处理拼接→剪切”耗时耗力。使用提示词引导 nano-banana，思路是让 AI 直接生成可以循环延续的背景，从源头解决问题。提示词如下。（含参考图）
```prompt
wide panoramic landscape, pixel art, village scene with multiple repeating elements, seamless repeating patterns, village in center, mountains and clouds repeating across width, warm colors
```
其中，“with multiple repeating elements”、“seamless repeating patterns”、“repeating across width” 都输入了了循环延续的语义。

![alt text](/images/2026-01-25-nano_banana生图随记/start-background.png) {: w="700" h="400" .shadow }
_参考图_

![alt text](/images/2026-01-25-nano_banana生图随记/start_background.png) {: w="700" h="400" .shadow }
_生成的图（经过后期 resize 和简单的手动填充）_