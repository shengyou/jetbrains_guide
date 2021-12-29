---
type: TutorialStep
date: 2021-09-20
title: 移动代码的例子
technologies: [ ]
topics: [ ]
author: hs
subtitle: 在一个类上调用重新排列代码并查看结果
thumbnail: ./thumbnail.png
---

## 代码重新排列前后的示例
让我们为这个例子修改代码排列设置。 具体来说，我们希望创建一个新的规则，将 private 方法放置在每个类的底部。

### 修改现有的排列规则
您可以使用 **⌘,**（macOS）或 **Ctrl+Alt+S**（Windows/Linux），然后搜索 _arrangement（排列）_来变更您的排列规则偏好设置。 从过滤列表中选择 **Editor（编辑器）> Code Style（代码样式）> Java**，然后选择 **Arrangement（排列）**标签。

### 排序设置/偏好设置
要修改您的代码排列的设置，使用 **⌘,**（macOS）或 **Ctrl+Shift+S**（Windows/Linux）打开偏好设置/设置对话框。 这个对话框是可以搜索的，所以您可以输入 _arrangement（排列）_。 这可以把对话框过滤到 **Code Style（代码样式）**。 然后您可以选择您正在使用的语言。 在这个教程中，我们将使用 **Java**。 或者您可以导航到 **Editor（编辑器）> Code Stytle（代码样式）> Java**。

