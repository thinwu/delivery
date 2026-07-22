# 🐱 BongoCat AutoTapper

为 BongoCat 提供自动打字、自动开箱和自动发表情功能。

无需修改游戏 DLL，也不需要额外启动器。插件通过本地 `winhttp.dll` 自动加载 `Mods\AutoTapper.dll`。

---

# 🚀 快速开始

## 1. 安装

将发布包中的文件复制到 BongoCat 游戏目录。

发布包结构如下：

```text
bc/
├─ winhttp.dll
├─ ReadMe.md
└─ Mods/
   └─ AutoTapper.dll
```

复制完成后，游戏目录应类似：

```text
BongoCat/
├─ BongoCat.exe
├─ winhttp.dll
├─ ReadMe.md
├─ Mods/
│  └─ AutoTapper.dll
└─ BongoCat_Data/
```

请确认：

- `winhttp.dll` 与 `BongoCat.exe` 位于同一目录
- `AutoTapper.dll` 位于 `Mods` 文件夹中

---

## 2. 启动

直接启动：

```text
BongoCat.exe
```

也可以正常通过 Steam 启动游戏。

不需要使用额外启动器。插件会在游戏启动时自动加载。

---

## 3. 确认插件已加载

进入游戏后，可以在猫咪下方看到状态栏：

```text
打字: ON • 开箱: ON • 表情: OFF • 速度: 0.20s
```

看到状态栏说明插件已成功加载。

---

# ✨ 功能介绍

## 🖱️ 自动打字

自动点击猫咪并持续累计点击数。

功能开启后：

- 自动持续点击猫咪
- 自动累计点击数
- 无需手动点击

---

## 📦 自动开箱

自动检测箱子刷新时间。

箱子可领取时：

- 自动检测
- 自动领取
- 自动处理普通箱子
- 自动处理表情箱子
- 自动尝试处理活动箱

---

## 😺 自动发表情

自动触发表情栏中的表情。

支持：

- 普通表情
- 永久表情
- 非消耗表情

自动发表情默认关闭，需要手动开启。

---

# ⌨️ 功能开关

| 功能 | 快捷键 |
| --- | --- |
| 自动打字 开 / 关 | Ctrl + F6 |
| 自动开箱 开 / 关 | Ctrl + F7 |
| 自动发表情 开 / 关 | Ctrl + F4 |
| 快速刷新模式 开 / 关 | Ctrl + F5 |

---

# 🐾 快速切换

双击猫咪：

```text
自动打字 ON ↔ OFF
```

效果等同于：

```text
Ctrl + F6
```

---

# ⚡ 调整速度

| 操作 | 按键 |
| --- | --- |
| 加快点击 | `=` 或小键盘 `+` |
| 降低点击速度 | `-` 或小键盘 `-` |

默认速度：

```text
0.20 秒 / 次
```

---

# 📊 查看当前状态

插件状态会实时显示在游戏界面：

```text
打字: ON • 开箱: ON • 表情: OFF • 速度: 0.20s
```

| 项目 | 说明 |
| --- | --- |
| 打字 | 自动点击状态 |
| 开箱 | 自动开箱状态 |
| 表情 | 自动发表情状态 |
| 速度 | 当前点击间隔 |

插件还会显示普通箱子和表情箱子的 Token 数量。

---

# 📁 日志文件

启动后会在游戏目录生成：

```text
AutoTapperNativeLoader.log
```

该日志用于排查 Native Loader、Mono 和插件入口的加载问题。

游戏自身的 Unity 日志也可能包含：

```text
[AutoTapperBootstrap]
[AutoTapper]
[AutoChest]
[AutoEmote]
[TokenBubble]
```

等相关信息。

---

# 🔧 故障排查

## 游戏无法启动

先将游戏目录中的：

```text
winhttp.dll
```

临时移走，再启动游戏。

如果移走后游戏恢复，说明问题与 Native Loader 版本或系统兼容性有关。

---

## 游戏能启动，但插件没有生效

检查以下文件是否存在：

```text
BongoCat\winhttp.dll
BongoCat\Mods\AutoTapper.dll
```

然后查看：

```text
AutoTapperNativeLoader.log
```

---

## 日志提示找不到入口类

例如：

```text
class BongoCat.AutoTapperBootstrap not found.
```

说明当前 `Mods\AutoTapper.dll` 中缺少以下入口：

```text
BongoCat.AutoTapperBootstrap.Initialize()
```

请更新或重新编译 `AutoTapper.dll`。

---

## 日志提示托管异常

例如：

```text
Managed exception returned from AutoTapperBootstrap.Initialize().
```

说明 Native Loader 已成功加载插件，但插件初始化过程中发生了异常。

请继续查看后面的：

```text
Managed exception:
```

内容，以确定具体原因。

---

## 更新 DLL 后仍然使用旧版本

更新插件前，请先完全退出游戏，并确认任务管理器中没有残留的：

```text
BongoCat.exe
```

然后再替换：

```text
Mods\AutoTapper.dll
```

Mono 已经加载到当前进程中的程序集不会因为磁盘文件被替换而自动刷新。

---

# 🔄 更新插件

通常只需要替换：

```text
Mods\AutoTapper.dll
```

如果 Native Loader 也有更新，再同时替换：

```text
winhttp.dll
```

更新前请完全退出游戏。

---

# ❌ 卸载

删除以下文件即可恢复原版游戏：

```text
winhttp.dll
Mods\AutoTapper.dll
AutoTapperNativeLoader.log
```

`Mods` 文件夹中如果没有其他插件，也可以一并删除。

---

# ⚠️ 注意事项

- 请直接启动 `BongoCat.exe`，或正常通过 Steam 启动
- 自动发表情默认关闭
- 建议将常用表情放在表情栏前面
- 自动开箱会持续检测刷新时间，属于正常行为
- 更新插件前请完全退出游戏
- 游戏大版本更新后，Native Loader 或插件可能需要重新适配
- 如果游戏更新后无法启动，先临时移走 `winhttp.dll` 进行确认

---
