---
type: TutorialStep
date: 2021-05-15
title: 运行 Gradle 任务
technologies:
  - gradle
topics:
  - 构建
author: tg
subtitle: 有多种方便的方法可以从 IntelliJ IDEA 中运行 Gradle 任务。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/6V6G3RyxEMk?start=824
---

我们之前已经了解到，可以在 Gradle 项目的[ Gradle 工具窗口](https://www.jetbrains.com/help/idea/jetgradle-tool-window.html)里导航到特定的 [Gradle 任务](https://docs.gradle.org/current/userguide/more_about_tasks.html) ，然后双击该任务让 IntelliJ IDEA 运行它。

![选择一个 Gradle 任务来运行它](./gradle-task.png)

我们还可以点击 Gradle 工具窗口顶部的大象来运行任何 Gradle 任务。

![Gradle 大象按钮](./elephant.png)

IntelliJ IDEA 用常见的 Gradle 任务和我们最近运行的任务来显示在这里。

![运行 Gradle 命令](./run-gradle-command.png)

这是运行多个 Gradle 任务的好方法，就像从命令行运行一样。 例如，运行  `gradle clean build`，以确保在提交更改之前一切如预期一样。

您可能已经注意到，这实际上使用了 [运行任何内容](https://www.jetbrains.com/help/idea/jetgradle-tool-window.html) 对话框，我们也可以通过按 Ctrl 两次来调出该对话框。 按**⌃⌃**（macOS），或**Ctrl+Ctrl** （Windows/Linux），输入“gradle”，后面跟着一个或多个 Gradle 任务的名称。

当然，我们也可以从 IntelliJ IDEA 内部的终端窗口运行 Gradle 命令。 按 **⌥F12**（macOS），或 **Alt+F12** （Windows/Linux）就可以打开终端窗口。

![打开终端窗口](./terminal.png)

如果我们输入一个 Gradle 命令，IntelliJ IDEA 会高亮显示它。 这意味着这是一个可以在 IDE 中运行的命令，不必从命令行运行。

![终端命令高亮显示](./terminal-ide-command.png)

如果我们按 **Enter**，它将像我们预期的那样从命令行运行。 如果我们按 **⌘⏎**（macOS），或 **Ctrl+Enter** （Windows/Linux），此命令将在 IntelliJ IDEA 中运行。 在这种情况下，将打开 [运行工具窗口](https://www.jetbrains.com/help/idea/jetgradle-tool-window.html) 并在其中运行命令。 我们看到的结果与从 Gradle 工具窗口运行的相同。

![运行窗口中的 Gradle 任务](./gradle-run-window.png)

接下来，让我们看一下在 IntelliJ IDEA 中使用Gradle的一些技巧。