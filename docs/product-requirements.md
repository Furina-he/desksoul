# DeskSoul 产品需求文档（PRD）

版本：0.1 Draft  
日期：2026-04-27  
状态：草案  
负责人：DeskSoul Contributors

---

## 1. 产品概述

DeskSoul 是一款非商业开源 AI 桌宠应用。它会在用户桌面上放置一个可互动的 AI 伴侣角色，第一阶段以 Live2D 角色为主，支持文字聊天、点击反馈、基础情绪反应和桌面拖拽；后续逐步支持语音、AstrBot 外接大脑、VRM 角色、角色包、插件系统，以及更丰富的桌宠行为。

DeskSoul 的 MVP 不追求成为通用生产力 Agent，而是优先让用户感受到“桌面上真的有一个活着的角色”：它可见、可拖拽、会回应、会表达情绪、足够轻量、容易启动。

### 1.1 一句话定位

DeskSoul 是一款 Live2D 优先的 AI 桌面宠物应用，支持外接 AstrBot 作为高级 AI 大脑，并参考 Mate-Engine 的桌宠交互体验进行自研实现。

### 1.2 核心方向

- 主路线：参考 AIRI 的桌面虚拟伴侣架构。
- AI 后端：MVP 先支持 OpenAI-compatible Provider，后续外接 AstrBot。
- 桌宠行为：参考 Mate-Engine 的交互体验，但不复制源码和资产。
- 角色渲染：Live2D 优先，VRM 第二阶段支持。
- 平台优先级：Windows 优先，macOS / Linux 后续。
- 项目定位：非商业开源社区项目。

---

## 2. 背景与动机

现有 AI 伴侣或桌宠项目通常偏向以下三类：

1. 聊天机器人优先，但视觉存在感弱。
2. 虚拟角色框架优先，但桌面宠物交互不足。
3. 桌宠应用优先，但 AI、插件和扩展能力有限。

DeskSoul 试图把这三类体验结合起来：

- 角色常驻桌面，而不只是一个聊天窗口。
- 用户可以快速和角色文字聊天。
- AI 回复能够驱动表情、动作和桌宠状态。
- 后续支持语音输入、语音输出和嘴型同步。
- 后续可外接 AstrBot，复用其 Agent、插件、知识库和 IM 生态。
- 后续提供角色包和插件机制，方便社区扩展。

第一阶段必须避免过度设计。产品的首要目标是尽快做出一个“可爱、可互动、能聊天”的桌宠原型，而不是一开始就做复杂 Agent 系统。

---

## 3. 目标与非目标

## 3.1 产品目标

### MVP 目标

1. 展示一个透明或无边框的桌面宠物窗口。
2. 加载一个 Live2D 占位角色。
3. 支持拖拽角色。
4. 支持缩放角色。
5. 支持通过 OpenAI-compatible Provider 进行基础文字聊天。
6. 在气泡或聊天面板中展示 AI 回复。
7. 根据 AI 回复推断基础情绪，并映射到角色表情。
8. 支持基础点击反馈。
9. 保存用户本地配置。
10. 为后续语音、AstrBot、VRM、角色包和插件系统预留清晰架构。

### 中期目标

1. 支持 TTS、STT 和嘴型同步。
2. 支持 AstrBot Bridge，让 DeskSoul 连接外部 AstrBot 实例。
3. 支持更丰富的 Mate-like 桌宠行为，例如睡眠、边缘吸附、跳舞、坐在窗口边缘。
4. 支持角色包导入和校验。
5. 支持 VRM 角色。
6. 提供桌宠插件 SDK 和 AstrBot 侧插件模板。

## 3.2 非目标

MVP 不包含以下内容：

1. 内置 AstrBot。
2. 内置 Python Runtime。
3. 完整 VRM 支持。
4. 长期记忆系统。
5. 知识库系统。
6. IM 平台同步。
7. 自动操作电脑。
8. 复杂多 Agent 编排。
9. 插件市场。
10. 官方构建的商业分发。
11. 未经授权的版权角色模型打包分发。
12. 复制 Mate-Engine 源码或资产。

