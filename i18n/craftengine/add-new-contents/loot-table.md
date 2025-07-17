---
description: This page mainly explains how to configure loots
---

# 💎 Loot Table

## Introduction

Under `loots`, there must be a `pools` list, which represents the loot pools. Each loot pool consists of four parts:&#x20;

`rolls` determines how many times the pool is rolled\
`conditions` represent the conditions for the loot\
`entries` denote the actual loot items \
`functions` are the post-processing functions, such as modifying the quantity of the loot, NBT data, and so on

{% hint style="info" %}
If you are well-acquainted with vanilla data packs, you will find this structure very familiar. The plugin employs this format and modifies it to facilitate a swift and smooth transition into the CraftEngine loot system.
{% endhint %}

```yaml
loot:
  functions: []
  pools:
    - rolls: 1
      conditions:
        - type: survives_explosion
      entries:
        - type: item
          item: "minecraft:apple"
      functions: []
```

## ☘️ Entry

The 'entry' specifies the actual contents of the drop, but in certain scenarios, it can also represent a choice among possible drops.

{% hint style="success" %}
All `entry` sections are capable of using `functions` and `conditions`.

```yaml
type: item
item: "minecraft:apple"
functions: []
conditions: []
```
{% endhint %}

### item

Set the type of the dropped item, which can be a custom item.

```yaml
type: item
item: "minecraft:apple"
```

### furniture\_item

Sets the item to the original furniture item when placed, otherwise uses the fallback item.

```yaml
type: furniture_item
item: "default:fallback_item"
```

### exp

Drop a certain amount of experience.

```yaml
type: exp
count: 1
```

### alternatives

Find the first `entry` from the given list that meets the `conditions`.

```yaml
type: alternatives
children:
  - type: item
    item: "${ore_block}"
    conditions:
      - type: enchantment
        predicate: minecraft:silk_touch>=1
  - type: item
    item: "${ore_drop}"
    functions:
      - type: apply_bonus
        enchantment: minecraft:fortune
        formula:
          type: ore_drops
      - type: explosion_decay
      - type: drop_exp
        count:
          type: uniform
          min: "${min_exp}"
          max: "${max_exp}"
```

## 🔧 Function

The role of the `function` is to perform additional operations on the item after its type has been set, such as adjusting the quantity. It can also handle concurrent operations like dropping experience or other extras.

{% hint style="success" %}
All `function` sections support the use of `conditions`.

```yaml
type: set_count
count: 10
conditions: []
```
{% endhint %}

### apply\_bonus

Increase the quantity of the dropped items based on the given enchantments and formulas. Refer to [#formula](#formula "mention") for more info.

```yaml
type: apply_bonus
enchantment: minecraft:fortune
formula:
  type: ore_drops
```

### set\_count

Set the count of the item.

```yaml
type: set_count
count: 10
add: true  # add or set
```

### explosion\_decay

Determines whether the quantity of this item diminishes upon explosion. In vanilla Minecraft, explosions often result in fewer blocks being dropped than originally present, which is due to the implementation of this function.

```yaml
type: explosion_decay
```

### drop\_exp

Drop a certain amount of experience.

```yaml
type: drop_exp
count: 1
```

## ⚖️ Condition

`condition` can provide prerequisites for both `entry` and `function`.

{% content-ref url="conditions" %}
[conditions](conditions)
{% endcontent-ref %}

## ➕️ Formula

### ore\_drops

The same drop algorithm used in vanilla Minecraft.

```yaml
type: ore_drops
```

### binomial\_with\_bonus\_count

The same binomial drop algorithm used in vanilla Minecraft. `extra` means a few extra attempts to drop the item, and `probability` represents the probability of success each time. The enchantment level will increase the number of attempts.

```yaml
type: binomial_with_bonus_count
extra: 3
probability: 0.5
```
