# Claude Code 配置说明

## 一、模型等级（Opus / Sonnet / Haiku）

Anthropic 对模型能力的分级命名，灵感来自诗歌体裁。

| 等级 | 英文 | 含义 | 特点 |
|------|------|------|------|
| 🏆 **Opus** | 大作 | 最强模型 | 推理能力最强，适合复杂任务，成本最高 |
| 🥈 **Sonnet** | 十四行诗 | 中等模型 | 平衡速度与质量，日常开发最常用 |
| 🥉 **Haiku** | 俳句 | 轻量模型 | 最快最便宜，适合简单任务和子任务 |

### 在 Claude Code 中的作用

Claude Code 会根据任务复杂程度自动选择不同级别的模型：

- **主对话** → 使用 `ANTHROPIC_MODEL` 指定的模型
- **子 agent 任务**（后台自动处理的小任务）→ 使用 `CLAUDE_CODE_SUBAGENT_MODEL` 指定的模型
- 不同级别的任务可分别指定不同模型，实现 **重活累活用好模型，跑腿杂活用轻量模型**

---

## 二、推理努力程度（Effort Level）

控制 Claude Code 在回答问题时的思考深度和时间投入。

| 等级 | 含义 | 适用场景 |
|------|------|----------|
| 🟢 **low** | 最低推理，快速响应 | 简单问答、快速修复小 bug |
| 🟡 **medium** | 中等推理 | 日常编码任务，平衡速度和质量 |
| 🟠 **high** | 较高推理 | 复杂逻辑、需要深入分析的问题 |
| 🔴 **xhigh** | 非常高推理 | 非常复杂的架构设计、大规模重构 |
| 🟣 **max** | 最高推理（全力） | 最困难的问题，愿意多花时间换取最佳方案 |

> 等级越高，Claude 会花更多时间"思考"，答案质量通常更高，但响应速度变慢、消耗的 token 也更多。

---

## 三、环境变量说明（DeepSeek 接入）

以下是在 Windows PowerShell 中配置 Claude Code 使用 DeepSeek 接口的环境变量。

```powershell
# DeepSeek 兼容 Anthropic API 的地址（固定不变）
$env:ANTHROPIC_BASE_URL="https://api.deepseek.com/anthropic"

# 你的 DeepSeek API Key（从 https://platform.deepseek.com/api_keys 获取）
$env:ANTHROPIC_AUTH_TOKEN="sk-你的Key"

# 主对话使用的模型
$env:ANTHROPIC_MODEL="deepseek-v4-flash"

# Opus 级别任务使用的模型
$env:ANTHROPIC_DEFAULT_OPUS_MODEL="deepseek-v4-pro"

# Sonnet 级别任务使用的模型
$env:ANTHROPIC_DEFAULT_SONNET_MODEL="deepseek-v4-pro"

# Haiku 级别任务使用的模型（flash 速度更快、成本更低）
$env:ANTHROPIC_DEFAULT_HAIKU_MODEL="deepseek-v4-flash"

# 子 agent（后台任务）使用的模型
$env:CLAUDE_CODE_SUBAGENT_MODEL="deepseek-v4-flash"

# 推理努力程度（low/medium/high/xhigh/max）
$env:CLAUDE_CODE_EFFORT_LEVEL="max"
```

### 推荐搭配

| 环境变量 | DeepSeek 模型 | 角色 |
|----------|-------------|------|
| `ANTHROPIC_MODEL` | `deepseek-v4-pro` | 主对话主力模型 |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | `deepseek-v4-flash` | 简单任务加速省钱 |
| `CLAUDE_CODE_SUBAGENT_MODEL` | `deepseek-v4-flash` | 后台子任务 |

---

## 四、快速启动脚本

创建 `start-deepseek.ps1` 文件，每次运行即可自动配置并启动：

```powershell
# Claude Code + DeepSeek 启动脚本
$env:ANTHROPIC_BASE_URL="https://api.deepseek.com/anthropic"
$env:ANTHROPIC_AUTH_TOKEN="sk-你的Key"
$env:ANTHROPIC_MODEL="deepseek-v4-flash"
$env:ANTHROPIC_DEFAULT_OPUS_MODEL="deepseek-v4-pro"
$env:ANTHROPIC_DEFAULT_SONNET_MODEL="deepseek-v4-pro"
$env:ANTHROPIC_DEFAULT_HAIKU_MODEL="deepseek-v4-flash"
$env:CLAUDE_CODE_SUBAGENT_MODEL="deepseek-v4-flash"
$env:CLAUDE_CODE_EFFORT_LEVEL="max"

Write-Host "环境变量已设置，正在启动 Claude Code..." -ForegroundColor Green
claude
```

使用方法：

```powershell
cd 你的项目目录
.\start-deepseek.ps1
```

---

## 五、参考链接

- [DeepSeek API 文档 - Claude Code 集成](https://api-docs.deepseek.com/zh-cn/quick_start/agent_integrations/claude_code)
- [DeepSeek Platform (获取 API Key)](https://platform.deepseek.com/api_keys)
- [Node.js 官网](https://nodejs.org/)
