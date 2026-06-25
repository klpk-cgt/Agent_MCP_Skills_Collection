# 🧰 Agent MCP Skills Collection

> 面向多 Agent 工具的 **Skills** 和 **MCP** 配置共享中心  
> A centralized hub for sharing **Skills** and **MCP** configurations across multi-agent tools

---

## 📦 仓库内容

### 📊 Skills 总览（14 个）

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

#### 🧪 Web 开发 & 测试 🆕

| # | Skill | 版本 | 来源 | 说明 |
|---|-------|------|------|------|
| 12 | **Webapp Testing** | - | ⭐ Anthropic 官方 | Playwright E2E测试，服务器管理，侦察-行动模式 |
| 13 | **Playwright CLI** | - | ⭐ Microsoft 官方 | 令牌高效浏览器自动化CLI，快照+ref定位 |
| 14 | **Vercel React Best Practices** | 1.0.0 | ⭐ Vercel 官方 | React/Next.js 70条性能规则，8大分类 |

### 6 个通用 MCP 配置模板

| MCP Server | 用途 |
|-----------|------|
| **GitHub** | 仓库管理、Issues、PR、搜索 |
| **Filesystem** | 文件系统读写操作 |
| **Fetch** | 网页内容抓取 |
| **Puppeteer** | 浏览器自动化 |
| **Chrome DevTools** | Chrome 开发者工具集成 |
| **PostgreSQL** | 数据库查询 |

> ⚠️ 所有模板中的 Token/密码均使用占位符，请替换为实际凭据

---

## 🚀 快速开始

```bash
git clone https://github.com/klpk-cgt/Agent_MCP_Skills_Collection.git
cd Agent_MCP_Skills_Collection

# 复制需要的 skill 到 CodeBuddy
cp -r skills/webapp-testing ~/.codebuddy/skills/
cp -r skills/vercel-react-best-practices ~/.codebuddy/skills/
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
│   ├── webapp-testing/          🆕
│   ├── playwright-cli/          🆕
│   └── vercel-react-best-practices/  🆕
└── mcp-templates/
    ├── github-mcp.json
    ├── filesystem-mcp.json
    ├── fetch-mcp.json
    ├── puppeteer-mcp.json
    ├── chrome-devtools-mcp.json
    └── postgresql-mcp.json
```

## 📄 许可证

各 Skill 保留其原始许可证。本文档和 MCP 模板使用 MIT 许可证。
