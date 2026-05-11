# DOS常用命令

## 一、目录和文件操作

**提示：**只掌握最常用的几个就行，其他的只做了解。

### 目录操作

| 命令           | 说明         | 示例                                |
| :------------- | :----------- | :---------------------------------- |
| `dir`          | 显示目录内容 | `dir` `dir /w` `dir /p`             |
| `cd`           | 改变当前目录 | `cd folder` `cd ..` `cd \`          |
| `md` / `mkdir` | 创建目录     | `md newfolder` `mkdir "new folder"` |
| `rd` / `rmdir` | 删除目录     | `rd oldfolder` `rmdir /s folder`    |
| `tree`         | 显示目录树   | `tree` `tree /f`                    |
| `cls`          | 清屏         | `cls`                               |

### 文件操作

| 命令             | 说明              | 示例                       |
| :--------------- | :---------------- | :------------------------- |
| `echo`           | 创建文件（创建空文件用`tpye nul > 文件`） | `echo hello > ok.txt` |
| `copy`           | 复制文件          | `copy file1.txt file2.txt` |
| `xcopy`          | 复制目录和文件    | `xcopy source dest /s /e`  |
| `move`           | 移动文件/重命名   | `move old.txt new.txt`     |
| `del` / `erase`  | 删除文件          | `del file.txt` `del *.tmp` |
| `ren` / `rename` | 重命名文件        | `ren old.txt new.txt`      |
| `type`           | 显示文件内容      | `type config.ini`          |
| `more`           | 分页显示文件      | `type long.txt | more`     |
| `attrib`         | 显示/修改文件属性 | `attrib +r file.txt`       |

## 二、磁盘操作

| 命令       | 说明              | 示例              |
| :--------- | :---------------- | :---------------- |
| `format`   | 格式化磁盘        | `format C: /q`    |
| `chkdsk`   | 检查磁盘          | `chkdsk C: /f`    |
| `diskpart` | 磁盘分区管理      | `diskpart`        |
| `vol`      | 显示磁盘卷标      | `vol C:`          |
| `label`    | 创建/修改磁盘卷标 | `label C: System` |

## 三、系统信息和管理

### 系统信息

| 命令         | 说明             | 示例             |
| :----------- | :--------------- | :--------------- |
| `ver`        | 显示系统版本     | `ver`            |
| `systeminfo` | 显示系统详细信息 | `systeminfo`     |
| `hostname`   | 显示计算机名     | `hostname`       |
| `date`       | 显示/设置日期    | `date` `date /t` |
| `time`       | 显示/设置时间    | `time` `time /t` |

### 进程和任务

| 命令       | 说明         | 示例                          |
| :--------- | :----------- | :---------------------------- |
| `tasklist` | 显示进程列表 | `tasklist` `tasklist /v`      |
| `taskkill` | 结束进程     | `taskkill /im notepad.exe`    |
| `schtasks` | 计划任务管理 | `schtasks /create /tn backup` |

### 网络相关

| 命令                 | 说明         | 示例                                            |
| :------------------- | :----------- | :---------------------------------------------- |
| `ipconfig`           | 显示IP配置   | `ipconfig` `ipconfig /all`（可以查本机Mac地址） |
| `ping`               | 测试网络连接 | `ping google.com`                               |
| `netstat`            | 显示网络状态 | `netstat -an`                                   |
| `tracert`            | 路由追踪     | `tracert google.com`                            |
| `nslookup`           | DNS查询      | `nslookup google.com`                           |
| `arp -d`             | 清除ARP缓存  |                                                 |
| `ipconfig /flushdns` | 清除DNS缓存  |                                                 |

## 四、用户和权限

| 命令             | 说明           | 示例                             |
| :--------------- | :------------- | :------------------------------- |
| `whoami`         | 显示当前用户   | `whoami`                         |
| `net user`       | 用户管理       | `net user` `net user admin pass` |
| `net localgroup` | 本地组管理     | `net localgroup administrators`  |
| `runas`          | 以其他用户运行 | `runas /user:admin cmd`          |

## 五、批处理和脚本

| 命令         | 说明         | 示例                  |
| :----------- | :----------- | :-------------------- |
| `echo`       | 显示消息     | `echo Hello World`    |
| `set`        | 设置环境变量 | `set PATH=C:\Windows` |
| `cls`        | 清屏         | `cls`                 |
| `pause`      | 暂停执行     | `pause`               |
| `rem` / `::` | 注释         | `rem 这是注释`        |
| `call`       | 调用批处理   | `call other.bat`      |
| `start`      | 启动程序     | `start notepad.exe`   |
| `exit`       | 退出命令行   | `exit`                |

## 六、实用工具命令

| 命令       | 说明       | 示例                          |
| :--------- | :--------- | :---------------------------- |
| `fsquirt`  | 蓝牙传输   |                               |
| `find`     | 查找文本   | `find "error" log.txt`        |
| `findstr`  | 查找字符串 | `findstr "ERROR|WARN" *.log`  |
| `fc`       | 比较文件   | `fc file1.txt file2.txt`      |
| `sort`     | 排序输出   | `dir | sort`                  |
| `shutdown` | 关机/重启  | `shutdown /s /t 0`            |
| `reg`      | 注册表操作 | `reg query HKLM\Software`     |
| `sc`       | 服务控制   | `sc query` `sc start service` |

## 七、帮助和参数

| 命令         | 说明         | 示例               |
| :----------- | :----------- | :----------------- |
| `help`       | 显示帮助列表 | `help`             |
| `command /?` | 命令帮助     | `dir /?` `copy /?` |
| `/?`         | 通用帮助     | `xcopy /?`         |

## 八、常用快捷键

| 快捷键    | 功能       | 说明                    |
| :-------- | :--------- | :---------------------- |
| `↑` / `↓` | 历史命令   | 浏览之前输入的命令      |
| `Tab`     | 自动补全   | 补全文件名/目录名       |
| `Ctrl+C`  | 终止命令   | 停止当前执行的命令      |
| `F7`      | 命令历史   | 显示命令历史列表        |
| `Ctrl+Z`  | 文件结束符 | 结束输入 (在有些命令中) |

## 九、注意事项

1. **区分大小写**：DOS命令不区分大小写
2. **路径分隔符**：使用反斜杠 `\`，也可用正斜杠 `/`
3. **通配符**：`*` 匹配多个字符，`?` 匹配单个字符
4. **管理员权限**：某些命令需要管理员权限
5. **长文件名**：含空格的文件名需用引号括起来