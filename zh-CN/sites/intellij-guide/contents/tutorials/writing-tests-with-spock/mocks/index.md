---
type: TutorialStep
date: 2021-05-20
title: Mock
technologies: [ ]
topics:
  - testing
author: tg
subtitle: Mock 是一个有用的测试工具。 我们可以提供 “空” 对象，所以我们不必初始化整个应用程序来测试一个部分，并且我们可以使用 mock 来检查我们的代码是否进行了我们期望的调用。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=1290
---

有时候我们需要模拟类或 API 来断言预期的行为。 [Mock 内置于 Spock](https://spockframework.org/spock/docs/2.0/all_in_one.html#interaction-based-testing) 中，我们不需要单独的库或框架来支持 Mock。 它也可以模拟具体的类。 如果您已经习惯了其他的 Mock 框架，您可能会预期只能模拟 Java 接口，但是 Spock 让我们能容易地从一个具体的类[创建一个 mock](http://spockframework.org/spock/docs/2.0/all_in_one.html#_creating_mock_objects)。

Spock 测试的 `given` 块是为我们的测试设置 mock 理想的地方。 很明显这是运行测试所需的所有的代码，但这不是正在测试的代码本身。

```groovy
def "should be able to mock a concrete class"() {
    given:
    Renderer renderer = Mock()
    def polygon = new Polygon(4, renderer)

    when:
    polygon.draw()

    then:
    4 * renderer.drawLine()
}
```

此测试模拟了一个 [Renderer](https://github.com/trishagee/spock-testing-demo/blob/16981a2a00ae52f13713d289e9829ac7ddd3a7fe/src/main/java/com/mechanitis/demo/spock/Renderer.java) 类，这是一个具体的 Java 类。 我们可以通过声明一个类型为 Renderer 的变量，并在没有任何参数的情况下调用 Mock 来执行此操作：

```groovy
Renderer renderer = Mock()
```
…或者如果我们更喜欢使用 Groovy 的 `def` 来定义我们的变量，我们需要将类型作为参数传递给 Mock 方法：

```groovy
def renderer = Mock(Renderer)
```

请记住，如果使用 “def” 声明它，则此变量使用的是 Groovy 的动态类型，所以并没有被 IDE 或代码强烈得识别为 Renderer 类型。 如果您不怎么使用 mock，这很好，但您有时可能想更清楚地指定类型，这对 Java 开发者来说当然会更自然。

`given` 块通过调用具有 `numberOfSides` 和模拟的 `renderer` 的构造器，还使用了给定的 renderer 来配置了一个多边形。

`when` 部分定义了实际上我们正在测试的内容的调用，在此测试中，我们希望查看当我们在此多边形上调用 `draw` 方法时会发生什么。 确保在多边形上有一个 `draw` 方法，在此阶段时它可以是空的，因为我们正在做一点儿 [TDD](https://en.wikipedia.org/wiki/Test-driven_development)：

```java
public void draw() {
}
```

`then` 定义了预期。 Spock 有一个[漂亮和清晰的语法，用于定义我们期望在模拟中看到的行为](http://spockframework.org/spock/docs/2.0/all_in_one.html#_mocking)。 在这个测试中，考虑到多边形有四个边，我们可能期望在 renderer 的 `drawLine` 方法上看到四次调用。 `then` 块声明了我们期望看到 `renderer.drawLine` 被调用了 4 次。

现在运行此测试，它应该会失败， 这是因为这些方法还没有做任何事情。 我们希望看到这个 drawLine 方法被调用四次，但它根本没有被调用。

![](./22.png)

进入到 `Polygon.draw` 方法的实现，并将其更改为在此处调用 renderer 的 drawLine 方法，调用与边数一样多的次数（请注意，这是一个极其简化的示例来演示测试）：

```java
public void draw() {
    for (int i = 0; i < numberOfSides; i++) {
        renderer.drawLine();
    }
}
```

重新运行该测试，它应该能通过。 代码在 `renderer` mock 上调用 `drawLine` 四次。

Mock 是一个强大并且有用的工具，可以确保我们正在测试的代码以我们期望的方式调用我们期望的 API。

现在您知道如何创建一个 mock 并编写一个测试，该测试显示运行测试时调用了特定的方法。 接下来让我们看一下如何使用 Spock 存根对象和方法。
