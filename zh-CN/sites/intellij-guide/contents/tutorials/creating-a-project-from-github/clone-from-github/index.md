---
type: TutorialStep
date: 2021-11-09
title: 克隆项目
technologies: [ ]
topics: [ ]
author: hs
subtitle: 从 GitHub 克隆您的项目
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/aBVOAnygcZw?start=9
---

我们需要做的第一件事是克隆仓库到我们的本地机器。 您需要导航到 GitHub 中您想克隆到 IntelliJ IDEA 的代码。 在本教程中，我们将使用 [ intellij-samples </em>项目](https://github.com/JetBrains/intellij-samples)。

![IntelliJ IDEA GitHub 仓库](github-project.png)

当您按绿色的 **Code（代码）**按钮，您可以看到有几种方式可以来执行。 我们将使用 HTTPS，因为它可能是最简单的选项。 在 HTTPS 选项卡中，点击剪贴板图标，这会将 URL 复制到您的剪贴板。

![使用 HTTPS 的 GitHub 克隆](github-clone-https.png)

现在您已经从 GitHub 获得了链接，您需要打开 IntelliJ IDEA。 如果您没有任何项目选项，您将会看到欢迎屏幕。 您将会看到这里有一个选项，**Get from Version Control（从版本控制获取）**，或者类似的选项（取决于 IntelliJ IDEA 版本）。  如果您已经有一个项目打开了，您可以使用 **File（文件）> New（新建）> Project from Version Control（来自版本控制的项目）** 来做相同的操作。 在较旧版本的 IntelliJ IDEA 中，您还可以使用 **VCS > Get from Version Control（从版本控制获取）**。 此菜单选项已经在新版本中，重命名为 **Git > Clone（克隆）**（当您打开了一个现有的 Git 项目）。

![IntelliJ IDEA 中的从版本控制中获取](intellij-clone-button.png)

当您按下此按钮时，您将看到一个选项，可以用于选择您的版本控制的位置（在本例中为 GitHub），然后从您的剪贴板里输入 URL 到 URL 字段。

![GitHub 克隆对话框](github-clone-dialog.png)

按 **Enter** 或 **Clone（克隆）** 将 GitHub 仓库克隆到您所选的目录。 IntelliJ IDEA 还将会选取插件的构建工具，比如说 Gradle 或 Maven，自动下载所需的依赖项，并构建项目。

当您打开项目窗口时，在一个像这样的 Maven 项目下，您还将看到 IntelliJ IDEA 已检测到了该项目中的模块，并正确设置了 _test_，_main_ 和 _resources_ 文件夹。

![项目窗口](project-window.png)

### Related YouTube Links
- [Cloning a Project from GitHub](https://www.youtube.com/watch?v=aBVOAnygcZw)