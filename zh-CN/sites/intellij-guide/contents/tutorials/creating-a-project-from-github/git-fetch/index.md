---
type: TutorialStep
date: 2021-11-09
title: Git Fetch（提取）
technologies: [ ]
topics: [ ]
author: hs
subtitle: 如何以及为什么调用 Git 提取
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/aBVOAnygcZw?start=292
---

您刚刚向此项目添加了一个新的远程，但它还未显示在 Git 日志工具窗口中。 这也意味着它的分支或提交都还看不到。 这是因为我们还没有提取新的远程的状态到我们的本地项目。 我们可以通过使用 ** Git > Fetch（提取）** 菜单来使用提取。 当您执行此操作时，IntelliJ IDEA 将从我们项目里有的 _all_ Git 仓库获取所有相关的详细信息，并且 Git 日志将使用这些详细信息来进行更新。 现在您可以在日志窗口中看到一个新的远程，并且我们可以看到该远程的所有分支。 我们还将能够在提交列表中看到远程的分支。 这使您清楚地知道哪些提交在哪些分支上，以及是否有什么分支需要更新。

![在 Git 日志工具窗里提取 Git 远程](git-fetch-remotes.png)

执行 Git 提取的另一个方法是点击 Git 日志窗口中分支树工具栏上的 **Fetch All Remotes（提取所有远程）** 按钮。 这也将会更新项目。

![提取所有远程按钮](fetch-all-remotes.png)