---
type: TutorialStep
date: 2021-08-09
title: 自动迁移测试
technologies: [ ]
topics: [ ]
author: hs
subtitle: 让 IntelliJ IDEA 自动迁移尽可能多的测试
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/F8UTTTDtbH0?start=452
---

现在，我们了解迁移测试的各个步骤，可以考虑更进一步。 让我们尝试自动迁移我们所有的测试。 按下 **⌘⇧A**（macOS）, 或 **Ctrl+Shift+A**（Windows/Linux）打开操作查找，输入“迁移”查看代码的迁移选项。 IntelliJ IDEA 提供了将代码从 Junit 4 迁移到 5 的选项。

![migrate.png](migrate.png)

这种迁移类似于我们做过的单独测试类，但是这次是对于所有测试类。 按 ** 运行 **，查看重构预览。 您可以使用**⌫**，或 **Delete**，在此处排除特定的类或方法。 按 “Do Refactor”（重构）按钮以执行重构。

![refactoring_preview.png](refactoring_preview.png)

我们希望所有的测试仍然像以前一样工作，按 **⌃⇧R**（macOS），或 **Ctrl+Shift+F10** (Windows/Linux)来运行。 You can also right-click on the 'tests' folder and select Run 'All Tests'.  The Test Results window shows us the outcome of running the tests.

![run_tests.png](run_tests.png)

There are no failed tests here and no indicator that anything went wrong so, can assume this migration worked as expected. You can now commit your changes if you want to.

After the migration, you can see that the test classes have been changed.  We can go through each of the files to check the changes before we commit them. Use **⇧⌘]** (macOS), or **Ctrl+Right Arrow** (Windows/Linux), to move to the next file to compare so you can quickly check all the files. As these are mostly simple JUnit tests, most of the changes are a change to the imports to use the new JUnit Jupiter test annotation instead of the old JUnit test annotation.

