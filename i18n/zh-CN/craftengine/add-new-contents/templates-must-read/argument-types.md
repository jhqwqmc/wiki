# 🟢 参数类型

## 直接作业

最简单的参数类型是直接作业，你直接在参数名称后写入值。

```yaml
参数:
  value_1: true
  value_2: 100

# 使用地图
参数:
  value_map:
    a: b
    c: d

# 使用列表
参数:
  value_list:
    - 123
    - 456
```

{% hint style="danger" %}
当直接分配地图时，地图参数不能包含 `type`，否则将发生错误！ 在这种情况下，你应该使用下面描述的地图类型。\
:cross_mark：

```yaml
参数:
  value_map:
    type : c
    a: b
    c: d
```

✔️

```yaml
参数:
  value_map:
    type : map
    map:
      type : c
      a: b
      c: d
```

{% endhint %}

{% hint style="info" %}
所有非直接作业参数类型都需要指定参数类型“type”。 以下是一些可用的参数类型和实例
{% endhint %}

## 自我提升Int

`self_incree_int` 是一个自动递增的数字ID，每次使用参数时增加1个。

> 配置

<pre class="language-yaml"><code class="lang-yaml"># Part of template
variants:
  axis=x:
    appearance: axisX
    id: "{internal_id}"
  axis=y:
    appearance: axisY
    id: "{internal_id}"
  axis=z:
    appearance: axisZ
    id: "{internal_id}"
<strong>
</strong># Part of the block config
arguments:
  internal_id:
    type: self_increase_int
    from: 0
    to: 2
</code></pre>

> 结果

```yaml
变量：
  坐标轴=x：
    外观：轴X
    id：0
  坐标轴=y：
    外观：轴
    id：1
  坐标：
    外观：
    id：2
```

## 表达式

```yaml
arguments:
  saturation:
    type: expression
    expression: "{nutrition} * 1.5"
    value-type: double # int/double/float/short/long/boolean
```

## 地图

用指定的地图替换占位符。

```yaml
参数:
  附魔:
    类型: 地图
    地图:
      minecraft:sharpness: 1
```

{% hint style="warning" %}
在这种情况下，地图无法正确应用

❌️

```
template:
  components:enchantments: "{enchantments}, 123"
```

✔️

```
template:
  components:enchantments: "{enchantments}"
```

{% endhint %}

## 列表

用指定的列表替换占位符。

```yaml
arguments:
  lore:
    type: list
    list:
      - "Hello, Minecraft!"
```

{% hint style="warning" %}
在这种情况下，列表无法正确应用

❌️

```
template:
  lore: "{lore}, 1"
```

✔️

```
template:
  lore: "{lore}"
```

{% endhint %}
