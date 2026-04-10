---
title: Nano-Banana-Pro-完整指南：专业资产制作的10个技巧
tags: [Art]
categories: [Art]
---

原文链接：https://x.com/GoogleAIStudio/status/1994480371061469306?s=20

Nano Banana Pro 是相较于上一代模型的一大飞跃，从“有趣”的图像生成转变为“功能性”的专业资产生产。它在文本渲染、角色一致性、视觉合成、世界知识（搜索）以及高分辨率（4K）输出方面表现出色。本指南涵盖了核心功能和如何有效提示它们的方法。

> By Guillaume Vernade, Gemini Developer Advocate, Google DeepMind

# 本文将介绍以下内容

0. 提示词的黄金法则
1. 文本呈现、信息图表与视觉整合
2. 角色一致性及热门缩略图
3. 利用谷歌搜索进行事实生成
4. 高级编辑、修复与色彩化
5. 维度转换（2D ↔ 3D）
6. 高分辨率与纹理
7. 思考与推理
8. 单幅分镜与概念艺术
9. 结构控制与布局指导

## 0. 提示词的黄金法则

Nano-Banana Pro 是一款“思考”型模型。它不仅仅匹配关键词；它还能理解意图、物理和组成。为了获得最佳结果，不再“做汤时只添加调料”（例如，狗、公园、4k、逼真），还可以添加怎么做汤、做什么汤等更多，向模型传递思考环境。

### 0.0 继续编辑而不是重做

模型在理解对话式编辑方面非常出色。如果一个图像有80%的正确率，不要从头开始生成新的图像。相反，只需提示你需要的具体更改即可。

> Example: "That's great, but change the lighting to sunset and make the text neon blue."【翻译】示例：“那很好，但将光线改为日落，并将文字改为霓虹蓝色。”

### 0.1 使用自然语言和完整句子

像向人类艺术家介绍信息一样与模型交流。使用正确的语法和描述性形容词。

> ❌不好："Cool car, neon, city, night, 8k."【翻译】“酷炫的汽车，霓虹，城市，夜晚，8k”
{: .prompt-tip }

> ✔️好："A cinematic wide shot of a futuristic sports car speeding through a rainy Tokyo street at night. The neon signs reflect off the wet pavement and the car's metallic chassis."【翻译】“一个电影般的广角镜头，展现一辆未来感十足的跑车在雨夜的东京街道上疾驰。霓虹灯的灯光在湿漉漉的路面和汽车的金属车身上闪烁。”
{: .prompt-tip }

### 0.2 具体且生动

模糊的提示只会产生千篇一律的结果。请明确**主题、场景、光线和氛围**。

> Subject: Instead of "a woman," say "a sophisticated elderly woman wearing a vintage chanel-style suit."【翻译】主题：与其说“一位女性”，不如说“一位穿着复古香奈儿风格套装的优雅老妇人”。
{: .prompt-tip }

> Materiality: Describe textures. "Matte finish," "brushed steel," "soft velvet," "crumpled paper."【翻译】材质：描述质感。“哑光质感”、“拉丝钢”、“柔软天鹅绒”、“皱纸”。
{: .prompt-tip }

### 0.3 提供上下文（“为什么”或“为谁”）

由于该模型能够“思考”，提供上下文信息有助于它做出合乎逻辑的艺术决策。

> Example: "Create an image of a sandwich for a Brazilian high-end gourmet cookbook." (The model will infer professional plating, shallow depth of field, and perfect lighting).【翻译】示例：“为一本巴西高端美食烹饪书创作一张三明治图片。”（模型将推断出专业的摆盘、浅景深以及完美的灯光效果）。
{: .prompt-tip }

## 1. 文本呈现、信息图表与视觉整合

Nano-Banana Pro 具备业界领先的能力，能够呈现清晰易读且风格化的文本，并将复杂信息转化为可视化形式。

**最佳实践：**

- 压缩：请模型将冗长的文本或PDF文件“压缩”成可视化辅助材料。
- 风格：具体指定您希望采用“精致的编辑风格”、“技术图表”还是“手绘白板”的风格。
- 引号：用引号括起您想要明确具体指定的文本，引号起着重作用。

**示例提示词：**

