---
type: TutorialStep
date: 2021-10-13
title: Sharing your project on GitHub - The quick approach
technologies: [ ]
topics: [ ]
author: hs
subtitle: How to enable version control for your project and share it to GitHub in one step
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/4ukhZvOmAtk?start=10
---

## Creating a Local Repository and Sharing it to GitHub in One Step

Let's look at how we can enable version control for our project, authenticate with GitHub, create our first commit, and share our project on GitHub in one step.

### 分享项目到 GitHub

您可以使用 IntelliJ IDEA 来创建一个本地的 Git 仓库，然后使用菜单上的 **VCS >  Share Project on GitHub（在 GitHub 上共享项目）**来分享项目到 GitHub 上。

![在 GitHub 上共享项目](share-project-github.png)

这会在 GitHub 对话框上显示项目分享的相关内容。 Here you can give your GitHub repository a name (must be unique in your repository), choose if you want it to be private, change the Remote (we recommend you don't), and give your project an optional description.

### Optional - Authenticating with GitHub
If you're not already authenticated with GitHub you will see an additional _Add Account_ link which has different options:

![Add GitHub Account](share-add-account.png)

我们将重点介绍本教程中的前两个选项。 首选，如果您选择 **Log in via GitHub（通过 GitHub 登录）**，将在您的默认的浏览器上打开一个窗口，要求您登录您的 GitHub 帐户并通过 IntelliJ IDEA 进行身份验证。

或者您可以选择 **Log in with Token（通过令牌登录）**来打开添加 GitHub 帐户的对话框。 您可以在这里按 **Generate（生成）**，在您的默认的浏览器上打开一个窗口，要求您登录您的 GitHub 帐户，然后您可以生成一个令牌以在 IntelliJ IDEA 中使用。 您可以按照 GitHub 上的说明执行此操作。 当您生成令牌后，您可以将其粘贴回对话框中，以便与 GitHub 进行身份验证。

这两种方法都实现了相关的结果，因为它们都允许 IntelliJ IDEA 与 GitHub 进行身份验证。

Tip: if you have multiple GitHub accounts, you can [add your GitHub accounts](https://www.jetbrains.com/help/idea/github.html) in the Settings/Preferences with **⌘,** (macOS), or **Ctrl+Alt+S** (Windows/Linux) and then search for _GitHub_. You can use the **+** to add multiple GitHub accounts.

### 在 GitHub 上创建仓库

Now you can press **Enter** or click **Share**, IntelliJ IDEA will go ahead and create that repository on your GitHub profile.

### Making Your First Commit
The IDE will ask you which files you want to put into this first commit. You could commit everything, but generally you don’t need to add the `.gradle` folder (if you’re using the [Gradle wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html)), and we don’t need to add the build folder, which is where IntelliJ IDEA puts the compiler output like class files.

![Add Files for Initial Commit](add-files-for-Initial-commit.png)

Everything else looks good to commit, you can use the default commit message and click **Enter** to commit it.

### 分享项目到 GitHub

IntelliJ IDEA creates a local Git repository for the project and then pushes it to your GitHub profile as a new repository with the details you just entered.

When this process is finished, IntelliJ IDEA will pop up a balloon, and you can click on the link to see the repository in GitHub in a browser.

![Shared On GitHub](shared-on-github.png)

We can see the repository, the code, the commit message, and the description in GitHub too.

![](shared-on-github-browser.png)