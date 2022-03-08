---
type: TutorialStep
date: 2021-05-20
title: 一个简单的断言测试
technologies: [ ]
topics: [ ]
author: tg
subtitle: 编写我们的第一个 Spock 测试
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=197
---

让我们从编写一个非常简单的测试开始，这样我们就可以看到 Spock 测试的样子。

从 [项目窗口](https://www.jetbrains.com/help/idea/project-tool-window.html)，我们可以使用快捷键 **⌘N**（macOS），或 **Alt+Insert**（Windows/Linux）来创建新文件。 让我们创建一个 Groovy 类，因为 Spock 测试是 Groovy 类：

![](./05-new-groovy-class.png)

通过在类名前输入完整的包名来创建包和目录结构。

![](./06-new-class-name.png)

Spock 测试通常会被称为 “Specifications”，因此可以命名为 `ExampleSpecification`，将其放入您觉得有意义的任何包路径中。 确保此类继承了 Spock 的 [Specification](http://spockframework.org/spock/docs/2.0/all_in_one.html#_specification) 类。

```groovy
import spock.lang.Specification

class ExampleSpecification extends Specification {


}

```
我们可以通过按 **⌘N**（macOS），或 **Alt+Insert**（Windows/Linux）让 IntelliJ IDEA 生成 Spock 规范的测试方法。

![](./07.png)

当我们不太熟悉编写 Spock 或 Groovy 代码时，这可能特别有用，因为 IntelliJ IDEA 将生成我们需要的基本结构。 该方法是使用“def”关键字定义的，Spock 的方法名称可以是任意字符串。 当我们创建测试时，这非常有用，因为文本格式为我们提供了很大的灵活性，可以准确描述我们指定的行为应该是什么。

```groovy
class ExampleSpecification extends Specification {
    def "should be a simple assertion"() {

    }
}
```

Spock 测试不使用注解或特定的测试方法命名格式来定义哪些方法是测试。 取而代之，他们使用标签。 我们将在整个教程中看到可以使用的不同类型的标签，对于这个最简单的测试，我们用 `expect`。 这可用于定义我们期望看到的最简单的行为。

```groovy
def "should be a simple assertion"() {
    expect:
    1 == 1
}
```

Spock 也不会使用 _Assertions_ 或者 _Assert_ 关键字，至少通常不会使用。 取而代之的是，您可以使用简单的检查，比如双等号。 `should be a simple assertion` 方法指定了一个简单的预期行为 - 数字 1 应该等于 1。 这不是一个现实的测试用例，但它展示出了 Spock 测试的基本。

通过按 **⌃R**（macOS），或 **Shift+F10**（Windows/Linux）或编辑器行号间距中的绿色箭头运行测试。 测试应该会通过。

![](./08.png)

现在，我们来更改它以使其失败，看到测试失败总是有帮助的，能确保它确实在工作并能正确测试。 当测试失败时，Spock 会显示一条有用的错误消息，准确显示失败的内容和原因。

```
条件不满足：

1 == 0
  |
  false
```

默认情况下，IntelliJ IDEA 会使用 Gradle 运行测试（如果它是 Gradle 项目）。 这通常是我们想要的，因为这意味着 IDE 正在使用与持续集成或构建环境相同的方式来运行测试。 在像这样的简单项目中，Gradle 构建并没有执行任何额外的操作（如生成代码或资源文件），所以使用 IntelliJ IDEA 运行测试可以更快。 我们可以在 [设置或首选项](https://www.jetbrains.com/help/idea/gradle-settings.html) 中找到相应设置，然后选择 IntelliJ IDEA 来运行测试。

![](09.png)

修复此测试并重新运行以确保它通过。 您应该看到 IDE 没有用 Gradle 来运行它，测试结果窗口中不应该有任何 Gradle 输出的内容。

现在，您了解了如何创建和运行简单的 Spock 测试。 接下来，我们将更详细地介绍如何使用 Spock 编写测试。

