---
type: TutorialStep
date: 2021-06-02
title: 创建仓库接口
technologies: [ ]
topics: [ ]
author: da
subtitle: 为 CRUD 操作创建 Spring Data 仓库。
thumbnail: ./thumbnail.png
---

现在，我们已经创建了我们的员工实体，我们需要一种方法来执行我们的 CRUD（创建、读取、更新、删除）操作。 幸运的是，Spring Data JPA 可以通过 Repositories （仓库）提供所有基本操作。 让我们看看它是如何工作的。

在 **Project（项目）** 窗口中，我们将选择 ` com.jetbrains.springdatajpaapp ` 包，并按 **Alt** + **Insert**（Windows/Linux）或**⌘N**（macOS）。 选择 ** Java Class （Java 类） **。 我们将之命名为 ` EmployeeRepository ` ，这次我们将选择 **Interface（接口）** 然后按 **Enter （回车键）**。 为了使我们的接口类能成为repository，我们需要它来继承 `CrudRespository<T, ID>` 接口，具有我们的实体类和实体的 ID 类型的参数。 因此，对于我们的应用程序，我们的仓库接口定义将是：`public interface EmployeeRepository extends CrudRepository<Employee, Long>`。

We will be using this `EmployeeRepository` interface to perform CRUD operations in our application code. Since we are extending `CrudRepository`, we get access to basic CRUD methods by default. For example, we can call the `save` method to insert an Employee object into our database. We could also call the `findAll` method to list all the Employees in your Employee table. We will see how to do this when we write our application logic.

In most applications, you'll find yourself wanting to do more than what the `CrudRepository` interface provides for you by default.  For example, let's say we want to find all employees that have a space in their last name. You can certainly write a SQL query to do that. However, an easier way is to take advantage of Spring Data JPA which lets you create methods in your repository that will be translated into queries based on your method name.

For example, let's say we want to add the method for finding all employees that have a certain string in their last name. We'll go to our `EmployeeRepository` interface and start declaring our method. My method will return a list of employees so we will use `List<Employee>` as our return type. Then, we need to specify a method name that has two parts: the introducer and the criteria. We can use **Ctrl**+**Space** in IntelliJ IDEA to see a list of method suggestions for the introducer:

![Repository Method Suggestion Introducer](./RepositoryMethodSuggestion.png)

We'll select `findEmployeesBy` for the introducer. Then, we will click **Ctrl**+**Space** again to see the list of criteria to choose from.

![Repository Method Suggestion Criteria](./RepositoryMethodSuggestion-Criteria.png)

We'll select `LastNameContaining`. Finally, we'll declare a String method parameter representing the string that we want to check for. We now have a method that finds all employees with a last name containing the string provided.

You might be thinking: if I've defined this interface, don't I have to implement it? The answer is no. Spring Data JPA takes care of that for you! All you need to do is define your Repository interface and declare your methods following the Spring Data conventions. As you're adding more methods, if you make mistakes in the method name, IntelliJ IDEA will point it out. For example, if we try to create a method for querying employees with an incorrect `LName` property, IntelliJ IDEA gives us an error saying `Cannot resolve property LName`.

![Method Signature Validation](./MethodSignatureValidation.png)

## 最终结果

Your `EmployeeRepository` interface should look like this:
```java
package com.jetbrains.springdatajpaapp;

import org.springframework.data.repository.CrudRepository;

import java.util.List;

public interface EmployeeRepository extends CrudRepository<Employee, Long> {
    List<Employee> findEmployeesByLastNameContaining(String str);
}
```

