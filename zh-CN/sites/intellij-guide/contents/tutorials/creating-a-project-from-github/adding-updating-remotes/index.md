---
type: TutorialStep
date: 2021-11-09
title: 添加和更新远程
technologies: [ ]
topics: [ ]
author: hs
subtitle: 管理您的仓库的远程
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/aBVOAnygcZw?start=173
---

当您在 GitHub 上处理开源项目时，通常会有多个远程与一个仓库相关联。 如果您回到我们之前从 GitHub 克隆的 intellij-samples 项目的话，我们可以看到这实际上是另外一个仓库的 fork（复制）。

![在 GitHub 里复制仓库](contents/tutorials/creating-a-project-from-github/adding-updating-remotes/github-fork.png)

这个上游的仓库是在 JetBrains 的组织里的，并且可能会有很多人以不同于我的速度来更新这个复制。 理想的情况，您会希望能看到上游仓库和您自己的复制，以便更好地了解有哪些变化，并用这些变化来更新我们自己的复制。

要做到它，可以使用我们之前使用的方法，使用 **Code（代码）** 按钮，然后复制 HTTP 链接到您的剪贴板来复制_上游_仓库的 URL。

![从 GitHub 里拷贝上游的仓库链接](upstream-link.png)

现在，让我们来按 **Shift** 键两次，来使用 Search Everywhere（随处搜索）。 在随处搜索对话框，输入 _Remotes（远程）_，其中的一个搜索结果是 _Git_ 下的 _ Manage Remotes（管理远程）_选项。 在该选项上按 **Enter** 来显示 **Git Remotes（Git 远程）**对话框。

![随处搜索 - 管理远程](search-everywhere-manage-remotes.png)

在这里，我们可以看到我们最初克隆此项目的远程，这是我们 _intellij-samples_ 仓库的复制。 我们希望为上游仓库（即最初的 JetBrains 仓库）添加新的仓库。

让我们通过按 **+** 按钮来添加此仓库。 现在您可以给它起个名字，并把剪贴板上的 JetBrains 仓库的路径粘贴进去。 您可以使用许多不同的惯例来决定您的远程的名字，比如说您可以叫它 "upstream"。 我们建议您使用组织或者配置名字来消除歧义。 如果有需要的话，您也可以使用此对话框来对您现有的远程进行更改。 例如，如果是您的特定分支，您可以将 "origin" 远程重命名为您的名字，就像本例子中的那样。

![在 IntelliJ IDEA 中添加远程](add-remote-intelij-idea.png)

当您在您的新的远程上按 **OK**，Git 远程对话框将会显示您的两个远程。

![添加和重命名远程](add-rename-remotes.png)

与 IntelliJ IDEA 中的大多数功能一样，有多种方法可以打开管理远程的对话框。 您还可以在 Git 日志工具窗口的分支树上右键_远程_节点，选择 **Manage Remote（管理远程）**。

### Related YouTube Links
- [Adding a Project to Git and GitHub](https://www.youtube.com/watch?v=mf2-MOl0VXY)