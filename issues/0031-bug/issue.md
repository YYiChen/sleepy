# [Bug]: 荣耀手机无法添加桌面小组件\n\n- Number: #31\n- State: open\n- Author: zysord\n- Created: 2026-09-10T13:12:11Z\n- Updated: 2026-09-14T15:06:56Z\n- URL: https://github.com/lingion/sleepy/issues/31\n\n## Body\n\n### Prerequisites

- [x] I am using the latest version of Sleepy
- [x] I have searched existing issues and found no duplicate
- [x] I will attach logs, screenshots, or a sample schedule file if helpful

### Current behavior

测试机型：荣耀Win RT
测试系统：MagicOS 10.0.0.170 （Android 16）
安全补丁日期：2026年7月1日

放置桌面小组件时，只有sleepy课程表的小组件放置后立马消失（无法截图），其他第三方APP放置的组件均正常放置。


### Expected behavior

如果是应用问题的话，希望修复Bug。
如果是我操作问题的话，请告知我如何修复。

### Steps to reproduce

1.长按桌面
2.添加桌面卡片—经典小组件
3.放置sleepy课程表的小组件时立即消失

### Schedule source

_No response_

### Additional context

_No response_

### Diagnostic info (auto-filled by app)

```markdown

```
\n\n## Comments\n\n### lingion — 2026-09-10T13:49:54Z\n\n感谢反馈。我这几天会调查国内各大厂启动器小组件的相关代码和设计规范，先完成荣耀手机的适配，顺便把其他启动器的兼容性也一起适配掉。\n\n### lingion — 2026-09-11T12:32:58Z\n\n上条说在调查,现在已经落地:修复随 [v1.0.53](https://github.com/lingion/sleepy/releases/tag/v1.0.53) 发布了,升级后按原来的步骤再放一次试试。

根因是添加流程里的配置页:荣耀 MagicOS 在添加小组件时会丢弃外部配置 Activity,启动器收到"取消"结果,就把刚绑定的小组件回滚掉了,所以表现为"放置立即消失"。首次添加本身不需要你填任何东西,这版直接跳过那一步,放置即完成;之后想换绑课表,在应用内「我的 → 通用设置 → 小组件」里改。

我手头没有荣耀真机,如果这版还有消失的情况,告诉我机型和系统版本,我接着查。\n\n### zysord — 2026-09-11T14:45:20Z\n\n此版本小组件无消失情况，但可能存在部分显示和操作问题。
1.每周课表2×2小组件无法直接使用左右箭头切换。点击后为直接打开软件（可能仅有荣耀出现此情况）。

https://github.com/user-attachments/assets/a6858ead-5cfd-42fc-acad-a516f9942aa9

2.每周课表4×5小组件显示不完全，也无法直接在小组件内部滑动（可能仅为荣耀出现此情况）。

<img width="1272" height="2800" alt="Image" src="https://github.com/user-attachments/assets/cb689a9c-a8cd-4ec2-9774-cb03c5efd5f4" />

3.不知道是不是我的错觉，感觉字体有点大。每周课表2×2小组件字体遮盖第一个切换箭头。（如第一个视频所示）\n\n### lingion — 2026-09-11T15:12:55Z\n\n1. 切换箭头:2×2 是妥协的结果,宽高更大的尺寸上箭头才放得下。2×2 太小,我本来是打算把这个切换按钮去掉的,现在还留着,反而多了点歧义,我会改掉。

2. 4×5 显示不完全、组件内不能滑:我会去翻荣耀的小组件规范排查。

这套每周课表小组件是针对 #24 做的新功能,还不成熟,给你添麻烦了,后面会好好打磨。荣耀的适配我接下来会专门做。

感谢反馈。\n\n### lingion — 2026-09-14T15:06:56Z\n\n这个 issue 系列修了几轮,v1.0.55 汇总一下当前状态:
- 添加组件静默失败:配置页启动方式已修正(v1.0.54 起);
- 翻页箭头点了打开应用:点按意图已重绑,恢复翻日期;
- 「载入窗口小部件时出现问题」:页脚用了一个启动器不支持的视图类型,已替换;
- 系统字号变化后组件不重绘:已改为立即重绘;
- 另外小组件整体重做:固定窗口分档 + 底部翻日期条,2×2 不会再出现点不了的裸箭头。

请在 v1.0.55 上重新添加试一下。如果还有问题,麻烦附一句 `adb logcat | grep -i appwidget` 的输出,荣耀的启动器行为需要日志才能进一步定位。

