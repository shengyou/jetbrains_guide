---
type: TutorialStep
date: 2021-05-20
title: 创建一个用 Spock 测试的项目
technologies: [ ]
topics:
  - gettingstarted
author: tg
subtitle: 首先创建一个新的 Java 项目，该项目将成为本教程其余部分的基础。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=10
---

让我们首先创建一个包含 Java 代码的新项目，并使用 Spock 对该代码进行单元测试。

从新建项目窗口中，我们可以选择以下任一选项：
- Java
- Maven
- Gradle

...从左侧选择创建我们的 JVM 项目。 在本教程中，我们将使用 [Gradle](../../working-with-gradle) 作为构建工具。

![](./01-new-project.png)

Spock 是一个 [Groovy](../../../technologies/groovy) 测试框架，尽管我们将使用它来测试 Java 代码，所以我们可以选择一开始就添加 Groovy 作为一个额外的库。 然而，我们也可以以后再添加 Groovy，因此我们暂且不在此处选择它。

我们在这个项目中使用 JDK 11，但这里没有需要 11 里特有的功能，你可以使用任何版本。

将项目命名为 `spock-tutorial`，并将其保存到可用的位置。

![](./02-project-name.png)

IntelliJ IDEA 会为项目创建文件并初始化项目的结构。 Gradle 会构建此项目，以确保下载并设置所有依赖项。

现在我们有一个简单的 Java 项目可以用了，然后进入下一步，添加 Spock 依赖项。

