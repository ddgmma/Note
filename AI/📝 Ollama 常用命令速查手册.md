# 📝 Ollama 常用命令速查手册

> 适用于 Windows / macOS / Linux  
> 默认 API 地址：`http://localhost:11434`

---

## 1. 模型管理

| 命令                          | 说明                               | 示例                                |
| ----------------------------- | ---------------------------------- | ----------------------------------- |
| `ollama pull <模型>`          | 下载模型（支持 `:tag` 指定版本）   | `ollama pull qwen3:8b`              |
| `ollama list`                 | 查看已安装的本地模型               | `ollama list`                       |
| `ollama show <模型>`          | 查看模型详细信息（参数量、模板等） | `ollama show qwen3:8b`              |
| `ollama cp <源模型> <新名称>` | 复制/重命名模型                    | `ollama cp qwen3:8b my-qwen:latest` |
| `ollama rm <模型>`            | 删除本地模型                       | `ollama rm qwen3:8b`                |

---

## 2. 运行与对话

| 命令                            | 说明               | 示例                                 |
| ------------------------------- | ------------------ | ------------------------------------ |
| `ollama run <模型>`             | 进入交互式对话模式 | `ollama run qwen3:8b`                |
| `ollama run <模型> "提示词"`    | 单次提问（非交互） | `ollama run qwen3:8b "什么是递归？"` |
| `ollama run <模型> < input.txt` | 从文件读取输入     | `ollama run qwen3:8b < prompt.txt`   |

> 在交互模式下，可使用以下命令：  
> - `/bye` – 退出  
> - `/show` – 显示当前模型信息  
> - `/load <模型>` – 切换到另一个已安装模型  
> - `/save <名称>` – 保存当前会话  
> - `/clear` – 清空上下文

---

## 3. 服务控制

| 命令           | 说明                                         |
| -------------- | -------------------------------------------- |
| `ollama serve` | 启动 Ollama 后台服务（Windows 通常自动启动） |
| `ollama stop`  | 停止当前正在运行的模型（释放显存）           |
| `ollama ps`    | 查看当前正在运行的模型列表及资源占用         |

---

## 4. 模型文件与自定义

| 命令                                  | 说明                              |
| ------------------------------------- | --------------------------------- |
| `ollama create <名称> -f <Modelfile>` | 根据 Modelfile 创建自定义模型     |
| `ollama show --modelfile <模型>`      | 输出某个模型对应的 Modelfile 内容 |

**Modelfile 简单示例**（可保存为 `myqwen.Modelfile`）：
```dockerfile
FROM qwen3:8b
SYSTEM "你是一个精通 Python 和 C++ 的编程助手。"
PARAMETER temperature 0.3
```
然后执行：
```bash
ollama create my-custom-qwen -f myqwen.Modelfile
ollama run my-custom-qwen
```

---

## 5. 其他实用命令

| 命令                              | 说明                                         |
| --------------------------------- | -------------------------------------------- |
| `ollama -v` 或 `ollama --version` | 查看 Ollama 版本                             |
| `ollama help`                     | 查看所有命令列表                             |
| `set OLLAMA_HOST=0.0.0.0`         | 允许局域网内其他设备访问（Windows 环境变量） |
| `set OLLAMA_NUM_PARALLEL=2`       | 设置并行处理数量                             |

---

## 6. 快速对照（按你的场景）

适合你当前配置（`RTX 3060 6G` + `32G`）的日常操作：

```bash
# 开机后确认服务在运行
ollama ps

# 下载推荐模型
ollama pull qwen3:8b

# 快速测试
ollama run qwen3:8b "用 Python 写一个二分查找"

# 用完想释放显存
ollama stop

# 查看本地所有模型
ollama list
```

---

这份笔记你可以直接复制粘贴到 Obsidian、Notion 或任何 Markdown 编辑器中长期保存。如果以后下载了新模型或遇到问题，随时回来查就好。