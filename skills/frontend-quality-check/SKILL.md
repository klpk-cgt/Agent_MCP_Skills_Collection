---
name: frontend-quality-check
description: 前端修改后的质量检查，覆盖依赖、lint、typecheck、build、测试、浏览器控制台和网络请求。
version: 1.0.0
tags: [前端, 质量检查, 测试, 调试]
---

# Frontend Quality Check Skill

## 触发场景

- 前端代码修改后验证
- PR 提交前检查
- 部署前验证
- Bug 修复后回归

## 推荐配合 MCP

- Playwright MCP — 浏览器自动化测试
- Chrome DevTools MCP — 控制台错误排查
- Context7 MCP — 最新文档查询
- GitHub MCP — PR 和 CI 管理

## 执行流程

1. **检查依赖安装**
   ```bash
   npm install  # 或 pnpm install / yarn install
   ```

2. **执行 Lint**
   ```bash
   npm run lint
   ```
   - 记录所有 warning 和 error
   - 修复新增的 lint 问题

3. **执行 TypeCheck**
   ```bash
   npx tsc --noEmit
   ```

4. **执行 Build**
   ```bash
   npm run build
   ```
   - 检查构建产物大小
   - 检查构建警告

5. **执行测试（如有）**
   ```bash
   npm run test
   ```

6. **浏览器验证**
   - 启动开发服务器
   - 打开关键页面
   - 检查控制台错误
   - 检查网络请求失败
   - 检查移动端样式（375px）

7. **输出问题清单**
   - 问题级别（Error / Warning / Info）
   - 问题位置（文件 + 行号）
   - 修复建议
   - 优先级排序

## 检查清单

- [ ] 依赖安装正常
- [ ] Lint 无新增错误
- [ ] TypeCheck 通过
- [ ] Build 成功
- [ ] 测试通过
- [ ] 控制台无错误
- [ ] 网络请求正常
- [ ] 移动端样式正常
- [ ] 无未使用的 import
- [ ] 无硬编码的 API 地址
