---
title: Unreal的BlueprintNativeEvent总结
tags: [Unreal, BlueprintNativeEvent, CLASS_Native]
categories: [Game]
---
### 场景
为什么下面的代码在没有定义 UpdateVisualization 的情况下，可以正常运行？
```cpp
UFUNCTION(BlueprintNativeEvent, Category = "Math Element")
void UpdateVisualization(float Time, const TArray<FAnimationLayer>& AnimationLayers);
virtual void UpdateVisualization_Implementation(float Time, const TArray<FAnimationLayer>& AnimationLayers);
```
其中，UpdateVisualization 没有被定义，但是 UpdateVisualization_Implementation 有被定义。当调用 UpdateVisualization 时，可以跳转到 UpdateVisualization_Implementation 的函数体中，这是为什么？

### UHT 实现自动选择调用哪个函数定义
在 Intermediate/Build/Win64/UnrealEditor/Inc/{project_name}/UHT/ 目录下，UHT 生成了 *.gen.cpp 文件，里面包括 UpdateVisualization 的定义。
```cpp
static const FName NAME_AMathElementActor_UpdateVisualization = FName(TEXT("UpdateVisualization"));
void AMathElementActor::UpdateVisualization(float Time, TArray<FAnimationLayer> const& AnimationLayers)
{
	UFunction* Func = FindFunctionChecked(NAME_AMathElementActor_UpdateVisualization);
	if (!Func->GetOwnerClass()->HasAnyClassFlags(CLASS_Native))
	{
		MathElementActor_eventUpdateVisualization_Parms Parms;
		Parms.Time=Time;
		Parms.AnimationLayers=AnimationLayers;
	ProcessEvent(Func,&Parms);
	}
	else
	{
		UpdateVisualization_Implementation(Time, AnimationLayers);
	}
}
```
Blueprint 类没有 CLASS_Native 标记，C++ 类有 CLASS_Native 标记。所以，上面的函数实现了自动选择调用蓝图函数还是 C++ 函数，如果蓝图中定义了 UpdateVisualization 函数，那么就会调用 UpdateVisualization 函数，否则就会调用 C++ 定义的 UpdateVisualization_Implementation 函数。

### 验证
创建 UBlueprintClassHelper 类，继承自 BlueprintFunctionLibrary。定义 IsNativeClass 和 GetClassDescription 两个函数，用于验证 UObject 对象是否为蓝图类，以及获取类的描述信息。
```cpp
bool UBlueprintClassHelper::IsNativeClass(UObject* Object)
{
    if (!Object)
    {
        return false;
    }

    UClass* Class = Object->GetClass();
    if (!Class)
    {
        return false;
    }

    // 检查是否有CLASS_Native标志
    return Class->HasAnyClassFlags(CLASS_Native);
}

FString UBlueprintClassHelper::GetClassDescription(UObject* Object)
{
    if (!Object)
    {
        return TEXT("Invalid Object");
    }

    UClass* Class = Object->GetClass();
    if (!Class)
    {
        return TEXT("No Class");
    }

    FString Description = Class->GetName();

    if (Class->HasAnyClassFlags(CLASS_Native))
    {
        Description += TEXT(" (Native C++)");
    }
    else
    {
        Description += TEXT(" (Blueprint)");
    }

    return Description;
}
```
![alt text](/images/2025-12-12-Unreal的BlueprintNativeEvent总结/image-1.png)
_验证 HasAnyClassFlags(CLASS_Native) 可以区分蓝图类和 C++ 类_

### 反射系统
UCLASS_Native 是 ObjectMacros.h 定义的一个宏。但不在 [类说明符](https://dev.epicgames.com/documentation/zh-cn/unreal-engine/class-specifiers) 中。
```cpp
/**
 * Flags describing a class.
 *
 * This MUST be kept in sync with EClassFlags defined in
 * Engine\Source\Programs\Shared\EpicGames.Core\UnrealEngineTypes.cs
 */
enum EClassFlags
{
	...
	/** Class is a native class - native interfaces will have CLASS_Native set, but not RF_MarkAsNative */
	CLASS_Native			  = 0x00000080u,
    ...
}
```
### Unreal 开发者助手
> CLASS_Native 是 Unreal Engine 内部用于表示“原生”C++类的标记或宏，而不是用户在 UCLASS() 宏中直接使用的类声明规范。
- 它标识那些直接由 C++ 编写、继承自 UObject 的类，区别于纯蓝图类或自动生成的类。
- 该标记帮助引擎区分原生类与非原生类，在运行时和编辑器中管理类的行为和元数据。
- 用户声明类时，通常使用的 UCLASS 规范有 Blueprintable、NotBlueprintable、BlueprintType 等，来控制类是否可被蓝图继承或使用，而 CLASS_Native 属于更底层的引擎内部实现细节。

一个完整的 UE5 C++ 类声明例子：
```cpp
UCLASS(Blueprintable)
class MYGAME_API AMyActor : public AActor
{
    GENERATED_BODY()

public:
    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="Stats")
    float Health;

    UFUNCTION(BlueprintCallable, Category="Actions")
    void PerformAction();
};
```
这里的 UCLASS(Blueprintable) 表示该类是原生 C++ 类且可被蓝图继承。CLASS_Native 是引擎对这类原生 C++ 类的内部标记，用于区分其特殊处理。

**总结：CLASS_Native 不是用户直接设置的属性，而是用来标识和管理以原生 C++ 形式存在的 UE 类的内部标志。**