---

## 4. 目标用户

## 4.1 核心用户

### 4.1.1 AI 伴侣爱好者

希望桌面上有一个可爱角色陪伴、聊天和互动的用户。

需求：

- 安装和启动简单。
- 桌面上有明显角色存在感。
- 能聊天。
- 有基础人格和情绪反应。
- 后续希望支持语音。

### 4.1.2 开源爱好者和开发者

希望修改项目、贡献功能、添加角色或二次开发的用户。

需求：

- 代码结构清晰。
- 模块边界明确。
- 文档完整。
- 容易创建 PR。
- 有明确路线图和 Issue 拆分。

### 4.1.3 AstrBot 用户

已经使用 AstrBot，希望给自己的 Agent 增加桌面角色前端的用户。

需求：

- 支持外接 AstrBot。
- 支持 API Key 配置。
- 支持流式回复。
- 支持 AstrBot 回复驱动表情和动作。

## 4.2 次级用户

### 4.2.1 角色创作者

希望为 DeskSoul 制作 Live2D / VRM 角色包的模型师或创作者。

需求：

- 明确的角色包格式。
- 明确的许可证声明。
- 导入校验。
- 角色预览。

### 4.2.2 插件开发者

希望编写插件控制桌宠行为的开发者。

需求：

- 稳定的插件接口。
- 事件和动作 API。
- 示例插件。
- AstrBot 插件模板。

---

## 5. 产品原则

1. 桌宠优先，Agent 第二。  
   先让角色像桌宠一样存在，再逐步增加复杂 AI 能力。

2. 首次启动体验要简单。  
   用户应能尽快看到角色出现在桌面上。

3. 架构必须模块化。  
   渲染、AI、语音、桌面行为、插件都要可替换。

4. 许可证安全优先。  
   不打包版权不明资源；Mate-Engine 只作为交互参考。

5. Windows 优先。  
   复杂桌面行为先在 Windows 上验证。

6. 外接 AI 后端优先。  
   AstrBot 作为可选外部服务，不在 MVP 内置。

7. 社区扩展友好。  
   角色包、动作包、语音包和插件都应有清晰贡献路径。

---

## 6. 用户故事

## 6.1 MVP 用户故事

### US-001：启动桌宠

作为用户，我希望启动 DeskSoul 后能看到一个角色出现在桌面上，从而感受到桌面伴侣的存在。

验收标准：

- 应用能打开一个桌宠窗口。
- 窗口默认置顶。
- 应用可通过托盘或菜单退出。

### US-002：拖拽角色

作为用户，我希望能拖动角色到桌面任意位置，以便把它放在自己喜欢的位置。

验收标准：

- 角色拖拽流畅。
- 拖拽结束后角色保持可见。
- 重启后恢复上次位置。

### US-003：缩放角色

作为用户，我希望能调整角色大小，以适配不同屏幕和个人偏好。

验收标准：

- 可从设置或快捷菜单调整缩放比例。
- 缩放比例本地保存。
- 缩放后点击和拖拽仍正常。

### US-004：文字聊天

作为用户，我希望能输入文字和桌宠聊天，并收到 AI 回复。

验收标准：

- 用户可以打开聊天输入。
- 应用能把消息发送给 OpenAI-compatible Provider。
- 回复显示在聊天气泡或聊天面板中。
- Provider 配置错误时有清晰提示。

### US-005：情绪反应

作为用户，我希望角色能根据 AI 回复做出不同情绪反应，让它看起来更像活着的角色。

验收标准：

- 至少支持 neutral、happy、sad、angry、thinking、sleepy 六种情绪。
- 情绪可以映射到 Live2D 表情。
- 缺失表情时回退到 neutral。

### US-006：点击反馈

作为用户，我希望点击角色时它能有反应，让它更有互动感。

