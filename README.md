# 安卓手机屏幕点击器（Accessibility + 悬浮窗）

这是一个**用于自动化测试/重复操作**的“屏幕点击器”示例工程：通过 **AccessibilityService 的 `dispatchGesture`** 在任意坐标执行点击；通过**悬浮窗**实现选点、开始/停止、设置间隔。

> 提醒：请只用于你有权限的场景（自己的设备/应用、测试与无障碍辅助等），不要用于破坏服务条款、刷量作弊等用途。

## 工程位置

工程在：`android-screen-clicker/`

## 使用步骤（真机）

1. 用 Android Studio 打开 `android-screen-clicker/`，等待 Gradle Sync。
2. 安装到手机。
3. 授予悬浮窗权限：
   - 系统设置 → 应用 → 本应用 → “显示在其他应用上层/悬浮窗” → 允许
4. 开启无障碍服务：
   - 系统设置 → 无障碍 → 已安装服务 → `Screen Clicker` → 开启
5. 回到 App，点击“启动悬浮窗”，在悬浮窗里：
   - 点“选点”，在屏幕上点一下目标位置（记录坐标）
   - 设置间隔（毫秒）
   - 点“开始”，即可循环点击；“停止”结束

## 关键实现

- `ClickAccessibilityService`：用 `dispatchGesture` 执行点击
- `OverlayController`：管理悬浮窗 UI、选点遮罩、点击循环
