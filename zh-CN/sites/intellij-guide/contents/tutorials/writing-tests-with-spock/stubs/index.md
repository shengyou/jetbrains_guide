---
type: TutorialStep
date: 2021-05-20
title: Stubs（存根）
technologies: [ ]
topics:
  - testing
author: tg
subtitle: 存根对象允许我们从测试中声明哪些值会被注入到我们的应用程序代码中， 它们可以提供简单的接口，因此我们不必初始化整个应用程序来测试其中一部分。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=1544
---

Mock 对于检查我们代码中的调用非常有用，[Stubs（存根）](http://spockframework.org/spock/docs/2.0/all_in_one.html#_stubbing)对我们正在测试的代码提供数据或值非常有用。

让我们看看新测试方法中的一个存根示例。

```groovy
def "should be able to create a stub"() {
    given:
    Palette palette = Stub()
    palette.getPrimaryColour() >> Colour.Red
    def renderer = new Renderer(palette)

    expect:
    renderer.getForegroundColour() == Colour.Red
}
```

`given` 块为测试设置了前置条件。 这一次我们将使用 `Stub()` 方法来为 [Palette](https://github.com/trishagee/spock-testing-demo/blob/main/src/main/java/com/mechanitis/demo/spock/Palette.java) 具体类[创建一个存根](http://spockframework.org/spock/docs/2.0/all_in_one.html#Stubs)。 与 `Mock()` 类似，您可以以这种方式来定义它，或者使用 `def` 并将类型传递给 `Stub()` 方法。

接下来该测试将设置 `palette` 存根，它将在被我们的代码调用时产生值。 我们使用右移（`>>`）来声明当 `getPrimaryColor` 方法被调用时，`Red` 枚举值将被返回。

设置的最后一步是使用此存根 `palette` 创建 [Renderer](https://github.com/trishagee/spock-testing-demo/blob/c86e83d18ae62a0bf6d36e001b4648bb1259a2c8/src/main/java/com/mechanitis/demo/spock/Renderer.java)。 如果您在 IDE 中依照这段代码，确保您的 Renderer 看起来像这样：

```java
public class Renderer {
    private Palette palette;

    public Renderer(Palette palette) {
        this.palette = palette;
    }

    public void drawLine() {
    }
}
```

该测试使用 `expect` 标签，因为测试和断言被组合在一起——我们预期当我们调用 `getForegroundColor` 时，这将返回 `Color.Red`。 此测试表明我们希望 `getForegroundColor` 返回与调色板原色相同的颜色。

我们可以再一次在这里使用测试驱动开发——我们可以用测试来驱动出我们期望的方法的样子，即使它们还不存在。 在任何红色方法名称上使用 **⌥⏎**（macOS）或 **Alt+Enter**（Windows/Linux），让 IntelliJ IDEA 创建使代码编译的最基本的方法，然后运行测试。

如果我们尚未实现 `getForegroundColor` 的细节，它应该失败。 先看到测试失败是件好事，这往往表明测试正在检查对的东西，即使这个对的东西还没有被实现。

更改 `getForegroundColor` 方法以返回调色板的原色。

```java
public Colour getForegroundColour() {
    return palette.getPrimaryColour();
}
```

重新运行该测试，它应该能通过。 该测试将一个存根 `palette` 注入到 `renderer` 中，我们告诉存根 `palette` 调用 `getPrimaryColor` 方法时要返回的内容，因此我们可以检查 `renderer` 执行了调用 `getForegroundColor` 时应该执行的操作。

如果我们将其设置为 Mock 而不是存根，这也会起作用。 Mock 对象[支持我们在上一次测试中看到的模拟行为和我们在这里看到的存根行为](http://spockframework.org/spock/docs/2.0/all_in_one.html#_combining_mocking_and_stubbing)，而[存根对象_仅_支持存根行为](http://spockframework.org/spock/docs/2.0/all_in_one.html#Stubs)，并不支持模拟。 我的偏好是在尽可能的情况下保持存根和 mock 行为的区别，所以通常最好只使用存根来实现存根行为，只用 Mock 来做模拟。

现在您知道了如何创建存根以提供预期值，因此测试可以验证是否使用了预期值。 接下来，我们将介绍如何在 Spock 测试中创建帮助方法。
