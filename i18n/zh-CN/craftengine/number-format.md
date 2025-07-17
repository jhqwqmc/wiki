---
description: >-
  插件支持此文章中提到的所有在使用数字的地方的内容。 它可以在你想到它的任何地方使用！
---

# :input_number: 数字格式

### 常量

提供一个固定的数值。

```yaml
类型: 常量
值: 1
```

{% hint style="success" %}
在大多数情况下，您可以使用以下缩写符号。

```yaml
计数:
  类型: 常量
  值: 1
```

->

```yaml
计数: 1
```

{% endhint %}

### 均匀度

提供给定范围内的随机数字。

```yaml
类型: 均匀的
最小: 1
最大: 3
```

{% hint style="success" %}
在大多数情况下，您可以使用以下缩写符号。

```yaml
计数：
  类型：均匀
  最小：1
  最大值：3
```

->

```yaml
计数: 1~3
```

`min`和最大`也支持嵌套使用 `number provider\`。&#x20;

```yaml
计数：
  类型：均匀
  最小：
    类型：均匀
    最小：2
    最大值：7
  最大值：“<papi:skilllevel_farming>*5~<papi:skilllevel_farming>*10”
```

{% endhint %}

### 表达式

[https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)

```yaml
输入：表达式
表达式：“20 + 70 / 2”
```

{% hint style="success" %}
在大多数情况下，您可以使用以下缩写符号。

```yaml
count:
  type: expression
  expression: "<papi:skilllevel_farming> / 20 + 5"
```

->

```yaml
count: "<papi:skilllevel_farming> / 20 + 5"
```

{% endhint %}
