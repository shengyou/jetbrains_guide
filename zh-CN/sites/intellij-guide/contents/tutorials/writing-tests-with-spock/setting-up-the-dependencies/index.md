---
type: TutorialStep
date: 2021-05-20
title: 设置依赖项
technologies:
  - gradle
topics:
  - testing
author: tg
subtitle: 将 Spock 框架依赖项添加到项目中
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=75
---

现在，项目的基础已经创建好了，让我们再仔细看看并设置所需的依赖项。

IntelliJ IDEA 会默认将 JUnit 5 添加为测试框架，这是一个符合逻辑的选择，但我们希望使用 Spock 而不是JUnit。 我们可以在 `build.gradle` 文件里通过 **⌘N** / **Alt+Insert** 为我们想要的库 [生成一个新的依赖关系](https://www.jetbrains.com/help/idea/work-with-gradle-dependency-diagram.html#add_gradle_dependency)，然后选择“添加 Maven 工件依赖项”。

![](./03-spock-dependency.png)

我们可以在搜索工件中搜索“spock”，并添加[ 最新版本的 spock-core 库 ](https://github.com/spockframework/spock/releases)。 目前的最新是 Spock 2.0：

 - 用 Groovy 3 的话，是 `org.spockframework:spock-core:2.0-groovy-3.0`
 - 用 Groovy 2 的话，是 `org.spockframework:spock-core:2.0-groovy-2.5`

这是一个测试依赖项，因此请确保用 `testImplementation` 声明了。

我们还需要依赖于 [Groovy](../../../technologies/groovy)，因为 Spock 测试是用 Groovy 编写的。 按照相同的步骤添加新的 Maven 工件依赖项，搜索 Groovy 并添加对 Groovy 3.0.8 的依赖项。 现在，我们只剩下使用 Groovy 进行测试了，所以我们也会将其声明为 `testImplementation` 。

您可以删除其他 JUnit 依赖项，因为我们不再需要它们，`build.gradle` 里面的依赖项应如下所示：

```groovy
dependencies {
  testImplementation 'org.spockframework:spock-core:2.0-groovy-3.0'
  testImplementation 'org.codehaus.groovy:groovy-all:3.0.8'
}
```

由于我们使用的是Groovy，因此我们需要将 [Groovy 插件](https://docs.gradle.org/current/userguide/groovy_plugin.html) 添加到 Gradle 中。 当我们使用 Groovy 插件时，我们不需要专门添加 Java 插件，因为所有这些功能都包含在 Groovy 插件中。 我们可以删除 `java` 插件，这样可以减少构建文件里面的冗余。 我们也可以保持插件部分是明确的，或者删除它以变得更简洁，这取决于我们自己的偏好。

```groovy
plugins {
    id 'groovy'
}
```

[完整的 build.gradle 代码](https://github.com/trishagee/spock-testing-demo/blob/1ced2b4d118a3bcb418f05c1470dbef665b8eee9/build.gradle)

现在，我们可以使用 **⇧⌘I**（macOS），或 **Ctrl+Shift+O**（Windows/Linux）加载所有 Gradle 的更改，IntelliJ IDEA 将下载所有新的依赖项，删除旧依赖项，并正确配置项目。

对于像这样的混合编程语言项目，组织文件结构的一种方法是将 Java 代码保存在 `java` 文件夹中，并为 Groovy 代码创建一个 `groovy` 文件夹。

从项目窗口中，选择 `test` 文件夹，然后按 **⌘N**（macOS），或 **Alt+Insert**（Windows/Linux）。 选择“目录”，然后在 **新建目录** 对话框中输入“groovy”。 IntelliJ IDEA 应该会在下拉列表中建议“groovy”，因为我们在 Gradle 中使用 Groovy 插件。

![](./04-groovy-dir.png)

现在，您应该了解了如何设置项目以使用 Spock。 接下来，我们将创建第一个 Spock 测试。

