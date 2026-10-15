# 安装可乐管理小组件

## 推荐先安装原生入口

先导入 `ColaManager.shortcut` 和四个中文命名入口，运行主程序初始化。将四个入口放进快捷指令的“可乐管理”文件夹，再把这个文件夹选为主屏幕快捷指令组件的内容。无需配置业务动作。

## 可选：Scriptable 数值面板

1. 在 iPhone 安装官方 Scriptable App。
2. 把 `ColaManager-Widget.js` 放进 iCloud Drive / Scriptable，或在 Scriptable 中新建脚本并导入此文件的完整内容。
3. 打开 Scriptable 的 Settings → File Bookmarks，添加文件夹书签，名称严格设为 **ColaManager**，通过系统文件选择器选择 **iCloud Drive / Shortcuts / ColaManager**。这里只授权项目目录，不需要授权整个 iCloud Drive。
4. 在 Scriptable 中运行该脚本，确认读取到真实数据。如果显示“数据不可用”，先修复书签或同步问题，不要把默认数字当成真实额度。
5. 长按 iPhone 主屏幕 → 添加小组件 → Scriptable → 小号或中号。编辑组件，Script 选此脚本。
6. 对照主快捷指令的本周报告核对数值，再在真实小组件里检查读取是否成功。

小号整体点击打开 ColaManager；中号提供饮用、漱口、刷牙、统计的跳转区域。组件支持动态浅色/深色背景，显示本周剩余额度、饮用量、两项打卡、连续合规周数、禁喝状态和文件修改时间。

## 共享权限与验证边界

Scriptable 的 `FileManager.iCloud().documentsDirectory()` 是它自己的容器，**不能用拼接路径假定能访问 Shortcuts 目录**。本脚本只使用用户授予的文件书签 `bookmarkedPath('ColaManager')`，读取书签目录里的 `state.json`。不绕过沙盒，不使用模拟数据，不静默退回旧缓存。

官方文档支持通过书签访问 Scriptable 容器外的文件/文件夹，但说明不同执行环境的书签权限存在差异：从 App 设置创建的书签不能直接假定用于 Siri、共享表单或快捷指令动作。若要从快捷指令执行 Scriptable，应使用其 Create File Bookmark 动作。本交付只用于 Scriptable App/Widget，不让原生主程序依赖 Scriptable。

**尚未用实际 iPhone 验证本版本 Scriptable 的 Widget 扩展能否读取这个书签。** 若 App 内成功、主屏幕组件失败，说明该设备的扩展访问仍未满足要求；此时组件必须保留“数据不可用”。不要改成猜测路径或显示默认一瓶。原生四入口仍可使用，动态数值面板须在设备端验证后启用。

验证步骤：主快捷指令查看报告 → 在 Scriptable App 预览对照 → 添加中号组件对照 → 等待 iCloud 同步后再次核对。不要为了验证而创建假的真实饮用记录；首次空历史也能验证已初始化文件的读取。

官方 API：https://docs.scriptable.app/filemanager/

## 刷新

脚本请求最早30分钟后刷新，但 WidgetKit 决定实际时机。这不是实时组件。文件修改时间表示当前读到的文件版本，不表示另一台设备已完成同步。入口操作完成后，组件可能仍显示旧数值；即时状态以重新运行主快捷指令得到的报告为准。

刷新 API：[Scriptable ListWidget](https://docs.scriptable.app/listwidget/#refreshafterdate)。
