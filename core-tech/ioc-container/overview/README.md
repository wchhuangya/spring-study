# 2.1.2 容器概述

接口 `org.springframework.context.ApplicationContext` 表示 `Spring IoC` 容器，并负责实例化、配置和组装上述 `bean`。容器通过读取配置元数据来获取有关要实例化、配置和组装的对象的指示信息。配置元数据用 `XML`、`Java` 注释或 `Java` 代码表示。它允许你表示组成应用程序的对象以及这些对象之间丰富的相互依赖关系。

`Spring` 提供了几个 `ApplicationContext` 接口的实现。在独立应用程序中，通常会创建 `ClassPathXmlApplicationContext` 或 `FileSystemXmlApplicationContext` 的实例。虽然 `XML` 是用于定义配置元数据的传统格式，但你也可以通过提供少量的 `XML` 配置来指示容器使用 `Java` 注释或代码作为元数据格式，以声明方式支持这些其他元数据格式。

在大多数应用场景中，显式用户代码不需要实例化 `Spring IoC` 容器的一个或多个实例。例如，在 `Web` 应用程序场景中，应用程序的 `web.xml` 文件中简单的 `8` 个（或多个）样板 `Web` 描述符用于描述 `XML` 行就足够了（请参阅 [**Web应用程序的便捷ApplicationContext实例化**](./) ）。如果你使用的是 `Eclipse` 开发环境中的 [**Spring Tools Suite**](https://spring.io/tools/sts) ，则只需点击几下鼠标或按键即可轻松创建此样板配置。

下图是 `Spring` 如何工作的高级视图。你的应用程序类与配置元数据相结合，这样就可以在创建并初始化 `ApplicationContext` 之后，拥有完全配置且可执行的系统或应用程序。

![](../../../.gitbook/assets/1.png)

