---
type: TutorialStep
date: 2021-05-14
title: 打开 Gradle 项目
technologies:
  - gradle
topics:
  - gettingstarted
author: tg
subtitle: 打开现有 Gradle 项目需要了解的内容
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/6V6G3RyxEMk?start=586
---

我们已经介绍了如何创建新的 Gradle 项目，让我们来看看可能更常见的情况，将现有的 Gradle 项目导入到 IntelliJ IDEA。

在这个例子中，我们将看看如何从本地目录打开一个 Gradle 项目，我们也可以很轻松地从远程存储库克隆代码，它们的工作方式类似。

在[欢迎画面](https://www.jetbrains.com/help/idea/new-project-wizard.html)我们可以选择“打开”，然后选择带有项目代码的目录。

![打开已有项目](./open-project.png)

IntelliJ IDEA 将在项目中寻找已知的构建系统，例如 Maven 和 Gradle，或 IntelliJ IDEA 的配置文件。

我选择的这个项目是一个多模块的 Gradle 项目，它具有[ Gradle Wrapper ](https://docs.gradle.org/current/userguide/gradle_wrapper.html)的设置。

![项目文件](./existing-project.png)

`settings.gradle` 文件里说明哪些模块组成了这个 Gradle 项目，并且每个模块都包含自己的 `build.gradle` 文件。

这个项目没有任何 IntelliJ IDEA 的设置，IntelliJ IDEA 会使用 Gradle 的配置来确定项目的结构、各个依赖项以及如何构建项目。

![导入的 Gradle 项目](./multi-module-project.png)

IntelliJ IDEA 会为这个多模块的 Gradle 应用程序中的每个子项目创建 IntelliJ IDEA 的模块。

这些 IntelliJ IDEA 模块中的每一个，本身就是一个 Gradle 项目，有自己的 `build.gradle` 以及自己的任务和依赖项。 如果我们打开 Gradle 工具窗口，就可以看到整个项目顶级的任务，以及每个子项目或模块的任务和依赖项。 这些可能各自不同，因为它们反映了每个模块的 `build.gradle` 文件中配置的内容。

![Gradle 工具窗口](./gradle-tool-window.png)

我们可以通过双击 Gradle 工具窗口中的 `build` 任务来构建整个项目，以查看它是否完全可以按照我们的预期工作。

如果它可以被成功构建，那么恭喜！

我们应该看到 Gradle 已经创建了一个目录，“build” 用于构建的输出。 IntelliJ IDEA 将其识别为输出目录，并将其标记为橙色（[已排除](https://www.jetbrains.com/help/idea/content-roots.html#folder-categories)）。 这意味着此处的文件不会被视为项目代码，也不会对它们进行索引编制。

![构建输出文件夹](./build-output.png)

接下来，让我们仔细看看 [Gradle 工具窗口](https://www.jetbrains.com/help/idea/jetgradle-tool-window.html)。