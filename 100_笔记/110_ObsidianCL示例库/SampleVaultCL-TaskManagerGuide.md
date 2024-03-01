---
Date: 2024-02-21 10:57:34
Author: CL
cssclasses:
  - darkblue
  - wideTable
  - darkblue-rounded
---
# 待办管理功能使用说明

## 标签系统

这个功能结合了 Obsidian 自带的标签系统，通过 `#标签文本` 标识标签，标签具有层级 `#主标签/二级标签/三级标签` 以此类推。 #主标签/二级标签/三级标签

首先需要说明待办的格式，使用这个功能需要用以下格式输入待办任务：

```text nums
按下Ctrl+Enter两次插入待办事项
输入这样的内容：

#类别/名称 #其他任务标签（可多个） 任务描述
```

以上输入在软件中会被自动渲染为如下形式，以下为一些示例：

- [ ] #个人/学习 #效率工具 Obsidian 使用
- [ ] #个人/测试 #效率工具 Obsidian 自动化流程测试
- [ ] #项目/项目名称A #项目验收 #文档输出 项目验收文档
- [ ] #项目/项目名称B #项目启动 #会议沟通 项目启动会

虽然目前只有 #个人/ #部门/ #项目/ #客户/ 四个主标签有标签颜色的改变，但是功能上您可以在输入的时候使用任意的主标签，比如 #测试/ 。

>[!question] 需要自定义更多的标签颜色？ [[自定义标签颜色]]
## 开始使用

### 创建与完成待办

按下 `Ctrl+Q` 选择 *在新窗口打开待办板和当周记录*

![[Pasted image 20240225231859.png]]

在输入框中按照上面的格式输入待办事项即可自动创建，**这里的输入请省略掉开头的** `- [ ]`。*图片小的话，点击图片可以滚轮放大*

![[SampleVaultCL-TaskManagerGuide 2024-02-25 23.22.07.excalidraw|1200]]

>[!info] 您可以在右侧日历的日记页面查看待办任务实际被保存的情况
>日记文件的标题被视为任务的创建时间，当勾选完成任务时，*task* 插件会自动创建完成的日期，这便是原理。
>![[Pasted image 20240225233050.png]]

>[!info] 自动的周汇总，根据带有 `\` 的标签对待办事项进行分类汇总。
### 待办的排期

>[!note] 待办板的任务列表仅显示 **排期在当天以前且未完成的任务** 和 **当天完成的任务**

也就是，如果排期在明天及以后的话，待办不会显示在任务列表，需要等到排期当天才会显示，如下图，您可以右键⏩符号排期任务

![[SampleVaultCL-TaskManagerGuide 2024-02-25 23.36.56.excalidraw|1200]]

### 循环的任务
在右上角的**书签栏**（*功能上类似收藏夹*），点击循环任务设置。

![[SampleVaultCL-TaskManagerGuide 2024-02-25 23.42.56.excalidraw|1200]]

| 常见循环语法示例 | 含义 |
| ---- | ---- |
| every 3 days | 每三天自动创建 |
| every 10 days when done | 每次事项完成时的第 10 天后 |
| every week | 每周，和创建的星期相关，如果第一次排期在周二，every week 则每周二自动创建 |
| every week on Tuesday，Friday | 每周二和每周五 |
| every 3 weeks on Friday | 每三周的周五 |
| every 2 months | 每两个月 |
| every months on the 1st | 每月第一天 |
| every months on the last | 每月最后一天 |
| every months on the last Friday | 每月的最后一个周五 |
| every months on the 2nd last Friday | 每月的倒数第二个周五 |
| every January on the 15th | 每年一月 15 号 |
| every April and December on the 1st and 24th | 每年四月的 1 号和 24 号，以及每年 12 月的 1 号和 24 号 |
| every year | 每年 |

更多内容参考 tasks 插件说明：[Tasks插件-循环任务说明](https://publish.obsidian.md/tasks/Getting+Started/Recurring+Tasks)

### 统计查询功能

在书签的待办事项统计板打开，您也可以直接在下面看到和尝试。您可以直接点一下 *查询* 试试。

![[待办事项统计板]]

子标签统计查询，是查询某个或某几个子标签，如 #个人/测试 #个人/学习 #个人/测试2 ，这里就有个人主标签的三个子标签，为*测试、学习、测试2*，主要标签 #个人 ，子标签包含**学习**，就是查询 #个人/学习 类任务共分别有多少个其他标签，并绘制成图。子标签可以为空，意思就是全查。

[[SampleVaultCL-BeginPage|-->返回]]