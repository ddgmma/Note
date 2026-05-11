# Linux 常用命令笔记

## 文件操作
| 命令 | 说明 | 示例 |
| :--- | :--- | :--- |
| `ls -la` | 列出所有文件（含隐藏文件） | `ls -la /home` |
| `cd /path` | 切换目录 | `cd /var/log` |
| `pwd` | 显示当前目录 | `pwd` |
| `cp file1 file2` | 复制文件 | `cp source.txt backup.txt` |
| `mv file1 file2` | 移动/重命名文件 | `mv old.txt new.txt` |
| `rm file` | 删除文件 | `rm temp.txt` |
| `mkdir dir` | 创建目录 | `mkdir new_folder` |
| `rmdir dir` | 删除空目录 | `rmdir empty_dir` |

## 文件查看编辑
| 命令 | 说明 | 常用选项 |
| :--- | :--- | :--- |
| `cat file` | 查看文件内容 | `-n` 显示行号 |
| `head -n 10 file` | 查看文件前10行 | `-n` 指定行数 |
| `tail -f file` | 实时查看文件变化 | `-f` 跟踪文件 |
| `vim file` | 编辑文件 | 模式：`i`插入，`:wq`保存退出 |
| `less file` | 分页查看文件 | `/text` 搜索，`q`退出 |

## 权限管理
| 命令 | 说明 | 权限说明 |
| :--- | :--- | :--- |
| `chmod 755 file` | 修改文件权限 | 755 = rwxr-xr-x |
| `chown user:group file` | 修改文件所有者 | `user:group` |
| `sudo command` | 以root权限执行命令 | 需要sudo权限 |

## 系统信息
| 命令 | 说明 | 常用选项 |
| :--- | :--- | :--- |
| `ps aux` | 查看所有进程 | `aux` 显示详细信息 |
| `top` | 实时系统监控 | 交互式界面 |
| `df -h` | 查看磁盘空间 | `-h` 人类可读格式 |
| `free -h` | 查看内存使用 | `-h` 人类可读格式 |
| `uname -a` | 查看系统信息 | 内核版本等 |

## 网络相关
| 命令 | 说明 | 示例 |
| :--- | :--- | :--- |
| `ping host` | 测试网络连接 | `ping 8.8.8.8` |
| `ifconfig` | 查看网络接口 | 显示IP地址等 |
| `netstat -tulpn` | 查看网络连接和端口 | `-t`TCP, `-u`UDP, `-l`监听 |
| `ssh user@host` | 远程连接 | `ssh root@192.168.1.1` |
| `scp file user@host:path` | 安全复制文件 | `scp file.txt user@host:/tmp/` |

## 包管理 (RedHat/CentOS)
| 命令 | 说明 | 注意 |
| :--- | :--- | :--- |
| `yum install package` | 安装软件包 | 需要root权限 |
| `yum remove package` | 卸载软件包 | `-y` 自动确认 |
| `yum update` | 更新所有软件包 | 更新系统 |

## 查找搜索
| 命令 | 说明 | 示例 |
| :--- | :--- | :--- |
| `find /path -name "*.txt"` | 查找文件 | `find /home -name "*.log"` |
| `grep "text" file` | 在文件中搜索文本 | `-i`忽略大小写，`-r`递归 |
| `which command` | 查找命令路径 | `which python` |

## 压缩解压
| 命令 | 说明 | 常用选项 |
| :--- | :--- | :--- |
| `tar -czf archive.tar.gz dir` | 压缩目录 | `-c`创建，`-z`gzip，`-f`文件 |
| `tar -xzf archive.tar.gz` | 解压文件 | `-x`解压 |
| `zip file.zip file` | 创建zip压缩包 | 压缩单个文件 |
| `unzip file.zip` | 解压zip文件 | `-d`指定目录 |

## 进程管理
| 命令 | 说明 | 注意 |
| :--- | :--- | :--- |
| `kill PID` | 结束进程 | 发送TERM信号 |
| `kill -9 PID` | 强制结束进程 | 发送KILL信号 |
| `pkill name` | 按进程名结束 | `pkill firefox` |
| `bg` | 后台运行进程 | 将挂起的进程放到后台 |
| `fg` | 前台恢复进程 | 将后台进程调到前台 |

## 系统管理
| 命令 | 说明 | 注意 |
| :--- | :--- | :--- |
| `reboot` | 重启系统 | 需要root权限 |
| `shutdown -h now` | 立即关机 | `-h`停机，`-r`重启 |
| `systemctl start service` | 启动服务 | `systemctl start nginx` |
| `systemctl stop service` | 停止服务 | `systemctl stop sshd` |
| `journalctl -xe` | 查看系统日志 | `-f`跟踪日志 |

x
