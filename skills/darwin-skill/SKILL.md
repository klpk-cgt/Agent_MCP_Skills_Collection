---
name: darwin-skill
description: "Darwin Skill (达尔文.skill): autonomous skill optimizer inspired by Karpathy's autoresearch. Evaluates SKILL.md files using an 8-dimension rubric (structure + effectiveness), runs hill-climbing with git version control, validates improvements through test prompts, and generates visual result cards. Use when user mentions "优化skill", "skill评分", "自动优化", "auto optimize", "skill质量检查", "达尔文", "darwin", "帮我改改skill", "skill怎么样", "提升skill质量", "skill review", "skill打分"."
version: 1.0.0
---

# Darwin Skill

> 借鉴 Karpathy autoresearch 的自主实验循环，对 skills 进行持续优化。
> 核心理念：**评估 → 改进 → 实测验证 → 人类确认 → 保留或回滚 → 生成成果卡片**
> GitHub: https://github.com/alchaincyf/darwin-skill

---

## 设计哲学

autoresearch 的精髓：
1. **单一可编辑资产** — 每次只改一个 SKILL.md
2. **双重评估** — 结构评分（静态分析）+ 效果验证（跑测试看输出）
3. **棘轮机制** — 只保留改进，自动回滚退步
4. **独立评分** — 评分用子agent，避免「自己改自己评」的偏差
5. **人在回路** — 每个skill优化完后暂停，用户确认再继续

与纯结构审查的区别：不只看 SKILL.md 写得规不规范，更看改完后**实际跑出来的效果是否更好**。

---

## 评估 Rubric（8维度，总分100）

### 结构维度（60分）— 静态分析

| # | 维度 | 权重 | 评分标准 |
|---|------|------|---------|
| 1 | **Frontmatter质量** | 8 | name规范、description包含做什么+何时用+触发词、≤1024字符 |
| 2 | **工作流清晰度** | 15 | 步骤明确可执行、有序号、每步有明确输入/输出 |
| 3 | **边界条件覆盖** | 10 | 处理异常情况、有fallback路径、错误恢复 |
| 4 | **检查点设计** | 7 | 关键决策前有用户确认、防止自主失控 |
| 5 | **指令具体性** | 15 | 不模糊、有具体参数/格式/示例、可直接执行 |
| 6 | **资源整合度** | 5 | references/scripts/assets引用正确、路径可达 |

### 效果维度（40分）— 需要实测

| # | 维度 | 权重 | 评分标准 |
|---|------|------|---------|
| 7 | **整体架构** | 15 | 结构层次清晰、不冗余不遗漏、与花叔生态一致 |
| 8 | **实测表现** | 25 | 用测试prompt跑一遍，输出质量是否符合skill宣称的能力 |

### 评分规则
- 维度1-7：每个维度打 1-10 分，乘以权重得到该维度得分
- 维度8（实测表现）：跑2-3个测试prompt，按输出质量打1-10分
- **总分 = Σ(维度分 × 权重) / 10**，满分100
- 改进后总分必须 **严格高于** 改进前才保留

---

## 自主优化循环

### Phase 0: 初始化
1. 确认优化范围（全部skills或指定列表）
2. 创建 git 分支：auto-optimize/YYYYMMDD-HHMM
3. 初始化 results.tsv（如不存在）

### Phase 0.5: 测试Prompt设计
为每个skill设计2-3个测试prompt，覆盖典型场景和复杂场景，保存到 skill目录/test-prompts.json

### Phase 1: 基线评估（Baseline）
- 结构评分：主agent按维度1-7逐项打分
- 效果评分：spawn独立子agent跑测试prompt，对比带/不带skill的输出
- 展示评分卡，暂停等用户确认

### Phase 2: 优化循环
max 3 rounds: 诊断最低维度 → 提出改进方案 → 执行改进 → 重新评估 → 决策（保留/回滚）
每个skill优化完后暂停，用户确认再继续

### Phase 2.5: 探索性重写（可选）
连续2个skill涨不动时，提议重写（需用户同意）

### Phase 3: 汇总报告
展示总优化数、保留/回滚次数、分数变化表、主要改进摘要

---

## results.tsv 格式

```tsv
timestamp	commit	skill	old_score	new_score	status	dimension	note	eval_mode
```

新增 eval_mode 列：full_test（跑了子agent测试）或 dry_run（模拟推演）

---

## 异常与边界条件

| 场景 | 触发条件 | 处理动作 |
|---|---|---|
| 不在 git 仓库 | git rev-parse 失败 | 提示用户 git init；拒绝则用文件备份代替 revert |
| results.tsv 缺失 | 文件不存在 | 新建并写表头行（9列含 eval_mode） |
| SKILL.md 找不到 | 目录存在但无 SKILL.md | 该 skill 终止，记 status=error |
| 优化后超150%体积 | 新文件 > 原×1.5 | 拒绝提交，回到改进步骤精简 |

---

## 约束规则

1. 不改变skill的核心功能和用途
2. 不引入新依赖
3. 每轮只改一个维度
4. 保持文件大小合理（≤150%原始大小）
5. 中文为主、简洁为上
6. 可回滚（git revert而非reset --hard）
7. 评分独立性（效果维度必须子agent评分）

---

## 使用方式

- **全量优化**：用户说"优化所有skills" → Phase 0-3 完整流程
- **单个优化**：用户说"优化 huashu-slides" → 只对指定skill执行
- **仅评估不改**：用户说"评估所有skills的质量" → 只执行基线评估
- **查看历史**：用户说"看看skill优化历史" → 读取展示 results.tsv

---

## 设计灵感

> "You write the goals and constraints in program.md; let an agent generate and test code deltas indefinitely; keep only what measurably improves the objective." — Karpathy, autoresearch

---

## 成果卡片生成

每个skill优化完成后自动生成视觉成果卡片（3种风格：Warm Swiss / Dark Terminal / Newspaper），2x高清PNG截图。

GitHub: https://github.com/alchaincyf/darwin-skill
