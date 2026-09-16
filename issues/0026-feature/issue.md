# [Feature]: 支持课程别名/简写\n\n- Number: #26\n- State: closed\n- Author: jim139129\n- Created: 2026-09-07T07:35:50Z\n- Updated: 2026-09-13T04:48:41Z\n- URL: https://github.com/lingion/sleepy/issues/26\n\n## Body\n\n### Prerequisites

- [x] I have searched existing issues and found no duplicate
- [x] I have confirmed this feature is not already in the latest release

### Problem or motivation

课表上的课程名称一般很长，在手机上有时候显示不全，但毕竟课表是给**人**看的，能看懂就行了。“模电”看着比“模拟电子技术...”看着舒服一些

### Proposed solution

给每个课程配置一个可选的“别名”选项，并允许在课表-周视图、网络视图、小组件中分别配置显示原名还是别名

### Alternatives considered

_No response_

### Additional context

_No response_

### Diagnostic info (auto-filled by app)

```markdown

```
\n\n## Comments\n\n### lingion — 2026-09-07T09:07:39Z\n\n感谢你的建议！课程别名/简写确实能改善长课程名称在手机上的显示体验。这个功能本身规模不大，不过目前手上积攒的 Issues 比较多，我会安排在接下来的 3 个版本内完成。届时会考虑支持按场景选择显示课程原名或别名。\n\n### lingion — 2026-09-11T12:26:15Z\n\n课程别名在 [v1.0.53](https://github.com/lingion/sleepy/releases/tag/v1.0.53) 交付了,和你提的方案一致:

编辑课程时多一个"别名"输入,比如"模拟电子技术"可以设成"模电"。周视图、网格视图、小组件三个场景各自选显示原名还是别名,默认全显示原名,不改任何行为。别名随 sleepy-v1 导入导出文件走,老文件导入不受影响。

"模电"看着确实舒服些。\n\n### jim139129 — 2026-09-11T16:10:43Z\n\n1.0.53别名无法保存\n\n### lingion — 2026-09-11T16:18:03Z\n\n收到 我紧急修复\n\n### lingion — 2026-09-11T23:46:02Z\n\n修好了,在 [v1.0.54](https://github.com/lingion/sleepy/releases/tag/v1.0.54),升级重试即可。

问题出在保存路径:编辑课程落库前有一层逐字段的行比对,字段清单里漏了别名。结果就是你只改别名、其他都不动时,比对结果判成「没变化」,保存动作被直接跳过,写进数据库的还是旧值。这也是为什么名字、教室这些改动一直正常,唯独别名存不上。

现在别名和其余字段一样参与比对,改别名能正常保存,清空别名也能存回去。场景开关(设置 → 主页显示设置里的「周视图显示别名」「网格视图显示别名」)不消再动,打开开关就能看到。

如果是导入的课表,别名要先在课程编辑里手动填,导入不会自动生成。
