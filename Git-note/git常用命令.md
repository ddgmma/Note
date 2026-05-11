# Git 常用命令文档

> 适合初学者快速查阅，按使用场景分类。

---

## 1. 仓库初始化与克隆

| 命令                        | 说明                                     |
| --------------------------- | ---------------------------------------- |
| `git init`                  | 在当前目录初始化一个新的 Git 仓库        |
| `git clone <url>`           | 克隆远程仓库到本地                       |
| `git clone --depth 1 <url>` | 浅克隆（只拉取最新的一次提交，节省时间） |

---

## 2. 查看状态与差异

| 命令                           | 说明                                              |
| ------------------------------ | ------------------------------------------------- |
| `git status`                   | 查看工作区和暂存区的状态（哪些文件被修改/未跟踪） |
| `git diff`                     | 查看工作区与暂存区的差异                          |
| `git diff --staged`            | 查看暂存区与上一次提交的差异                      |
| `git diff <commit1> <commit2>` | 比较两次提交之间的差异                            |

---

## 3. 添加与提交

| 命令                       | 说明                                                         |
| -------------------------- | ------------------------------------------------------------ |
| `git add <file>`           | 将指定文件添加到暂存区                                       |
| `git add .`                | 添加所有修改（包括新文件、修改、删除）到暂存区               |
| `git add -u`               | 仅添加已跟踪文件的修改（不包含未跟踪的新文件）               |
| `git commit -m "message"`  | 提交暂存区内容，并附上提交信息                               |
| `git commit -am "message"` | 跳过 `git add`，直接提交所有**已跟踪**文件的修改（不包含新文件） |
| `git commit --amend`       | 修改上一次提交（信息或内容，慎用于已推送的提交）             |

---

## 4. 分支管理

| 命令                                     | 说明                                  |
| ---------------------------------------- | ------------------------------------- |
| `git branch`                             | 列出本地分支（当前分支前有 `*` 标记） |
| `git branch -r`                          | 列出远程分支                          |
| `git branch -a`                          | 列出所有分支（本地 + 远程）           |
| `git branch <branch-name>`               | 创建新分支（但不会切换过去）          |
| `git checkout <branch-name>`             | 切换到指定分支                        |
| `git checkout -b <branch-name>`          | 创建并切换到新分支                    |
| `git switch <branch-name>`               | Git 2.23+ 推荐，切换分支（更清晰）    |
| `git switch -c <branch-name>`            | 创建并切换分支                        |
| `git branch -d <branch-name>`            | 删除本地分支（已合并时安全删除）      |
| `git branch -D <branch-name>`            | 强制删除未合并的分支                  |
| `git push origin --delete <branch-name>` | 删除远程分支                          |

---

## 5. 合并与变基

| 命令                         | 说明                                           |
| ---------------------------- | ---------------------------------------------- |
| `git merge <branch>`         | 将指定分支合并到当前分支                       |
| `git merge --no-ff <branch>` | 禁用快进合并，保留分支历史                     |
| `git rebase <branch>`        | 将当前分支的提交变基到目标分支上（使历史线性） |
| `git rebase --continue`      | 解决冲突后继续变基                             |
| `git rebase --abort`         | 放弃变基，回到原状态                           |

> **提示**：公共分支（如 main）不要使用 `rebase`，否则会造成他人困扰。

---

## 6. 远程仓库

| 命令                          | 说明                                                   |
| ----------------------------- | ------------------------------------------------------ |
| `git remote -v`               | 查看远程仓库别名及 URL                                 |
| `git remote add origin <url>` | 添加远程仓库，命名为 origin                            |
| `git remote remove <name>`    | 删除指定的远程仓库别名                                 |
| `git push -u origin <branch>` | 首次推送并建立本地分支与远程分支的关联                 |
| `git push`                    | 推送到已关联的远程分支                                 |
| `git push --force`            | 强制推送（慎用，会覆盖远程历史）                       |
| `git pull`                    | 拉取远程分支并合并到当前分支（相当于 `fetch + merge`） |
| `git fetch`                   | 拉取远程更新但不合并                                   |
| `git fetch --prune`           | 拉取并删除本地已不存在的远程分支引用                   |

---

## 7. 查看提交历史

| 命令                                   | 说明                               |
| -------------------------------------- | ---------------------------------- |
| `git log`                              | 查看完整提交历史                   |
| `git log --oneline`                    | 简洁单行显示                       |
| `git log --graph --oneline --decorate` | 图形化显示分支结构                 |
| `git log -n 5`                         | 只显示最近 5 条提交                |
| `git log --author="name"`              | 按作者筛选                         |
| `git blame <file>`                     | 查看文件每一行是谁在哪次提交修改的 |

---

## 8. 撤销与回退

| 命令                          | 说明                                                    |
| ----------------------------- | ------------------------------------------------------- |
| `git restore <file>`          | 丢弃工作区的修改（恢复成暂存区或最近提交的状态）        |
| `git restore --staged <file>` | 将文件从暂存区撤出，但保留工作区修改                    |
| `git reset <commit>`          | 回退到指定提交，**保留**工作区和暂存区内容（混合模式）  |
| `git reset --hard <commit>`   | **彻底回退**，丢弃所有后续修改（危险）                  |
| `git reset --soft <commit>`   | 回退，仅移动 HEAD，工作区和暂存区内容不变（可重新提交） |
| `git revert <commit>`         | 生成一个新提交来“反做”某个提交（安全用于已推送的提交）  |

---

## 9. 暂存（Stash）

| 命令                          | 说明                         |
| ----------------------------- | ---------------------------- |
| `git stash`                   | 将当前工作区的修改暂存起来   |
| `git stash push -m "message"` | 带信息暂存                   |
| `git stash list`              | 查看暂存堆栈                 |
| `git stash apply`             | 应用最近的暂存，但不清除堆栈 |
| `git stash pop`               | 应用最近的暂存并移出堆栈     |
| `git stash drop`              | 删除指定的暂存               |
| `git stash clear`             | 清空所有暂存                 |

---

## 10. 标签（Tag）

| 命令                                 | 说明                 |
| ------------------------------------ | -------------------- |
| `git tag`                            | 列出所有标签         |
| `git tag <tagname>`                  | 创建轻量标签         |
| `git tag -a <tagname> -m "message"`  | 创建附注标签（推荐） |
| `git push origin <tagname>`          | 推送指定标签到远程   |
| `git push origin --tags`             | 推送所有本地标签     |
| `git tag -d <tagname>`               | 删除本地标签         |
| `git push origin --delete <tagname>` | 删除远程标签         |

---

## 11. 实用别名（简化常用命令）

在 Git 配置中设置别名，让操作更高效：

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"
```

之后就能用 `git st`、`git lg` 等短命令。

---

## 12. 常用工作流示意（新手推荐）

```bash
git clone <url>                # 克隆项目
git checkout -b feature-xxx    # 新建并切换分支
# 修改代码...
git add .                      # 添加所有修改
git commit -m "feat: xxx"      # 提交
git push -u origin feature-xxx # 首次推送
# （后续）git push
# 发起 Pull Request → 合并后删除本地分支
```

---

## 小贴士

- **提交信息**建议遵循规范，如：`feat: 添加登录功能`、`fix: 修复按钮点击崩溃`
- 频繁推送前先 `git pull` 避免冲突
- 遇到冲突时，耐心阅读 `git status` 提示，手动解决后 `add` + `commit`
- 使用 `git help <command>` 查看官方帮助文档

> 📌 持续练习，犯错是学习最好的方式！