---
title: LyraStarterGame学习
tags: [Unreal, LyraStarterGame]
categories: [Game]
mermaid: true
---

### 理解LyraExperienceManager架构

> Experience 是 Lyra 的核心架构，它定义了不同游戏模式的完整规则集（包括游戏模式、pawn、UI等）。理解 Experience 后，可以快速切换不同的游戏体验。
{: .prompt-info }

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

🏗️ 架构概览

Lyra 实际上有两个管理器：
1. ULyraExperienceManager (EngineSubsystem) - 编辑器环境下的简单管理器
2. ULyraExperienceManagerComponent (GameStateComponent) - 游戏运行时的核心管理器

🔄 完整的初始化流程

SetCurrentExperience()
    ↓
StartExperienceLoad()
    ↓
加载Experience和ActionSet资产
    ↓
OnExperienceLoadComplete()
    ↓
加载并激活GameFeature插件
    ↓
OnGameFeaturePluginLoadComplete()
    ↓
OnExperienceFullLoadCompleted()
    ↓
执行GameFeatureActions
    ↓
Loaded状态完成

📝 详细步骤解析

步骤1: 设置当前Experience (第56-68行)

void SetCurrentExperience(FPrimaryAssetId ExperienceId)

做什么：
- 通过 AssetManager 加载Experience定义
- 验证Experience不为空
- 检查当前没有已加载的Experience
- 设置 CurrentExperience 并开始加载

关键点：
- 每次只能有一个活跃的Experience
- 使用 PrimaryAssetId 作为标识符

---
步骤2: 开始加载Experience (第123-212行)

void StartExperienceLoad()

做什么：
1. 记录加载状态：ELyraExperienceLoadState::Loading
2. 收集需要加载的资产：
- Experience本身
- 所有ActionSets
3. 准备Bundles（资源包）：
- FLyraBundles::Equipped - 装备资源
- LoadStateClient - 客户端GameFeatures
- LoadStateServer - 服务器端GameFeatures
4. 判断网络模式（第154-164行）：
const ENetMode OwnerNetMode = GetOwner()->GetNetMode();
const bool bLoadClient = GIsEditor || (OwnerNetMode != NM_DedicatedServer);
const bool bLoadServer = GIsEditor || (OwnerNetMode != NM_Client);
5. 异步加载资产 (第166-176行)：
- 使用 FStreamableManager 进行异步加载
- Bundle资产（批量加载）
- Raw资产（列表加载）

关键点：
- 使用异步加载避免阻塞主线程
- 根据客户端/服务器角色加载不同的资源

---
步骤3: Experience资产加载完成 (第214-276行)

void OnExperienceLoadComplete()

做什么：
1. 记录日志：资产加载完成
2. 收集GameFeature插件URLs (第226-259行)：
- 从Experience定义中读取 GameFeaturesToEnable
- 从每个ActionSet读取 GameFeaturesToEnable
- 通过 UGameFeaturesSubsystem::Get().GetPluginURLByName() 获取插件URL
3. 加载并激活GameFeatures (第261-275行)：
NumGameFeaturePluginsLoading = GameFeaturePluginURLs.Num();
for (const FString& PluginURL : GameFeaturePluginURLs) {
    UGameFeaturesSubsystem::Get().LoadAndActivateGameFeaturePlugin(PluginURL, ...);
}

关键点：
- GameFeatures是模块化的功能插件
- 可以动态加载和卸载
- 这是Lyra实现模块化开发的核心

---
步骤4: GameFeature加载完成 (第278-287行)

void OnGameFeaturePluginLoadComplete()

做什么：
- 每当一个GameFeature加载完成，减少计数
- 当所有GameFeatures加载完毕后，调用 OnExperienceFullLoadCompleted()

关键点：
- 需要等待所有异步加载的GameFeatures完成

---
步骤5: 完全加载完成 (第289-343行)

void OnExperienceFullLoadCompleted()

做什么：

1. 可选的测试延迟 (第293-306行)：
const float DelaySecs = LyraConsoleVariables::GetExperienceLoadDelayDuration();
if (DelaySecs > 0.0f) {
    LoadState = ELyraExperienceLoadState::LoadingChaosTestingDelay;
    GetWorld()->GetTimerManager().SetTimer(...);
    return;
}
- 用于测试目的，可以插入随机延迟
2. 执行GameFeature Actions (第308-334行)：
- 设置状态为 ExecutingActions
- 创建 FGameFeatureActivatingContext（激活上下文）
- 对每个Action调用：
Action->OnGameFeatureRegistering();  // 注册
Action->OnGameFeatureLoading();      // 加载
Action->OnGameFeatureActivating(Context); // 激活
3. 触发完成委托 (第345-354行)：
LoadState = ELyraExperienceLoadState::Loaded;
OnExperienceLoaded_HighPriority.Broadcast(CurrentExperience);
OnExperienceLoaded.Broadcast(CurrentExperience);
OnExperienceLoaded_LowPriority.Broadcast(CurrentExperience);

关键点：
- Actions定义了GameFeature激活时的具体行为
- 分三个优先级广播：High、Normal、Low
- 不同系统可以订阅不同优先级

---
🎯 状态转换图

Unloaded (未加载)
    ↓ SetCurrentExperience()
Loading (加载资产中)
    ↓ 资产加载完成
LoadingGameFeatures (加载GameFeatures中)
    ↓ 所有GameFeatures加载完成
LoadingChaosTestingDelay (可选测试延迟)
    ↓ 延迟结束/无延迟
ExecutingActions (执行Actions中)
    ↓ Actions执行完成
Loaded (已加载) ✅

📦 核心概念总结

1. Experience Definition：定义游戏模式的完整配置
2. ActionSets：一组GameFeature Actions
3. GameFeatures：可动态加载的功能模块
4. GameFeatureActions：激活GameFeature时的具体操作（如添加能力、输入绑定等）
5. 异步加载：使用StreamableManager不阻塞主线程
6. 网络模式适配：根据客户端/服务器加载不同资源
7. 多优先级广播：High/Normal/Low三种广播，满足不同系统需求

💡 学习要点

✅ 理解核心思想：
- Experience = 完整的游戏模式配置
- 通过加载不同的Experience快速切换游戏体验

✅ 关键设计模式：
- 模块化：GameFeatures可独立加载
- 异步：资源加载不阻塞
- 基于组件：每个功能都是独立的Component

✅ 理解工作流程：
1. 设置Experience → 2. 加载资产 → 3. 加载GameFeatures → 4. 执行Actions → 5. 完成

> 🔍 后续学习方向
> 1. GameFeatureActions - 具体的Action类型
> 2. LyraExperienceDefinition - Experience的数据结构
> 3. 如何定义自己的Experience
{: .prompt-tip }

**研究 Experience 的生命周期管理（如何加载、激活、停用 Experience）**