验收标准：

- 点击角色触发基础反馈。
- 未来可扩展为头、脸、身体等区域。
- 点击反馈不会异常打断关键状态。

### US-007：本地设置

作为用户，我希望 API、窗口位置、角色大小等设置能被保存。

验收标准：

- Provider 配置可保存。
- API Key 不出现在日志中。
- 窗口位置和缩放比例可在重启后恢复。

## 6.2 后续用户故事

### US-101：语音输出

作为用户，我希望桌宠能把回复读出来，让互动更自然。

### US-102：语音输入

作为用户，我希望可以用麦克风和桌宠说话。

### US-103：嘴型同步

作为用户，我希望角色说话时嘴巴会动。

### US-104：AstrBot 集成

作为 AstrBot 用户，我希望 DeskSoul 能连接本地或远程 AstrBot，让桌宠使用 AstrBot Agent、插件和知识库。

### US-105：角色包

作为用户，我希望能导入不同角色包，自定义自己的桌宠。

### US-106：Mate-like 桌面行为

作为用户，我希望桌宠能睡觉、吸附边缘、跳舞、坐在窗口边缘，让它更像真实桌宠。

---

## 7. 功能需求

## 7.1 桌面壳

### MVP 需求

- Electron 桌面应用。
- 透明或无边框桌宠窗口。
- Always-on-top 默认开启。
- 系统托盘菜单。
- 设置窗口。
- 聊天气泡或聊天面板。
- 本地配置存储。

### 后续需求

- 多窗口布局。
- 全局快捷键。
- 多显示器选择。
- 鼠标穿透模式开关。
- 开机自启动选项。

## 7.2 Pet Core

### MVP 需求

- 桌宠状态机。
- 核心状态：
  - booting
  - idle
  - thinking
  - speaking
  - dragging
  - touch_reacting
  - error
- 情绪类型：
  - neutral
  - happy
  - sad
  - angry
  - thinking
  - sleepy
- 动作类型：
  - idle
  - wave
  - nod
  - thinking
- 事件总线，用于连接 UI、Renderer 和 Brain。

### 后续需求

- sleeping
- dancing
- sitting_on_screen_edge
- sitting_on_window
- sitting_on_taskbar
- feeding
- reminders
- 多角色状态隔离

## 7.3 Renderer

### MVP 需求

- 加载 Live2D 占位角色。
- 支持表情映射。
- 支持基础动作映射。
- 支持缩放。
- 尽量支持看向鼠标。
- 支持表情和动作 fallback。

### 后续需求

- Live2D hitTest 区域。
- 嘴型同步。
- VRM Renderer Adapter。
- VRM BlendShape 情绪映射。
- VRM 动画映射。
- 角色包导入。

## 7.4 Brain Core

### MVP 需求

- 定义 BrainProvider 接口。
- 实现 OpenAI-compatible Provider。
- 支持 Provider 配置：
  - base URL
  - API Key
  - model name
  - temperature
  - streaming toggle
- 支持流式文本输出。
- 将最终回复转换为 PetReply。

### 后续需求

- AstrBot Provider。
- Ollama Provider。
- 本地模型 Provider。
- Tool / Action 事件。
- Persona 注入。
- 角色级 Prompt 模板。

## 7.5 情绪与动作映射

### MVP 需求

- 用简单规则从回复文本推断情绪。
- 将情绪映射到 Renderer 表情。
- 将基础意图映射到动作。
- 提供 fallback 行为。

### 后续需求

- 模型结构化标签输出。
- AstrBot PET 标签解析。
- 每个角色可配置情绪映射。
- 每个角色可配置动作库。

## 7.6 语音

### MVP 需求

v0.1 不包含语音。

### v0.2 需求

- TTS Provider 抽象。
- 播放 TTS 音频。
- 用音量驱动简易嘴型同步。
- STT Provider 抽象。
- 按住说话输入。

## 7.7 AstrBot Bridge

### MVP 需求

