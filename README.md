# 🧰 Agent MCP Skills Collection

> 面向多 Agent 工具的 **Skills** 和 **MCP** 配置共享中心  
> A centralized hub for sharing **Skills** and **MCP** configurations across multi-agent tools

---

## 📦 仓库内容

### 6 个 CodeBuddy Skills 存档

| # | Skill | 版本 | 核心领域 |
|---|-------|------|---------|
| 1 | **Darwin Skill** | 1.0.0 | Skill 质量评估与自动优化（8维度评分+爬山算法） |
| 2 | **GitHub** | 1.0.0 | 通过 gh CLI 与 GitHub 交互 |
| 3 | **Grill Me** | 1.0.0 | 方案深度追问式审查（决策树逐层拆解） |
| 4 | **GSAP 动画开发助手** | 1.0.0 | GSAP 动画代码生成与审查 |
| 5 | **Impeccable（前端设计工具集）** | 2.0.0 | 高品质前端 UI/UX 设计全流程 |
| 6 | **前端开发** | 0.1.1 | 全栈前端开发 + AI 媒体生成 |

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
cp -r skills/darwin-skill ~/.codebuddy/skills/
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
│   └── frontend-dev/
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
