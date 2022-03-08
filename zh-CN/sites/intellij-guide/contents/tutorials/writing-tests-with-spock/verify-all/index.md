---
type: TutorialStep
date: 2021-05-20
title: 全验证
technologies: [ ]
topics:
  - testing
author: tg
subtitle: 测试框架通常会在第一次失败时停止测试， 了解如何运行所有条件以查看哪些通过和哪些失败。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=1893
---

让我们看一下如何确保所有断言都被运行，无论是否有断言失败。 试试这个测试（请留意，使用字符串形式的方法名，我们就可以轻松地添加引号和其他特殊字符）。

```groovy
def "should demonstrate 'verifyAll'"() {
    given:
    Renderer mockRenderer = Mock()
    def shapeFactory = new ShapeFactory(mockRenderer)

    when:
    def polygon = shapeFactory.createDefaultPolygon()

    then:
    verifyAll(polygon) {
        numberOfSides == 5
        renderer == null
    }
}
```

我们可以将 `with()` ，改为 [verifyAll()](https://spockframework.org/spock/docs/2.0/all_in_one.html#_using_verifyall_to_assert_multiple_expectations_together)。 运行（上面的代码应该失败）并查看结果会怎样 - 不仅 numberOfSides 断言失败，而且对 renderer 的检查也是失败。

``` 
org.opentest4j.MultipleFailuresError: Multiple Failures (2 failures)
    org.spockframework.runtime.SpockComparisonFailure: Condition not satisfied:

numberOfSides == 5
|             |
4             false

    org.spockframework.runtime.SpockComparisonFailure: Condition not satisfied:

renderer == null
|        |
|        false
Mock for type 'Renderer' named 'mockRenderer'
```

使用 `verifyAll`，所有断言都会运行，我们可以看到哪个失败和哪个通过。 这可以帮助我们在编写和修复测试之间快速迭代。

返回测试并进行修复：

```groovy
then:
verifyAll(polygon) {
    numberOfSides == 4
    renderer == mockRenderer
}
```

（请注意，此代码与视频略有不同，因为使用两个名称为  `renderer` 的变量使得很难看到正在测试的内容）

现在我们知道如何检查所有条件的输出。 接下来，让我们看一下如何设置或解除我们的测试。