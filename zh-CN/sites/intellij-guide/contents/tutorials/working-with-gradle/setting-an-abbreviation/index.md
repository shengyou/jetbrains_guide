---
type: TutorialStep
date: 2021-05-14
title: 设置缩写
technologies: [ ]
topics:
  - tricks
author: tg
subtitle: 使用唯一的缩写快速导航到 Gradle 工具窗口
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/6V6G3RyxEMk?start=767
---

您可能已经注意到，当我们在随处搜索选项中输入 “Gradle” 时，会有很多结果。 我们希望可以提供一种快速访问 Gradle 工具窗口的方法。

当然，您可以 [设置键盘快捷键](https://www.jetbrains.com/help/idea/configuring-keyboard-and-mouse-shortcuts.html#add-keyboard-shortcut)，并且可能需要设置一个用于打开 Gradle 工具窗口的快捷键。

或者，我们甚至可以 [添加一个缩写](https://www.jetbrains.com/help/idea/configuring-keyboard-and-mouse-shortcuts.html#add-abbreviation).。

按 **⌘,**（macOS），或 **Ctrl+Alt+S** （Windows/Linux），然后打开“设置/首选项”对话框的“键盘映射”，右键单击某个操作，然后选择 **添加缩写**。

![添加缩写](./add-abbreviation.png)

我们可以设置一个简短，好记忆的文本字符串，然后就可以在搜索 Gradle 工具窗口时使用它。 例如，输入 “grdl”，然后按 **Enter**，或 **OK**。

![输入缩写](./abbreviation-to-use.png)

现在，如果我们通过按两次 **Shift** 来打开“随处搜索”对话框，然后输入 "grdl"，我们将看到 Gradle 工具窗口作为第一个结果，它不会隐藏在类似结果的列表中。

![输入缩写](./grdl-search-results.png)

接下来，让我们看一下如何运行 Gradle 任务。