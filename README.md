# OC2 Test 1 Recipe Counter

测试1记菜器 v2.8，用于 *Overcooked! 2* 的 DIYLevel 自定义测试1关卡。

## 功能

- 只针对测试1关卡：`s_test_level`。
- 统计已经出现过的菜单次数。
- 支持四人模式和双人模式。
- 四人模式显示 1 / 2 / 3 / 4 号位菜单。
- 双人模式中：
  - 双人 1号位 = 四人 1号位 + 四人 4号位；
  - 双人 2号位 = 四人 2号位 + 四人 3号位。
- 如果四人模式和双人模式都关闭，进入测试1不会显示记菜器窗口。

## 安装

仓库中的源码包以 Base64 分片保存。先把分片合并并解码：

```powershell
Get-Content .\archive\OC2Test1RecipeCounter_v2_8_source.zip.b64.part* | Set-Content .\OC2Test1RecipeCounter_v2_8_source.zip.b64
certutil -decode .\OC2Test1RecipeCounter_v2_8_source.zip.b64 .\OC2Test1RecipeCounter_v2_8_source.zip
```

然后解压 zip，进入有 `build.ps1` 的目录，编译安装：

```powershell
powershell -ExecutionPolicy Bypass -File .\build.ps1 -GameDir "E:\SteamLibrary\steamapps\common\Overcooked! 2" -Install
```

如果你的游戏在 D 盘，把 `GameDir` 改成你的实际路径。

## 控制台设置

Configuration Manager 中分为三部分：

```text
1. 四人模式
2. 双人模式
3. 通用功能
```

规则：

```text
只开四人模式 => 显示四人 1/2/3/4 号位
只开双人模式 => 显示双人 1/2 号位
两个都开 => 自动只保留最后打开的模式
两个都关 => 不显示菜单
```

## 启动确认

进入游戏后，在 `BepInEx/LogOutput.log` 里应看到：

```text
Loading [测试1记菜器 2.8.0]
测试1记菜器 v2.8.0 loaded.
```

## Disclaimer

Unofficial fan-made mod. Not affiliated with Team17, Ghost Town Games, or the official *Overcooked! 2* developers. Use at your own risk. Do not use gameplay-altering mods in public lobbies or with players who have not agreed to modded gameplay.
