# TaskDock 使用说明

## 系统要求

- Windows 11 x64
- 可运行的本地 Codex CLI 或本地 Codex session 文件

## 安装与启动

从 [TaskDock Releases](https://github.com/kc0577/TaskDock/releases) 下载 ZIP，解压后运行 `TaskDock.exe`。首次启动不需要管理员权限。

当前版本未进行代码签名，Windows SmartScreen 可能显示“未知发布者”提示。请核对下载来源和发布页公布的校验信息，不要关闭 Defender、SmartScreen 或其他系统安全保护。

## 界面

- 状态灯：绿色表示空闲/完成，蓝色表示工作中/等待，红色表示错误；
- 5 小时和 7 天额度行：显示额度剩余或重置倒计时；
- 当前任务行：显示 Codex 侧栏标题或项目/任务名称；
- 统计页面：显示本地 Token 消耗趋势和当日任务明细；
- 托盘菜单：提供刷新、设置、置顶、锁定位置、开机启动和退出。

## 本地数据兼容

设置和 Token 历史继续保存在 `%APPDATA%\CodexBar`，升级到 TaskDock 不会要求迁移该目录。

## 卸载

退出 TaskDock，删除解压后的程序目录；如果启用了开机启动，先在设置中关闭，或从当前用户的启动项中删除 `TaskDock`。
