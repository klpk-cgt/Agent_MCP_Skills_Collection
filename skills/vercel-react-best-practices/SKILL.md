---
name: vercel-react-best-practices
description: "React and Next.js performance optimization guidelines from Vercel Engineering. Contains 70 rules across 8 categories. Use when writing, reviewing, or refactoring React/Next.js code."
description_zh: "Vercel React 最佳实践：Vercel工程团队官方的React/Next.js性能优化指南，70条规则覆盖8大分类（消除瀑布流、打包优化、服务端性能、客户端数据获取、重渲染优化、渲染性能、JS性能、高级模式）"
license: MIT
source: https://github.com/vercel-labs/agent-skills
---

# Vercel React Best Practices

Comprehensive performance optimization guide for React and Next.js applications, maintained by Vercel. Contains 70 rules across 8 categories, prioritized by impact.

## When to Apply

Reference these guidelines when:
- Writing new React components or Next.js pages
- Implementing data fetching (client or server-side)
- Reviewing code for performance issues
- Refactoring existing React/Next.js code
- Optimizing bundle size or load times

## Rule Categories by Priority

| Priority | Category | Impact | Prefix |
|:---------|:---------|:-------|:-------|
| 1 | Eliminating Waterfalls | CRITICAL | `async-` |
| 2 | Bundle Size Optimization | CRITICAL | `bundle-` |
| 3 | Server-Side Performance | HIGH | `server-` |
| 4 | Client-Side Data Fetching | MEDIUM-HIGH | `client-` |
| 5 | Re-render Optimization | MEDIUM | `rerender-` |
| 6 | Rendering Performance | MEDIUM | `rendering-` |
| 7 | JavaScript Performance | LOW-MEDIUM | `js-` |
| 8 | Advanced Patterns | LOW | `advanced-` |

## Quick Reference: Top Rules

### Eliminating Waterfalls (CRITICAL)
- `async-cheap-condition-before-await` — Check cheap conditions before await
- `async-defer-await` — Defer await to the last moment
- `async-parallel` — Parallelize independent async operations
- `async-suspense-boundaries` — Use Suspense boundaries strategically

### Bundle Size Optimization (CRITICAL)
- `bundle-barrel-imports` — Avoid barrel file imports
- `bundle-dynamic-imports` — Use dynamic imports for code splitting
- `bundle-defer-third-party` — Defer third-party scripts
- `bundle-conditional` — Conditionally load heavy dependencies

### Server-Side Performance (HIGH)
- `server-cache-react` — Use React cache() for deduplication
- `server-parallel-fetching` — Parallel data fetching on server
- `server-serialization` — Minimize serialized props
- `server-after-nonblocking` — Use after() for non-blocking work

### Client-Side Data Fetching (MEDIUM-HIGH)
- `client-swr-dedup` — Deduplicate requests with SWR
- `client-event-listeners` — Clean up event listeners
- `client-passive-event-listeners` — Use passive event listeners

### Re-render Optimization (MEDIUM)
- `rerender-memo` — Use React.memo appropriately
- `rerender-dependencies` — Stabilize hook dependencies
- `rerender-derived-state` — Derive state instead of storing
- `rerender-transitions` — Use useTransition for non-urgent updates
- `rerender-use-deferred-value` — Defer value updates
- `rerender-no-inline-components` — Avoid inline component definitions

### Rendering Performance (MEDIUM)
- `rendering-content-visibility` — Use CSS content-visibility
- `rendering-hydration-no-flicker` — Prevent hydration mismatch flicker
- `rendering-resource-hints` — Add resource hints (preload/prefetch)

### JavaScript Performance (LOW-MEDIUM)
- `js-batch-dom-css` — Batch DOM/CSS reads and writes
- `js-cache-function-results` — Cache expensive function results
- `js-early-exit` — Early exit from loops/functions
- `js-set-map-lookups` — Use Set/Map for lookups instead of arrays

### Advanced Patterns (LOW)
- `advanced-effect-event-deps` — Effect event dependency management
- `advanced-init-once` — Initialize once patterns
- `advanced-use-latest` — useLatest pattern for callbacks

---

**Source**: [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) — Vercel Official, 32K+ Installs
