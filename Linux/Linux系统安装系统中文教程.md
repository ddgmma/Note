## ✅ 一、Debian 系（Ubuntu / Debian）
步骤：
```bash
# 1. 更新软件源
sudo apt update

# 2. 安装简体中文语言包（核心）
sudo apt install -y language-pack-zh-hans

# （可选）安装 GNOME 桌面完整中文支持（桌面用户建议加装）
sudo apt install -y language-pack-gnome-zh-hans

# 3. 设置系统默认语言为中文
echo 'LANG="zh_CN.UTF-8"' | sudo tee /etc/default/locale

# 4. 重启生效
sudo reboot
```
## ✅ 二、CentOS 系（CentOS 7/8、RHEL、Rocky、AlmaLinux）
步骤：
```bash
# 1. 安装中文语言支持包（glibc-langpack-zh 包含 zh_CN.UTF-8 locale）
sudo dnf install -y glibc-langpack-zh    # CentOS 8+ / RHEL 8+ / Rocky / Alma

sudo yum install -y glibc-common glibc-langpack-zh    # CentOS 7

# 2. 设置系统默认语言为中文
sudo localectl set-locale LANG=zh_CN.UTF-8

# 3. 验证配置（无需重启，立即生效）
localectl status
```

## Ubuntu安装中文输入法（建议22版本以下）
1. 安装输入法框架 Fcitx + Rime（中州韵）：

```bash
sudo apt update
sudo apt install -y fcitx fcitx-rime
```
2. 设置系统用 Fcitx：

```bash
im-config -n fcitx
```
3. 重启或注销后生效
