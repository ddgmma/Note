# Git 极简高频命令（初学者版）

---

## 1. 下载一个项目到本地

```bash
git clone <仓库地址>
```

## 2. 查看当前状态（最常用）

```bash
git status
```
> 随时敲一下，就知道哪些文件改过了、哪些还没提交。

## 3. 把修改交给 Git（两步走）

```bash
git add <文件名>      # 1. 把文件放进“暂存区”
git commit -m "说明"  # 2. 正式提交，写好备注
```
> 偷懒写法：`git commit -am "说明"` （只对已跟踪的文件有效）

## 4. 推送到远程仓库（上传）

```bash
git push
```
> 第一次推送某个分支时用：`git push -u origin 分支名`

## 5. 拉取远程更新（下载+合并）

```bash
git pull
```
> 每天开始写代码前先敲一下，避免和别人冲突。

## 6. 查看提交历史

```bash
git log --oneline
```
> 简洁一行一个提交，够用了。

## 7. 分支操作（最常用的三条）

```bash
git branch                 # 查看所有分支
git checkout -b 新分支名   # 创建并切换到新分支
git checkout 分支名         # 切换分支
```

## 8. 合并分支

```bash
git merge 要合并的分支名
```
> 例如：先在 `main` 分支上，然后 `git merge feature-login`

## 9. 放弃工作区的修改（还没 add）

```bash
git restore <文件名>
```
> 想把文件改回上一次提交的样子，就用这个。

## 10. 把 add 错了的文件撤回来

```bash
git restore --staged <文件名>
```
> 文件还在，只是不放在暂存区了。

---

## 一个最简单的日常流程（抄作业版）

```bash
git pull                    # 1. 拉取最新代码
git checkout -b my-feature  # 2. 新建自己的分支
# … 写代码，改文件 …
git add .                   # 3. 添加所有改动
git commit -m "完成功能xxx" # 4. 提交
git push -u origin my-feature  # 5. 推送（第一次需要 -u）
# 然后去网页上发起合并请求（Pull Request）
```

---

## 遇到冲突怎么办？

1. `git pull` 时会提示冲突
2. 打开冲突文件，找到 `<<<<<<<` 和 `>>>>>>>` 之间的内容
3. 手动删掉不要的，保留正确的代码
4. 再次执行 `git add .` + `git commit`

---

**总结：先学会这 10 多个命令，足够应付 90% 的场景。剩下的遇到再查就行，不用一次性全背。**