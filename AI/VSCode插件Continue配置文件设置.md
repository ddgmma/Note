## 🌟 推荐配置

```yaml
name: Local Config
version: 1.0.0
schema: v1

models:
  - name: DeepSeek V4 Flash
    provider: deepseek
    model: deepseek-v4-flash
    apiKey: YOUR_DEEPSEEK_API_KEY    # 在这里填入你的 API Key
    roles:
      - chat
      - edit
      - apply
    capabilities:
      - tool_use                    # 开启 Agent 模式所需的工具调用能力
    defaultCompletionOptions:
      maxTokens: 4096               # 最大输出 token 数
      temperature: 0.0              # 代码场景推荐 0.0，更精确
      topP: 0.95
    requestOptions:
      timeout: 60000                # 请求超时时间（毫秒）

  - name: DeepSeek V4 Pro
    provider: deepseek
    model: deepseek-v4-pro
    apiKey: YOUR_DEEPSEEK_API_KEY
    roles:
      - chat
      - edit
      - apply
    capabilities:
      - tool_use
    defaultCompletionOptions:
      maxTokens: 8192
      temperature: 0.0
      topP: 0.95
      reasoning: true               # 开启 DeepSeek 的思考/推理模式
    requestOptions:
      timeout: 120000               # Pro 模型思考模式耗时更长，超时设长一些
```

---

## 📋 配置说明

根据 DeepSeek API 文档：

| 参数 | 当前可用的值 |
|------|------------|
| **base_url** | `https://api.deepseek.com`（OpenAI 兼容格式） |
| **model (推荐)** | `deepseek-v4-flash`（快速、便宜）或 `deepseek-v4-pro`（更强、支持思考） |
| **model (将弃用)** | ~~`deepseek-chat`~~ → 对应 `deepseek-v4-flash` |
| | ~~`deepseek-reasoner`~~ → 对应 `deepseek-v4-pro` + thinking |

> ⚠️ **注意**：`deepseek-chat` 和 `deepseek-reasoner` 将在 **2026/07/24 弃用**，请尽快迁移到新模型名。

## 🔑 关键配置要点

| 选项 | 推荐值 | 说明 |
|------|--------|------|
| `provider` | `deepseek` | Continue 原生支持，不需额外设置 `apiBase` |
| `capabilities` | `tool_use` | 让 DeepSeek 在 **Agent 模式** 下能调用工具/函数 |
| `temperature` | `0.0` | 代码补全和编辑场景下推荐最低值，输出更稳定 |
| `reasoning` | `true` | 仅对 `deepseek-v4-pro` 有效，开启深度思考能力 |
| `roles` | `chat, edit, apply` | Continue 的三大核心场景 |

如果你还需要 **Tab 自动补全（Autocomplete）** 功能，可以再加一个轻量级配置（但 DeepSeek 目前没有专门的 FIM 补全模型对外提供，所以 autocomplete 暂不推荐用 DeepSeek）。

快去 [DeepSeek Platform](https://platform.deepseek.com/api_keys) 申请 API Key 填进去就可以用了！🚀