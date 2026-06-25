---
name: docker-compose-debug
description: 排查 Docker Compose 项目问题，包含配置检查、日志分析、端口冲突、数据卷权限等。
version: 1.0.0
tags: [Docker, Docker Compose, 运维, 调试]
---

# Docker Compose Debug Skill

## 触发场景

- Docker Compose 服务启动失败
- 容器频繁重启
- 端口冲突
- 数据卷权限问题
- 镜像拉取失败

## 执行流程

1. **检查配置**
   ```bash
   docker compose config        # 验证 compose 文件语法
   docker compose config --quiet # 仅在有错误时输出
   ```

2. **检查容器状态**
   ```bash
   docker compose ps            # 查看所有服务状态
   docker compose ps --format json
   ```

3. **查看日志**
   ```bash
   docker compose logs          # 所有服务日志
   docker compose logs <service> # 特定服务日志
   docker compose logs -f --tail=50 <service>
   ```

4. **检查端口占用**
   ```bash
   sudo netstat -tlnp | grep :<port>
   sudo lsof -i :<port>
   ```
   - 如果端口被占用，找到占用进程
   - 修改 compose 文件中的端口映射或停止占用进程

5. **检查镜像问题**
   ```bash
   docker images               # 查看本地镜像
   docker pull <image>:<tag>   # 手动拉取镜像
   ```
   - 检查镜像是否存在
   - 检查镜像标签是否正确
   - 检查网络是否能访问 registry

6. **检查数据卷权限**
   ```bash
   docker volume ls
   docker volume inspect <volume>
   ls -la <mount-path>
   ```
   - 检查挂载目录权限
   - 检查 UID/GID 是否匹配

7. **检查环境变量**
   ```bash
   docker compose config | grep -A5 environment
   docker exec <container> env
   ```

8. **给出修复方案**
   - 最小化修改
   - 说明修改原因
   - 评估影响范围

9. **验证修复**
   ```bash
   docker compose down
   docker compose up -d
   docker compose ps
   docker compose logs --tail=20
   ```

## 常见问题排查

| 问题 | 可能原因 | 解决方案 |
|------|---------|----------|
| 容器Exited(1) | 启动命令错误 | 检查 entrypoint / command |
| 端口已占用 | 其他进程占用 | 修改端口映射或停止进程 |
| 权限拒绝 | UID不匹配 | 设置 user 或 chown |
| 镜像拉取失败 | 网络/认证问题 | 检查网络和 registry 登录 |
| OOM Killed | 内存不足 | 调整 mem_limit |

## 禁止行为

- 不要直接删除 volume（数据丢失风险）
- 不要使用 `docker compose down -v`（会删除数据卷）
- 删除数据前必须明确风险提示
- 不要在生产环境使用 `--force-recreate`
