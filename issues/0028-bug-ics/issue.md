# [Bug]: ics导入节次混乱\n\n- Number: #28\n- State: closed\n- Author: jim139129\n- Created: 2026-09-07T09:55:23Z\n- Updated: 2026-09-15T03:41:54Z\n- URL: https://github.com/lingion/sleepy/issues/28\n\n## Body\n\n### Prerequisites

- [x] I am using the latest version of Sleepy
- [x] I have searched existing issues and found no duplicate
- [x] I will attach logs, screenshots, or a sample schedule file if helpful

### Current behavior

问题比较多，
1. 导入前自动识别每节课时间乱成一团
<img width="1271" height="1939" alt="Image" src="https://github.com/user-attachments/assets/012de399-0ca3-412d-8986-4169b8e054d1" />
2. 自动模式添加课间按钮无效

<img width="1271" height="2062" alt="Image" src="https://github.com/user-attachments/assets/5626a57f-d7c1-43fc-99d9-dce29dd87756" />
点了没有反应也不能用
3. 即使我手动调整了每日每节课的时间(从错误的16节改成正确的12节)，导入完课程仍然显示要在13-16节上课而不会自适应

<img width="1272" height="1624" alt="Image" src="https://github.com/user-attachments/assets/5728b952-4dda-4c40-a55a-38ef783ae111" />

<img width="1272" height="2668" alt="Image" src="https://github.com/user-attachments/assets/cc1e3e76-0fe8-4664-b79b-f331cc7e37f9" />

### Expected behavior

从ics导入对上下课时间识别更智能
手动调整上课时间后可以自动适配对应节次

### Steps to reproduce

导入示例ics文件
调整时间课次

### Schedule source

通用

### Additional context

[test-ics.zip](https://github.com/user-attachments/files/31907961/test-ics.zip)
导入此脱敏课表可复现

### Diagnostic info (auto-filled by app)

```markdown

```
\n\n## Comments\n\n### lingion — 2026-09-09T00:44:43Z\n\n这个 v1.0.52 还没修,如实说。

三个问题都看到了:ics 导入前自动识别的节次时间乱、自动模式的"添加课间"点了没反应、把时间表从 16 节改成 12 节后已导入的课仍挂在 13-16 节不跟随。脱敏复现文件已留档。

这版带出去的逐卡自定义节次能单独给一门课设自己的时间,但覆盖不了"导入时自动按时间表适配节次"这条链路,ics 导入的节次识别还是原样。等排查完在这里同步进展。
\n\n### lingion — 2026-09-11T12:26:04Z\n\n三个问题在 [v1.0.53](https://github.com/lingion/sleepy/releases/tag/v1.0.53) 都修了,逐条对上:

1. **导入前节次时间乱**:解析改按教学块整表重建。同一开始时刻的事件不再共享步数,节次时间不再倒挂,之前丢失的节次行也回来了。用你留档的脱敏 ics 验证:节次 1..12 连续、锚点时间准确。
2. **自动模式"添加课间"点了没反应**:按钮的改动没接进导入确认框,点击结果被丢了。已接上,点了就生效。
3. **改完时间表课程不跟随**:现在编辑作息保存时,课程按新旧表的绝对时间自动重排,16 节改 12 节后原来 13-16 节的课会落到新表对应的节次。

升级 v1.0.53 后用你那个测试文件再导一次,有问题继续发这里。
