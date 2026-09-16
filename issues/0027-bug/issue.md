# [Bug]: 东北大学教务系统无法导入\n\n- Number: #27\n- State: open\n- Author: jim139129\n- Created: 2026-09-07T09:10:47Z\n- Updated: 2026-09-09T00:44:41Z\n- URL: https://github.com/lingion/sleepy/issues/27\n\n## Body\n\n### Prerequisites

- [x] I am using the latest version of Sleepy
- [x] I have searched existing issues and found no duplicate
- [x] I will attach logs, screenshots, or a sample schedule file if helpful

### Current behavior

两个bug，首先是这个红色提示出现了除非退出到软件课表管理页否则不会消失

<img width="1272" height="2800" alt="Image" src="https://github.com/user-attachments/assets/510fd4c7-69ab-4d81-83d9-62df0eb186e1" />

其次现在教务系统是金智教务但是改了好几个版本，现有的软件无法正常提取，同学推荐的这个项目好像可以正常提取(我测试了安卓移植版可以用)
https://github.com/CreamPig233/neu_wisedu2wakeup
可以参考这个实现

### Expected behavior

正常提取课表并导入

### Steps to reproduce

-

### Schedule source

东北大学

### Additional context

如还需使用提供的工具提取教务页面可以晚一点提供

### Diagnostic info (auto-filled by app)

```markdown

```
\n\n## Comments\n\n### lingion — 2026-09-09T00:44:41Z\n\n导入这条修好了,改动就是你的 PR #29,已合入并随 v1.0.52 发布:https://github.com/lingion/sleepy/releases/tag/v1.0.52

课表提取换成金智新版的移动接口:先取当前学期和校区,再提交课表详情请求拿 arrangedList 解析。这套方案是你真机验证过的,装这版应该就能正常导入。

另外你提的红色错误提示不退出页面不消失的问题,这版没动,单独记着,后面排查。

