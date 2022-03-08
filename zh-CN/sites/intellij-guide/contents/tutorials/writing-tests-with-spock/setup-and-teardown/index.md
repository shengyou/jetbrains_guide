---
type: TutorialStep
date: 2021-05-20
title: 设置和解除
technologies: [ ]
topics:
  - testing
author: tg
subtitle: 了解如何在 Spock 中设置或清理测试类和方法。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=1947
---

如果您使用过其他测试框架，那么对 [设置和解除](http://spockframework.org/spock/docs/2.0/all_in_one.html#_comparison_to_junit) 应该会比较熟悉。

Spock 提供了一个 `setup` 方法（我们可以使用 IntelliJ IDEA 的 [代码生成](https://www.jetbrains.com/help/idea/generating-code.html) 来在 [每个单独的测试方法之前](http://spockframework.org/spock/docs/2.0/all_in_one.html#_fixture_methods) 创建它）。 这可用于在每次测试开始时设置清理状态。

若要在每个测试方法结束时清理数据或状态，需要用 `cleanup` 方法。 这是在每个单独的测试方法之后运行的。

使用 `setupSpec` 方法在设置开始时设一次状态，这适用于在各个测试方法之间不会更改的内容。

创建一个 `cleanupSpec` 方法，用于最后的解除，此方法将在运行所有测试结束时被调用一次。

最后一条有用的信息。 本教程中的测试在测试方法本身里创建了“被测对象”。 但是，您可能还希望将测试对象的实例创建为测试中的字段。 您可以在字段上使用 [@Subject](http://spockframework.org/spock/docs/2.0/all_in_one.html#_subject) 注解来表示这是测试的对象（您也可以在方法中的局部变量上使用此注解）。 然后，您可以在测试方法中引用此字段，就像您在任何 Java 或 Groovy 类中那样。

```groovy
@Subject
private Polygon polygon = new Polygon(5)
```

现在，我们知道如何设置和解除我们的测试类和方法。 让我们看一下 Spock 测试如何不仅能做测试，还可以作为说明预期功能的应用程序的文档。
