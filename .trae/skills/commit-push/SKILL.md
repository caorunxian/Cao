---
name: commit-push
description: 将当前项目 commit 并 push 到 GitHub 远程仓库 https://github.com/caorunxian/Cao。当用户说提交、push、推送到 GitHub、commit 项目时触发。不要用于初始化仓库或处理非本项目的远端。
---

# Commit & Push 到 GitHub

将当前项目的所有更改提交并推送到 GitHub 仓库。

## 固定参数

- 远程仓库：`https://github.com/caorunxian/Cao.git`
- 若远程不存在或需重建，使用 `git remote add origin https://github.com/caorunxian/Cao.git`
- 分支：`main`（若项目当前为 `master`，以实际分支为准）

## 步骤

1. **检查状态**
   ```powershell
   git status
   git branch --show-current
   git remote -v
   ```

2. **若项目未初始化**（`.git` 不存在），一次性完成：
   ```powershell
   git init
   git branch -M main
   git remote add origin https://github.com/caorunxian/Cao.git
   ```

3. **暂存所有更改**
   ```powershell
   git add -A
   ```

4. **提交**
   - 优先使用用户提供的提交信息
   - 未指定时根据改动自动生成简洁中文信息，格式：`功能：简述本次改动`
   - PowerShell 下直接用 `-m "..."`，不要使用 bash heredoc
   ```powershell
   git commit -m "功能：<简述>"
   ```

5. **推送**
   ```powershell
   git push -u origin <当前分支>
   ```

## 故障处理

- **推送被拒绝（远程领先）**：先 `git pull --rebase origin <分支>`，无冲突后再 `git push`
- **SSH 公钥已配置**，但仍提示鉴权失败：改用 https 地址重试，或让用户检查 GitHub SSH key 设置
- **首次 push 要求用户名密码**：当前环境已配置 SSH 公钥，可切到 SSH 远程地址 `git@github.com:caorunxian/Cao.git` 规避 HTTPS 凭证问题

## 注意事项

- 不要修改 global git config（user.name / user.email 已设置：`caorunxian` / `632053542@qq.com`）
- 推送完成后必须回显远端最新一次 commit hash 与分支信息，确认推送成功
- 不要用 `gh` CLI；只用原生 `git` 命令
