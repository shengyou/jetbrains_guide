---
type: TutorialStep
date: 2021-05-20
title: 给 Java 开发者的 Groovy 小技巧
technologies:
  - groovy
topics: [ ]
author: tg
subtitle: Groovy 的语法和功能对于 Java 开发人员来说一开始可能很不寻常，但它对测试非常有帮助。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=486
---

在进一步深入 Spock 示例之前，让我们看一下一些可能看起来很奇怪的东西，如果我们习惯于使用 [Java](../../../technologies/java) 来测试 Java 代码的话。

```groovy
when:
int sides = polygon.numberOfSides
```

在最后一个例子中测试的 `when` 部分，我们实际上是直接进入到了 Java 类的内部来检查一个私有字段的值。 我们可以从 Groovy 做到这一点，这对测试私有字段或方法很有帮助，而且不会折中它们在生产代码中的可见性。 然而 IntelliJ IDEA 将会给我们一个警告，以防这不是我们有意想要做的情况。

![](./11.png)

通常如果我们需要一些可见的东西进行测试，我们可能也需要它在生产代码里也可见。

进入您的 Polygon 类，然后在字段上按 **⌥⏎**（macOS），或 **Alt + Enter**（Windows / Linux），来让 IntelliJ IDEA 为该字段创建一个 getter。

![](./12.png)

现在看下测试，您已经对 Polygon 类进行了此更改。 现在 `polygon.numberOfSides` 的调用有一些奇怪的地方。 警告已经消失， `numberOfSides` 不再是粗体，它不再看起来像在引用字段。 事实上并不是。 如果我们按住 **⌘**，或 **Ctrl**，然后将我们的鼠标移到这上面，我们可以看到它实际上引用了 `getNumberOfSides` 方法。

![](./13.png)

如果我们从 Groovy 代码中调用 Java getter，我们可以忽略方法名称开头的 “get”，Groovy 仍然会使用 getter 而不是字段。 这对减少干扰很有用，但是如果您愿意，您仍然可以使用带有 “get” 的完整方法名称，这取决于您认为什么是最可读的。 有时删除 “get” 可能会令人困惑。

在本节中，我们介绍了一些使用 Groovy 编写测试的技巧。 现在您知道如何阅读 Groovy 代码，并了解它的行为可能与 Java 开发人员预期的不同。

接下来，我们将返回到我们的测试，并进一步地探索测试中的标签。 