v0.1 不包含 AstrBot Bridge。

### v0.3 需求

- 设置项：
  - enabled
  - base URL
  - API Key
  - username
  - session ID
  - streaming
- 连接测试。
- 对接 `POST /api/v1/chat`。
- SSE 解析。
- AstrBot 回复转 BrainChunk。
- PET 结构化标签解析。
- 错误处理。

## 7.8 角色包

### MVP 需求

- 使用占位角色资源。
- 不打包版权不明资源。

### 后续需求

- `.petpack` 格式。
- manifest.json 校验。
- license.md 必填。
- preview image。
- persona.md。
- Live2D 和 VRM 入口。
- 表情和动作映射。

---

## 8. 非功能需求

## 8.1 性能

MVP 目标：

- 应用在现代 Windows 设备上能较快启动。
- 空闲 CPU 占用应保持较低。
- 拖拽角色时不明显卡顿。
- Electron 内存占用应控制在可接受范围。

初始非强制目标：

- 空闲 CPU 占用低于 5%。
- 内存占用尽量低于 500 MB。

## 8.2 稳定性

- Provider 请求失败不能导致应用崩溃。
- Renderer 加载失败时应显示清晰错误。
- 缺失表情或动作时应 fallback。
- 本地配置损坏时不能阻止应用启动。

## 8.3 隐私与安全

- API Key 不应写入日志。
- 敏感配置应尽量安全保存。
- MVP 不自动读取用户文件。
- MVP 不自动控制用户电脑。
- 未启用 AstrBot 时，不向 AstrBot 发送数据。

## 8.4 许可证

- 代码：AGPL-3.0-or-later。
- 原创资源：默认 CC BY-NC-SA 4.0，除非单独声明。
- 第三方资源必须包含许可证文件。
- 主仓库不得复制 Mate-Engine 源码和资产。
- 复用 AIRI 的 MIT 代码时必须在 NOTICE 中保留署名。

## 8.5 平台

MVP 平台：

- Windows 10 / Windows 11。

后续平台：

- macOS。
- Linux。

---

## 9. MVP 范围

## 9.1 v0.1 范围内

- Electron 应用骨架。
- 透明或无边框桌宠窗口。
- Always-on-top。
- 托盘菜单。
- 设置窗口。
- 聊天气泡或面板。
- Live2D 占位角色加载。
- 拖拽。
- 缩放。
- OpenAI-compatible Provider 文字聊天。
- 基础情绪识别。
- 基础表情映射。
- 本地设置保存。
- 基础日志和错误处理。

## 9.2 v0.1 范围外

- AstrBot 集成。
- 语音输入输出。
- VRM。
- 长期记忆。
- 插件 SDK。
- 角色包市场。
- 窗口坐下。
- 任务栏坐下。
- IM 集成。
- 游戏集成。
- 自动系统操作。

---

## 10. 版本里程碑

## v0.0：项目基础

目标：完成仓库和应用基础。

交付物：

- 项目文档。
- 许可证文件。
- Workspace 设置。
- Electron + Vue 骨架。
- 基础应用启动。

退出标准：

- `pnpm install` 可执行。
- `pnpm dev:desktop` 能启动 Electron 窗口。

## v0.1：桌宠 + 文字聊天

目标：第一个可用桌宠版本。

交付物：

- 桌宠窗口。
- 占位角色。
- 拖拽。
- 文字聊天。
- OpenAI-compatible Provider。
- 情绪反应。

退出标准：

- 用户能启动应用。
- 用户能移动桌宠。
- 用户能和桌宠聊天。
- 桌宠能做基础表情反应。

## v0.2：语音 + 情绪动作

目标：让桌宠能说话，互动更自然。

交付物：

- TTS。
- STT。
- 嘴型同步。
- 触摸区域。
- 睡眠 / 唤醒状态。

## v0.3：AstrBot Bridge

目标：连接 AstrBot 作为可选外部大脑。

交付物：

