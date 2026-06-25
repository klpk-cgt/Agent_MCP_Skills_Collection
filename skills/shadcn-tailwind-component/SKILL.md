---
name: shadcn-tailwind-component
description: 基于 shadcn/ui 和 Tailwind CSS 快速生成现代化组件，覆盖卡片、弹窗、表单、数据看板等场景。
version: 1.0.0
tags: [shadcn/ui, Tailwind, 组件开发, UI]
---

# shadcn + Tailwind Component Skill

## 触发场景

- 卡片、弹窗、Tabs 组件
- 筛选器、排行榜
- 表单、登录页
- 后台面板、数据看板

## 前置条件

- 项目已安装 Tailwind CSS
- 项目已配置 shadcn/ui
- `components.json` 已正确配置

## 执行流程

1. **确认项目配置**
   - 检查 `tailwind.config.ts`
   - 检查 `components.json`
   - 检查 `globals.css` 中的 CSS 变量

2. **分析需求**
   - 确认组件类型
   - 确认数据结构
   - 确认交互方式
   - 确认响应式需求

3. **安装依赖组件**
   ```bash
   npx shadcn@latest add button card dialog input label
   npx shadcn@latest add table tabs select badge
   ```

4. **开发组件**
   - 使用 shadcn/ui 基础组件组合
   - 使用 Tailwind 类名定制样式
   - 保持组件可复用
   - 支持 `className` prop 扩展

5. **样式规范**
   - 使用 CSS 变量（`bg-background` / `text-foreground`）
   - 使用 `cn()` 工具函数合并类名
   - 响应式：`sm:` `md:` `lg:` 前缀
   - 暗色模式支持

6. **验证**
   - `npm run build`
   - 检查 TypeScript 类型
   - 检查移动端适配

## 组件模板

```tsx
import { cn } from "@/lib/utils"
import { Card, CardHeader, CardTitle, CardContent } from "@/components/ui/card"

interface DataCardProps<T> {
  data: T
  className?: string
}

export function DataCard<T extends { title: string; value: string }>({
  data,
  className
}: DataCardProps<T>) {
  return (
    <Card className={cn("w-full", className)}>
      <CardHeader>
        <CardTitle>{data.title}</CardTitle>
      </CardHeader>
      <CardContent>
        <p className="text-2xl font-bold">{data.value}</p>
      </CardContent>
    </Card>
  )
}
```
