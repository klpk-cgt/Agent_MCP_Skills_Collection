# Web Application Testing

Anthropic 官方 Web 应用测试 Skill，基于 Playwright。

## 核心功能

- **决策树工作流**：自动判断静态 HTML vs 动态 WebApp，选择最佳测试策略
- **服务器生命周期管理**：`with_server.py` 自动启动/停止开发服务器
- **侦察-行动模式**：先截图/DOM检查 → 识别选择器 → 执行操作
- **多服务器支持**：前后端同时启动测试
- **控制台日志捕获**：调试 JavaScript 错误
- **示例代码库**：元素发现、静态HTML、控制台日志

## 适用场景

- Web 应用功能验证
- UI 行为调试
- 浏览器截图对比
- 前端自动化回归测试
- 本地开发环境 E2E 测试

## 安装

```bash
npx skills add https://github.com/anthropics/skills --skill webapp-testing -g -y
```

## 来源

- GitHub: [anthropics/skills](https://github.com/anthropics/skills) ⭐ 127K+
- 许可证: Apache 2.0
