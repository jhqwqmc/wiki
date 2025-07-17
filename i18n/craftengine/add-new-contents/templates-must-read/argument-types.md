# 🟢 Argument Types

## Direct Assignment

The simplest type of parameter is direct assignment, where you directly write the value after the parameter name.

```yaml
arguments:
  value_1: true
  value_2: 100

# Use a map
arguments:
  value_map:
    a: b
    c: d

# Use a list
arguments:
  value_list:
    - 123
    - 456
```

{% hint style="danger" %}
When directly assigning a map, the parameters of the map must not include `type`, otherwise an error will occur! In such cases, you should use the Map type as described below.\
❌️

```yaml
arguments:
  value_map:
    type: c
    a: b
    c: d
```

✔️

```yaml
arguments:
  value_map:
    type: map
    map:
      type: c
      a: b
      c: d
```
{% endhint %}

{% hint style="info" %}
All non-direct assignment parameter types require specifying the parameter type `type`. Below are some available parameter types and examples
{% endhint %}

## Self Increase Int

`self_increase_int` is an auto-incrementing numeric ID that increases by 1 each time the parameter is used.

> Config

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

> Result

```yaml
variants:
  axis=x:
    appearance: axisX
    id: 0
  axis=y:
    appearance: axisY
    id: 1
  axis=z:
    appearance: axisZ
    id: 2
```

## Expression

```yaml
arguments:
  saturation:
    type: expression
    expression: "{nutrition} * 1.5"
    value-type: double # int/double/float/short/long/boolean
```

## Map

Replace the placeholder with the specified map.

```yaml
arguments:
  enchantments:
    type: map
    map:
      minecraft:sharpness: 1
```

{% hint style="warning" %}
In this case, the map cannot be applied correctly

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

## List

Replace the placeholder with the specified list.

```yaml
arguments:
  lore:
    type: list
    list:
      - "Hello, Minecraft!"
```

{% hint style="warning" %}
In this case, the list cannot be applied correctly

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
