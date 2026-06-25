# 🧰 Agent MCP Skills Collection

> 面向多 Agent 工具的 **Skills** 和 **MCP** 配置共享中心  
> A centralized hub for sharing **Skills** and **MCP** configurations across multi-agent tools

---

## 📦 仓库内容

### 📊 Skills 总览（28 个）

#### 🏗 通用工具

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 1 | **Darwin Skill** | 1.0.0 | 社区 | Skill 质量评估与自动优化（8维度评分+爬山算法） |
| 2 | **GitHub** | 1.0.0 | CodeBuddy | 通过 gh CLI 管理 Issues/PR/CI |
| 3 | **Grill Me** | 1.0.0 | Matt Pocock | 方案深度追问式审查（决策树逐层拆解） |

#### 🎨 前端设计

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 4 | **Impeccable** | 2.0.0 | Paul Bakaus | 高品质前端 UI/UX 设计全流程（20+场景） |
| 5 | **前端开发** | 0.1.1 | CodeBuddy | 全栈前端 + AI 媒体生成 |
| 6 | **UI/UX Pro Max** | 1.0.0 | CodeBuddy | 57种UI风格、95+调色板、56字体配对 |
| 7 | **Canvas Design** | 1.0.0 | Anthropic | 设计哲学驱动 PNG/PDF 视觉艺术创作 |
| 8 | **Algorithmic Art** | 1.0.0 | Anthropic | p5.js 生成艺术（粒子/流场/递归） |
| 9 | **Theme Factory** | 1.0.0 | Anthropic | 10个预设主题+自定义主题工厂 |
| 10 | **Lucide Icons** | 1.0.0 | CodeBuddy | 1000+ SVG 图标搜索/下载/定制 |

#### ⚡ 动画开发

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 11 | **GSAP 动画助手** | 1.0.0 | GreenSock | GSAP 动画代码生成与审查 |

#### 🧪 Web 开发 & 测试

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 12 | **Webapp Testing** | - | Anthropic 官方 | Playwright E2E测试，服务器管理，侦察-行动模式 |
| 13 | **Playwright CLI** | - | Microsoft 官方 | 令牌高效浏览器自动化CLI，快照+ref定位 |
| 14 | **Vercel React Best Practices** | 1.0.0 | Vercel 官方 | React/Next.js 70条性能规则，8大分类 |

#### 🔧 工程实践 🆕

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 15 | **Project Review** | 1.0.0 | 🆕 自建 | 项目接手时完整分析，输出理解报告后再修改 |
| 16 | **Bugfix Debug Loop** | 1.0.0 | 🆕 自建 | 规范Bug修复流程，复现→定位→最小修改→验证 |
| 17 | **Git Safe Workflow** | 1.0.0 | 🆕 自建 | Git安全操作，小步提交，不自动推送主分支 |
| 18 | **API Integration** | 1.0.0 | 🆕 自建 | 第三方API接入，Key管理、字段映射、错误兜底 |

#### 🖥 前端开发 🆕

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 19 | **Frontend UI Redesign** | 1.0.0 | 🆕 自建 | UI重构保留数据结构，优先移动端适配 |
| 20 | **Frontend Quality Check** | 1.0.0 | 🆕 自建 | 前端修改后质量检查（lint/typecheck/build/浏览器） |
| 21 | **Figma/Screenshot to Code** | 1.0.0 | 🆕 自建 | Figma设计稿/截图还原前端页面 |
| 22 | **Mobile First Web App** | 1.0.0 | 🆕 自建 | 移动端优先网页开发，375px/390px适配 |
| 23 | **shadcn + Tailwind Component** | 1.0.0 | 🆕 自建 | shadcn/ui + Tailwind快速生成现代化组件 |

#### 🚀 部署 & 运维 🆕

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 24 | **Deploy Linux Server** | 1.0.0 | 🆕 自建 | Windows开发→Linux部署完整流程，含回滚方案 |
| 25 | **Docker Compose Debug** | 1.0.0 | 🆕 自建 | Docker Compose问题排查，端口/日志/权限/镜像 |
| 26 | **Database Migration Safe** | 1.0.0 | 🆕 自建 | 数据库迁移安全流程，备份→分析→dry-run→校验 |
| 27 | **Windows Ops Script** | 1.0.0 | 🆕 自建 | Windows运维自动化，装机/DNS/加域/日志采集 |
| 28 | **Doc HTML Import** | 1.0.0 | 🆕 自建 | 文档/网页导入知识库，图片下载上传替换URL |

### 21 个通用 MCP 配置模板

#### 通用开发 MCP

| MCP Server | npm 包 | 用途 |
|-----------|--------|------|
| **GitHub** | `@modelcontextprotocol/server-github` | 仓库管理、Issues、PR、搜索 |
| **Filesystem** | `@modelcontextprotocol/server-filesystem` | 文件系统读写操作 |
| **Fetch** | `@modelcontextprotocol/server-fetch` | 网页内容抓取 |
| **Context7** | `@upstash/context7-mcp` | 实时获取版本特定的库文档 |
| **Memory** | `@modelcontextprotocol/server-memory` | 知识图谱记忆系统 |
| **Git** 🆕 | `@modelcontextprotocol/server-git` | Git仓库操作、历史和diff |
| **Sequential Thinking** 🆕 | `@modelcontextprotocol/server-sequential-thinking` | 复杂任务分步推理 |

#### 前端开发 MCP

