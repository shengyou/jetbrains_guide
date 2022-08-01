---
type: TutorialStep
date: 2021-05-20
title: 数据表
technologies: [ ]
topics:
  - testing
author: tg
subtitle: 数据表提供了和数据管道一样的功能，但是对于更复杂的数据集，此语法有时更具可读性。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=1122
---

数据管道是一个指定要测试的有限数据集的好方式。 Spock 还支持[数据表](http://spockframework.org/spock/docs/2.0/all_in_one.html#data-tables) ，用于更复杂的数据驱动测试。

正如我们所看到的，想要传入一系列数值以检查同一条件是否适用于所有的这些数值是很平常的。 通常我们可能有多个输入，并希望根据多个输入检查它们。 比方说我们想检查一些东西的计算，比如说两个值的最大值——`a` 和 `b`。 我们需要检查返回值是否为预期的最大值（这与[文档里的例子相同](http://spockframework.org/spock/docs/2.0/all_in_one.html#data-tables)）。

```groovy
    def "should use data tables for calculating max"() {
        expect:
        Math.max(a, b) == max

        where:
        a | b | max
        1 | 3 | 3
        7 | 4 | 7
        0 | 0 | 0
    }
```

我们再次使用 `where` 标签来定义测试的输入。 这一次，它被设置为一个数值表。 第一行是表头，是我们将要在测试中使用的变量的名称，用管道符号分隔。 然后我们为测试中的每组输入添加一行。

运行这个测试，可以看到与数据管道测试类似的内容。

![](./19.png)

数据表中的每一行都有一个通过的“测试”，使用方法名称和每个输入变量的值来进行描述。 如果我们使其中的一个失败，我们将看到所有例子都已运行，其中的一个失败了。

![](./20.png)

Spock 的[强力断言（power assertions）](http://spockframework.org/spock/docs/2.0/all_in_one.html#_assertions_with_explicit_messages_now_include_power_assertions_output)显示计算结果、所有输入值以及失败时的比较。 我们可以使用它来修复问题。

``` 
Condition not satisfied:

Math.max(a, b) == max
|    |   |  |  |  |
|    7   7  4  |  5
|              false
class java.lang.Math
```

我们可以通过在输入列和输出列之间创建分隔符来使这些数据表更具可读性。 尝试使用 IntelliJ IDEA 的 [克隆文本光标](https://www.jetbrains.com/help/idea/pro-tips.html#multiple-selections)功能，将文本光标放置在 `b` 和 `max` 之间的 `|` ，然后按 **⌥** （macOS） 或 **Ctrl** （Windows/Linux） 两次，在第二次按下时按住它，然后按向下箭头在第一个文本光标下方创建第二个文本光标——执行此操作，直到每行一个，有四个文本光标。 现在如果我们输入第二个管道，它将出现在所有行上。

![](./21.png)

这个管道不会改变测试的意思，它只是帮助我们更好地理解表格。 在我们的例子中，我们将预期的输出分组在一侧，输入在另一侧。 运行测试以确保其按预期工作。

和之前一样，我们可以通过将数据变量的名称添加到测试名称中来使测试更清晰一些。 现在当我们查看测试运行时，可以非常清楚正在被测试的内容以及预期的结果是什么。

```groovy
def "should use data tables for calculating max. Max of #a and #b is #max"() {
    expect:
    Math.max(a, b) == max

    where:
    a | b || max
    1 | 3 || 3
    7 | 4 || 7
    0 | 0 || 0
}
```

现在您已经了解如何设计数据表以创建更复杂的输入和输出数据集。 接下来，让我们来看看 Spock 内置的 mock。