排列标签可以分为两个区域：
- [分组规则](#grouping-rules)
- [匹配规则](#matching-rules)

#### 分组规则
IntelliJ IDEA 允许您对这三个代码元素进行分组：

**Getters and Setters（getter 和 setter）** 是相当不言自明的。 当选择此复选框，并调用重排代码时，您的 getter 和 setter 将在您的类中被分组在一起。 这是默认选项。

**Override methods（重写方法）**类似 Getters 和 Setters，因为它将在您的类中将您的重写方法分组在一起。 您还可以使用根据它们在超类或者接口的顺序的选项来排序它们，或者根据它们的名字排序。 在我们的例子里，让我们选择此复选框。

**Dependent methods（依赖方法）** 有下拉框，可以允许您选择广度优先或者深度优先的方式来组合方法。 您可能有此选项的用例，但对于大多数随着时间的推移而演变的 Java 代码库，尝试将_相关_的方法放在一起通常不是您想要做的。 如果您选择使用此选项，则它会优先于匹配规则。 我们建议您使用此选项或匹配规则，而不是两者都使用。 在我们的示例中，我们将使用下一节中定义的匹配规则，因为这是一个更常见的真实场景。

#### 匹配规则
这里您可以定义当您使用重新排列代码时，您希望您的类如何被排序。 您可以选择一行，并根据需要用右上角的箭头向上或向下移动。 您也可以点击每一行右边的铅笔图标来修改规则，选择更精细的粒度。

### 添加新的排列规则
要添加我们的新规则，请滑到规则 22 并按下 **+** 按钮。 这将使新规则在 22 之下。 选择类型：**method（方法）** 和修饰符：**private**。 如果需要的话，您可以给它起个名字，但是类型和修饰符都显示了，所以对这个例子来说可能没有必要。

![New rule for private methods](new_arrangement_rule.png)

Now we've modified our [code arrangement](https://www.jetbrains.com/help/idea/reformat-and-rearrange-code.html#arrange_code) let's take a look at what it looks like. Note our specific rule here that puts `private` methods at the bottom of the class which can be very useful. You can see this in rule 23.

Given you can't scroll a screenshot, here is the order in text form, so you can see what's happening:

|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
 1 | field | public | static | final | 2 | field | protected | static | final | 3| field | package private | static | final| 4| field | private | static | final| 5| field | public | static | | 6| field | protected | static | | 7| field | package private | static | | 8| field | private | static | | 9| initializer block | static | | | 10| field | public | final | | 11| field | protected | final | | 12| field | package private | final | | 13| field | private | final | | 14| field | public | | | 15| field | protected | | | 16| field | package private | | | 17| field | private | | | 18| field | | | | 19| initializer block | | | | 20| constructor | | | | 21| method | static | | | 22| method | | | | 23| method | private | | | 24| enum | | | | 25| interface | | | | 26| class | static | | | 27| class | | | |

Here's the code that we're going to rearrange. As you can see, the getter and setter methods are not together, private methods are in the middle of the class and override methods are also scattered throughout the class.

```java
public class RearrangeCode {
    private int id;

    public int getId() {
        return id;
    }

    @Override
    public String toString() {
        return "RearrangeCode{" +
               "id=" + id +
               ", firstName='" + firstName + '\'' +
               ", middleName='" + middleName + '\'' +
               ", lastName='" + lastName + '\'' +
               ", phone='" + phone + '\'' +
               ", notes='" + notes + '\'' +
               ", ordersById=" + ordersById +
               '}';
    }

    private String firstName;

    private void privateHelperMethod() {
        // does something in here
    }

    public void setId(int id) {
        int newID = 1;
        System.out.println(newID);
        this.id = id;
    }

    private String middleName;

    public String getMiddleName() {
        return middleName;
    }

    public void setMiddleName(String middleName) {
        this.middleName = middleName;
    }

    private String lastName;

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    private String phone;

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }

    private String notes;

    public String getNotes() {
        return notes;
    }

    public void setNotes(String notes) {
        this.notes = notes;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        RearrangeCode that = (RearrangeCode) o;
        return id == that.id &&
               Objects.equals(firstName, that.firstName) &&
               Objects.equals(middleName, that.middleName) &&
               Objects.equals(lastName, that.lastName) &&
               Objects.equals(phone, that.phone) &&
               Objects.equals(notes, that.notes) &&
               Objects.equals(ordersById, that.ordersById);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, firstName, middleName, lastName, phone, notes, ordersById);
    }

    private Collection<Order> ordersById;

    public Collection<Order> getOrdersById() {
        return ordersById;
    }

    public void setOrdersById(Collection<Order> ordersById) {
        this.ordersById = ordersById;
    }
}

```

Let's invoke [rearrange code](https://www.jetbrains.com/help/idea/reformat-and-rearrange-code.html#arrange_code) with **⌘⇧A** (macOS), or **Ctrl+Shift+A** (Windows/Linux). In the Find Actions dialog you can type in _Rearrange Code_:

![Rearrange Code](rearrange-code.png)

Press **Enter** on **Rearrange Code** option to apply the settings to the whole class.

When you do this, the code will be rearranged (see below). Here is a list of changes:
- All the fields have moved to the top of the class because that's what we specified in our grouping rows 1-8.
- The getter and setter methods are grouped because IntelliJ IDEA has grouped them together from the grouping rules.
- The Override methods have been grouped together because we specified we wanted to keep them together in the grouping rules). The Override methods are also implemented in the order they appear in the Object super class.
- Next are the remaining two public methods, which are obeying line 22 of our matching rules.
- Finally, there's the private method which is obeying line 23 of our matching rules.

```java
public class RearrangeCode {
    private int id;
    private String firstName;
    private String middleName;
    private String lastName;
    private String phone;
    private String notes;
    private Collection<Order> ordersById;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        int newID = 1;
        System.out.println(newID);
        this.id = id;
    }

    public String getMiddleName() {
        return middleName;
    }

    public void setMiddleName(String middleName) {
        this.middleName = middleName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }

    public String getNotes() {
        return notes;
    }

    public void setNotes(String notes) {
        this.notes = notes;
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, firstName, middleName, lastName, phone, notes, ordersById);
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        RearrangeCode that = (RearrangeCode) o;
        return id == that.id &&
               Objects.equals(firstName, that.firstName) &&
               Objects.equals(middleName, that.middleName) &&
               Objects.equals(lastName, that.lastName) &&
               Objects.equals(phone, that.phone) &&
               Objects.equals(notes, that.notes) &&
               Objects.equals(ordersById, that.ordersById);
    }

    @Override
    public String toString() {
        return "RearrangeCode{" +
               "id=" + id +
               ", firstName='" + firstName + '\'' +
               ", middleName='" + middleName + '\'' +
               ", lastName='" + lastName + '\'' +
               ", phone='" + phone + '\'' +
               ", notes='" + notes + '\'' +
               ", ordersById=" + ordersById +
               '}';
    }

    public Collection<Order> getOrdersById() {
        return ordersById;
    }

    public void setOrdersById(Collection<Order> ordersById) {
        this.ordersById = ordersById;
    }

    private void privateHelperMethod() {
        // does something in here
    }
}


```
## Rearranging Just Code You've Changed
Now you've seen a worked example of rearranging a whole class, let's take a look at the use-case for only rearranging code that you've edited rather than the whole class. 