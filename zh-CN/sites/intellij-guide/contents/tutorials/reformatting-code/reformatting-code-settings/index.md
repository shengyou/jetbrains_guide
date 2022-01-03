---
type: TutorialStep
date: 2021-09-06
title: 重新格式化代码设置
technologies: [ ]
topics: [ ]
author: hs
subtitle: 重新格式化代码的设置以及在哪里可以找到它们
thumbnail: ./thumbnail.png
---

## 更改代码格式化设置的方法
您可以按 **⌘,**（macOS），或 **Ctrl+Alt+S**（Windows/Linux）来打开设置对话框，查看代码格式化设置。 此对话框是可搜索的，因此查找设置的最快方式是搜索 _代码样式_。 然后，您可以选择要更改设置的编程语言。 这个教程里，我选择 _Java_。

在更改设置之前，请注意这些设置是分别在项目级别和 IDE 级别定义的。 您只能有一个项目级别的设置，它适用于您当前的项目。 要更改它，您需要首先选择默认的 IDE 级别设置，然后按下拉菜单旁边的小齿轮并选择“副本”。 如果愿意，您可以随后将此设置复制到您的项目级别设置中。

![复制代码样式](copy-code-style-scheme.png)

这里有很多设置，熟悉它们的最简单方法是四处浏览并尝试，选择或清除复选框，然后查看对右侧代码的影响。 实时预览非常有助于了解设置将影响些什么。

As a side note, if you do make some changes here, and you want to reset them without resetting all the settings, you can click the blue **Reset** link on the top-right of this dialog. 只有当您更改了设置后，它才会显示。

If you go to the **Wrapping and Braces** tab and then scroll down to **'for()' statement**, you will see the **Force braces** change we made earlier when we changed it to _Always_.

![对于 for 循环 - 始终添加大括号](for-statement-braces-setting.png)

## 重新格式化后再提交
通常，您会希望在提交代码之前应用重新格式设置（无论是整个类还是仅仅针对您更改的代码）。 我们将在下一步中看看如何做到这一点。 