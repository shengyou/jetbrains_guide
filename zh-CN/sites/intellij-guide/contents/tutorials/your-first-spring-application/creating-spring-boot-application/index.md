---
type: TutorialStep
date: 2021-05-20
title: 创建您的 Spring Boot 项目
technologies: [ ]
topics: [ ]
author: hs
subtitle: 使用 IntelliJ IDEA 新建项目向导创建 Spring 项目并选择依赖项。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/4fRx1rA83jE
---

## 创建您的 Spring Boot 项目
在本教程中，我们将使用 IntelliJ IDEA Ultimate，因为我们希望使用 Spring Initializr 创建一个新项目。 此功能仅适用于 IntelliJ IDEA Ultimate。 本教程基于 [Building an Application with Spring Boot](https://spring.io/guides/gs/spring-boot/) 的内容。

1） 如果您已经在 IntelliJ IDEA 项目中，请选择 **File（文件）** > **Project（项目）**。 或者，点击欢迎画面上的 **New Project（新建项目）** 按钮。

2）选择左侧的 **Spring Initializr**，然后输入以下：

| 字段名称   | 您输入的内容                                                                                                                                   |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| 名称     | 为您的项目指定一个名称，例如 `HelloWorld`。                                                                                                             |
| 地点     | 这里默认为 IntelliJ IDEA 项目的位置，您可以根据需要进行更改。                                                                                                   |
| 类型     | 此演示使用 [Maven 构建系统](https://maven.apache.org/what-is-maven.html) 因此请选择该选项。 如果您想使用 [Gradle 构建系统](https://gradle.org/)，那么请告诉我们，我们会将其添加到列表中。 |
| 语言     | 此演示使用 Java。                                                                                                                              |
| 组      | 这里构成了包名的一部分，如果有需要您可以更改。                                                                                                                  |
| 工件     | 这是为产生的任何工件指定的名称，它将派生自您的项目名称，因此您无需更改它。                                                                                                    |
| 软件包名称  | 这是您的组和项目名称的串联，因此您无需更改它。                                                                                                                  |
| 项目 SDK | 这是用来编译项目的 Java SDK 版本。 此演示使用 Java 11。                                                                                                    |
| Java   | 这是您的项目的语言级别，它决定了编辑器中提供的编码辅助功能。 同样，此演示使用 Java 11。                                                                                         |
| 打包     | 我们将在此演示中使用 JAR，因为我们不打算在应用程序服务器上运行它。 要采取后者的方式，您需要选择 WAR。                                                                                  |

您的页面应如下所示：

![新建 Spring 项目的详情](new-spring-project-details.png)

然后，我们点击 **Next（下一步）**。

3）下一页是您可以配置 Spring Initializr 项目并添加所需依赖项的地方。 这个项目将非常简单，因为我们只想在本地浏览器中显示字符串 “Hello World”。 让我们输入 _Web_ ，看看能得到什么选项。 您会看到与 _Web_ 开发相关的所有依赖项，我们想要的是第一个，**Spring Web**。 或者，您可以展开 Web 节点（顶部第二个），然后选择 **Spring Web**。 这就是您在这里需要做的所有事情。

这里需要注意的一件事是，在你创建了 Spring 项目后，可以很容易的向 Spring 项目添加依赖项。 您只需要在此步骤中添加您知道需要的依赖项即可。 在以后添加依赖项比删除将来可能依赖，或不依赖的更容易！

您的页面应如下所示，具体取决于您如何查找的 **Spring Web**：

![新的 Spring 项目依赖项](new-spring-project-dependencies.png)

点击 **Finish（完成）**。

这就是我们在 IntelliJ IDEA 中建立我们基本的 Spring 项目所要做的。 在下一步中，我们将看看自动创建了什么内容，以及最重要的，它的原因。

