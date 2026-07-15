# TaskDock 隐私说明

TaskDock 是本地运行的非官方 Windows 工具。当前版本不要求账号，不包含遥测、广告、崩溃上传或远程日志功能。

## 本机读取

- Codex app-server 返回的本机额度信息；
- `%USERPROFILE%\.codex\sessions\**\*.jsonl`；
- `%USERPROFILE%\.codex\session_index.jsonl`；
- `%APPDATA%\CodexBar` 下的设置和 Token 历史；
- 当前用户的开机启动注册表项。

## 不上传

TaskDock 不上传用户代码、session 日志、任务内容、本机路径、Token 历史、账号凭据或遥测数据，也不收集遥测。统计记录只保存在本机。

## 变更

如果未来版本增加联网更新、崩溃上报或遥测，发布前会更新本说明并明确告知用户。
