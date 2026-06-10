# FaceTime - AI 面试实时助手

> 面试场景下的 AI 实时应答工具，支持语音识别、截图问答、悬浮窗、会议记录和模拟面试。

## 核心功能

- **AI 实时回答** — 输入问题或语音转写，AI 以第一人称给出可直接参考的回答
- **四种回答模式** — 详细版（深度回答）、逐字稿（口语化可念）、速答（快速反应）、两者（详细+逐字稿）
- **语音识别** — 支持 DashScope 云端识别和 Vosk 本地识别，实时转写面试问题
- **截图问答** — 一键截取屏幕题目，支持视觉模型直传图片或本地 OCR 兜底
- **悬浮窗** — 始终置顶的浮动窗口，支持隐身模式（屏幕共享不可见）
- **会议记录** — 双通道录音（系统音频+麦克风），自动生成结构化会议纪要
- **模拟面试** — AI 扮演面试官提问，实时评分（5 维度），生成评估报告
- **历史记录** — 所有对话、会议、面试记录均可查看、复制、导出
- **多 Key 轮换** — 支持配置多个 API Key，遇到限流自动切换
- **资料上传** — 上传 JD 和简历，AI 结合背景信息生成更有针对性的回答

---

## 快速上手

### 1. 配置 AI 模型

打开「设置」→「AI模型设置」：

- **服务商**：选择 `openai`（兼容 DeepSeek、MiMo、硅基流动、OpenAI、Ollama 等）或 `claude`（Anthropic）
- **API Key**：填入你的 API 密钥
- **Base URL**：第三方中转填写对应地址，官方接口留空
- **模型**：填写模型名称，如 `deepseek-chat`、`gpt-4o`、`mimo-v2`

内置预设：MiMo、DeepSeek、OpenAI、Claude、Ollama，点击即可快速填充配置。

### 2. 配置语音识别（可选）

「设置」→「语音识别设置」：

- **云端模式**（推荐）：填入 DashScope API Key，识别准确率高
- **本地模式**：填入 Vosk 模型路径，完全离线，无需网络

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
| `1` | 开始/停止语音录音 |
| `2` | 截图问答 |
| `Space` | 录音中按空格发送当前转写文字 |
| `W` / `S` | 上下滚动回答区域 |
| `Enter` | 发送输入框文字 |
| `Ctrl+Shift+O` | 显示/隐藏悬浮窗 |
| `Ctrl+Shift+S` | 开始/停止录音（全局） |
| `Ctrl+Shift+C` | 截图（全局） |

---

## 支持的 AI 模型

所有兼容 OpenAI Chat Completions 接口的服务均可使用：

| 服务商 | 推荐模型 |
|--------|----------|
| DeepSeek | `deepseek-chat`、`deepseek-reasoner` |
| MiMo | `mimo-v2`、`mimo-v3` |
| 硅基流动 | 各类开源模型 |
| OpenAI | `gpt-4o`、`gpt-4-turbo` |
| Anthropic | `claude-sonnet-4-6`、`claude-opus-4-7` |
| Ollama | 本地部署的任意模型 |

截图问答对支持视觉的模型效果更好：GPT-4o、Claude 3/4、MiMo-V2、Qwen-VL、Gemini 等。

---

## 常见问题

**API 报错怎么办？**
检查 API Key 是否正确、Base URL 是否匹配、模型名称是否准确、账户余额是否充足。支持多 Key 轮换，在设置中填入备用 Key（逗号分隔）。

**语音识别不准？**
确保说话清晰、网络稳定（云端模式）。可在「语音测试」页面先测试效果。本地模式可下载更大的 Vosk 模型提升准确率。

**悬浮窗屏幕共享会被看到吗？**
默认开启「隐身模式」，对方看不到。建议正式使用前先和朋友测试确认。

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
| 语音识别 | DashScope（云端）/ Vosk（本地） |
| OCR | Tesseract.js |
| PDF 解析 | pdf-parse |
| DOCX 解析 | mammoth |

### 项目结构

```
src/
├── main/                        # Electron 主进程
│   ├── index.ts                 # 窗口管理、IPC 注册、全局快捷键
│   └── services/
│       ├── ai.ts                # AI 接口服务（OpenAI / Claude）
│       ├── streamingAsr.ts      # 流式语音识别（DashScope WebSocket）
│       ├── vosk.ts              # Vosk 本地语音识别
│       ├── voskModelManager.ts  # Vosk 模型管理
│       └── ocr.ts               # Tesseract.js OCR
├── preload/
│   └── index.ts                 # 预加载脚本，暴露 window.api
└── renderer/                    # React 前端
    ├── App.tsx                  # 主布局（侧边栏 + 内容区）
    ├── main.tsx                 # React 入口
    ├── components/
    │   ├── AnswerPanel/         # AI 回答主面板
    │   ├── MockInterview/       # 模拟面试（Setup/Interview/Evaluation）
    │   ├── Overlay/             # 悬浮窗
    │   ├── History/             # 历史记录
    │   ├── Settings/            # 设置
    │   ├── AudioRecorder/       # 语音测试
    │   ├── ScreenCapture/       # 屏幕捕获
    │   └── Guide/               # 使用说明
    ├── hooks/
    │   ├── useAI.ts             # AI 生成逻辑、回答模式、Key 轮换
    │   ├── useStreamingAsr.ts   # 流式 ASR 钩子
    │   ├── useMeetingTranscript.ts  # 双通道会议记录
    │   └── useAudio.ts         # 批量语音识别（Whisper）
    ├── stores/
    │   ├── settingsStore.ts     # 设置（Zustand + persist）
    │   ├── aiStore.ts           # AI 对话状态
    │   ├── historyStore.ts      # 历史记录
    │   └── mockInterviewStore.ts # 模拟面试状态
    ├── styles/
    │   ├── App.css              # 布局样式
    │   └── global.css           # 全局样式
    └── types/
        └── electron.d.ts        # window.api 类型定义
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
```

### 核心模块说明

**AI 服务 (`src/main/services/ai.ts`)**
封装 OpenAI SDK 和 Anthropic SDK，支持流式输出。通过 IPC 暴露给渲染进程，支持动态切换 provider。

**语音识别**
- 云端：`streamingAsr.ts` 通过 WebSocket 连接 DashScope 实时语音识别服务
- 本地：`vosk.ts` 调用 Vosk 本地引擎，支持离线识别
- 两套实例分别处理系统音频（面试官）和麦克风（面试者）

**预加载脚本 (`src/preload/index.ts`)**
通过 `contextBridge` 暴露 `window.api` 对象，包含 AI、ASR、OCR、屏幕捕获、文件解析等所有主进程功能的调用接口。

### License

MIT
