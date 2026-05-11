# my_note

## 修改Linux系统语言（适合Ubuntu系）

1. 安装中文语言包

```bash
sudo apt update
sudo apt install language-pack-zh-hans
```

2. 生成中文语言环境
   sudo locale-gen zh_CN.UTF-8

3. 设置系统语言
   sudo update-locale LANG=zh_CN.UTF-8

**查看当前语言设置**
locale

**查看当前语言环境**
echo $LANG

**⭐ 注意：**这只是系统语言环境，主要影响系统工具和部分软件的消息显示。命令行工具的帮助信息和错误提示大多仍是英文

## vim空格缩进设置
```vim
" 在 ~/.vimrc 中添加
set expandtab       " 按Tab键时插入空格
set tabstop=4       " Tab显示为4空格宽度
set shiftwidth=4    " 自动缩进使用4空格
```

## 基本设置

1. 更新系统
   apt update && apt upgrade -y
2. 安装常用工具
   apt install -y vim git curl wget htop net-tools
3. 创建普通用户（推荐）
   adduser ddgmmf
   usermod -aG sudo ddgmmf

## SCP命令使用教程

| 传输方式 | 命令格式（模板）| 实际例子 |
| :------ | :------ | :------ |
| **1. 上传到远程** （本地 -> 远程） | `scp 本地文件 用户名@远程IP:远程路径` | `scp "D:\test" ddgmmf@192.168.1.100:~` |
| **2. 从远程下载** （远程 -> 本地） | `scp 用户名@远程IP:远程文件 本地路径` | `scp ddgmmf@192.168.1.100:~  "D:\test" |
| **3. 远程之间互传**（远程A -> 远程B） | `scp 用户A@IP_A:文件 用户B@IP_B:路径` | `scp ddgmma@10.0.0.1:~ ddgmmb@10.0.0.2:~ |

**注意：**

* `-r`：**递归复制整个目录**（传文件夹必须加）
```bash
scp -r "D:\test" ddgmmf@ddgmm.top:~
```

* `-i`：**指定密钥文件**（如果服务器禁用密码，用密钥登录）
```bash
scp -i 密钥文件路径 ddgmmf@ddgmm.top:~
```

## Linux系统缩放倍数

解决Linux系统（带图形界面）无法调节非整数倍数之外的系统缩放问题：

```bash
# 第一步：确保基础缩放为100%（整数倍）
gsettings set org.gnome.desktop.interface scaling-factor 1
# 第二步：设置文本和界面缩放因子为1.5倍（即150%）
gsettings set org.gnome.desktop.interface text-scaling-factor 1.5
```

查看当前设置：

```bash
# 整体界面缩放倍数
gsettings get org.gnome.desktop.interface scaling-factor
# 获取文字单独缩放倍数
gsettings get org.gnome.desktop.interface text-scaling-factor
```

**原理：**就是打开设置里面的辅助功能的大号文本，默认是1.25倍。用命令可以更精确的控制。

## 安装Glow阅读器

**glow 是一个linux命令行markdown文档阅读器**

```bash
sudo apt update
sudo snap install glow
```

**如果软件源里没有，用这个：**

```bash
# 下载
wget https://github.com/charmbracelet/glow/releases/download/v2.1.1/glow_2.1.1_amd64.deb
# 安装
sudo dpkg -i glow_*.deb
```

## Ubuntu 虚拟机内安装 open-vm-tools（推荐！）

安装 open-vm-tools 及桌面增强包

```bash
sudo apt install open-vm-tools open-vm-tools-desktop
```

>**注意！**
>`open-vm-tools` 提供基本支持
>`open-vm-tools-desktop` 是实现复制粘贴、拖放、自动分辨率的关键，必须装！

`reboot`重启虚拟机

## Linux清理垃圾流程

```bahs
sudo apt clean          # 清下载的包
sudo apt autoclean      # 清旧版本包
sudo apt autoremove     # 删无用依赖
```

## 安装fcitx5输入法

```bash
# 1. 安装fcitx5核心
sudo apt install fcitx5 fcitx5-chinese-addons -y

# 2. 安装配置工具（可选）
sudo apt install fcitx5-configtool -y

# 3. 设置环境变量
echo "export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx" >> ~/.profile

# 4. 立即生效
source ~/.profile
```

注销重新登录后可以使用

## 安装 iFlow CLI 教程

iFlow CLI 是一款直接在终端中运行的强大 AI 助手。它能够无缝分析代码仓库、执行编程任务、理解上下文需求，通过自动化处理从简单的文件操作到复杂的工作流程，全面提升您的工作效率。

