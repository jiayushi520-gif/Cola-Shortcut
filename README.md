# Cola Shortcut / 可乐快捷指令

每自然周一瓶无糖可乐，饮用、漱口、刷牙打卡及下一周处罚共用一份 JSON 记录。适合希望记录可乐饮用习惯的人；打卡不代表验证实际刷牙行为。

版本 **1.0.0** · MIT · [English](README_EN.md)

已使用 Apple 官方命令签名，Mac 导入和核心运行已测试。**目标 iOS 26.1 尚未实机验证**；签名不等于 Apple 认证。Scriptable 书签和主屏幕扩展也待 iPhone 验证。

## 下载与安装

仓库：[GitHub](https://github.com/jiayushi520-gif/Cola-Shortcut)。从 [Releases](https://github.com/jiayushi520-gif/Cola-Shortcut/releases) 下载成品；文件也在 [shortcut](shortcut) 目录。RoutineHub 和 Apple iCloud 分享链接尚未生成，不提供虚构链接。

可以不用 iCloud 分享链接安装：下载 `.shortcut` 后通过 AirDrop 传到 iPhone，在“文件”中打开并添加。先装 ColaManager-Test 测试，再装 ColaManager 和配套入口。**安装传输可不用 iCloud，当前业务数据存储仍依赖 iCloud Drive。**

[安装和授权](docs/installation.md) · [使用与自动化](docs/usage.md) · [小组件安装](docs/WIDGET_INSTALL.md)

## 实际功能

- 周一至下一周一的一瓶额度、不累计、二次确认和重复登记检查。
- 关联记录 ID 的漱口和刷牙打卡；可配置截止时间，支持跨午夜。
- 到期未按时打卡，下一自然周禁喝一周；查询和饮用时重新计算。
- 本周、4/12/52周及全部历史统计，连续合规周数、完成率，无样本显示不适用。
- JSON 导出、备份、恢复；每周报告及截止检查配套快捷指令。
- 四个原生小组件入口；可选 Scriptable 小号/中号、浅色/深色只读面板。

## 依赖与权限

iPhone 需快捷指令、iCloud Drive、文件访问及提醒事项/通知授权。主程序无 Python、Mac 在线或第三方 API 依赖。Scriptable 仅为可选面板，需手动授权共享文件夹书签。主程序名称必须保留 ColaManager。个人自动化需在 iPhone 设置触发时间。

数据同步不是跨设备事务；请一次只在一台设备写入。小组件遵循系统调度，不保证实时刷新。

[隐私](docs/privacy.md) · [故障排查](docs/troubleshooting.md) · [测试报告](docs/TEST_REPORT.md) · [开发日志](development/DEVELOPMENT_LOG.md) · [更新日志](CHANGELOG.md) · [发布流程](docs/releasing.md)
