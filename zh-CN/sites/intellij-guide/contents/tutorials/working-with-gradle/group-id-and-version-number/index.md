---
type: TutorialStep
date: 2021-05-14
title: 组 ID 和版本号
technologies:
  - gradle
topics: [ ]
author: tg
subtitle: 如何设置或更改项目的组 ID 和版本号。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/6V6G3RyxEMk?start=537
---

现在我们已经介绍了 Gradle 项目的基础知识，让我们回过头来看看如何设置项目的 [groupID 和版本号](https://maven.apache.org/guides/mini/guide-naming-conventions.html) 。

让我们按照之前的相同步骤，使用 Java 和 Groovy DSL 创建一个新的 Gradle 项目。

![创建另一个新项目](./second-new-project.png)

输入项目名称后，例如 “more-gradle”，我们可以点击“工件坐标”为项目配置更多设置。

![工件坐标](./artifact-coords.png)

我们可以输入一个新的 GroupID，通常是公司的域。 如果我们尝试更改 ArtifactID，IntelliJ IDEA 会警告我们，它应该与项目名称相同。

如果我们的项目有不同的版本号，或者不同的版本号格式，我们也可以更改项目的版本号。

创建好项目时，我们可以看到在 build.gradle 文件中设置了 GroupID 和版本号。

```groovy
group 'com.jetbrains'
version '1.0-SNAPSHOT'
```

接下来，我们将看看如何打开现有的 Gradle 项目，以及 IntelliJ IDEA 能提供哪些帮助。