# 🦞 OpenClaw 常用命令速查手册

OpenClaw 的命令主要分为终端命令（在电脑终端使用）和对话命令（在聊天框中直接发送）。

## 🚀 安装与环境

先确保电脑安装了Node.js22+

 **更推荐安装官网方式：**https://openclaws.io/zh/

先设置国内镜像加速下载：`npm config set registry https://registry.npmmirror.com`

下载官网英文版：`npm i -g openclaw`

**或者新手方式：**

 `powershell -c "irm https://openclaw.ai/install.ps1 | iex"`  一行搞定，推荐新手 

---

**下载社区中文版：**`iwr -useb https://clawd.org.cn/install.ps1 | iex`

 `iwr -useb httpsopenclaw.aiinstall.ps1  iex`  一键安装 (Windows)，需管理员身份运行PowerShell 
 `openclaw --version` 或 `-v`  查看已安装的版本号 
 `openclaw update`  将 OpenClaw 更新到最新版本 

---

**安装完成后可以在运行状态下打开控制面板：**

```
http://127.0.0.1:18789
```


## ⚙️ 配置与服务管理
 命令  说明 
---  ---
 `openclaw onboard`  交互式配置向导，强烈推荐，会一步步引导你完成模型、网关等关键设置 
 `openclaw configure`  手动调出配置向导，用于修改之前的设置 
 `openclaw doctor`  配置修复利器，当出现奇怪问题时，用它来诊断并修复 
 `openclaw doctor --fix`  运行自动修复，如果有小问题，它通常会帮你搞定 
 `openclaw gateway start`  以后台服务模式启动网关，适合长期使用 
 `openclaw gateway restart`  重启网关服务，修改配置后常用 
 `openclaw gateway status`  查看网关的运行状态和端口信息 


## 🚦 状态与诊断
 命令  说明 
---  ---
 `openclaw status`  常用命令，查看总体运行状态，包括网关和通道健康度 
 `openclaw status --deep`  深度诊断，会执行实时检查来探测通道状态 
 `openclaw status --usage`  专门查看 API 的 Token 用量和配额 
 `openclaw channels list`  列出所有已配置的聊天渠道（如微信、钉钉） 
 `openclaw channels status`  查看各渠道的连接状态是否正常 
 `openclaw models list`  列出所有已配置的 AI 模型 
 `openclaw models status`  检查 API 提供商和模型是否可用 


## 🎮 日常交互与对话
 命令  说明 

---

 `openclaw tui`  在终端里直接与 AI 进行文本对话 
 `openclaw dashboard`  在浏览器中打开图形化控制面板 
 `new`  对话命令，在聊天中发送，用于开启一个全新的干净会话 
 `reset`  对话命令，重置当前对话的短期记忆，但保留个人偏好 
 `status`  对话命令，快速查看当前会话的状态和模型信息 
 `model [模型名]`  对话命令，例如 `model gpt-4`，动态切换当前使用的AI模型 


## 🔌 技能 (Skills) 管理
 命令  说明 
---  ---
 `openclaw skills list`  列出当前已安装的所有技能 
 `openclaw skill install 技能名`  从官方市场安装新技能（例如 `openclaw skill install email-sender`） 
 `openclaw skill uninstall 技能名`  卸载不再需要的技能 


### 💡 使用提示
遇到问题先别急，可以试试这条黄金命令：`openclaw doctor --fix`，很多常见问题它都能自动帮你修复！

### 日常场景总结

| 你想干嘛                 | 用什么                             |
| ------------------------ | ---------------------------------- |
| 在终端里跟我聊天         | `openclaw tui`                     |
| 启动后台服务（给我上线） | `openclaw gateway start`           |
| 关掉我                   | `openclaw gateway stop`            |
| 看看我还在不在           | `openclaw status`                  |
| 在浏览器里用控制面板     | 直接打开 `http://127.0.0.1:18789/` |

### 网关操作

```powershell
# 启动网关
openclaw gateway run 
# 打开控制面板
openclaw dashboard
# 关闭网关
openclaw gateway stop
# 重启网关
openclaw gateway start
```

## 🦞 Gateway 常用命令

### 安装与管理

|             命令             |       作用       |
| :--------------------------: | :--------------: |
|  `openclaw gateway install`  | 安装后台网关服务 |
| `openclaw gateway uninstall` | 卸载后台网关服务 |
|  `openclaw gateway status`   | 查看网关运行状态 |

### 启动与停止

|            命令            |     作用     |
| :------------------------: | :----------: |
|  `openclaw gateway start`  | 启动网关服务 |
|  `openclaw gateway stop`   | 停止网关服务 |
| `openclaw gateway restart` | 重启网关服务 |

### 诊断

|          命令           |            作用            |
| :---------------------: | :------------------------: |
|    `openclaw doctor`    | 检查所有组件状态（含网关） |
| `openclaw doctor --fix` |    自动修复检测到的问题    |