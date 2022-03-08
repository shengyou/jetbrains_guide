---
type: TutorialStep
date: 2021-05-20
title: With
technologies: [ ]
topics: [ ]
author: tg
subtitle: 有时我们想检查一个对象上的多个值。 我们可以使用 “with” 来做到这点。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=1834
---

让我们来看一种测试单个对象中的多个属性的方法。 我们可以将之前的测试更改为以下内容：

```groovy
 def "should use a helper method"() {
    given:
    Renderer mockRenderer = Mock()
    def shapeFactory = new ShapeFactory(mockRenderer)

    when:
    def polygon = shapeFactory.createDefaultPolygon()

    then:
    with(polygon) {
        numberOfSides == 4
        renderer == null
    }
}
```
我们可以使用 Spock 的 [with()](https://spockframework.org/spock/docs/2.0/all_in_one.html#_using_with_for_expectations) 来检查 `polygon`上的多个值。 在这个大括号中，我们不必用 `polygon` 的方式，我们只断言属性与预期值的匹配。

请注意，此测试中，在 `given` 里创建的模拟渲染器称为 `mockRenderer` - 这样可以清楚地看出，在 `with` 区域里的 `renderer` 就是 `polygon.renderer`， 而不是整个测试范围中的 renderer。

然后更改测试以使其失败，这样我们就可以看到它应该是：

![](./24.png)

与 helper 方法一样，如果第一个断言失败，则不会运行下一步的断言。 这可能是您希望从测试中得到的，如果一个值是错误的，那么无论怎样，整个测试都应该失败。 但是，有时我们想要运行所有断言，以便我们可以确切地看到哪些成功，哪些失败。

现在我们有了一个简单的机制来检查一个对象里面所有的值。 但是，有时我们希望进行多次检查，并确保它们都通过（或找出那些失败的），而不是在第一个错误时就运行失败。 在下一节中，我们将介绍如何做到这点。