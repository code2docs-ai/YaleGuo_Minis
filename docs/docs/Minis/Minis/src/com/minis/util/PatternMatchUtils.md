# 基础信息

|      |      |
|------|------|
| 名称 | PatternMatchUtils |
| 编码语言 | .java |
| 代码路径 | Minis/src/com/minis/util/PatternMatchUtils.java |
| 包名 | com.minis.util |
| 依赖项 | ['java.util.Arrays'] |
| 概述说明 | PatternMatchUtils类支持简单模式和URI的字符串匹配。 |

# 说明

PatternMatchUtils类是一个用于字符串模式匹配的工具类，主要提供两种匹配功能：简单模式匹配和URI匹配。简单模式匹配适用于基础的字符串模式识别，而URI匹配则专门针对URI格式的字符串进行匹配。该类旨在帮助开发者高效地处理字符串模式匹配需求，适用于多种应用场景。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| PatternMatchUtils | class | PatternMatchUtils类提供字符串模式匹配功能，支持简单模式和URI匹配。 |



## 类 PatternMatchUtils

|      |      |
|------|------|
| 访问范围 | public abstract |
| 类型 | class |
| 名称 | PatternMatchUtils |
| 说明 | PatternMatchUtils类提供字符串模式匹配功能，支持简单模式和URI匹配。 |


### UML类图

```mermaid
classDiagram
    class PatternMatchUtils {
        <<Abstract>>
        +static boolean simpleMatch(String pattern, String str)
        +static boolean simpleMatch(String[] patterns, String str)
        +static boolean URIMatch(String patterns, String uri)
    }
```

### 描述
`PatternMatchUtils` 是一个抽象类，提供了三种静态方法用于字符串模式匹配。`simpleMatch` 方法支持简单的通配符模式匹配，如 `"xxx*"`, `"*xxx"`, `"*xxx*"` 和 `"xxx*yyy"`，并支持直接相等匹配。`URIMatch` 方法用于匹配 URI 路径，支持路径中的占位符匹配。这些方法在处理字符串匹配时非常有用，特别是在需要灵活匹配规则的场景中。


### 内部方法调用关系图

```mermaid
graph TD
    A["类PatternMatchUtils"]
    B["方法: boolean simpleMatch(String pattern, String str)"]
    C["方法: boolean simpleMatch(String[] patterns, String str)"]
    D["方法: boolean URIMatch(String patterns, String uri)"]
    E["检查pattern或str是否为null"]
    F["返回false"]
    G["查找pattern中第一个'*'的位置"]
    H["检查pattern是否等于str"]
    I["返回true"]
    J["检查pattern长度是否为1"]
    K["查找下一个'*'的位置"]
    L["检查str是否以pattern的剩余部分结尾"]
    M["提取pattern中的部分字符串"]
    N["检查部分字符串是否为空"]
    O["递归调用simpleMatch"]
    P["查找部分字符串在str中的位置"]
    Q["递归调用simpleMatch"]
    R["返回false"]
    S["检查str长度是否大于等于firstIndex"]
    T["检查pattern和str的前缀是否匹配"]
    U["递归调用simpleMatch"]
    V["遍历patterns数组"]
    W["调用simpleMatch"]
    X["返回false"]
    Y["拆分patterns和uri为数组"]
    Z["检查数组长度是否相等"]
    AA["遍历数组"]
    AB["检查数组元素是否相等"]
    AC["检查数组元素是否以'{'开头并以'}'结尾"]
    AD["返回false"]
    AE["返回true"]

    A --> B
    A --> C
    A --> D
    B --> E
    E -->|是| F
    E -->|否| G
    G -->|等于-1| H
    H -->|是| I
    H -->|否| S
    G -->|不等于-1| J
    J -->|是| I
    J -->|否| K
    K -->|等于-1| L
    L -->|是| I
    L -->|否| R
    K -->|不等于-1| M
    M --> N
    N -->|是| O
    N -->|否| P
    P -->|不等于-1| Q
    Q -->|是| I
    Q -->|否| R
    S -->|是| T
    T -->|是| U
    U -->|是| I
    U -->|否| R
    C --> V
    V --> W
    W -->|是| I
    W -->|否| X
    D --> Y
    Y --> Z
    Z -->|是| AA
    AA --> AB
    AB -->|是| AE
    AB -->|否| AC
    AC -->|是| AE
    AC -->|否| AD
```

**描述：** 该流程图展示了`PatternMatchUtils`类中三个主要方法的执行流程。`simpleMatch`方法用于匹配字符串与模式，支持多种模式样式，如`xxx*`、`*xxx`等。`simpleMatch`方法的重载版本用于匹配字符串与多个模式。`URIMatch`方法用于匹配URI路径与模式，支持路径参数的匹配。每个方法都包含详细的步骤和条件判断，确保匹配的准确性和灵活性。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| simpleMatch | boolean | 该方法用于匹配字符串与模式，支持通配符*。 |
| URIMatch | boolean | 方法URIMatch用于匹配URI与模式，返回布尔值。 |
| simpleMatch | boolean | 检查字符串是否匹配任一模式，匹配则返回真。 |




