---
type: TutorialStep
date: 2021-05-20
title: 将规格说明作为文档
technologies: [ ]
topics: [ ]
author: tg
subtitle: Spock 测试不仅告诉计算机如何测试应用程序，还可以帮助开发人员了解应用程序应该做什么。
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/i5Qu3qYOfsM?start=2057
---

让我们看看[最后一个功能](http://spockframework.org/spock/docs/2.0/all_in_one.html#specifications_as_documentation)，来通过测试帮助记录需求。

我们已经看到 Spock 把可读性和测试作为文档的重点。 [@Subject](http://spockframework.org/spock/docs/2.0/all_in_one.html#_subject) 注解、[标签块](http://spockframework.org/spock/docs/2.0/all_in_one.html#_blocks)、[字符串作为测试方法的名字](http://spockframework.org/spock/docs/2.0/all_in_one.html#_feature_methods)以及所有您可以做的[自定义这些字符串值](https://spockframework.org/spock/docs/2.0/all_in_one.html#_unrolled_iteration_names)，都有助于将自动化测试作为系统应如何做的文档。

我们还可以在测试的块中[添加更多信息](http://spockframework.org/spock/docs/2.0/all_in_one.html#specifications_as_documentation)，同样出于可读性或文档目的。

```groovy
def "should be able to create a stub"() {
    given: "a palette with red as the primary colour"
    Palette palette = Stub()
    palette.getPrimaryColour() >> Colour.Red

    and: "a renderer initialised with the red palette"
    def renderer = new Renderer(palette)

    expect: "the renderer to use the palette's primary colour as foreground"
    renderer.getForegroundColour() == Colour.Red
}
```

我们可以在标签旁边添加一个字符串来提供该块的更详细的描述。 如果我们想把一个块划分成更多的块，为了可读性或为了添加文档，我们可以使用 [and:](http://spockframework.org/spock/docs/2.0/all_in_one.html#specifications_as_documentation) 标签，这只是为了让我们进一步划分。

该文本对 Spock 运行时是可用的，所以这些信息可以在信息和报告中使用。

在 Groovy 语言的帮助下，Spock 测试可以非常具有描述性。 这些自动化测试还告诉我们开发人员，我们应该期望从我们的应用程序中看到什么。

最后让我们来总结一下我们已经看到的，以及我们使用的快捷键。