> Earnings Report Infographic (Data Ingestion):
[Input PDF of Google's latest earnings report]
"Generate a clean, modern infographic summarizing the key financial highlights from this earnings report. Include charts for 'Revenue Growth' and 'Net Income', and highlight the CEO's key quote in a stylized pull-quote box."【翻译】财报信息图（数据导入）：[输入谷歌最新财报的 PDF 文件]“生成一张简洁、现代的信息图，概括本财报中的主要财务亮点。包含‘营收增长’和‘净利润’的图表，并在设计精美的引语框中突出显示 CEO 的关键发言。”

![财报信息图](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image.png)
_财报信息图_

> Retro Infographic:
"Make a retro, 1950s-style infographic about the history of the American diner. Include distinct sections for 'The Food,' 'The Jukebox,' and 'The Decor.' Ensure all text is legible and stylized to match the period."【翻译】复古信息图：“制作一张复古风格的1950年代风格信息图，介绍美国餐馆的历史。请分别设置‘美食’、‘点唱机’和‘装饰’独立板块。确保所有文字清晰易读，并采用符合该时期风格的排版。”

![复古信息图](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image2.png)
_复古信息图_

> Technical Diagram:
"Create an orthographic blueprint that describes this building in plan, elevation, and section. Label the 'North Elevation' and 'Main Entrance' clearly in technical architectural font. Format 16:9."【翻译】技术图示：“绘制一份正投影蓝图，展示该建筑的平面图、立面图和剖面图。请使用建筑技术字体清晰标注‘北立面’和‘主入口’。画面比例为16:9。”

![技术图示](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image3.png)
_技术图示_

> Whiteboard Summary (Educational):
"Summarize the concept of 'Transformer Neural Network Architecture' as a hand-drawn whiteboard diagram suitable for a university lecture. Use different colored markers for the Encoder and Decoder blocks, and include legible labels for 'Self-Attention' and 'Feed Forward'."【翻译】白板总结（教育类）：“请将‘Transformer神经网络架构’的概念总结为一幅手绘白板图，适合用于大学课堂讲授。请使用不同颜色的记号笔分别标注编码器和解码器模块，并为‘自我注意力’和‘前馈’添加清晰易读的标签。”

![白板总结](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image4.png)
_白板总结_

## 2. 角色一致性及热门缩略图

Nano-Banana Pro 最多支持 14 张参考图像（其中 6 张为高保真图像）。这使得“身份锁定”功能成为可能——即将特定人物或角色置入新场景中，同时确保面部不发生变形。

**最佳实践：**
- 身份锁定：明确说明：“确保该人物的面部特征与图片1完全一致。”
- 表情/动作：在保持角色身份不变的前提下，描述情绪或姿势的变化。
- 热门内容创作：将**主题**与醒目的**图形**和**文字**一气呵成地**融合**在一起。

**示例提示词：**
> The "Viral Thumbnail" (Identity + Text + Graphics):
"Design a viral video thumbnail using the person from Image 1. Face Consistency: Keep the person's facial features exactly the same as Image 1, but change their expression to look excited and surprised. Action: Pose the person on the left side, pointing their finger towards the right side of the frame. Subject: On the right side, place a high-quality image of a delicious avocado toast. Graphics: Add a bold yellow arrow connecting the person's finger to the toast. Text: Overlay massive, pop-style text in the middle: '3分钟搞定!' (Done in 3 mins!). Use a thick white outline and drop shadow. Background: A blurred, bright kitchen background. High saturation and contrast."【翻译】“热门缩略图”（人物形象 + 文字 + 图形）：“使用图片1中的人物设计一个热门视频缩略图。面部一致性：保持人物面部特征与图片1完全一致，但将表情改为兴奋且惊讶的样子。动作：让人物站在画面左侧，手指指向画面右侧。 主体：画面右侧放置一张美味牛油果吐司的高清图片。图形：添加一条醒目的黄色箭头，连接人物的手指与吐司。文字：在画面中央叠加超大号、波普风格的文字：“3分钟搞定！”，采用粗白边框并添加阴影效果。背景：模糊的明亮厨房背景，高饱和度与高对比度。

![热门缩略图](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image5.png)
_热门缩略图_

> The "Fluffy Friends" Scenario (Group Consistency):
[Input 3 images of different plush creatures]
"Create a funny 10-part story with these 3 fluffy friends going on a tropical vacation. The story is thrilling throughout with emotional highs and lows and ends in a happy moment. Keep the attire and identity consistent for all 3 characters, but their expressions and angles should vary throughout all 10 images. Make sure to only have one of each character in each image."【翻译】“毛茸茸的朋友”场景（组内一致性）：[输入3张不同毛绒动物的图片]“用这3个毛茸茸的朋友去热带度假的故事，创作一个有趣的10幅连环画。整个故事充满惊险刺激，情感起伏跌宕，最终以一个幸福的时刻收尾。请确保这3个角色的服装和身份保持一致，但表情和拍摄角度应在全部10张图片中有所变化。请务必确保每张图片中只出现其中一个角色。”

![“毛茸茸的朋友”场景](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image6.png)
_“毛茸茸的朋友”场景_

> Brand Asset Generation:
[Input 1 image of a product]
"Create 9 stunning fashion shots as if they’re from an award-winning fashion editorial. Use this reference as the brand style but add nuance and variety to the range so they convey a professional design touch. Please generate nine images, one at a time."【翻译】品牌资产生成：[输入1张产品图片]“生成9张令人惊艳的时尚大片，风格需仿若出自获奖时尚专题报道。以此参考图为品牌风格基准，但需在系列中加入细微差别和多样性，以展现专业设计感。请分批生成9张图片，每次生成1张。”

![品牌资产生成](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image7.png)
_品牌资产生成_


## 3. 利用谷歌搜索进行事实生成

Nano-Banana Pro 利用 Google 搜索，基于实时数据、时事或事实核查生成图像，从而减少针对时下热门话题的幻觉生成。

**最佳实践：**
- 请求生成动态数据（天气、股票、新闻）的可视化图表。
- 该模型会在生成图像之前对搜索结果进行“思考”（推理）。

**示例提示词：**

> Event Visualization:
"Generate an infographic of the best times to visit the U.S. National Parks in 2025 based on current travel trends."【翻译】事件可视化：“根据当前的旅游趋势，生成一张关于2025年游览美国国家公园最佳时机的信息图。”

![事件可视化](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image8.png)
_事件可视化_

## 4. 高级编辑、修复与色彩化

该模型擅长通过对话式提示进行复杂的图像编辑。这包括“填补”（移除/添加物体）、“修复”（修复老照片）、“上色”（漫画/黑白照片）以及“风格转换”。

**最佳实践：**

- 语义说明：无需手动进行掩码处理；只需自然地告诉模型需要修改哪些内容即可。
- 物理引擎理解：你可以提出诸如“将液体倒满这只玻璃杯”之类的复杂指令，以此测试物理引擎的生成能力。

**示例提示词：**

> Object Removal & In-painting:
"Remove the tourists from the background of this photo and fill the space with logical textures (cobblestones and storefronts) that match the surrounding environment."【翻译】“物体移除与填补”： “将这张照片背景中的游客移除，并用与周围环境相符的合理纹理（鹅卵石路面和店面）填补该区域。”

![物体移除与填补](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image9.png)
_物体移除与填补_

> Manga/Comic Colorization:
[Input black and white manga panel]
"Colorize this manga panel. Use a vibrant anime style palette. Ensure the lighting effects on the energy beams are glowing neon blue and the character's outfit is consistent with their official colors."【翻译】漫画上色：[输入黑白漫画分镜]“请为这幅漫画分镜上色。采用鲜艳的动漫风格配色方案。确保能量光束的光效呈现发光的霓虹蓝，且角色的服装颜色与官方配色保持一致。”

![漫画上色](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image10.png)
_漫画上色_

> Localization (Text Translation + Cultural Adaptation):
[Input image of a London bus stop ad]
"Take this concept and localize it to a Tokyo setting, including translating the tagline into Japanese. Change the background to a bustling Shibuya street at night."【翻译】本地化（文本翻译 + 文化适配）：[伦敦公交车站广告图片]“请将这个创意本地化为东京场景，包括将广告标语翻译成日语。将背景改为夜晚熙熙攘攘的涩谷街道。”

![文本翻译+文化适配](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image11.png)
_文本翻译+文化适配_

Lighting/Seasonal Control:
[Input image of a house in summer]
"Turn this scene into winter time. Keep the house architecture exactly the same, but add snow to the roof and yard, and change the lighting to a cold, overcast afternoon."【翻译】光照/季节控制：[夏季房屋图片]“将这个场景转换为冬季。房屋建筑结构保持完全不变，但在屋顶和院子里添加积雪，并将光照效果调整为阴冷的多云午后。”

![光照/季节控制](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image12.png)
_光照/季节控制_

## 5. 维度转换（2D ↔ 3D）

一项强大的新功能能够将2D示意图转换为3D可视化效果，反之亦然。这对于室内设计师、建筑师和表情包创作者来说再合适不过了。

**示例提示词：**

> 2D Floor Plan to 3D Interior Design Board:
"Based on the uploaded 2D floor plan, generate a professional interior design presentation board in a single image. Layout: A collage with one large main image at the top (wide-angle perspective of the living area), and three smaller images below (Master Bedroom, Home Office, and a 3D top-down floor plan). Style: Apply a Modern Minimalist style with warm oak wood flooring and off-white walls across ALL images. Quality: Photorealistic rendering, soft natural lighting."【翻译】2D平面图转3D室内设计展示板：“根据上传的2D平面图，生成一张专业室内设计展示图。布局：采用拼贴形式，顶部为一张大主图（客厅的广角透视图），下方为三张小图（主卧室、家庭办公室以及3D俯视平面图）。 风格：采用现代极简风格，所有图片均使用暖色橡木地板和米白色墙面。质量：照片级真实感渲染，柔和自然光线。”

![2D平面图转3D室内设计展示板](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image13.png)
_2D平面图转3D室内设计展示板_

> 2D to 3D Meme Conversion:
"Turn the 'This is Fine' dog meme into a photorealistic 3D render. Keep the composition identical but make the dog look like a plush toy and the fire look like realistic flames."【翻译】2D 转 3D 表情包制作：“将‘This is Fine’狗狗表情包转化为逼真的 3D 渲染图。保持画面构图不变，但让狗狗看起来像毛绒玩具，火焰则呈现出真实的火焰效果。”

![2D转3D表情包制作](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image14.png)
_2D转3D表情包制作_

## 6. 高分辨率与纹理

Nano-Banana Pro 支持原生生成 1K 至 4K 分辨率的图像。这对于精细纹理或大幅面打印尤为有用。

**最佳实践：**
- 如果您的 API/接口支持，请明确要求使用高分辨率（2K 或 4K）。
- 描述高保真细节（瑕疵、表面纹理）。

**示例提示词：**
> 4K Texture Generation:
"Harness native high-fidelity output to craft a breathtaking, atmospheric environment of a mossy forest floor. Command complex lighting effects and delicate textures, ensuring every strand of moss and beam of light is rendered in pixel-perfect resolution suitable for a 4K wallpaper."【翻译】4K 纹理生成：“利用原生高保真输出技术，打造令人叹为观止、充满氛围感的苔藓森林地面环境。精准掌控复杂的光照效果与细腻的纹理，确保每一缕苔藓和每一束光线都能以像素级完美分辨率呈现，堪称 4K 壁纸的绝佳素材。”

![4K纹理生成](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image15.png)
_4K纹理生成_

> Complex Logic (Thinking Mode):
"Create a hyper-realistic infographic of a gourmet cheeseburger, deconstructed to show the texture of the toasted brioche bun, the seared crust of the patty, and the glistening melt of the cheese. Label each layer with its flavor profile."【翻译】复杂逻辑（思考模式）：“制作一张超写实的美食信息图，展示一份精致芝士汉堡的剖面图，呈现烤过的布里欧修面包的质地、肉饼的焦脆外皮以及芝士融化后闪闪发光的状态。为每一层标注其风味特征。”

![复杂逻辑（思考模式）](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image16.png)
_复杂逻辑（思考模式）_

## 7. 思考与推理

Nano-Banana Pro 默认采用“思考”模式，在此模式下，它会生成中间思考图像（不额外付费）来优化构图，然后才渲染最终输出。这有助于进行数据分析并解决视觉问题。

**示例提示词：**

> Solve Equations:
"Solve log_{x^2+1}(x^4-1)=2 in C on a white board. Show the steps clearly."【翻译】解方程：“在复数集合C中，于白板上解方程 log_{x^2+1}(x^4-1)=2。请清晰地展示解题步骤。”

![解方程](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image17.png)
_解方程_

> Visual Reasoning:
"Analyze this image of a room and generate a 'before' image that shows what the room might have looked like during construction, showing the framing and unfinished drywall."【翻译】视觉推理：“分析这张房间的照片，并生成一张‘施工前’的图片，展示房间在施工期间可能的样子，包括木框架和未完工的石膏板。”

![视觉推理](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image18.png)
_视觉推理_

## 8. 单幅分镜与概念艺术

您可以无需网格即可绘制连环画或分镜图，从而确保在单次创作中保持连贯的叙事节奏。这种做法在“电影概念艺术”（例如即将上映电影的假泄露图）中也很受欢迎。

**示例提示：**

> "Create an addictively intriguing 9-part story with 9 images featuring a woman and man in an award-winning luxury luggage commercial. The story should have emotional highs and lows, ending on an elegant shot of the woman with the logo. The identity of the woman and man and their attire must stay consistent throughout but they can and should be seen from different angles and distances. Please generate images one at a time. Make sure every image is in a 16:9 landscape format."【翻译】"请创作一个引人入胜、令人欲罢不能的9集故事，通过9张图片展现一对男女在获奖的奢侈品行李箱广告中的故事。故事应包含情感的高潮与低谷，并以一位女性手持品牌标识的优雅画面作为结尾。男女主角的身份及其着装在整个故事中必须保持一致，但应从不同的角度和距离进行呈现。请逐张生成图片，并确保每张图片均为16:9的横向格式。

![行李箱广告的9集故事](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image19.png)
_行李箱广告的9集故事_

## 9. 结构控制与布局指导

输入图像不仅限于字符参考或待编辑的对象。您还可以利用它们来精确控制最终输出的构图和布局。对于需要将餐巾纸草图、线框图或特定的网格布局转化为精美素材的设计师而言，这无疑是一项革命性的突破。

**最佳实践：**
- 草图与设计稿：上传手绘草图，以精确确定文本和对象的摆放位置。
- 线框图：利用现有布局或线框图的截图来生成高保真界面原型。
- 网格：使用网格图像，强制模型为基于瓦片的游戏或 LED 显示屏生成资源。

**示例提示词：**

> Sketch to Final Ad:
"Create a ad for a [product] following this sketch."【翻译】草图到最终广告：“根据此草图为[产品]制作一则广告。”

![草图到最终广告](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image20.png)
_草图到最终广告_

> UI Mockup from Wireframe:
"Create a mock-up for a [product] following these guidelines."【翻译】基于线框图的界面原型：“请按照以下指南为[产品]制作一个原型。”

![基于线框图的界面原型](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image21.png)
_基于线框图的界面原型_

> Pixel Art & LED Displays:
"Generate a pixel art sprite of a unicorn that fits perfectly into this 64x64 grid image. Use high contrast colors."
(Tip: Developers can then programmatically extract the center color of each cell to drive a connected 64x64 LED matrix display).【翻译】像素艺术与LED显示屏：“生成一张独角兽的像素艺术贴图，使其完美适配这张64x64的网格图像。请使用高对比度的颜色。”（提示：开发者随后可以通过编程提取每个像素格的中心颜色，以驱动连接的64x64 LED矩阵显示屏。）

![像素艺术与LED显示屏](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image22.png)
_像素艺术与LED显示屏_

> Sprites:
"Sprite sheet of a woman doing a backflip on a drone, 3x3 grid, sequence, frame by frame animation, square aspect ratio. Follow the structure of the attached reference image exactly.."
(Tip: You can then extract each cell and make a gif)【翻译】Sprites：“一名女子在无人机上后空翻的贴图集，3x3 网格，序列，逐帧动画，正方形宽高比。请完全遵循附件参考图片的结构。”（提示：之后你可以提取每个单元格并制作成 GIF 动图）

![Sprites](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image23.png)
_Sprites_

![Sprites-GIF](assets/img/2026-04-19-Nano-Banana-Pro-完整指南：专业资产制作的10个技巧/image24.gif)
_Sprites-GIF_

