# TaskDock

TaskDock 是面向 Windows 11 的非官方 Codex 本地状态与额度工具。它读取本机 app-server 和 session 文件，在任务栏附近显示状态、额度、任务和统计信息。

> TaskDock 不是 OpenAI 官方产品，也不代表 OpenAI 的授权、认可或合作关系。

## 下载

[下载最新 Windows x64 版本](https://github.com/kc0577/TaskDock/releases/latest)

解压后运行 `TaskDock.exe`。当前版本未进行代码签名，Windows SmartScreen 可能显示未知发布者提示；请从本仓库 Release 下载并核对发布页信息，不要关闭系统安全保护。

## 功能

- 状态灯与 5 小时/7 天额度
- 多个 Codex 任务的运行状态
- 当前任务名称和本地 Token 统计
- 托盘菜单、置顶、位置锁定和开机启动
- 浅色/深色视觉模式

## 隐私

TaskDock 只在本机读取 Codex app-server、session 文件、`session_index.jsonl`、`%APPDATA%\CodexBar` 和当前用户启动项，不上传代码、任务内容、日志、Token 历史、凭据或遥测数据。详见 [PRIVACY.md](PRIVACY.md)。

## 支持开发

TaskDock 免费提供下载。赞助入口将在官方爱发电页面准备完成后添加；任何赞助均为自愿支持，不影响下载和功能。

## 许可证

- [MIT License](LICENSE)
- [第三方声明](THIRD_PARTY_NOTICES.md)
- [使用说明](USAGE.md)
- [安全说明](SECURITY.md)
