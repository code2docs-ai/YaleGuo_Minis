# 基础信息

|      |      |
|------|------|
| 名称 | ContextLoaderListener |
| 编码语言 | .java |
| 代码路径 | Minis/src/com/minis/web/context/ContextLoaderListener.java |
| 包名 | com.minis.web.context |
| 依赖项 | ['javax.servlet.ServletContext', 'javax.servlet.ServletContextEvent', 'javax.servlet.ServletContextListener', 'com.minis.web.context.support.XmlWebApplicationContext'] |
| 概述说明 | ContextLoaderListener初始化Web应用上下文并加载XML配置。 |

# 说明

ContextLoaderListener用于初始化Web应用上下文，它通过读取XML配置文件来加载应用上下文，并将该上下文设置为ServletContext的属性，以便在整个Web应用中共享和使用。这一过程确保了应用上下文的正确加载和配置，为后续的Web请求处理提供了必要的环境支持。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| ContextLoaderListener | class | ContextLoaderListener初始化Web应用上下文，通过XML配置加载并设置ServletContext属性。 |



## 类 ContextLoaderListener

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | ContextLoaderListener |
| 说明 | ContextLoaderListener初始化Web应用上下文，通过XML配置加载并设置ServletContext属性。 |


### UML类图

```mermaid
classDiagram
    class ContextLoaderListener {
        +String CONFIG_LOCATION_PARAM
        -WebApplicationContext context
        +ContextLoaderListener()
        +ContextLoaderListener(WebApplicationContext context)
        +void contextDestroyed(ServletContextEvent event)
        +void contextInitialized(ServletContextEvent event)
        -void initWebApplicationContext(ServletContext servletContext)
    }

    class ServletContextListener {
        <<Interface>>
        +void contextDestroyed(ServletContextEvent event)
        +void contextInitialized(ServletContextEvent event)
    }

    class WebApplicationContext {
        <<Interface>>
        +void setServletContext(ServletContext servletContext)
    }

    class XmlWebApplicationContext {
        +XmlWebApplicationContext(String configLocation)
    }

    class ServletContext {
        +String getInitParameter(String name)
        +void setAttribute(String name, Object value)
    }

    class ServletContextEvent {
        +ServletContext getServletContext()
    }

    ContextLoaderListener ..|> ServletContextListener : 实现
    ContextLoaderListener --> WebApplicationContext : 依赖
    ContextLoaderListener --> XmlWebApplicationContext : 依赖
    ContextLoaderListener --> ServletContext : 依赖
    ContextLoaderListener --> ServletContextEvent : 依赖
    XmlWebApplicationContext ..|> WebApplicationContext : 实现
```

这段代码定义了一个 `ContextLoaderListener` 类，它实现了 `ServletContextListener` 接口，用于监听 Servlet 上下文的初始化和销毁事件。在 `contextInitialized` 方法中，它通过 `initWebApplicationContext` 方法初始化了一个 `WebApplicationContext`，并将其设置为 Servlet 上下文的属性。`XmlWebApplicationContext` 是 `WebApplicationContext` 的一个具体实现，用于加载 XML 配置的上下文。


### 内部方法调用关系图

```mermaid
graph TD
    A["类ContextLoaderListener"]
    B["常量: String CONFIG_LOCATION_PARAM"]
    C["属性: WebApplicationContext context"]
    D["构造方法: ContextLoaderListener()"]
    E["构造方法: ContextLoaderListener(WebApplicationContext context)"]
    F["重写方法: contextDestroyed(ServletContextEvent event)"]
    G["重写方法: contextInitialized(ServletContextEvent event)"]
    H["方法: initWebApplicationContext(ServletContext servletContext)"]
    I["获取参数: servletContext.getInitParameter(CONFIG_LOCATION_PARAM)"]
    J["创建对象: WebApplicationContext wac = new XmlWebApplicationContext(sContextLocation)"]
    K["设置上下文: wac.setServletContext(servletContext)"]
    L["赋值: this.context = wac"]
    M["设置属性: servletContext.setAttribute(WebApplicationContext.ROOT_WEB_APPLICATION_CONTEXT_ATTRIBUTE, this.context)"]

    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
    A --> G
    G --> H
    H --> I
    H --> J
    H --> K
    H --> L
    H --> M
```

这段代码定义了一个`ContextLoaderListener`类，实现了`ServletContextListener`接口，用于在Web应用启动时初始化Spring的`WebApplicationContext`。`contextInitialized`方法会在Servlet上下文初始化时被调用，进而调用`initWebApplicationContext`方法，该方法从Servlet上下文中获取配置参数，创建并设置`WebApplicationContext`对象，并将其存储在Servlet上下文中。整个流程确保了Spring应用上下文的正确初始化和配置。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| CONFIG_LOCATION_PARAM = "contextConfigLocation" | String | 定义配置位置参数的静态常量字符串。 |
| context | WebApplicationContext | 私有Web应用上下文变量声明。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| initWebApplicationContext | void | 初始化Web应用上下文，设置ServletContext并存储为根上下文。 |
| contextInitialized | void | 重写ServletContextEvent初始化方法以初始化Web应用上下文。 |
| contextDestroyed | void | 重写ServletContextEvent销毁方法，无具体实现。 |




