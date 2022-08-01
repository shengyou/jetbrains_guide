---
type: TutorialStep
date: 2021-05-20
title: Helper 方法
technologies: [ ]
topics: [ ]
author: tg
subtitle: 有时我们需要将测试代码移动到单独的方法中。 在本节中，我们将介绍一些相关的小技巧。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=1716
---

当测试代码变得很庞大时，我们可能希望将大部分代码或常见代码拆分为  [一些 helper 方法](http://spockframework.org/spock/docs/2.0/all_in_one.html#_helper_methods)。

假设我们有一个像这样的测试。

```groovy
def "should use a helper method"() {
    given:
    Renderer renderer = Mock()
    def shapeFactory = new ShapeFactory(renderer)

    when:
    def polygon = shapeFactory.createDefaultPolygon()

    then:
    polygon.numberOfSides == 4
    polygon.renderer == renderer
    //could check lots of different values on this polygon... 
}

```

它使用 [ShapeFactory](https://github.com/trishagee/spock-testing-demo/blob/main/src/main/java/com/mechanitis/demo/spock/ShapeFactory.java) 来创建一个默认的形状，然后我们执行一些检查以确保这符合我们的期望。 您可以想象的到，在实际的生产环境的代码中，这里可能有很多值需要检查。

我们可能很想将所有这些检查移到它们自己的方法中去，特别是如果它们将会被多个测试使用的情况。

```groovy
def "should use a helper method"() {
    //given... when... code

    then:
    checkDefaultShape(polygon, renderer)
}

private static void checkDefaultShape(Polygon polygon, Renderer renderer) {
    polygon.numberOfSides == 4
    polygon.renderer == renderer
}
```

运行测试 - 它将通过。 但是，如果我们更改代码使其失败，我们将看到它仍然会通过。 这个 helper 方法并没有符合我们的预期。

![](./23.png)

如果我们将断言移动到这样的 helper 方法中，则它不能再使用比较运算符来定义预期的行为。 相反，我们需要添加 `assert` 关键字。

```groovy
private static void checkDefaultShape(Polygon polygon, Renderer renderer) {
    assert polygon.numberOfSides == 4
    assert polygon.renderer == renderer
}
```
现在，如果您在 `checkDefaultShape` 中用错误的值去运行测试的话，它应该会失败。

还有其他一些事情需要注意 - 它会在第一个断言上失败，它永远不会运行断言来检查 polygon.renderer。 稍后我们将介绍如何解决这个问题。

现在，我们知道如何将测试的各个部分拆分为单独的方法。 接下来，让我们看一下在单个对象上检查多个值的方法。