# Git 回滚操作

> 分清本地和远程，记住这三个命令就够了。

---

## 本地（未推送）

```shell
# 撤回最近一次提交，保留改动
git reset --soft HEAD~1

# 撤回最近一次提交，丢弃改动（慎用）
git reset --hard HEAD~1
```

---

## 远程（已推送）

```shell
# 安全撤销（推荐）
git revert HEAD
git push

# 强制覆盖（慎用）
git reset --hard HEAD~1
git push --force
```

---

## 速查

| 场景 | 命令 |
|------|------|
| 刚提交，想重新改 | `git reset --soft HEAD~1` |
| 刚提交，想彻底删 | `git reset --hard HEAD~1` ⚠️ |
| 已推送，安全撤销 | `git revert HEAD` → `git push` |
| 已推送，强制回滚 | `git reset --hard HEAD~1` → `git push --force` ⚠️ |
| 后悔了想找回 | `git reflog` → `git reset --hard <commit>` |