| MCP Server | npm 包 | 用途 |
|-----------|--------|------|
| **Playwright** | `@playwright/mcp` | 完整浏览器自动化 E2E 测试 |
| **Chrome DevTools** | `chrome-devtools-mcp` | Chrome 开发者工具集成 |
| **Puppeteer** | `@modelcontextprotocol/server-puppeteer` | 浏览器自动化 |
| **Integrated Browser** | `@anthropic/integrated-browser-mcp` | 集成浏览器自动化工具集 |
| **Figma** 🆕 | `ai-figma-mcp` | Figma设计稿读取和操作 |

#### 后端 / 数据库 MCP

| MCP Server | npm 包 | 用途 |
|-----------|--------|------|
| **Supabase** | `@supabase-community/supabase-mcp` | Supabase数据库集成 |
| **PostgreSQL** | `@modelcontextprotocol/server-postgres` | PostgreSQL数据库查询 |
| **SQLite** 🆕 | `@modelcontextprotocol/server-sqlite` | SQLite本地数据库操作 |
| **Redis** 🆕 | `@modelcontextprotocol/server-redis` | Redis缓存操作 |

#### 部署 / 运维 MCP

| MCP Server | npm 包 | 用途 | 风险 |
|-----------|--------|------|------|
| **Sentry** 🆕 | `@wallacewen/sentry-mcp-server` | 错误监控和事件追踪 | 🟢 低 |
| **Vercel** 🆕 | `vercel-mcp-server` | Vercel部署和域名管理 | 🟡 中 |
| **Docker** 🆕 | `@modelcontextprotocol/server-docker` | Docker容器和镜像操作 | 🟡 中 |
| **SSH** 🆕 | `@modelcontextprotocol/server-ssh` | 远程服务器SSH操作 | 🔴 高 |
| **Shell** 🆕 | `@modelcontextprotocol/server-shell` | 任意Shell命令执行 | 🔴 高 |

> ⚠️ 所有模板中的 Token/密码均使用占位符，请替换为实际凭据  
> 🔴 高风险 MCP 不建议全局启用，仅在具体项目按需使用

---

## 🚀 快速开始

```bash
git clone https://github.com/klpk-cgt/Agent_MCP_Skills_Collection.git
cd Agent_MCP_Skills_Collection

# 复制需要的 skill 到你的 Agent
cp -r skills/project-review ~/.codebuddy/skills/
cp -r skills/bugfix-debug-loop ~/.codebuddy/skills/

# 复制 MCP 配置模板
cp mcp-templates/git-mcp.json ~/.codebuddy/mcp/
```

## 📂 目录结构

```
Agent_MCP_Skills_Collection/
├── README.md
├── 使用指南.md
├── skills/
│   ├── darwin-skill/
│   ├── github/
│   ├── grill-me/
│   ├── gsap-animation-assistant/
│   ├── impeccable/
│   ├── frontend-dev/
│   ├── ui-ux-pro-max/
│   ├── canvas-design/
│   ├── algorithmic-art/
│   ├── theme-factory/
│   ├── lucide-icons/
│   ├── webapp-testing/
│   ├── playwright-cli/
│   ├── vercel-react-best-practices/
│   │
│   │   # ===== 工程实践 🆕 =====
│   ├── project-review/              🆕
│   ├── bugfix-debug-loop/           🆕
│   ├── git-safe-workflow/           🆕
│   ├── api-integration/             🆕
│   │
│   │   # ===== 前端开发 🆕 =====
│   ├── frontend-ui-redesign/        🆕
│   ├── frontend-quality-check/      🆕
│   ├── figma-or-screenshot-to-code/  🆕
│   ├── mobile-first-web-app/        🆕
│   ├── shadcn-tailwind-component/   🆕
│   │
│   │   # ===== 部署 & 运维 🆕 =====
│   ├── deploy-linux-server/         🆕
│   ├── docker-compose-debug/        🆕
│   ├── database-migration-safe/     🆕
│   ├── windows-ops-script/          🆕
│   └── doc-html-import/             🆕
│
├── mcp-templates/
│   ├── github-mcp.json
│   ├── filesystem-mcp.json
│   ├── fetch-mcp.json
│   ├── puppeteer-mcp.json
│   ├── chrome-devtools-mcp.json
│   ├── postgresql-mcp.json
│   ├── context7-mcp.json
│   ├── memory-mcp.json
│   ├── playwright-mcp.json
│   ├── supabase-mcp.json
│   ├── integrated-browser-mcp.json
│   ├── git-mcp.json                 🆕
│   ├── sequential-thinking-mcp.json  🆕
│   ├── figma-mcp.json               🆕
│   ├── vercel-mcp.json              🆕
│   ├── sqlite-mcp.json              🆕
│   ├── redis-mcp.json               🆕
│   ├── sentry-mcp.json              🆕
│   ├── docker-mcp.json              🆕
│   ├── ssh-mcp.json                 🆕
│   └── shell-mcp.json               🆕
│
├── rules/
│   └── common-rules.md              🆕 Agent通用规则
│
├── docs/
│   └── mcp-security.md              🆕 MCP安全要求
│
└── mcp/
    └── env.example                  🆕 环境变量模板
```

## 🔒 安全注意事项

1. **敏感信息不入库** — API Key、Token、密码使用 `mcp/env.example` 占位
2. **高风险 MCP 按需启用** — SSH、Shell、Docker 不全局启用
3. **数据库默认只读** — 生产数据库 MCP 不默认启用写入
4. **不自动推送主分支** — Agent 修改代码后需人工确认推送
5. **详见** [docs/mcp-security.md](docs/mcp-security.md)

## 📄 许可证

各 Skill 保留其原始许可证。本文档和 MCP 模板使用 MIT 许可证。
