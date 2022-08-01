---
type: TutorialStep
date: 2021-05-20
title: 创建您的 Spring 控制器
technologies: [ ]
topics: [ ]
author: hs
subtitle: 使用 IntelliJ IDEA 新建项目向导创建 Spring 控制器并选择依赖项。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/wC6NiR8eKHE
---

## 创建您的 Spring 控制器
现在我们有了正常运行的 Spring 项目，我们需要  [创建一个控制器](https://spring.io/guides/gs/serving-web-content/#initial) 来处理 Web 请求。

### 创建控制器
这里要注意的一件事是，您不需要告诉 Spring Application 类有关 Spring Controller 类的信息。 这由 Application 类中的 `@SpringBootApplication` 注解处理，它还包含其他注解，包括 `@ComponentScan`。 这意味着将扫描当前包和子包以查找 Spring 组件。 当你第一次开始使用Spring时，这有点令人不安，但随着时间的推移，一旦你了解了 Spring 在幕后为你所做的一切，你就会习惯它。

1）在 `HelloWorldApplication.java` 的同一位置创建一个新的名为 `HelloWorldController.java` 的类。

2）我们需要做的第一件事是告诉 Spring 这是一个 REST 控制器，所以你需要添加一个类级注解 `@RestController`。 它意味着组件扫描将选取此类，因为它与我们的 Application 类位于同一包中。 因此，我们的 REST 控制器 `HelloWorldController`，可以从应用程序的上下文中使用。

3）下一步是创建一个方法，该方法将告诉 Spring，如果我们使用Web服务器的根目录，我们希望看到字符串 _Hello World from Spring Boot_。 为此，我们需要添加一个带有 `@RequestMapping` 注解的方法，比如 `helloWorld`：

```java
package com.example.helloworld;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloWorldController {

  @RequestMapping("/")
  public String helloWorld(){
    return "Hello World from Spring Boot";
  }
}
```
4）现在我们需要重新运行 Spring 应用程序。 如果它从上一个教程开始时就仍在运行状态，则需要先停止它。 您可以使用 **Ctrl**+**R**（macOS），或 **Shift**+**F10**（Windows/Linux）再次运行它。

5）当您打开浏览器后，请输入以下URL `localhost:8080`。 您应该会看到返回的文本：

![浏览器中显示的 Hello World](hello-world-text.png)

6）如果它工作正常，您可以开始更多新的尝试。 尝试在第一个方法下面添加此新代码：

```java
@RequestMapping("/goodbye")
public String helloWorld(){
  return "Goodbye from Spring Boot";
}
```

7） 现在再次运行您的应用程序。 在根目录中，您仍然应该看到 _Hello World from Spring Boot_，因为 `@RequestMapping` 是 _/_ 代表根目录。 但是，如果您现在输入 `localhost:8080/goodbye`，您应该会看到 _Goodbye from Spring Boot_。

就是这样！ 您已经完成了，恭喜您创建了第一个 Spring 应用程序并在浏览器中显示了一些文本！ 在下一节中，我们将为应用程序创建一个测试。 