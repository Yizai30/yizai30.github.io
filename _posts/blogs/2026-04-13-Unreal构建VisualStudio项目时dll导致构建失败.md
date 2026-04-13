---
title: Unreal构建VisualStudio项目时dll导致构建失败
tags: [Unreal, Game]
categories: [Unreal, Game]
---

# 报错信息
```bash
Running D:/EpicEditor/UE_5.5/UE_5.5/Engine/Build/BatchFiles/Build.bat  -projectfiles -project="D:/Unreal/MathVis/MathVis.uproject" -game -rocket -progress
Using bundled DotNet SDK version: 8.0.300
Running UnrealBuildTool: dotnet "..\..\Engine\Binaries\DotNET\UnrealBuildTool\UnrealBuildTool.dll" -projectfiles -project="D:/Unreal/MathVis/MathVis.uproject" -game -rocket -progress
Unhandled exception: ReflectionTypeLoadException: Unable to load one or more of the requested types.
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
   at System.Reflection.RuntimeModule.GetTypes(RuntimeModule module)
   at System.Reflection.RuntimeModule.GetTypes()
   at UnrealBuildTool.UnrealBuildTool.GetModes() in D:\EpicEditor\UE_5.5\UE_5.5\Engine\Source\Programs\UnrealBuildTool\UnrealBuildTool.cs:line 336
   at UnrealBuildTool.UnrealBuildTool..cctor() in D:\EpicEditor\UE_5.5\UE_5.5\Engine\Source\Programs\UnrealBuildTool\UnrealBuildTool.cs:line 350Wrapped by TypeInitializationException: The type initializer for 'UnrealBuildTool.UnrealBuildTool' threw an exception.
   at UnrealBuildTool.UnrealBuildTool.Main(String[] ArgumentsArray) in D:\EpicEditor\UE_5.5\UE_5.5\Engine\Source\Programs\UnrealBuildTool\UnrealBuildTool.cs:line 523
Unhandled exception. System.TypeInitializationException: The type initializer for 'UnrealBuildTool.UnrealBuildTool' threw an exception.
 ---> System.Reflection.ReflectionTypeLoadException: Unable to load one or more of the requested types.
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
   at System.Reflection.RuntimeModule.GetTypes(RuntimeModule module)
   at System.Reflection.RuntimeModule.GetTypes()
   at UnrealBuildTool.UnrealBuildTool.GetModes() in D:\EpicEditor\UE_5.5\UE_5.5\Engine\Source\Programs\UnrealBuildTool\UnrealBuildTool.cs:line 336
   at UnrealBuildTool.UnrealBuildTool..cctor() in D:\EpicEditor\UE_5.5\UE_5.5\Engine\Source\Programs\UnrealBuildTool\UnrealBuildTool.cs:line 350
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
System.IO.FileLoadException: Could not load file or assembly 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'. Ӧ?????????????ļ?(0x800711C7)
File name: 'D:\EpicEditor\UE_5.5\UE_5.5\Engine\Binaries\DotNET\UnrealBuildTool\EpicGames.Horde.dll'
   --- End of inner exception stack trace ---
   at UnrealBuildTool.UnrealBuildTool.Main(String[] ArgumentsArray) in D:\EpicEditor\UE_5.5\UE_5.5\Engine\Source\Programs\UnrealBuildTool\UnrealBuildTool.cs:line 704
```

# 解决方法

1. 在 PowerShell 中检查 SmartAppControlState 选项：

```bash
PS C:\WINDOWS\system32> Get-MpComputerStatus

...
SmartAppControlState             : On
...

PS C:\WINDOWS\system32>
```

2. 关闭Smart App Control
- 按 Win + I 打开设置
- 进入 "隐私和安全性" → "Windows安全中心"
- 点击 "应用和浏览器控制" 卡片
- 找到 "智能应用控制" 部分
- 点击 "智能应用控制设置" 进入，将其设置为 "关闭"