[具体流程文档](https://platform.iflow.cn/cli/quickstart)

[Github地址](https://github.com/iflow-ai/iflow-cli)

## 安装Clash.Verge

安装流程如下：

```bash
# 1. 首先更新软件包列表
sudo apt update
# 2. 开始安装
sudo dpkg -i Clash.Verge_2.4.3_amd64.deb
# 3. 如果出现报错,执行如下命令修复所有依赖
sudo apt -f install
```

## Linux安装Emoji字体

```bash
sudo apt install fonts-noto-color-emoji
```

> `Noto Color Emoji` 是 Google 开发的开源彩色 Emoji 字体，支持几乎所有现代 Emoji，而且和 Android/iOS 风格接近

## Linux压缩解压

📦 压缩（打包+压缩）

```bash
tar -czvf 名字.tar.gz 要压缩的文件或文件夹
```

📂 解压（通用 .tar.gz）

```bash
tar -xzvf 文件名.tar.gz
```

**参数介绍：**

* `-c` = create（创建）
* `-z` = 用 gzip 压缩
* `-v` = verbose（显示过程，让你看得爽）
* `-f` = 指定文件名（必须放最后！）

zip格式

```bash
zip -r 压缩名.zip 文件/目录
```

解压zip

```bash
unzip 压缩名.zip
```

## Snap 商店更新失败

在snap软件商店点击更新出现下面提示：

```text
无法安装更新:
(null): cannot refresh "snap-store": snap "snap-store" has running
apps (ubuntu-software), pids: 1897
```

问题本质：Ubuntu 软件商店（snap-store）无法在运行时更新自己。

**解决：**

```bash
sudo pkill -f snap-store
sudo snap refresh snap-store
```

**预防**：以后直接在终端更新所有Snap：

`sudo snap refresh`

## CentOS停更后解决软件更新问题

**第一步，彻底清理所有旧源：**

```bash
# 1. 删除所有 repo 文件（一个不留）
sudo rm -rf /etc/yum.repos.d/*
# 2. 删除所有缓存
sudo rm -rf /var/cache/dnf/*
sudo dnf clean all
```

**第二步，手动创建阿里云存档源：**

```bash
# 直接创建新的 repo 文件
sudo tee /etc/yum.repos.d/aliyun.repo << 'EOF'
[aliyun-base]
name=Aliyun CentOS 8.5.2111 - Base
baseurl=https://mirrors.aliyun.com/centos-vault/8.5.2111/BaseOS/$basearch/os/
gpgcheck=0
enabled=1

[aliyun-appstream]
name=Aliyun CentOS 8.5.2111 - AppStream
baseurl=https://mirrors.aliyun.com/centos-vault/8.5.2111/AppStream/$basearch/os/
gpgcheck=0
enabled=1

[aliyun-extras]
name=Aliyun CentOS 8.5.2111 - Extras
baseurl=https://mirrors.aliyun.com/centos-vault/8.5.2111/extras/$basearch/os/
gpgcheck=0
enabled=1

[aliyun-powertools]
name=Aliyun CentOS 8.5.2111 - PowerTools
baseurl=https://mirrors.aliyun.com/centos-vault/8.5.2111/PowerTools/$basearch/os/
gpgcheck=0
enabled=1
EOF
```

**第三步，生成缓存并测试：**

```bash
# 1. 生成新缓存
sudo dnf makecache
# 2. 测试更新
sudo dnf update -y
```

## 将普通用户加入sudo组

**Ubuntu/Debian：**

```bash
# 切换到root
su -
# 把用户加入sudo组
usermod -aG sudo ddgmmc
# 验证
groups ddgmmc  # 应该能看到 sudo
```

**CentOS/RHEL：**

```bash
# 切换到root
su -
# 把用户加入wheel组（CentOS的sudo组叫wheel）
usermod -aG wheel ddgmmc
# 验证
groups ddgmmc  # 应该能看到 wheel
```

**测试一下：**`sudo whoami`

## 火狐浏览器设置中文问题

添加语言包时出现了这样的提示：
`Firefox can't update your languages right now. Check that you are connected to the internet or try again.`

可能是连不上火狐的语言包下载服务器

**解决方案：**

1. 如果是**Ubuntu / Debian：**

 ```bash
 sudo apt update
 sudo apt install firefox-locale-zh-hans
 ```

2. 如果是**CentOS / RHEL / Fedora：**

```bash
# CentOS/RHEL 8 及更早版本
sudo dnf install firefox-l10n-zh-CN

# CentOS/RHEL 7 或更早版本
sudo yum install firefox-i18n-zh-CN
```
