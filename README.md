# FaceTime - AI 面试实时助手

> 面试场景下的 AI 实时应答工具，支持语音识别、截图问答、悬浮窗、会议记录和模拟面试。

## 下载安装

**最新版本：v2026.06.12**

[![GitHub Release](https://img.shields.io/badge/download-latest-blue)](https://github.com/ZRegod/FaceTime/releases/latest)

- Windows 安装包：[FaceTime Setup 2026.6.12.exe](https://github.com/ZRegod/FaceTime/releases/download/v2026.06.12/FaceTime%20Setup%202026.6.12.exe)
- 内置语音识别模型（中英双语带标点），安装后无需下载即可使用
- 支持自定义安装目录（不再强制安装到 C 盘）
- 完整更新日志：[Release Notes](https://github.com/ZRegod/FaceTime/releases/tag/v2026.06.12)

## 核心功能

- **AI 实时回答** — 输入问题或语音转写，AI 以第一人称给出可直接参考的回答
- **三种回答模式** — 详细版（深度回答）、逐字稿（口语化可念）、两者（详细+逐字稿同时生成，可随时切换查看）
- **语音识别** — 支持 DashScope 云端识别和 Sherpa-ONNX 本地识别，实时转写面试问题
- **模型内置** — 安装包自带中英双语带标点模型（128MB），首次启动自动配置，开箱即用
- **更多本地模型** — 另有 4 种模型可选（极小中文 20MB / 轻量中文 71MB / 中文增强 59MB / 中英双语 331MB），支持 GitHub 镜像加速下载
- **双重验证识别** — 在线流式识别 + 离线修正两遍校验，内置 VAD 语音检测和热词库（技术面试专用），需额外下载离线修正模型（130MB）
- **截图问答** — 一键截取屏幕题目，支持视觉模型直传图片或本地 OCR 兜底，自动检测模型是否支持图片输入
- **悬浮窗** — 始终置顶的浮动窗口，支持隐身模式（屏幕共享不可见）
- **会议记录** — 双通道录音（系统音频+麦克风），自动生成结构化会议纪要
- **模拟面试** — AI 扮演面试官提问，实时评分（5 维度），生成评估报告
- **历史记录** — 所有对话、会议、面试记录均可查看、复制、导出
- **多 Key 轮换** — 支持配置多个 API Key，遇到限流自动切换
- **资料上传** — 上传 JD 和简历，AI 结合背景信息生成更有针对性的回答
- **两者模式优化** — 详细版和逐字稿同时并行请求，生成中可随时切换查看
- **界面 DIY** — 三种主题风格（深色/深夜/浅色）、8 种预设主题色 + 自定义取色、窗口透明度、背景不透明度，实时预览
- **触摸屏支持** — 完整支持触摸屏滑动和鼠标滚轮滚动
- **首次引导** — 未配置 API Key 时自动弹出引导配置向导
- **检查更新** — 设置页面可一键检查 GitHub 新版本
- **许可证激活** — 支持机器绑定的许可证密钥激活

---

## 快速上手

### 1. 配置 AI 模型

打开「设置」→「AI模型设置」：

- **服务商**：选择 `openai`（兼容 DeepSeek、MiMo、硅基流动、OpenAI、Ollama 等）或 `claude`（Anthropic）
- **API Key**：填入你的 API 密钥
- **Base URL**：第三方中转填写对应地址，官方接口留空
- **模型**：填写模型名称

内置预设（点击即可快速填充）：

| 预设 | 模型 |
|------|------|
| MiMo | `mimo-v2.5` |
| DeepSeek | `deepseek-v4-flash` |
| OpenAI | `gpt-4o` |
| Claude | `claude-sonnet-4-20250514` |
| Ollama | `qwen2.5` |

### 2. 配置语音识别（可选）

「设置」→「语音识别设置」：

- **云端模式**（推荐）：填入 DashScope API Key，识别准确率高
- **本地模式**：默认已内置模型，无需额外配置。也可在设置中切换其他模型或手动指定模型路径

不确定？去「语音测试」页面先试试效果。

### 3. 开始使用

- 在「AI 回答」页面输入面试问题，按回车获取回答
- 按 `1` 开启语音监听，实时转写面试官提问
- 按 `2` 截取屏幕问题，自动识别并回答
- 按 `Ctrl+Shift+O` 打开悬浮窗，面试时扫一眼就能看到答案

---

## 快捷键

| 快捷键 | 功能 |
|--------|------|
| `` ` `` | 显示/隐藏主窗口 |
| `1` | 开始/停止语音录音 |
| `2` | 截图问答 |
| `Space` | 录音中按空格发送当前转写文字 |
| `W` / `S` | 上下滚动回答区域 |
| `Enter` | 发送输入框文字 |
| `Ctrl+Shift+O` | 显示/隐藏悬浮窗 / 切换窗口置顶 |
| `Ctrl+Shift+S` | 开始/停止录音（全局） |
| `Ctrl+Shift+C` | 截图（全局） |

所有快捷键均可在「设置」→「快捷键设置」中自定义。

---

## 支持的 AI 模型

所有兼容 OpenAI Chat Completions 接口的服务均可使用：

| 服务商 | 推荐模型 |
|--------|----------|
| DeepSeek | `deepseek-v4-flash`、`deepseek-reasoner` |
| MiMo | `mimo-v2.5` |
| 硅基流动 | 各类开源模型 |
| OpenAI | `gpt-4o`、`gpt-4-turbo` |
| Anthropic | `claude-sonnet-4-20250514` |
| Ollama | 本地部署的任意模型（如 `qwen2.5`） |

截图问答对支持视觉的模型效果更好：GPT-4o、Claude 3/4、MiMo-V2、Qwen-VL、Gemini 等。应用会自动检测当前模型是否支持图片输入。

---

## 常见问题

**API 报错怎么办？**
检查 API Key 是否正确、Base URL 是否匹配、模型名称是否准确、账户余额是否充足。支持多 Key 轮换，在设置中填入备用 Key（逗号分隔）。

**语音识别不准？**
确保说话清晰、网络稳定（云端模式）。可在「语音测试」页面先测试效果。本地模式可切换更大的模型提升准确率。

**悬浮窗屏幕共享会被看到吗？**
默认开启「隐身模式」，对方看不到。建议正式使用前先和朋友测试确认。

**安装后语音识别不可用？**
内置模型会在首次启动时自动配置。如果未自动生效，可在「设置」→「语音识别设置」中手动点击「下载模型」。

---

## 开发者指南

### 技术栈

| 层 | 技术 |
|----|------|
| 框架 | Electron + electron-vite |
| 前端 | React 18 + TypeScript |
| UI | Ant Design 5（暗色主题） |
| 状态管理 | Zustand |
| AI 接口 | OpenAI SDK + Anthropic SDK |
| 语音识别 | DashScope（云端）/ Sherpa-ONNX（本地，双重验证） |
| OCR | Tesseract.js |
| PDF 解析 | pdf-parse |
| DOCX 解析 | mammoth |

### 项目结构

```
src/
├── main/                          # Electron 主进程
│   ├── index.ts                   # 窗口管理、IPC 注册、全局快捷键
│   ├── machineHash.ts             # 机器码生成（用于许可证）
│   └── services/
│       ├── ai.ts                  # AI 接口服务（OpenAI / Claude）
│       ├── streamingAsr.ts        # 流式语音识别（DashScope WebSocket）
│       ├── vosk.ts                # Sherpa-ONNX 本地语音识别
│       ├── twoPassVosk.ts         # 双重验证识别（在线流式 + 离线修正 + VAD + 热词）
│       ├── whisper.ts             # Whisper 云端语音识别
│       ├── audio.ts               # 音频采集管理
│       ├── ocr.ts                 # Tesseract.js OCR
│       └── sherpaModelManager.ts  # 模型管理（内置模型 + 在线下载 + 镜像加速）
├── preload/
│   └── index.ts                   # 预加载脚本，暴露 window.api
└── renderer/                      # React 前端
    ├── App.tsx                    # 主布局（侧边栏 + 内容区）
    ├── main.tsx                   # React 入口
    ├── components/
    │   ├── AnswerPanel/           # AI 回答主面板
    │   ├── MockInterview/         # 模拟面试（Setup/Interview/Evaluation）
    │   ├── Overlay/               # 悬浮窗
    │   ├── History/               # 历史记录
    │   ├── Settings/              # 设置（含 AppearanceSettings、ShortcutRecorder）
    │   ├── AudioRecorder/         # 语音测试
    │   ├── ScreenCapture/         # 屏幕捕获
    │   ├── SetupWizard/           # 首次引导配置向导
    │   ├── LicenseGate.tsx        # 许可证验证门控
    │   └── Guide/                 # 使用说明
    ├── hooks/
    │   ├── useAI.ts               # AI 生成逻辑、回答模式、Key 轮换
    │   ├── useStreamingAsr.ts     # 流式 ASR 钩子
    │   ├── useMeetingTranscript.ts # 双通道会议记录
    │   ├── useAudio.ts            # 批量语音识别
    │   └── useThemeApply.ts       # 主题应用钩子
    ├── stores/
    │   ├── settingsStore.ts       # 设置（Zustand + persist）
    │   ├── aiStore.ts             # AI 对话状态
    │   ├── historyStore.ts        # 历史记录
    │   ├── mockInterviewStore.ts  # 模拟面试状态
    │   ├── appearanceStore.ts     # 主题/外观配置
    │   └── licenseStore.ts        # 许可证激活状态
    ├── styles/
    │   ├── App.css                # 布局样式
    │   └── global.css             # 全局样式
    ├── types/
    │   └── electron.d.ts          # window.api 类型定义
    └── utils/
        └── crypto.ts              # 许可证密钥验证
scripts/
├── prepare-model.ps1              # 打包前复制模型到 resources/
└── generate-license.js            # 许可证密钥生成工具
```

### 开发环境

```bash
# 安装依赖
npm install

# 启动开发模式
npm run dev

# 构建
npm run build

# 预览构建产物
npm run preview

# 打包安装包（含内置模型）
npm run pack
```

### 打包说明

`npm run pack` 会依次执行：
1. `prepare-model` — 将默认模型复制到 `resources/models/`
2. `build` — 构建前端和主进程
3. `electron-builder --win nsis` — 生成 Windows 安装包

安装包内置中英双语带标点模型，用户安装后首次启动自动复制到 userData 目录，无需网络下载。

### 核心模块说明

**AI 服务 (`src/main/services/ai.ts`)**
封装 OpenAI SDK 和 Anthropic SDK，支持流式输出。DeepSeek 模型自动禁用推理模式。通过 IPC 暴露给渲染进程，支持动态切换 provider。

**语音识别**
- 云端：`streamingAsr.ts` 通过 WebSocket 连接 DashScope 实时语音识别服务
- 本地：`vosk.ts` 调用 Sherpa-ONNX 本地引擎，支持离线识别
- 两套实例分别处理系统音频（面试官）和麦克风（面试者）

**模型管理 (`src/main/services/sherpaModelManager.ts`)**
管理 5 种流式模型 + 1 种离线修正模型 + VAD 模型。支持从安装目录自动复制内置模型（`ensureBundledModel`），在线下载时自动尝试 GitHub 镜像加速。

**预加载脚本 (`src/preload/index.ts`)**
通过 `contextBridge` 暴露 `window.api` 对象，包含 AI、ASR、OCR、屏幕捕获、文件解析等所有主进程功能的调用接口。

### 版本历史

- **v2026.06.12** - 重大更新版本。内置语音识别模型安装即用；修复滚轮卡死、滚动引擎锁死、ASR 文字重复叠加、18 秒延迟等 24 项问题；关闭 DeepSeek 深度思考模式（首字延迟降至 ~1 秒）；逐字稿回答质量优化；新增检查更新、首次引导、配置缺失提示、语音测试模拟发送；界面 DIY（三种主题 + 8 种预设色）；5 种本地模型可选 + 双重验证识别；许可证激活系统
- **v2026.06.11** - 功能优化和 bug 修复
- **v2026.06.10** - 初始版本发布

完整更新日志请查看 [GitHub Releases](https://github.com/ZRegod/FaceTime/releases)

### License

MIT
