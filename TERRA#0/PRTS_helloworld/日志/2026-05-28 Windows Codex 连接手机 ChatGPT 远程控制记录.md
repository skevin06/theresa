# Windows Codex 连接手机 ChatGPT 远程控制记录

日期：2026-05-28

## 学习总结

打开 PowerShell 查日志：

```powershell
$logDir = Join-Path $env:USERPROFILE '.codex\remote-control-logs'
Get-ChildItem -LiteralPath $logDir -Filter '*.log' | Sort-Object LastWriteTime -Descending
$latest = Get-ChildItem -LiteralPath $logDir -Filter '*.err.log' | Sort-Object LastWriteTime -Descending | Select-Object -First 1
Get-Content -LiteralPath $latest.FullName -Tail 80
```

连接排查流程：

```text
手机 Waiting
-> 查 remote-control 日志
-> Multi-factor authentication required：重新 codex logout / codex login，完成 MFA
-> os error 10060：Windows 直连 OpenAI 超时
-> 检查 Clash 端口 127.0.0.1:7890
-> 用 HTTP_PROXY / HTTPS_PROXY / ALL_PROXY 启动 codex app-server
-> 手机刷新设备列表，连接 DESKTOP-LEIHJHN
```

连接原理：

```text
手机 ChatGPT App
-> HTTPS/WebSocket
-> ChatGPT/OpenAI 远程服务
-> WebSocket 长连接
-> Windows Codex remote-control
```

关键网络点：

- 不是局域网 IP 直连，不要求同 Wi-Fi。
- `--listen off` 表示 Windows 不开放本地监听端口。
- 手机和 Windows 都要能访问 OpenAI 服务。
- WebSocket 负责保持远程控制长连接。
- HTTPS 负责登录、鉴权、设备注册等请求。
- 本机网络直连超时，所以 Windows 端通过 Clash HTTP 代理 `127.0.0.1:7890` 出口访问。

## 目标

让手机 ChatGPT App 通过 Codex remote connection 发现并连接这台 Windows 电脑。

设备名：

```text
DESKTOP-LEIHJHN
```

## 最终可用结论

本次连接成功的关键不是局域网直连，而是：

```text
手机 ChatGPT App
-> ChatGPT/OpenAI 远程服务
-> Windows Codex remote-control
```

因此手机和 Windows 都必须能访问 ChatGPT/OpenAI 服务。

Windows 端直连 `chatgpt.com` 不稳定，会超时，所以最终使用 Clash 本地代理：

```text
127.0.0.1:7890
```

## 本机已确认状态

Codex CLI：

```powershell
codex --version
# codex-cli 0.134.0
```

npm：

```powershell
npm --version
# 11.13.0
```

登录状态：

```powershell
codex login status
# Logged in using ChatGPT
```

配置文件：

```text
C:\Users\admin\.codex\config.toml
```

关键配置：

```toml
[features]
remote_connections = true
remote_control = true
```

`config.toml` 已设置为只读，避免被自动覆盖。

## 实际成功启动方式

因为 Windows 直连 ChatGPT/OpenAI 会超时，需要让 `codex app-server` 继承代理环境变量。

可在 PowerShell 中运行：

```powershell
$env:HTTP_PROXY = 'http://127.0.0.1:7890'
$env:HTTPS_PROXY = 'http://127.0.0.1:7890'
$env:ALL_PROXY = 'http://127.0.0.1:7890'
$env:NO_PROXY = 'localhost,127.0.0.1,::1'
codex app-server --listen off --remote-control
```

说明：

- `--listen off`：不开放局域网本地监听端口。
- `--remote-control`：把这台 Windows 注册到 ChatGPT/Codex 远程连接服务。
- 手机不是通过局域网 IP 连接 Windows，而是通过 OpenAI/Codex 远程通道连接。

## 今天遇到的问题

### 1. MFA 未满足

日志中曾出现：

```text
Multi-factor authentication required
```

处理方式：

```powershell
codex logout
codex login
```

然后在浏览器里完整完成 ChatGPT 登录和 MFA 验证。

注意：启用 MFA 后，需要重新登录 Codex，旧会话不会自动变成已完成 MFA 的远程控制会话。

### 2. Windows 直连 ChatGPT 超时

日志中曾出现：

```text
os error 10060
```

并且直连测试 `chatgpt.com:443` 超时。

本机发现 Clash 正在运行，代理端口：

```text
127.0.0.1:7890
```

通过代理访问 ChatGPT/GitHub 可通，因此最终改为代理启动 `codex app-server`。

### 3. `codex remote-control start` 不适用于 Windows

Windows 上执行：

```powershell
codex remote-control start --json
```

返回：

```text
codex app-server daemon lifecycle is only supported on Unix platforms
```

所以 Windows 端使用：

```powershell
codex app-server --listen off --remote-control
```

## 手机端连接方式

1. 打开手机 ChatGPT App。
2. 进入 Codex / connection / remote connection 页面。
3. 确保手机登录同一个 ChatGPT/OpenAI 账号和 workspace。
4. 刷新设备列表。
5. 选择：

```text
DESKTOP-LEIHJHN
```

连接成功后，手机端发送的 prompt 可以进入 Windows Codex 当前会话。

## 保持连接需要什么

Windows 端必须保持：

- 电脑开机，不睡眠。
- 网络可用。
- Clash 运行。
- `127.0.0.1:7890` 可用。
- `codex app-server --listen off --remote-control` 进程运行。
- Codex 登录态有效。

手机端必须保持：

- ChatGPT App 登录同一账号。
- 手机网络能访问 ChatGPT/OpenAI。
- 如果处于不支持区域，需要 VPN；否则连接可能短时间保留，但心跳或重连会失败。

## 手机退后台

手机 ChatGPT App 可以短时间退后台。

如果彻底杀掉 App，之后通常需要重新进入 connection 页面并重新选择 Windows 设备。

不应关闭 Windows 端的 Clash、Codex remote-control 服务或电脑网络。

## 重新连接检查清单

Windows 端检查：

```powershell
codex login status
```

应显示：

```text
Logged in using ChatGPT
```

检查 Clash 代理：

```powershell
curl.exe -I -x http://127.0.0.1:7890 --connect-timeout 20 https://chatgpt.com/backend-api/
```

启动 remote-control：

```powershell
$env:HTTP_PROXY = 'http://127.0.0.1:7890'
$env:HTTPS_PROXY = 'http://127.0.0.1:7890'
$env:ALL_PROXY = 'http://127.0.0.1:7890'
$env:NO_PROXY = 'localhost,127.0.0.1,::1'
codex app-server --listen off --remote-control
```

查看日志：

```text
C:\Users\admin\.codex\remote-control-logs
```

如果看到：

```text
Multi-factor authentication required
```

重新执行：

```powershell
codex logout
codex login
```

如果看到：

```text
os error 10060
```

说明网络直连或代理不通，优先检查 Clash 和 `127.0.0.1:7890`。

## 当前结论

本机已成功通过手机端发送 prompt 到 Windows Codex 会话。

最终稳定条件：

```text
Windows Clash 运行
+ Codex 使用代理启动 remote-control
+ 手机 ChatGPT 能访问 OpenAI 服务
+ 同账号同 workspace
```
