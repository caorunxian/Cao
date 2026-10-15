---
name: 提交项目
description: 使用 git commit 并 push 当前项目到 Gitee 远程仓库 (https://gitee.com/cao-runxian/caorunxian.git)
---

## 工作流程

将当前项目的所有更改提交并推送到 Gitee 远程仓库。

### 步骤

1. **检查当前状态**
   ```bash
   git status
   ```
   查看有哪些文件被修改、新增或删除。

2. **暂存所有更改**
   ```bash
   git add -A
   ```

3. **提交更改**
   ```bash
   git commit -m "提交项目更新"
   ```
   如果用户指定了提交信息，使用用户提供的信息。

4. **推送到远程仓库**
   ```bash
   git push origin master
   ```
   如果主分支不是 `master`，先检查当前分支：
   ```bash
   git branch --show-current
   ```
   然后推送到对应分支。

### 注意事项

- 如果推送被拒绝（远程有更新），先执行 `git pull --rebase`，解决冲突后再推送。
- 如果用户未指定提交信息，使用默认信息或根据更改内容生成简洁的中文提交信息。
- 确保远程仓库地址为 `https://gitee.com/cao-runxian/caorunxian.git`。
