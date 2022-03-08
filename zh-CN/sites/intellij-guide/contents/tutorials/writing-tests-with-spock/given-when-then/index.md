---
type: TutorialStep
date: 2021-05-20
title: Given，When 和 Then
technologies: [ ]
topics:
  - testing
author: tg
subtitle: 看看 Spock 测试通常是如何被组织的
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=386
---

Spock 最强大的功能之一是它的描述性。 它不仅用于测试代码，还用于描述和记录预期的行为。

在我们上一次的测试中，我们使用了 `expect` 标签来表示简单的期望。 Spock 支持许多不同的标签用于测试[块](http://spockframework.org/spock/docs/2.0/all_in_one.html#_blocks)。 我个人最喜欢的标签集是 `given`， `when` 和 `then`。 让我们来创建一个新的测试方法：

```groovy
def "should demonstrate given-when-then"() {
    given:
    def polygon = new Polygon(4)

    when:
    int sides = polygon.numberOfSides

    then:
    sides == 4
}
```

您还需要在 `src/main/java` 中创建一个 Java 类 [Polygon](https://github.com/trishagee/spock-testing-demo/blob/main/src/main/java/com/mechanitis/demo/spock/Polygon.java)。 我们可以使用 Spock 来测试 Java 或 Groovy 代码。

```java
public class Polygon {
    private final int numberOfSides;

    public Polygon(int numberOfSides) {
        this.numberOfSides = numberOfSides;
    }
}
```

回到测试中，您可以看到 `given` 标签用于表示该方法的这一部分正在设置所需的条件。 此测试需要一个有四条边的 `Polygon` 实例。

```groovy
given:
def polygon = new Polygon(4)
```

接下来我们看看 `when`。 这是我们实际要测试的东西，是我们要检查的行为。 这个测试确保 `numberOfSides` 已经被正确设置，并且我们可以从类中获得它。

```groovy
when:
int sides = polygon.numberOfSides
```

最后我们看看 `then`。 此部分检查所有我们期望得到满足的条件。 此测试检查边数是否为四，即传入给构造函数的原始边数。

```groovy
then:
sides == 4
```

您可以像这样读一个 given/when/then 测试：

- _**假定（given）**_我有一个四个边的多边形，
- _**当（when）**_ 我们获得它的边数，
- _**那么（then）**_边数应该等于四。

运行此测试看看它是否能通过。 您应该可以得到一个像这样的输出：

![](./10.png)

使用这些标签可能看起来会使测试方法的代码行数增加一倍，但请记住，测试中往往有更多的代码行，以这种方式分组有助于描述发生了什么。

在此步骤中，我们介绍了一些使用 Spock 编写测试的技巧， 现在您知道了如何使用标签来定义您的测试块。


