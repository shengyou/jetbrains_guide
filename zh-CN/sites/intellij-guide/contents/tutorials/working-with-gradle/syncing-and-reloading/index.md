---
type: TutorialStep
date: 2021-05-14
title: 同步和重新加载
technologies:
  - gradle
topics:
  - 构建
author: tg
subtitle: 有些时候您可能需要让 IntelliJ IDEA 重新加载 Gradle 配置中的更改。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/6V6G3RyxEMk?start=917
---

我们看到 IntelliJ IDEA 通常会在 Gradle 构建文件或设置发生更改时告诉我们需要触发 Gradle 设置的重新加载，以便 IntelliJ IDEA 可以使用新的设置。 我们可以 [设置](https://www.jetbrains.com/help/idea/jetgradle-tool-window.html) IntelliJ IDEA 的 Gradle 同步方式，在[ Gradle tool window （Gradle 工具窗口） ](https://www.jetbrains.com/help/idea/jetgradle-tool-window.html)中按设置按钮，然后选择**Auto-Reload Settings（自动重新加载设置）**。

![打开用于加载的 Gradle 设置](./gradle-load-settings.png)

我们可以将 IntelliJ IDEA 设置为，在更改构建脚本文件中的 "Any changes"（任何变更）内容后，自动重新加载项目，以便应用这些变更后的设置。 或者，我们可以仅在外部系统进行更改后才自动重新加载项目，例如从版本控制系统中获取更新的文件。 默认情况下，“External Changes”（外部变更）会是选中的状态。 这可以防止在每次小更改后重新加载项目，并且能让我们（开发人员）决定何时要重新加载更改。

![Gradle 设置](./gradle-settings.png)

我们可以选择在任何更改后不重新加载，以方便我们控制，但由于我们可能并不总是知道是否需要重新加载，因此选择 “External Changes”（外部变更）至少可确保 IntelliJ IDEA 自动应用这些更改。

正如我们之前所看到的，当我们对构建文件进行更改时，我们可以使用  **⇧⌘I**（macOS），或 **Ctrl+Shift+O**（Windows/Linux）重新加载这些更改。

![加载更改](./load-gradle-changes.png)

有时我们会想要强制重新加载整个项目，以便 IntelliJ IDEA 使用 Gradle 设置和构建项目。 在进行大量外部更改后，或者如果项目的行为不符合我们的预期，这个功能可能特别有效。

![重新加载所有项目](./reload-all-projects.png)

有时，执行重新加载，然后 [重新构建](https://www.jetbrains.com/help/idea/compiling-applications.html?keymap=primary_windows#rebuild_project) 很有用，方法是从 **构建** 菜单里选择 **重新构建项目**。 这是一个确保整个项目完全同步并正确构建的好方法。

接下来，让我们看看 IntelliJ IDEA 中一些更有用的 Gradle 设置。
