# 🐱 BongoCat AutoTapper

为 BongoCat 提供自动打字、自动开箱和自动发表情功能。

无需修改游戏 DLL，支持独立加载。

---

# 🚀 快速开始

## 1. 安装

将发布包中的文件复制到游戏目录。

发布包结构如下：

```text
bc/
├─ AutoTapperLauncher.exe
├─ version.dll
├─ ReadMe.md
└─ Mods/
   └─ AutoTapper.dll
```

复制完成后，游戏目录应类似：

```text
BongoCat/
├─ BongoCat.exe
├─ AutoTapperLauncher.exe
├─ version.dll
├─ Mods/
│  └─ AutoTapper.dll
└─ BongoCat_Data/
```

---

## 2. 启动

请使用：

```text
AutoTapperLauncher.exe
```

启动游戏。

插件会自动加载。

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

自动点击猫咪，持续获取点击数。

功能开启后：

* 自动持续点击猫咪
* 自动累计点击数
* 无需手动点击

---

## 📦 自动开箱

自动检测箱子刷新时间。

箱子可领取时：

* 自动检测
* 自动领取
* 自动处理普通箱子
* 自动处理表情箱子

---

## 😺 自动发表情

自动触发表情栏中的表情。

支持：

* 普通表情
* 永久表情
* 非消耗表情

默认关闭，需要手动开启。

---

# ⌨️ 功能开关

| 功能           | 快捷键       |
| ------------ | --------- |
| 自动打字 开 / 关   | Ctrl + F6 |
| 自动开箱 开 / 关   | Ctrl + F7 |
| 自动发表情 开 / 关  | Ctrl + F4 |
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

| 操作     | 按键        |
| ------ | --------- |
| 加快点击   | = 或 小键盘 + |
| 降低点击速度 | - 或 小键盘 - |

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

状态说明：

| 项目 | 说明      |
| -- | ------- |
| 打字 | 自动点击状态  |
| 开箱 | 自动开箱状态  |
| 表情 | 自动发表情状态 |
| 速度 | 当前点击间隔  |

---

# 📁 日志文件

启动后会生成：

```text
AutoTapperLauncher.log
AutoTapperNativeLoader.log
```

用于排查插件加载问题。

---

# 🔄 更新插件

通常只需要替换：

```text
Mods/AutoTapper.dll
```

即可完成插件更新。

如果加载器有更新，再同时替换：

```text
AutoTapperLauncher.exe
version.dll
```

---

# ❌ 卸载

删除以下文件即可恢复原版游戏：

```text
AutoTapperLauncher.exe
version.dll
Mods/AutoTapper.dll
```

---

# ⚠️ 注意事项

* 请使用 AutoTapperLauncher.exe 启动游戏
* 自动发表情默认关闭
* 建议将常用表情放在表情栏前面
* 自动开箱会持续检测刷新时间，属于正常行为
* 游戏大版本更新后可能需要重新适配插件

---
