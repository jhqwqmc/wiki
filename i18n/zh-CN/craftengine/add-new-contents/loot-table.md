---
description: 这个页面主要解释如何配置掠夺物
---

# 💎 战利品表

## 一. 导言

在“lots”项下，必须有一个“池”列表，代表掠夺池。 每个战利品池由四个部分组成：&#x20;

`rolls` determines how many times the pool is rolled\
`conditions` represent the conditions for the loot\
`entries` denote the actual loot items \
`functions` are the post-processing functions, such as modifying the quantity of the loot, NBT data, and so on

{% hint style="info" %}
如果你非常熟悉原版数据包，你会发现这个结构非常熟悉。 插件使用此格式并修改它，以方便快速和顺利地过渡到CraftEngine战利品系统。
{% endhint %}

```yaml
lot:
  函数: []
  池:
    - 滚动: 1
      条件:
        - 类型: 幸存者_severy
      条目:
        - 类型: 项目
          项目: "minecraft:apple"
      函数: []
```

## ☘️ 条目

"条目"指定了下拉的实际内容，但在某些场景中，它也可以在可能的下拉菜单中作出选择。

{% hint style="success" %}
所有`entry`部分都能使用 `functions` 和 `conditions`。

```yaml
输入：项目
项：“minecraft:apple”
函数：[]
条件：[]
```

{% endhint %}

### 项目

设置丢弃项目的类型，它可以是自定义项目。

```yaml
输入：项目
条目：“minecraft:apple”
```

### 家具\_物品

将物品设置为放置后的原家具，否则使用后备物品。

```yaml
类型：abwure_item
item: "default:fallback_item"
```

### exp

丢掉一定的经验。

```yaml
类型: exp
计数: 1
```

### 备选办法

从指定的列表中找到符合`conditions`的第一个“条目”。

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

## 🔧 函数

\`function' 的作用是在项目类型设置后执行额外的操作，例如调整数量。 它也可以处理并行操作，如丢弃经验或其他扩展。

{% hint style="success" %}
所有`function` 部分支持使用 `conditions` 。

```yaml
类型：set_count
计数：10
条件：[……]
```

{% endhint %}

### 应用\_加成

根据给定的附魔和公式增加丢弃物品的数量。 更多信息请参阅[#formula](#formulate "mention")

```yaml
类型：应用红包
附魔：minecraft：幸运的
公式：
  类型：ore_drops
```

### 设置\_计数

设置项目的计数。

```yaml
类型：set_count
计数：10
添加：true # 添加或设置
```

### explosion\_decay

确定爆炸时该物品的数量是否减少。 在香草矿中，爆炸常常导致丢弃的区块少于原先的区块，这是因为执行了这一功能。

```yaml
类型：爆炸损益
```

### 丢弃\_exp

丢掉一定的经验。

```yaml
类型: drop_exp
计数: 1
```

## :balanc_scale : 条件

`condition` 可以为`entry` 和 `function` 提供前提条件。

{% content-ref url="conditions" %}
[conditions](conditions
{% endcontent-ref %}

## ➕ 公式：

### 矿石\_掉落率

原版Minecraft中使用的同一丢弃算法。

```yaml
类型：矿石掉落数
```

### 二进制\_with\_bonus\_count

原版Minecraft中使用的同一个二级拖放算法。 “额外”意味着几次额外尝试丢弃物品，“概率”表示每次成功的概率。 附魔级别将增加尝试次数.

```yaml
类型: binomial_with_bonus_count
额外: 3
概率: 0.5
```
