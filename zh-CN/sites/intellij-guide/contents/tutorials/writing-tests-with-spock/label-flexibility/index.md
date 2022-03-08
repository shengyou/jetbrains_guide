---
type: TutorialStep
date: 2021-05-20
title: 灵活的标签
technologies: [ ]
topics: [ ]
author: tg
subtitle: Spock 支持一系列不同的测试标签，以帮助您编写最易读的测试
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=573
---

我们已经看过 `expect` 和 `given, when and then`，但 Spock 在使用哪些标签以及何时使用方面提供了很大的灵活性， 这一切都是为了创建描述性测试的。

在我们上一个测试中，标签可能会在如此短的测试中看起来很杂乱。 设置非常简单，例如，我们可以将其内联到实际测试本身中。 如果在 `when` 中内联设置的代码，则可以删除 `given` 标签，然后只使用 [when 和 then](http://spockframework.org/spock/docs/2.0/all_in_one.html#_when_and_then_blocks)。

```groovy
def "should demonstrate given-when-then"() {
    when:
    int sides = new Polygon(4).numberOfSides

    then:
    sides == 4
}
```

测试应像以前一样成功运行。 我们可以灵活地以我们认为最可读的方式标记代码块，因此测试记录了代码的预期行为。

现在，我们介绍了一些有关如何使用标签来明确定义测试中发生的情况的技巧。 接下来，我们将看看 Spock IntelliJ IDEA 插件可以提供哪些帮助。

