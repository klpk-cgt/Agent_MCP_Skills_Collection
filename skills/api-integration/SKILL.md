---
name: api-integration
description: 接入第三方 API，包含 Key 管理、字段映射、错误兜底、状态处理和安全规范。
version: 1.0.0
tags: [API, 第三方集成, 后端, 安全]
---

# API Integration Skill

## 触发场景

- DeepSeek API
- AI 预测 API
- 天气 API
- 比赛数据 API
- 赔率数据 API
- 地图 / 地铁 / 城市资讯 API

## 执行流程

1. **确认 API 信息**
   - 阅读官方文档
   - 确认请求方式（GET / POST）
   - 确认证证方式（API Key / Bearer Token / OAuth）
   - 确认请求频率限制
   - 确认返回数据格式

2. **设计字段映射表**
   ```
   | API 字段        | 本地字段       | 类型     | 说明       |
   |----------------|--------------|---------|-----------|
   | user_id        | userId       | string  | 用户ID     |
   | created_at     | createdAt    | Date    | 创建时间    |
   ```

3. **实现 API 调用层**
   - 创建独立的 service 文件
   - 使用 TypeScript 类型定义
   - 封装请求和响应类型

4. **安全规范**
   - API Key 必须走环境变量
   - 前端不能暴露私钥
   - 后端代理敏感 API 调用
   - 使用 `.env.example` 记录所需变量

5. **错误处理**
   - 网络错误兜底
   - 超时处理
   - 限流处理（429）
   - 服务器错误（5xx）重试

6. **状态处理**
   - loading 状态
   - empty 状态（无数据）
   - error 状态（请求失败）
   - success 状态（正常展示）

7. **Mock 数据**
   - 创建 mock 数据文件
   - 支持开发环境切换
   - 文档记录 mock 数据来源

8. **额度说明**
   - 免费额度限制
   - 限流风险提示
   - 缓存策略建议

## 代码模板

```typescript
// services/api-service.ts
const API_BASE = process.env.NEXT_PUBLIC_API_BASE_URL

export async function fetchData<T>(endpoint: string): Promise<T> {
  try {
    const res = await fetch(`${API_BASE}${endpoint}`, {
      headers: { 'Authorization': `Bearer ${process.env.API_KEY}` }
    })
    if (!res.ok) throw new Error(`API Error: ${res.status}`)
    return res.json()
  } catch (error) {
    console.error('API request failed:', error)
    throw error
  }
}
```

## 禁止行为

- 不要在前端代码中硬编码 API Key
- 不要忽略错误处理
- 不要跳过 loading / empty / error 状态
- 不要将私钥暴露给前端
