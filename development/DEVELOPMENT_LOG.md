# 开发日志 — 2026-10-15

这是根据保留源码、测试结果与签名审计整理的开发记录，不是逐条聊天转录。完整原始工作目录另有本地恢复包；公开包排除第三方参考下载、签名解包中间证书、缓存、私人路径和任何工作目录外数据。

## 实现与验证

1. 在 macOS 15.7.2 检查 shortcuts CLI、Python 与生成格式。生成二进制工作流，官方 anyone 签名，最小测试及主程序完成 Mac 导入。
2. 原生动作实现周一自然周、唯一记录、二次确认、关联打卡和截止处罚。跨周尚未到期的记录不提前判违规；新周饮用暂缓至结算。
3. 实现本周及长期报告、空样本不适用、JSON 持久化和备份。写入前复读比较不等于跨设备原子事务。
4. 四个入口统一调用 ColaManager。每周报告、截止检查、睡前提醒为独立辅助入口；个人自动化需设备配置。
5. Scriptable 读取用户授权书签，读取异常展示不可用；测试用模拟环境覆盖小/中尺寸和深浅色，但不冒充 iOS 扩展实测。
6. 测试中修正工作流变量引用及文本 token 的 UTF-16 位置处理，最终结构检查通过。早期 IO 曾超时，最终查询成功；未证明唯一根因。
7. 发布准备只读解包九个 AEA 签名成品，动作与未签名生成源一致，无已识别敏感字段或网络请求动作；保持成品原字节。

## 保存的证据

- native-results.json：11 组原生规则结果、每组15项指标。
- mutation-results.json：首次饮用、重复饮用、漱口及重复、刷牙及重复六个隔离写入场景。
- final-code-tests.txt：21 核心规则和9个组件模拟场景。
- final-dst-tests.txt、final-structure-tests.txt：DST 与结构检查。
- entry-results.json、final-query.json、file-performance.json：入口、只读查询和文件性能记录。
- release-sign-results.json、signed-file-audit.json：签名命令及实际签名内容审计。

以上为历史执行证据，路径已脱敏；此次整理的复跑记录单列 publication-retest.txt。完整验证范围和失败限制见 docs/TEST_REPORT.md。设置、导出恢复选择器、iPhone 导入、两设备同步、锁屏自动化及 Scriptable 真实书签仍需验证。

## 清理和恢复原则

先本地归档逐文件 SHA-256 校验，再上传并核验 GitHub，最后只清理项目目录中已归档且未变化的重复及临时文件。不删除真实 iCloud 数据、用户其他文稿或系统快捷指令。恢复包留在本机 outputs/archives。
