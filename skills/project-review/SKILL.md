---
name: project-review
description: Agent 接手项目时先完整了解项目结构、技术栈、入口文件、路由、数据来源等，输出项目理解报告后再提出修改建议。
version: 1.0.0
tags: [项目审查, 代码分析, 技术栈识别]
---

# Project Review Skill

## 触发场景

- 网页项目接手
- GitHub 项目分析
- 部署项目前检查
- 新项目接手
- 代码结构分析

## 执行流程

1. **阅读项目元数据**
   - 读取 `README.md`、`package.json`、`tsconfig.json`、`.env.example`
   - 识别项目名称、版本、描述、脚本命令

2. **判断技术栈**
   - 前端框架（React / Vue / Next.js / Nuxt 等）
   - UI 库（Tailwind / shadcn / Ant Design 等）
   - 后端框架（Express / Fastify / NestJS 等）
   - 数据库（PostgreSQL / SQLite / Supabase 等）
   - 部署方式（Vercel / Docker / PM2 / Nginx 等）

3. **找入口文件**
   - `src/main.ts` / `src/index.ts` / `src/App.tsx`
   - `pages/` / `app/` 目录
   - `server.ts` / `index.js`

4. **找路由结构**
   - 前端路由（React Router / Vue Router / Next.js App Router）
   - 后端 API 路由

5. **找数据来源**
   - API 调用层（`src/api/` / `src/services/`）
   - 数据库配置（`prisma/schema.prisma` / `drizzle/`）
   - 状态管理（Redux / Zustand / Pinia）

6. **找环境变量**
   - `.env.example` 中的变量列表
   - 代码中 `process.env` 的使用

7. **找部署方式**
   - `Dockerfile` / `docker-compose.yml`
   - `vercel.json` / `netlify.toml`
   - PM2 配置文件
   - Nginx 配置

8. **找构建命令**
   - `package.json` 中的 `scripts`
   - 构建工具配置（Vite / Webpack / Turbopack）

9. **输出项目理解报告**
   - 项目概述
   - 技术栈
   - 目录结构
   - 关键文件
   - 数据流
   - 环境变量
   - 部署方式

10. **提出修改建议**
    - 基于理解提出针对性建议
    - 标注风险点
    - 给出优先级排序

## 禁止行为

- 不要在未理解项目前直接修改代码
- 不要跳过任何分析步骤
- 不要凭空猜测项目结构
