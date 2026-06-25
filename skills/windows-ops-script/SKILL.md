---
name: windows-ops-script
description: Windows 运维自动化脚本，涵盖装机、驱动、DNS、加域退域、网络修复、日志采集等。
version: 1.0.0
tags: [Windows, 运维, 自动化, PowerShell]
---

# Windows Ops Script Skill

## 触发场景

- 装机流程自动化
- 驱动安装
- DNS 检测与修复
- 加域 / 退域
- 网络修复
- 日志采集
- 管理员权限检测

## 执行要求

1. **管理员权限**
   ```powershell
   # 必须检测管理员权限
   if (-NOT ([Security.Principal.WindowsPrincipal]::
       [Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole(
       [Security.Principal.WindowsBuiltInRole]::Administrator)) {
       Write-Host "请以管理员身份运行此脚本" -ForegroundColor Red
       exit
   }
   ```

2. **日志记录**
   ```powershell
   $logFile = "C:\Ops\logs\$(Get-Date -Format 'yyyyMMdd_HHmmss').log"
   function Write-Log {
       param([string]$Message, [string]$Level = "INFO")
       $time = Get-Date -Format "yyyy-MM-dd HH:mm:ss"
       "$time [$Level] $Message" | Tee-Object -FilePath $logFile -Append
   }
   ```

3. **失败提示**
   - 每个操作都要有 try-catch
   - 失败时输出明确错误信息
   - 提供可能的解决建议

4. **高风险操作提示**
   ```powershell
   function Confirm-Action {
       param([string]$Message, [switch]$Dangerous)
       if ($Dangerous) {
           Write-Host "⚠️ 高风险操作: $Message" -ForegroundColor Red
       }
       $confirm = Read-Host "确认执行？(y/N)"
       if ($confirm -ne 'y') { exit }
   }
   ```

5. **回滚方案**
   - 记录修改前的状态
   - 提供回滚命令
   - 关键操作前创建还原点

## 常用脚本模板

### DNS 检测
```powershell
Write-Log "开始检测 DNS..."
$dns = Get-DnsClientServerAddress -AddressFamily IPv4
$dns | Format-Table -AutoSize
```

### 网络修复
```powershell
Write-Log "重置网络..."
ipconfig /flushdns
netsh winsock reset
netsh int ip reset
Write-Log "网络重置完成，请重启计算机"
```

### 日志采集
```powershell
Write-Log "采集系统日志..."
Get-EventLog -LogName System -Newest 100 | Export-Csv "C:\Ops\logs\system_events.csv"
Get-EventLog -LogName Application -Newest 100 | Export-Csv "C:\Ops\logs\app_events.csv"
```

## 禁止行为

- 不要在未检测管理员权限的情况下执行高风险操作
- 不要跳过日志记录
- 不要在加域/退域操作中忽略失败提示
- 不要自动重启而不给出提示
