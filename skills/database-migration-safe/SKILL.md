---
name: database-migration-safe
description: 数据库迁移安全流程，包含备份、分析、迁移计划、dry-run、校验和回滚方案。
version: 1.0.0
tags: [数据库, 迁移, 安全, Prisma, Supabase]
---

# Database Migration Safe Skill

## 触发场景

- JSON 转 MySQL
- SQLite 转 MySQL
- Prisma 迁移
- Supabase 迁移
- 排行榜数据迁移
- 用户积分数据迁移

## 执行流程

1. **备份**
   ```bash
   # MySQL
   mysqldump -u root -p db_name > backup_$(date +%Y%m%d).sql

   # PostgreSQL
   pg_dump -U user db_name > backup_$(date +%Y%m%d).sql

   # SQLite
   cp database.db backup_$(date +%Y%m%d).db
   ```

2. **分析现有表结构**
   ```sql
   SHOW TABLES;
   DESCRIBE <table_name>;
   SELECT COUNT(*) FROM <table_name>;
   ```

3. **生成迁移计划**
   - 列出所有变更（新增表、修改字段、删除字段）
   - 标注每项变更的风险等级
   - 确认执行顺序（依赖关系）
   - 估算执行时间

4. **Dry Run**
   ```bash
   # Prisma
   npx prisma migrate diff --from-schema-datasource --to-schema-datamodel

   # 手动 SQL
   -- 在事务中执行，然后 ROLLBACK
   BEGIN;
   -- 迁移 SQL
   ROLLBACK;
   ```

5. **执行迁移**
   - 在低峰期执行
   - 逐条执行，每步验证
   - 记录每步执行时间

6. **校验数据**
   ```sql
   -- 行数对比
   SELECT COUNT(*) FROM old_table;
   SELECT COUNT(*) FROM new_table;

   -- 抽样数据对比
   SELECT * FROM new_table ORDER BY id DESC LIMIT 10;
   ```

7. **输出回滚方案**
   ```bash
   # 回滚命令
   mysql -u root -p db_name < backup_YYYYMMDD.sql

   # Prisma 回滚
   npx prisma migrate resolve --rolled-back <migration_name>
   ```

## 禁止行为

- 禁止直接 DROP 表
- 禁止跳过备份步骤
- 禁止在生产环境跳过 dry-run
- 禁止同时执行多个迁移
- 删除数据前必须明确提示风险
