# [Bug]: 正方教务同名称课程不同地点导入时错误\n\n- Number: #22\n- State: closed\n- Author: dark-knifes\n- Created: 2026-09-06T21:05:58Z\n- Updated: 2026-09-09T04:51:13Z\n- URL: https://github.com/lingion/sleepy/issues/22\n\n## Body\n\n### Prerequisites

- [x] I am using the latest version of Sleepy
- [x] I have searched existing issues and found no duplicate
- [x] I will attach logs, screenshots, or a sample schedule file if helpful

### Current behavior

注意到当从教务导入相同名字不同地点时的课程，即使地点不同，时间是共享的。例如某新时代特色思想有线上下两种上课方式，删除一次线上课的部分会导致所有地点被线上课覆盖

### Expected behavior

线上和线下分为两门课或者时间根据地点区分开

### Steps to reproduce

1.导入课表
2.修改冲突课程上课时间
3.复现

### Schedule source

_No response_

### Additional context

_No response_

### Diagnostic info (auto-filled by app)

```markdown

```
\n\n## Comments\n\n### dark-knifes — 2026-09-06T21:10:35Z\n\n仅名字相同，地点老师均不同但共用时间的两门课
<img width="1440" height="6275" alt="Image" src="https://github.com/user-attachments/assets/44a7367e-c777-4ec8-bfb7-22eae0aa4673" />
<img width="1440" height="5568" alt="Image" src="https://github.com/user-attachments/assets/83dda0db-930e-4380-88a1-c4aff0f3fdd8" />\n\n### lingion — 2026-09-07T00:13:30Z\n\n感谢你补充的截图和说明。你提到的情况是：课程名相同、地点和老师不同，但导入后共用同一份时间；修改线上课后，其他地点的课程也跟着被覆盖。这个问题我记下了。

我会继续排查同名课程的区分方式，争取在接下来的两个版本内修好。\n\n### lingion — 2026-09-09T00:44:37Z\n\n这个在 v1.0.52 修了:https://github.com/lingion/sleepy/releases/tag/v1.0.52

同名课不再合并成一门:每个地点/老师各成一个课块,各自的老师、地点、备注、颜色都保留,导入预览会提醒你同名课有多个地点。改其中一个课块,不会再把同名的其他课块一起覆盖。
\n\n### jim139129 — 2026-09-09T03:35:09Z\n\n> 同名课不再合并成一门

其实把教室和地点放到上课时段里面配置会不会更合适？同名课程绝大多数情况就是一门课，只不过可能在不同地点授课。和“周次范围”一样给一个一键全部应用的选项，这样也方便手动配置。\n\n### dark-knifes — 2026-09-09T03:37:07Z\n\n> > 同名课不再合并成一门
> 
> 其实把教室和地点放到上课时段里面配置会不会更合适？同名课程绝大多数情况就是一门课，只不过可能在不同地点授课。和“周次范围”一样给一个一键全部应用的选项，这样也方便手动配置。

附议，这样感觉更好\n\n### lingion — 2026-09-09T03:54:16Z\n\n> > 同名课不再合并成一门
> 
> 其实把教室和地点放到上课时段里面配置会不会更合适？同名课程绝大多数情况就是一门课，只不过可能在不同地点授课。和“周次范围”一样给一个一键全部应用的选项，这样也方便手动配置。

我可能没看懂您的意思，也有可能是我上一条回复不够明确。现在已经是每一个上课时段里面都可以编辑各自时段、授课老师和上课地点了。\n\n### jim139129 — 2026-09-09T04:40:44Z\n\n> > > 同名课不再合并成一门
> > 
> > 
> > 其实把教室和地点放到上课时段里面配置会不会更合适？同名课程绝大多数情况就是一门课，只不过可能在不同地点授课。和“周次范围”一样给一个一键全部应用的选项，这样也方便手动配置。
> 
> 我可能没看懂您的意思，也有可能是我上一条回复不够明确。现在已经是每一个上课时段里面都可以编辑各自时段、授课老师和上课地点了。

那就是对的，我误解了回复，其实就是这么实现的
