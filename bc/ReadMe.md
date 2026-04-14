# BongoCat AutoTapper 使用说明

这是一个给最终用户阅读的说明文档，用于介绍当前 DLL 中的自动化功能和使用方式。

本脚本包含 3 个核心功能：

- 自动打字
- 自动开箱
- 自动表情

---

## 一、功能简介

### 1. 自动打字

自动调用猫咪点击逻辑，持续累积点击次数。

脚本会在游戏运行后自动寻找当前激活的 `Cat`，并通过反射调用 `Cat.Tap(int)`。

默认参数：

- 自动打字：开启
- 默认间隔：`0.2s`

### 2. 自动开箱

自动检测普通箱子和表情箱的刷新状态，并在可领取时尝试打开。

主要特性：

- 读取商店刷新剩余时间
- 到点前进入抢占窗口
- 到点后短时间内高频重试
- 支持普通箱和表情箱
- 读取菜单中的表情宝箱开关
- 可选尝试 `PromoItemChecker` 的活动箱逻辑

### 3. 自动表情

自动尝试触发表情栏中的表情。

当前逻辑：

- 优先模拟按钮点击，适合不消耗的永久表情
- 如果按钮点击不可用，再回退到 `Consume()`，适合有数量的消耗型表情
- 默认关闭
- 默认间隔：`5.0s`

---

## 二、自动初始化机制

脚本由 `AutoTapperBootstrap` 自动初始化。

初始化方式包括：

- `RuntimeInitializeOnLoadMethod(AfterAssembliesLoaded)`
- `RuntimeInitializeOnLoadMethod(BeforeSceneLoad)`
- `RuntimeInitializeOnLoadMethod(AfterSceneLoad)`
- 也可以通过在 `Pets.Awake()` 中插入 `BongoCat.AutoTapperBootstrap.AutoTapperBootstrap_Init();` 来确保生效。

初始化时会：

1. 检查场景中是否已有 `AutoTapper`
2. 若已有，则复用
3. 若没有，则创建 `~AutoTapper`
4. 将对象标记为 `DontDestroyOnLoad`，跨场景保留。

---

## 三、热键说明

### Ctrl + F6
切换自动打字开关。

### Ctrl + F7
切换自动开箱开关。

### Ctrl + F4
切换自动表情开关。

### Ctrl + F5
切换短周期模式：

- 开：刷新周期设为 `10s`
- 关：刷新周期设为 `1800s` 

### `-` / 小键盘 `-`
降低自动打字速度，间隔加大。

### `=` / 小键盘 `+`
提高自动打字速度，间隔减小，最低 `0.05s`。

---

## 四、HUD 显示说明

游戏内会自动创建一个 HUD，显示当前状态：

- 打字：ON / OFF
- 开箱：ON / OFF
- 表情：ON / OFF
- 速度：当前自动打字间隔 

脚本还会在 HUD 附近生成一个 Token 泡泡，用于显示：

- 箱子数量
- 表情箱数量 

---

## 五、自动表情说明

自动表情分两类处理：

### 1. 永久表情 / 不消耗表情
优先走按钮点击逻辑，不直接调用消耗方法。

### 2. 消耗型表情
若按钮点击不可用，才会检查其数量和 `_steamItem`，并尝试 `Consume()`。

使用建议：

- 如果用户主要使用永久表情，建议把常用永久表情放在表情栏前面
- 自动表情默认关闭，按 `Ctrl + F4` 手动开启
- 默认每 `5s` 尝试一次，避免过于频繁 

---

## 六、安装说明

### 建议步骤

1. 备份原始 `Assembly-CSharp.dll`
2. 保存并覆盖原 DLL
3. 启动游戏，观察日志是否出现：
   - `[AutoTap] Bootstrap via Pets.Awake`
   - `[AutoTap] Ready. ...`
   - `[AutoTap] HUD (UGUI) created under Pets counter.`

---

## 七、常见问题

### 1. 为什么游戏里没有自动生效？

先确认：

- 日志中是否出现 bootstrap 成功信息。

### 2. 为什么没有 HUD？

脚本会尝试把 HUD 挂到 `Pets` 的文本节点下。如果游戏 UI 结构变化，可能导致 HUD 找不到锚点。

### 3. 为什么自动表情没反应？

常见原因：

- 没有开启 `Ctrl + F4`
- 表情栏为空
- 目标表情按钮不可用
- 目标表情属于特殊类型，当前按钮点击链路未覆盖。

### 4. 为什么开箱日志很多？

自动开箱包含商店检测、抢占窗口和 Promo 检查，因此日志会比普通脚本多。如果不需要活动箱逻辑，可考虑关闭相关功能或降低触发频率。

---

## 八、默认配置

当前版本默认值：

- `Enabled = true`
- `IntervalSeconds = 0.2f`
- `AutoChestEnabled = true`
- `AutoClaimPromo = true`
- `AutoEmoteEnabled = false`
- `EmoteInterval = 5.0f`

---

## 九、日志关键字

以下日志一般说明脚本已经工作：

- `[AutoTap] Bootstrap via Pets.Awake`
- `[AutoTap] Ready. ...`
- `[AutoTap] HUD (UGUI) created under Pets counter.`
- `[TokenBubble] created near HUD.`
- `[AutoChest] ...`
- `[AutoEmote] ...`

---

## 十、给最终用户的简版说明

### 开关

- `Ctrl + F6`：自动打字
- `Ctrl + F7`：自动开箱
- `Ctrl + F4`：自动表情
- `Ctrl + F5`：切换短周期

### 调速

- `-`：变慢
- `=`：变快

### 建议

- 自动表情默认关闭，需要手动打开
- 永久表情建议放在表情栏前面
- 使用前建议先备份原 DLL

---
