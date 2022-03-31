---
type: TutorialStep
date: 2021-05-20
title: 测试您的 Spring Boot 应用程序
technologies: [ ]
topics: [ ]
author: hs
subtitle: 让我们来添加一个测试来检查本地提供的内容
thumbnail: ./thumbnail.png
longVideo:
  poster: ./poster_long.png
  url: https://youtu.be/hRZ34CMvQi0
---

## 为 Spring Boot 应用程序创建测试
让我们写一个测试来检查当发生一个 HTTP 请求时，我们获得了我们预期的结果，在这个例子里，是 _Hello World from Spring Boot_ 字符串。

Spring Boot 的测试是使用标准的[JUnit5 测试库](https://junit.org/junit5/docs/current/user-guide/)写的。 如果一个测试需要访问 Spring 应用程序的上下文，它需要使用 `@SpringBootTest` 注解。 这些实际上是集成测试，因为它们依赖于在运行测试之前引导 Spring 的上下文。

1) 我们需要在与我们的 `HelloWorldApplicationTest.java` 相同的位置创建一个新的测试类，我们将调用我们的 `CheckHTTPResponse.java`。

2) 粘贴下面的代码到您的测试类：
```java
@SpringBootTest(webEnvironment = WebEnvironment.RANDOM_PORT)
public class CheckHTTPResponse {
    @LocalServerPort
    private int port;

    @Autowired
    private TestRestTemplate restTemplate;

    @Test
    public void shouldPassIfStringMatches() throws Exception {
        assertThat(restTemplate.getForObject("http://localhost:" + port + "/",
                String.class)).contains("Hello World from Spring Boot");
    }
}
```
传递 `WebEnvironment.RANDOM_PORT` 到 `@SpringBootTest` 注解来使用一个随机的端口号启动 web 服务器。 我们可以通过 `@LocalServerPort` 注解一个 `int` 字段（在我们的例子里是 `int port;`）来找到这个端口，测试框架将用那个随机端口号注入到这个字段。

当使用 `@SpringBootTest` 注解测试时，我们可以免费地获得一个 `TestRestTemplate`。 `@Autowired` 注解告诉 Spring，我们希望从上下文中获得它。

我们的测试本身用 `@Test` 注解。 当我们的预期值与来自网站服务器的实际值相同时，它就会通过——我们的断言语句将我们在这个 localhost 的随机端口里提供的字符串与断言语句后半部分的字符串进行比较——_Hello world from Spring Boot_。

3) 让我们运行测试来检查它是否有效。 您可以使用 **Ctrl**+**R**（macOS），或 **Shift**+**F10**（Windows/Linux）再次运行它。 我们应该可以看到我们的测试是绿色的。

![通过 HTTP 测试](passing-http-test.png)

检查我们的假设总是值得的，所以试着将文本改为 _Hello World from Spring Boot_ 以外的内容，并检查测试是否失败。 它应该是这样的！

在下一步，我们将总结到此为止的工作，并列出我们使用过的资源。 