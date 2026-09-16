# [Feature]: 小组件增加多重尺寸\n\n- Number: #21\n- State: closed\n- Author: dark-knifes\n- Created: 2026-09-06T20:48:53Z\n- Updated: 2026-09-14T15:26:57Z\n- URL: https://github.com/lingion/sleepy/issues/21\n\n## Body\n\n### Prerequisites

- [x] I have searched existing issues and found no duplicate
- [x] I have confirmed this feature is not already in the latest release

### Problem or motivation

注意到小组件并没有提供多个尺寸或者可变尺寸，这导致在改变小组件大小时会导致字体拉伸。比如最近两天的课程由4x3挤压成4x2时，字体会被压扁，关闭vivo自带的小组件优化时，小组件被裁剪。

### Proposed solution

我真的很需要一个4x2的格式，我认为作为wakeup的替代版甚至升级版，sleepy应该包容它已有的功能。

### Alternatives considered

_No response_

### Additional context

_No response_

### Diagnostic info (auto-filled by app)

```markdown

```
\n\n## Comments\n\n### lingion — 2026-09-07T00:13:31Z\n\n感谢你把小组件的实际表现写清楚了：最近两天课程从 4×3 压到 4×2 时字体会被压扁，关闭 vivo 的小组件优化后又会被裁剪。4×2 确实是一个很实际的尺寸需求。

我会处理多尺寸适配，争取在接下来的两个版本内修好。\n\n### lingion — 2026-09-14T15:07:00Z\n\nv1.0.55 已扩展:今日/最近两天/本周列表/周视图/网格五种形态,各有小、常规两档,今日/最近两天/本周列表另有矮而宽的宽档,共 13 档可添加;且每档按自身尺寸定死绘制,拖拽不再拉伸变形。麻烦更新后看看想要的尺寸覆盖到了没有。
\n\n### dark-knifes — 2026-09-14T15:26:57Z\n\n已解决
