---
description: >-
  Plugin supports all the content mentioned in this article in all places where
  numbers are used. It can be used wherever you can think of it!
---

# 🔢 Number Format

### constant

Provide a fixed numerical value.

```yaml
type: constant
value: 1
```

{% hint style="success" %}
In most cases, you can use the following abbreviated notation.

```yaml
count:
  type: constant
  value: 1
```

->

```yaml
count: 1
```
{% endhint %}

### uniform

Provide a random number within the given range.

```yaml
type: uniform
min: 1
max: 3
```

{% hint style="success" %}
In most cases, you can use the following abbreviated notation.

```yaml
count:
  type: uniform
  min: 1
  max: 3
```

->

```yaml
count: 1~3
```

Both `min` and `max` also support the nested use of `number provider`.&#x20;

```yaml
count:
  type: uniform
  min:
    type: uniform
    min: 2
    max: 7
  max: "<papi:skilllevel_farming>*5~<papi:skilllevel_farming>*10"
```
{% endhint %}

### expression

[https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)

```yaml
type: expression
expression: "20 + 70 / 2"
```

{% hint style="success" %}
In most cases, you can use the following abbreviated notation.

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
