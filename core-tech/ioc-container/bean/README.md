# 2.1.3 bean 概述

`Spring IoC` 容器管理一个或多个 `bean`。这些 `bean` 是使用容器的配置元数据创建的，例如，以 `XML <bean />`定义的形式。

在容器本身中，这些 `bean` 定义表示为 `BeanDefinition` 对象，其中包含以下元数据（以及其他信息）：

* 包限定的类名称：通常是所定义的 `bean` 的实际实现类
* `Bean` 行为配置元素，它说明 `bean` 在容器中的行为（范围，生命周期回调等）
* 引用其它的 `bean` 为其个 `bean` 工作。这样的引用也称为协作或依赖关系
* 在新创建的对象中设置的其他配置，例如，用于管理连接池 `Bean` 的连接数量或池的大小限制。这个元数据转化为一组构成每个 `bean` 定义的属性。

元数据转换为组成 `bean` 定义的一系列属性：

| 属性 | 解释 |
| --- | --- |
| `class` | [**实例化 bean**](2.1.3.2-shi-li-hua-bean.md) |
| `name` | [**bean 的命名**](2.1.3.1-bean-de-ming-ming.md) |
| `scope` | [**bean 范围**](./) |
| `constructor arguments` | [**依赖注入**](./) |
| `properties` | [**依赖注入**](./) |
| `autowiring mode` | [**自动装配协作**](./) |
| `lazy-initialization mode` | [**延迟初始化 bean**](./) |
| `initialization method` | [**初始化回调**](./) |
| `destruction method` | [**销毁回调**](./) |

除了包含有关如何创建特定 `bean` 信息的 `bean` 定义之外， `ApplicationContext` 实现还允许用户在容器外部创建的现有对象的注册。这是通过 `getBeanFactory（）` 方法访问 `ApplicationContext` 的 `BeanFactory` 来完成的，该方法返回 `BeanFactory` 实现的 `DefaultListableBeanFactory`。`DefaultListableBeanFactory` 通过方法 `registerSingleton（..）` 和 `registerBeanDefinition（..）` 来支持这种注册。但是，典型的应用程序只能通过元数据 `bean` 定义来定义 `bean`。

> `Bean` 元数据和手动提供的单例实例需要尽早注册，以便容器在自动装配和其他自省步骤中去推理它们。虽然重写现有的元数据和现有的单例实例在某种程度上受到支持，但在运行时注册新的 `Bean`（与实时访问工厂同时）并未得到正式支持，并且可能导致并发访问异常和/或 `bean` 容器中的状态不一致。

