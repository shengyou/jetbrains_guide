---
type: TutorialStep
date: 2021-05-20
title: 预期异常
technologies: [ ]
topics:
  - testing
author: tg
subtitle: 测试不只是检查成功的路径，有时候我们会期待一个特定的异常。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=657
---

测试不仅仅是测试成功的路径。 我们还应该检查异常的情况。

通常我们希望检查是否抛出了正确的异常类型。 如果您创建一个零个边的新多边形，这听起来应该会导致错误。 让我们来编写一个测试：

```groovy
def "should expect Exceptions"() {
    when:
    new Polygon(0)

    then:
    thrown(TooFewSidesException)
}
```

`then` 块检查是否正确的异常被抛出了。 我们通过调用 `thrown()` 和我们期望被抛出的异常的类来做这件事情。 在我们的例子中，通过调用构造函数，我们期望一个 [TooFewSidesException](https://github.com/trishagee/spock-testing-demo/blob/main/src/main/java/com/mechanitis/demo/spock/TooFewSidesException.java) 被抛出（如果您想要该测试正确运行，请在项目中创建此异常）。

请注意在 Java 中，我们通常需要在 `TooFewSidesException` 末尾添加 .class，来定义这是异常类型。 在 Groovy 中，我们不需要这个，但是如果您认为它使代码更清晰，则可以添加它：

```groovy
then:
thrown(TooFewSidesException.class)
```

运行此测试来查看代码的行为是否正确。 测试应该会失败，因为 Polygon 类尚未抛出此异常。

![](./14.png)

更改 [Polygon](https://github.com/trishagee/spock-testing-demo/blob/main/src/main/java/com/mechanitis/demo/spock/Polygon.java) 的构造函数，以便检查边数，并在少于三条边时抛出异常：

```java
public Polygon(int numberOfSides) {
    if (numberOfSides <= 2) {
        throw new TooFewSidesException("You can't have fewer than 3 sides for a polygon", numberOfSides);
    }
    this.numberOfSides = numberOfSides;
}
```

重新运行该测试，它应该能通过。

我们甚至可以将抛出的异常分配给一个变量，以便我们可以对其执行更多的检查。 让我们检查存储在 TooFewSidesException 上的边数，看看它是否与创建多边形的边数相匹配。

```groovy
then:
def exception = thrown(TooFewSidesException)
exception.numberOfSides == 0
```

重新运行测试：尝试使用查找操作（Find Action）**⌘⇧A**（macOS），或 **Ctrl+Shift+A**（Windows/Linux），然后输入 “Rerun” 来运行测试。 该测试应该能通过。

现在您知道如何编写预期异常情况的测试了。 接下来，我们将看看如何使用多个输入运行测试。