- AstrBot 设置。
- 连接测试。
- 流式聊天。
- PET 标签解析。

## v0.4：桌宠行为增强

目标：实现更丰富的 Mate-like 桌宠行为。

交付物：

- 屏幕边缘吸附。
- 睡眠。
- 跳舞。
- 实验性窗口坐下。

## v0.5：社区生态

目标：支持社区自定义与扩展。

交付物：

- 角色包导入。
- 插件 SDK 原型。
- 示例插件。

---

## 11. 成功指标

## 11.1 MVP 成功指标

- 用户可以在 Windows 上启动应用。
- 用户可以在桌面看到角色。
- 用户可以拖拽和缩放角色。
- 用户可以配置 OpenAI-compatible Provider。
- 用户可以和角色聊天。
- 角色至少支持 5 种基础情绪状态。
- 常见 Provider 错误不会导致应用崩溃。

## 11.2 社区指标

- README 和开发文档清晰。
- Issue 拆分足够具体，方便贡献。
- 至少有一个占位角色加载路径说明。
- 新贡献者可以从零完成项目启动。

---

## 12. 风险与缓解方案

## 12.1 Live2D 资源许可证风险

风险：内置模型可能没有明确再分发权限。

缓解：

- 早期只使用占位资源或用户自行导入。
- 角色包必须包含 license.md。
- 官方默认角色后续自制。

## 12.2 过度设计风险

风险：在桌宠可用之前就同时做 AstrBot、VRM、语音、插件和复杂桌面行为，导致 MVP 延迟。

缓解：

- v0.1 聚焦桌宠窗口、Live2D、拖拽、文字聊天和情绪反应。

## 12.3 Electron 性能风险

风险：Electron 作为桌宠可能占用较多内存。

缓解：

- 保持窗口和渲染逻辑简单。
- 避免 Renderer 中执行重型后台任务。
- v0.1 后进行性能 Profiling。

## 12.4 Provider 兼容风险

风险：不同 LLM Provider 的流式 API 行为不完全一致。

缓解：

- MVP 只支持 OpenAI-compatible。
- 先抽象 BrainProvider，再增加其他 Provider。

## 12.5 桌面集成复杂度风险

风险：窗口坐下、任务栏坐下受 Windows 版本、DPI、多屏幕和任务栏设置影响。

缓解：

- 推迟到 v0.4。
- 先实现屏幕边缘吸附。
- 高级行为默认实验性开关。

---

## 13. 待确认问题

1. 第一版 Live2D Runtime / Wrapper 具体选型是什么？
2. v0.1 是否使用 electron-vite 作为主构建方案？
3. Windows 下 API Key 第一版如何保存？
4. 第一版聊天 UI 使用气泡、侧边面板，还是两者都做？
5. 示例 OpenAI-compatible Provider 使用哪个？
6. 鼠标穿透模式是否默认关闭？
7. AIRI 代码复用范围控制到什么程度？

---

## 14. 推荐下一步

1. 完成 Electron + Vue + TypeScript 项目骨架。
2. 添加 PetState、PetEmotion、PetMotion 类型。
3. 实现透明桌宠窗口。
4. 实现拖拽和缩放。
5. 确定 Live2D Runtime。
6. 加载 Live2D 占位角色。
7. 实现 OpenAI-compatible Provider。
8. 将聊天回复接入情绪映射。

---

## 15. 附录：初始内部类型

```ts
export type PetState =
  | 'booting'
  | 'idle'
  | 'thinking'
  | 'speaking'
  | 'dragging'
  | 'touch_reacting'
  | 'error'

export type PetEmotion =
  | 'neutral'
  | 'happy'
  | 'sad'
  | 'angry'
  | 'thinking'
  | 'sleepy'

export type PetMotion =
  | 'idle'
  | 'wave'
  | 'nod'
  | 'thinking'

export interface PetReply {
  text: string
  emotion?: PetEmotion
  motion?: PetMotion
}
```
