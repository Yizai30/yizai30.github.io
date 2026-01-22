---
title: LyraStarterGame学习
tags: [Unreal, LyraStarterGame]
categories: [Game]
mermaid: true
---

### 理解LyraExperienceManager架构
学习Experience管理器的工作原理和在Lyra中的作用。

**阅读 LyraExperienceManager.h 文件，了解类的基本结构和继承关系**
0. 类介绍
- experiences 管理员——主要负责处理多个PIE会话之间的仲裁

1. 类的基本结构
- 三个 public 成员函数：`LYRAGAME_API void OnPlayInEditorBegun();`、`static void NotifyOfPluginActivation(const FString PluginURL);`、`static bool RequestToDeactivatePlugin(const FString PluginURL);`
- 一个 private 成员属性：`TMap<FString, int32> GameFeaturePluginRequestCountMap;`，给定游戏功能插件的活动计数请求映射（用于在PIE期间实现先进后出激活管理）。

2. 类的继承关系
- public 继承自 UEngineSubsystem 类

**查看 LyraExperienceManager.cpp 文件，理解管理器的初始化流程**
