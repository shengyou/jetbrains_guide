---
type: TutorialStep
date: 2021-05-20
title: 数据管道
technologies: [ ]
topics:
  - testing
author: tg
subtitle: 当我们想要使用不同的数据集来测试同一组条件时， 数据管道是执行该操作的一种机制。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=829
---

当我们在测试特定的路径时，我们有时候希望检查一组已知的值是否会导致相同的结果。

[我们刚刚写的](../expecting-exceptions/)异常测试是一个很好的例子——我们知道有多个输入应该会导致这个异常抛出，并且我们可能想要测试所有的输入。 在我们的例子中，任何小于三的整数都会导致异常。 当您正在使用测试来纪录预期的行为，添加可以导致异常的完整的值列表或者至少添加一个样本列表来演示我们的预期会很有帮助。 创建一个使用[数据管道](http://spockframework.org/spock/docs/2.0/all_in_one.html#_data_pipes)的新测试方法来执行此操作：

```groovy
def "should expect an Exception to be thrown for a number of invalid inputs"() {
    when:
    new Polygon(sides)

    then:
    def exception = thrown(TooFewSidesException)
    exception.numberOfSides == sides

    where:
    sides << [-1, 0, 1, 2]
}
```

请注意末尾的新标签 `where`，它指定了测试的输入值。 该测试多次运行，并将不同的值传入到构造函数中。 因此它通过变量 `sides` 传入，而不是传入零。 断言还需要检查异常上的 `numberOfSides` 是否与我们传递给构造函数的相同数字匹配。

变量 `sides` 也定义在 `where` 块中。 这里使用左移运算符（`<<`）给出了一个我们希望的 `sides` 的值列表。

```groovy
where:
sides << [-1, 0, 1, 2]
```

这里有一些 Groovy 的地方需要注意：

- 首先，Groovy 支持[运算符重载](https://groovy-lang.org/operators.html#Operator-Overloading)，因此这里的左移运算符（`<<`）意味着“这是在测试中使用的值的管道”；
- 其次，Groovy 有一个[友好的语法用于创建值列表](http://docs.groovy-lang.org/latest/html/documentation/working-with-collections.html#_list_literals)，就是简单地将值放在中括号之间。

`where` 块表示“使用以下的每个值运行此测试：负值，零，一和二”。

运行此测试看看会发生什么。

![](./15.png)

该测试有效地运行了四次，整个测试使用 `sides` 列表中的每个值运行一次。 IntelliJ IDEA 显示测试的名称，然后在测试名称的下方加上 `sides` 四个值中每个的值。 所有的这四个运行都已通过，因为我们的代码正确地为每个值抛出了预期的异常。

如果我们愿意，我们可以改变方法的名称，以便更容易理解什么正在被测试。 我们可以在方法名称中使用[井号和数据变量的名称](https://spockframework.org/spock/docs/2.0/all_in_one.html#_method_uprolling_and_unrolling)来创建准确的描述。

```groovy
def "should expect an Exception to be thrown for invalid input: #sides"() {
```

重新运行它，IntelliJ IDEA 将显示该更新后的方法名称，其值为 “sides”，并且没有额外的干扰内容。

![](./16.png)

（注意：这是在最新的 Spock 版本里的行为。 如果您看不到此行为，您可能需要使用 [@Unroll](https://spockframework.org/spock/docs/2.0/all_in_one.html#_method_uprolling_and_unrolling) 来注解您的方法）。

让我们看一下，如果其中一个值导致测试失败，会发生什么情况。 我们知道这个异常应该在边数为二或者更少时抛出，所以我们把一个值改为三。

```groovy
def "should expect an Exception to be thrown for invalid input: #sides"() {
    when:
    new Polygon(sides)

    then:
    def exception = thrown(TooFewSidesException)
    exception.numberOfSides == sides

    where:
    sides << [-1, 0, 3, 2]
}
```

运行测试就可以看到数据驱动测试的一个伟大之处——即使其中的一个测试失败，也会运行所有的测试。

![](./17.png)

因此，我们可以清楚地看到哪些情况通过，哪些情况失败。 如果其中的一个失败了，我们可以看到导致该问题的原因。 在我们的例子中，测试被期望抛出一个异常，但它没有。 返回并通过将 `3` 替换为 `1` 来修复测试。

数据管道不仅适用于测试异常情况。 我们可能希望使用它们来测试一系列有效的输入。

创建另一个测试：

```groovy
def "should be able to create a polygon with #sides sides"() {
    when:
    def polygon = new Polygon(sides)

    then:
    polygon.numberOfSides == sides

    where:
    sides << [3, 4, 5, 8, 14]
}
```

测试将再次创建具有指定边数的多边形。 然后它会检查边数是否为预期值。 `sides` 变量是使用一整个列表的有效值来设置的。 运行这个测试显示了与前一个测试类似的情况——`sides` 的每个值都是通过测试的。

![](./18.png)

这个测试相当简单，我们可以减少代码量并做同样的事情。 我们可以内联多边形的创建（通过在 `polygon` 变量名上按 **⌘⌥N**（macOS），或 **Ctrl+Alt+N**（Windows/Linux）），来让构造函数与断言在同一行中被调用。 如果我们只有一条语句来配置、测试和断言，我们可以使用 `expect` 标签，就像我们在我们的第一个简单的断言测试中做的那样。 当然我们仍然需要 `where` 块，因为这设置了边数的所有的预期值。

```groovy
def "should be able to create a polygon with #sides sides"() {
    expect:
    new Polygon(sides).numberOfSides == sides

    where:
    sides << [3, 4, 5, 8, 14]
}
```

现在我们已经了解了如何编写 Spock 测试，来使用数据管道向测试输入许多不同的值。 这意味着我们可以在许多条件下测试和记录代码的预期行为。

接下来，我们将看看数据表，这是执行相同操作的另一种机制。