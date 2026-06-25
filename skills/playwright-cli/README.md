# Playwright CLI

微软官方浏览器自动化 CLI，专为编码 Agent 设计的令牌高效浏览器控制工具。

## 核心功能

- **令牌高效**：快照机制 + ref 定位，最小化上下文窗口消耗
- **全浏览器支持**：Chrome、Firefox、WebKit、Edge
- **多标签页管理**：创建/切换/关闭标签页
- **网络拦截/模拟**：route/unroute 请求
- **视频录制**：完整操作回放
- **追踪调试**：性能分析和调试
- **存储状态管理**：cookies/localStorage/sessionStorage CRUD
- **UI 审查**：`show --annotate` 在页面上标注反馈

## 安装

```bash
npm install -g @playwright/cli@latest
```

## 适用场景

- 编码 Agent 浏览器自动化
- Web 应用交互测试
- 表单自动填写
- 截图/PDF 生成
- 网络请求监控
- UI 审查与反馈

## 来源

- GitHub: [microsoft/playwright-cli](https://github.com/microsoft/playwright-cli)
- 作者: Microsoft
- 类型: CLI + Agent Skill
