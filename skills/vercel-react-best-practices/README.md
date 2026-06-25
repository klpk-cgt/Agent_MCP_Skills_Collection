# Vercel React Best Practices

Vercel 工程团队官方的 React/Next.js 性能优化指南。

## 核心内容

- **70 条规则**：覆盖 React/Next.js 性能优化的方方面面
- **8 大分类**：按优先级排序（CRITICAL → LOW）
- **实战导向**：每条规则都有代码示例和反模式说明

## 规则分类

| 优先级 | 分类 | 规则数 |
|--------|------|--------|
| CRITICAL | 消除瀑布流 | 6 |
| CRITICAL | 打包优化 | 6 |
| HIGH | 服务端性能 | 10 |
| MEDIUM-HIGH | 客户端数据获取 | 4 |
| MEDIUM | 重渲染优化 | 15 |
| MEDIUM | 渲染性能 | 11 |
| LOW-MEDIUM | JavaScript 性能 | 14 |
| LOW | 高级模式 | 4 |

## 适用场景

- 编写新的 React 组件/Next.js 页面
- 代码审查时检查性能问题
- 重构现有 React/Next.js 代码
- 优化打包体积和加载时间

## 安装

```bash
npx skills add https://github.com/vercel-labs/agent-skills --skill vercel-react-best-practices -g -y
```

## 来源

- GitHub: [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)
- 作者: Vercel Engineering
- 安装量: 32K+
- 许可证: MIT
