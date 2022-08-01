---
date: 2021-05-10
title: 使用 Streams API 里的新方法
technologies:
  - java
topics:
  - latest
  - inspections
author: tg
subtitle: 检查可以向我们展示 Java 16 里的新功能
thumbnail: ./thumbnail.png
cardThumbnail: ./card.png
shortVideo:
  poster: ./tip.png
  url: https://youtu.be/4XkazKdTO1U
seealso:
  - 
    title: (video) Good Old Stream API - JetBrains Technology Day for Java
    href: https://www.youtube.com/watch?v=nklbYYQpQi8
leadin: |
  Java 16 introduced some new methods on the Streams API. IntelliJ IDEA shows us places that can use the new methods and can automatically convert the code to use these new methods.

  The code will be highlighted in yellow as a warning. Press **⌥⏎** (macOS) or **Alt+Enter** (Windows/Linux) and choose "Replace collect(toUnmodifiableList()) with toList()".

  请注意，只有当您使用 Java 16 及以上的语言级别时，才能使用此功能。
---

