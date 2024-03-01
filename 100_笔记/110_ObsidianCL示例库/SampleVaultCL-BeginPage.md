---
Date: 2024-02-20 23:16:05
Author: CL
cssclasses:
  - darkblue
  - wideTable
  - darkblue-rounded
---
# CL 的示例库介绍

>[!question] **欢迎使用 CL 的示例库，您想要了解些什么？**
> - **简单介绍**下这个示例库：[[SampleVaultCL-BeginPage#简要的介绍|简要的介绍]]
> - 新增的**待办管理**功能怎么用：[[SampleVaultCL-TaskManagerGuide|待办管理功能使用说明]]
> - 没有用过 **markdown** 语法的笔记软件，速度说下文本编辑相关的功能：[[SampleVaultCL-ObsidianQuickStartGuide|Obsidian快速开始]]
> - 告诉下**常用的快捷键**：[[SampleVaultCL-HotKeys|常用快捷键]]
> - obsidian 没有免费的云端备份服务，怎么**用 Git 进行云端备份**
> 	1. Git 是什么？需要了解下 Git 和其基本的使用方法：[[Git 的使用]]
> 	2. 管他 Git 是什么，说下每一步的配置方法，照做配好后只要按个按钮就行的那种：[[使用 Obsidian Git 插件备份笔记]]

---
## 简要的介绍

- 对主题、外观、样式进行了调整
- 以简化输入为目的新增了必要的插件
	- 通过 *QuickAdd* 插件增加：`Ctrl+Q` 快捷键有配置了一些快速输入提示框的选项
	- *EasyTyping* 插件
		- 框选文字按下引号、括号等为在框选文字两侧增加双引号、括号等
		- 使用中文输入法时，连续按下两个逗号、句号等标点符号，会将中文标点转换为英文标点
		- 自动在中文和英文单词之间增加空格，英文首字母自动大写等等
		- **这个插件的在输入时的自动修改可以通过** `Ctrl+Z` **取消**
- 结合 *Templater*、*Dataview*、*Tasks*、*Charts*、*Calendar* 插件制作了一个简单的任务管理的自动化流程作为 *obsidian* 客制化的小示例

这是一个精简的、近乎无客制的示例库，*obsidian* 是允许高度客制化的开源笔记软件，通常而言，有兴致的使用者常会花很多时间鼓捣插件、编写脚本使得笔记库过于个人化。但是过于个性而复杂的示例库其实很难开箱即用，容易让人望而却步，并存在较高的维护开销。

这个示例库尽力做了减法，希望能够让 *obsidian* 在更加的好看、好用一些的同时，尽可能轻量，*obsidian* 是一款很优秀的笔记软件。

### 关于工具栏按钮

关于对左侧工具栏按钮的调整如下图所示：

![[SampleVaultCL-BeginPage 2024-02-25 22.27.33.excalidraw|700]]

### 关于表格样式

表格样式通过文档属性的 *cssclasses* 属性定义，在 *000_收件* 文件夹新建的笔记，通过 `ctrl + o` 快捷键新建的笔记，以及通过新标签页新建的笔记都默认在 *000_收件* 文件夹新建，会自动配置相关的属性，这是通过 Templater 插件实现的，相应的模板路径为 *500_模板/默认收件模板*

在 *500_模板/tablesCSS* 文件夹下，您可以找到不同的可用表格样式的属性值。

![[Pasted image 20240226005812.png]]

### 关于代码块

如下，代码块可以通过 `nums` 显示行号，通过 `{1,2,4-6}` 的形式高亮特定行。功能来自插件 *Advance Codeblock*

```python nums {2,4, 7-8}
# python code block
import json


print('Hello')




```

[[SampleVaultCL-BeginPage#CL 的示例库介绍|-->返回]]