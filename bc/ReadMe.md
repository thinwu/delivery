## 📦 安装与部署

### 目录结构

发布包结构如下：

```text
bc/
├─ AutoTapperLauncher.exe
├─ version.dll
├─ ReadMe.md
└─ Mods/
   └─ AutoTapper.dll
```

---

### 安装方法

打开 BongoCat 游戏目录：

```text
...\Steam\steamapps\common\BongoCat
```

将发布包中的文件复制到游戏目录。

最终目录应类似：

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

### 启动方式

请使用：

```text
AutoTapperLauncher.exe
```

启动游戏。

启动器会自动：

* 启动 BongoCat
* 加载 AutoTapper 插件
* 记录运行日志

无需修改游戏文件。

---

### 更新插件

后续更新时通常只需要替换：

```text
Mods/AutoTapper.dll
```

即可。

如果启动器或加载器有更新，再同时替换：

```text
AutoTapperLauncher.exe
version.dll
```

---

### 游戏更新后

本插件不会修改：

```text
Assembly-CSharp.dll
```

因此大多数游戏更新后无需重新安装。

通常只需重新启动游戏即可继续使用。

如遇插件失效，请更新最新版插件包。

---

### 卸载

删除以下文件即可：

```text
AutoTapperLauncher.exe
version.dll
Mods/AutoTapper.dll
```

删除后游戏会恢复原始状态。
