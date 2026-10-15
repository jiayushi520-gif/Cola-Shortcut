# 发布流程

VERSION 是项目发行版本；JSON schema_version 独立管理，不随文档发行强行改变。

1. 修改源码，更新 VERSION、CHANGELOG 与发布说明。
2. 运行 python3 src/build_release.py，再运行 Python 结构测试、Node 核心/组件和 DST 测试，命令见 usage.md。
3. 在 Mac 使用 python3 src/sign.py，通过 Apple shortcuts sign --mode anyone 签名；绝不直接编辑已签名文件。
4. 导入并运行成品；重新进行只读签名内容审计和敏感信息检查。iPhone 实测单独记录。
5. 将本次已验证成品复制到 shortcut/，更新校验和、README 和测试证据。
6. 确认公开内容后提交 Git，打与 VERSION 一致的 v 标签，建立 GitHub Release。
7. 使用 Apple 官方分享生成真实 iCloud 链接，完成 RoutineHub 登录和发布，保持同版本并回填真实链接。

更新由用户下载并确认安装；未实现自动检查或自动安装更新。RoutineHub/iCloud 未成功时保持未发布状态。
