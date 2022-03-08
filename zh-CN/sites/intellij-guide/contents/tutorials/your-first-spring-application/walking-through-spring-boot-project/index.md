---
type: TutorialStep
date: 2021-05-20
title: 浏览您的 Spring Boot 项目
technologies: [ ]
topics: [ ]
author: hs
subtitle: 让我们来看看 IntelliJ IDEA 为我们创建了什么以及为什么它创建了这些。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/XkO1ana4nqI
---

## 项目一览
在之前的步骤中，我们让 IntelliJ IDEA 为我们创建了一个 Spring Boot 项目，包含有一个 **Spring web** 依赖项。 现在让我们看一下已经自动创建了的内容，以便我们在下一步可以在此基础上进行构建。

让我们来看看这个项目的一些方面。 最简单的方法是通过项目工具窗口来查看，您可以在 macOS 上使用 **⌘1**，或在 Windows 和 Linux 上使用 **Alt**+**1** 来访问它。 我们将看看：

- .mvn 文件夹
- pom.xml 文件
- HelloWorldApplication.java
- HelloWorldApplicationTests.java

### .mvn 文件夹
这个文件之所以被创建是因为当您使用 Maven 构建系统创建 Spring Boot 项目时，Spring Boot 使用 Maven wrapper。 这意味这你不需要在本地安装 Maven 来运行您的 Spring Boot 项目。 您可以提交该项目到版本控制，但是您可以现在先忽略它。

### Maven 的 pom.xml 文件
这文件是用我们在创建此项目时您所选择的依赖项生成的。

```xml
<dependencies>
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
  </dependency>

  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
  </dependency>
</dependencies>
```
第一个依赖项 `spring-boot-starter-web` 在那里是因为我们选择了 **Spring Web** 作为依赖。 第二个依赖项 `spring-boot-starter-test` 是您在任何 Spring 应用程序中都可以获得的。 它使您能够使用各种测试库创建测试。

当您创建项目后，将依赖项添加到 `pom.xml` 文件非常容易。 使用 **⌘N** （macOS）或 **Alt+Ins**（Windows/Linux），然后浏览您的依赖项。 然而对于我们的演示，这些是我们唯一需要的依赖。


### SpringHelloWorldDemoApplication.java 文件
在您的 **main** > **java** > **com.example.helloworld** 文件结构，您将可以看到您的 `HelloWorldApplication.java` 文件。 让我们更详细地看一下。

这就是您的 Java 文件的模样。 该名称将是您对这个文件的称呼，并在其后面加上 _Application_。

```java
package com.example.helloworld;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class HelloWorldApplication {

    public static void main(String[] args) {
        SpringApplication.run(HelloWorld.class, args);
    }
} 
```

正如你所期望的那样，我们的软件包在类的顶部，然后是我们的导入语句。

`@SpringBootApplication` 注解启用了额外的 Spring Boot 功能，在您发现您在故障排除您的代码时，了解这些功能是非常有用的。

最重要的一行是：`SpringApplication.run(HelloWorldApplication.class, args);`

这会调用 SpringBoot 的 `run` 方法，并且我们需要将项目的 main 类传递给 Spring，在这个例子里，它是同一个类。

当您运行这个方法，Spring 会查看 Maven 从我们的 pom.xml 文件里的依赖项中加入的类路径和其他的，然后从那里对您的项目构造作出假设。 Maven 可以根据 Spring 在您的类路径和 `application.properties` 文件中发现的内容，加入大量的_传递_依赖项。 传递依赖项是依赖项所依赖的依赖项。

例如，我们在 Maven 的 pom.xml 中有一个依赖项称为  `spring_boot_starter_web`。 它有一个传递依赖项 `spring-boot-starter-tomcat`。 在这个例子里，当 Spring `run` 方法被调用时，它检查类路径和您的 `application.properties` 文件（它是空的）和其他的，然后发现您想要一个 Tomcat 网站服务器，所以它为您创建了一个。

### HelloWorldApplicationTests.java 文件
如果您查看 **test** > **java** > **com.example.springhelloworlddemo** 文件夹，您可以看到您有另外一个类叫 `SpringHelloWorldDemoApplicationTests.java`。 这是您使用 Spring Boot 时免费获得的测试。 它检查应用程序的上下文是否可以启动，如果不能，它将失败。 该测试可以成为创建您自己的集成测试的一个有用的起点。

## 运行您的 Spring Boot 应用程序
此时，我们已经有了 Spring Boot 应用程序的基础知识。 您可以使用 **Ctrl**+**R**（macOS），或 **Shift**+**F10**（Windows/Linux）运行它。 或者，您可以使用间距图标：

![用间距图标运行应用程序](gutter-icon-run-application.png)

该应用程序将使用 Tomcat 网站服务器运行。 您可以通过 Web 浏览器并输入 `localhost:8080` 来验证它是否正常工作。 8080 是 Tomcat 的默认端口。

您应该会得到一个 404 响应，大概会是下面的样子：

![White label 404 响应](white-label-404-response.png)

我们之所以获得此页面，是因为我们有支持 REST 控制器的 `spring-boot-starter-web` 依赖项，但我们还需要创建一个控制器并为该控制器添加请求映射。 我们将在下一步中执行这两项操作。

最后，在我们进行任何进一步的开发之前，最好先停止服务器运行。 您可以按 **⌘F2**（macOS），或 **Ctrl**+**F2**（Windows、Linux）来停止服务。 