---
name: git-safe-workflow
description: 规范 Agent 修改代码时的 Git 操作，小步修改、小步提交、不自动推送主分支。
version: 1.0.0
tags: [Git, 工作流, 安全, 版本控制]
---

# Git Safe Workflow Skill

## 触发场景

- Agent 修改代码
- 功能开发
- Bug 修复
- 代码重构

## 执行流程

1. **修改前检查**
   ```bash
   git status              # 查看工作区状态
   git branch              # 确认当前分支
   git log --oneline -5    # 查看最近提交
   ```

2. **分支管理**
   ```bash
   # 新功能使用新分支
   git checkout -b feature/<feature-name>

   # Bug 修复使用修复分支
   git checkout -b fix/<bug-description>
   ```

3. **小步修改**
   - 每次只修改一个功能点
   - 修改后立即验证
   - 不累积大量修改

4. **小步提交**
   ```bash
   git add <specific-files>    # 添加特定文件
   git commit -m "feat: add user login form"
   ```

5. **Commit Message 规范**
   ```
   feat: 新功能
   fix: Bug 修复
   refactor: 重构
   style: 样式调整
   docs: 文档
   test: 测试
   chore: 构建/工具
   ```

6. **输出 Diff 摘要**
   ```bash
   git diff --stat
   git diff --name-only
   ```

7. **回滚支持**
   ```bash
   # 回滚最近一次提交（保留修改）
   git reset --soft HEAD~1

   # 回滚最近一次提交（丢弃修改）
   git reset --hard HEAD~1

   # 撤销特定提交
   git revert <commit-hash>
   ```

## 禁止行为

- 不要自动 push 到 main / master 分支
- 不要使用 `git add .` 或 `git add -A`（可能提交敏感文件）
- 不要使用 `git push --force`
- 不要在没有验证的情况下提交
- 不要提交 `.env`、密钥、凭证文件
- 不要在提交信息中使用模糊描述（如 "update"、"fix bug"）
