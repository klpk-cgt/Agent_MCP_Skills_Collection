---
name: deploy-linux-server
description: Windows 本地开发，Linux 云服务器部署的完整流程，包含构建、推送、部署、验证和回滚。
version: 1.0.0
tags: [部署, Linux, 运维, Docker, PM2, Nginx]
---

# Deploy Linux Server Skill

## 触发场景

- 前端项目部署
- Node.js 项目部署
- Docker Compose 部署
- Nginx 反向代理排查
- 云服务器项目更新

## 执行流程

1. **本地检查**
   ```bash
   git status              # 确认无未提交修改
   npm run build           # 本地构建验证
   ```

2. **检查环境配置**
   - 确认 `.env.production` 存在且配置正确
   - 确认数据库连接字符串
   - 确认 API 密钥

3. **提交并推送**
   ```bash
   git add .
   git commit -m "release: deploy update"
   git push origin main
   ```

4. **服务器部署**
   ```bash
   ssh user@server
   cd /path/to/project
   git pull origin main
   npm install --production
   npm run build
   ```

5. **重启服务**
   - PM2 方式：
     ```bash
     pm2 restart app-name
     pm2 logs app-name --lines 20
     ```
   - Docker Compose 方式：
     ```bash
     docker compose up -d --build
     docker compose logs -f --tail=20
     ```
   - systemd 方式：
     ```bash
     sudo systemctl restart app-name
     sudo journalctl -u app-name -n 20
     ```

6. **检查 Nginx**
   ```bash
   sudo nginx -t              # 配置检查
   sudo systemctl reload nginx
   ```

7. **检查端口**
   ```bash
   sudo netstat -tlnp | grep :3000
   curl -I http://localhost:3000
   ```

8. **验证访问**
   - 浏览器访问域名
   - 检查 HTTPS 证书
   - 检查 API 响应
   - 检查静态资源加载

9. **回滚方案**
   ```bash
   # Git 回滚
   git log --oneline -5
   git revert HEAD
   git push origin main

   # PM2 回滚
   pm2 reload app-name

   # Docker 回滚
   docker compose down
   docker compose up -d <previous-image>
   ```

## 部署检查清单

- [ ] 本地 build 通过
- [ ] .env.production 配置正确
- [ ] 代码已推送到远程
- [ ] 服务器 git pull 成功
- [ ] 依赖安装成功
- [ ] 构建成功
- [ ] 服务重启成功
- [ ] Nginx 配置正常
- [ ] 端口监听正常
- [ ] 域名访问正常
- [ ] HTTPS 证书有效
- [ ] 日志无错误

## 禁止行为

- 不要直接在服务器上修改代码
- 不要跳过本地构建验证
- 不要忘记备份回滚信息
- 不要在高峰期部署
