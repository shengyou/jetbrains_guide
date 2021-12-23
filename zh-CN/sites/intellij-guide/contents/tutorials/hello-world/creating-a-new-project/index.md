---
type: TutorialStep
date: 2021-25-08
title: 创建一个新项目
technologies: [ ]
topics: [ ]
author: hs
subtitle: 使用新项目向导创建新项目。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/H_XxH66lm3U?start=25
---

在此教程中，您将会创建、运行和打包一个简单的 Java 应用程序，该应用程序可以打印 "Hello World" 到系统输出。 您还将看到一些 IntelliJ IDEA 功能，这些功能可以提高您的工作效率，例如编码辅助和辅助工具。 本教程中的所有功能在 IntelliJ IDEA Community 和 IntelliJ IDEA Ultimate 中都可以使用。

**在每个教程步骤的底部，都有视频相关部分的链接。**

1）您可以使用[新项目向导](https://www.jetbrains.com/help/idea/creating-and-running-your-first-java-application.html)在 IntelliJ IDEA 中创建新项目。 在欢迎屏幕界面，您可以点击 **New Project（新建项目）**，或者如果您已经在一个项目里时，您可以使用 **File（文件）** > **New（新建）** > **Project（项目）**。

如果您之前还没有打开项目， **New Project（新建项目）** 选项位于欢迎屏幕中：

![Welcome Screen - New Project Highlighted](welcome-screen.png)

如果您以前已打开了一个项目， **New Project（新建项目）** 按钮将在顶部栏上。

![img.png](welcome-screen-existing-projects.png)

2）您需要创建一个 Java 项目，这是默认的选项。 您还需要从项目 SDK 下拉菜单中选择一个 JDK 用于编译此项目：

![Java Project and JDK selection](java-select-jdk.png)

IntelliJ IDEA 将在列表的顶部显示已配置的 JDK 列表，并在列表的底部显示它在您的机器上检测到的 JDK 的列表。 您可以选择其中的任何一个，或者您可以点击 **Download JDK（下载 JDK）**。

有许多不同的供应商打包和提供 Java。 该列表显示了一些最常见的。 OpenJDK 是 Oracle 的免费、开放的 JDK 构建，它将永远是最新的版本。 如果您选择另一个供应商，比如说 Adopt OpenJDK，您将看到该供应商所有可用的版本。

![Different JDK Vendors](different-jdk-vendors.png)

This tutorial doesn't need the latest version of Java, so feel free to select the one you're most comfortable with. Finally, if you want to use a JDK that's on your machine, but hasn't been detected by IntelliJ IDEA, you can press **Add JDK** to browse to it.

The IDE will spend a bit of time downloading and installing the Java Development Kit if you opted to download a JDK. You don't need to do any additional configuration once it's downloaded, IntelliJ IDEA handles that for you.

3) You don't need any additional libraries or frameworks for this tutorial so press **Next**


4) You could create a project from a template, but we're going to do everything from scratch for this tutorial, so press **Next**.

   ![No templates selected](no-templates.png)

5) You need to give your project a name. We recommend _HelloWorld_. You could change the default project location if you want to, but the default is fine for this tutorial.

   ![Name Project HelloWorld](name-hello-world.png)

6) Press **Finish** so IntelliJ IDEA can create your project.


---

