```markdown
# Git 极简入门教程

这份教程覆盖日常使用 90% 的场景，看完就能上手。

---

## 1. 三个核心概念

| 概念 | 通俗解释 |
|------|----------|
| **工作区** | 你电脑里的项目文件夹，你在里面改代码 |
| **暂存区** | 一个“购物车”，决定哪些修改要提交 |
| **仓库** | 存储所有提交历史的地方（本地 `.git` 文件夹 + 远程仓库如 GitHub） |

**核心流程：**  
改文件 → 放入暂存区 → 提交到仓库 → 推送到远程

---

## 2. 第一次使用 Git

### 2.1 设置身份（仅第一次）

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

### 2.2 两种开始方式

**A. 从零开始新项目**
```bash
git init          # 在当前文件夹创建仓库
```

**B. 克隆已有远程项目**
```bash
git clone <远程仓库地址>   # 把远程项目下载到本地
```

---

## 3. 日常基本操作（最常用）

### 查看状态
```bash
git status        # 看哪些文件修改了，哪些暂存了
```

### 添加文件到暂存区
```bash
git add 文件名      # 添加指定文件
git add .          # 添加当前目录所有修改
```

### 提交到本地仓库
```bash
git commit -m "写一句描述做了什么修改"
```

### 查看提交历史
```bash
git log --oneline   # 简洁版历史，一行一条
```

### 推送到远程仓库
```bash
git push origin main   # 把本地 main 分支推到远程（分支名可能是 master）
```

### 拉取远程更新
```bash
git pull origin main   # 把远程 main 分支的更新拉到本地
```

---

## 4. 分支（并行开发不冲突）

- `main` 是默认主分支（旧项目可能是 `master`）
- 开发新功能时，**新建分支**，完成后合并回去

```bash
git branch 分支名         # 创建分支
git switch 分支名         # 切换到该分支（也可用 git checkout 分支名）
git switch -c 分支名      # 创建并切换（一步到位）

git merge 分支名          # 把该分支合并到当前分支
git branch -d 分支名      # 删除已合并的分支
```

---

## 5. 典型一天的工作流

```bash
git pull origin main          # 1. 开始前先拉取最新代码
git switch -c feature-login   # 2. 创建并切换到新功能分支

# ... 写代码 ...

git status                    # 3. 查看改了哪些文件
git add .                     # 4. 暂存所有修改
git commit -m "完成登录功能"    # 5. 提交
git push origin feature-login # 6. 推送新分支到远程

# 然后去 GitHub/GitLab 提交 Pull Request，等待合并
```

---

## 6. 后悔药（简单版）

| 场景 | 命令 |
|------|------|
| 改乱了文件，想回到上次提交的状态 | `git restore 文件名` |
| `git add` 多了，想移出暂存区 | `git restore --staged 文件名` |
| 提交信息写错了（还没推送） | `git commit --amend -m "新信息"` |

---

## 7. 一张图总结

```
工作区         暂存区          本地仓库         远程仓库
  │   git add   │  git commit   │  git push    │
  │ ──────────> │ ────────────> │ ───────────> │
  │             │               │              │
  │             │               │  git pull    │
  │ <────────── │ <──────────── │ <─────────── │
  │  git restore│ git checkout  │  git fetch   │
```

---

> **贴心提示：** 遇到问题先敲 `git status`，它会告诉你下一步该做什么。这就够用了。
```