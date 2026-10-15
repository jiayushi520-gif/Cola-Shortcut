# 隐私与安全

正式数据位于 iCloud Drive/Shortcuts/ColaManager。记录包含饮用、漱口、刷牙时间和截止时间。iCloud 同步由 Apple 提供；项目无自建服务器或第三方 API。

发布内容不包含真实饮用记录、私人绝对路径、账号凭据或本机完整恢复包。测试记录为合成数据。签名成品经过只读解包，动作与生成源一致；审计结果见 development/evidence/signed-file-audit.json。扫描不构成绝对安全保证。

Scriptable 只读用户授权的文件夹书签；读取失败显示数据不可用。WidgetKit 刷新由系统调度。签名中保留 Apple 官方封装和证书信息，未修改成品签名字节。

公开开发证据中的本机用户名统一替换为 LOCAL_USER。完整原始文件仅保存在开发电脑本地恢复归档中，不上传。请勿在 issue 中贴真实 state.json 或凭据。
