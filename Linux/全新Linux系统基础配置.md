# 全新Linux系统基础配置

## 1. 更新系统

apt update && apt upgrade -y

## 2. 安装开发者常用工具包
apt install vim git curl wget htop net-tools

## 3. 创建普通用户（推荐）
adduser 用户名

将普通用户添加sudo权限：

usermod -aG sudo 用户名（Ubuntu系）

usermod -aG wheel 用户名

## 4. 配置时区（如果需要）
timedatectl set-timezone Asia/Shanghai

## 5. 配置SSH（禁用密码登录，只允许密钥）

**🌟提示：建议搭配`服务器安全配置指南`后再操作**

vim /etc/ssh/sshd_config

## 6. 重启SSH服务
systemctl restart ssh

## 7 .配置防火墙
apt install ufw
ufw allow OpenSSH
ufw enable