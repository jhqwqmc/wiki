---
description: 此页主要解释了如何添加新项目到您的服务器。
---

# 🗡️ 项目

## 要配置的小组

完整的项目配置包含以下部分：

- **材料** (必填)

`material`是项目的基本模板，例如`paper`或`wooden_sword`。

- **客户端-边界材料** (可选)

用于此项目的 "客户端-边界-材料" 。 您可以使用此功能为服务器/客户端上的项目分配完全不同的基础材料，从而影响他们在服务器/客户端环境中的特定行为。

- **自定义模型数据** (可选)

`custom-model-data`是一个正整数，同一个`material`的自定义项目应具有不同的`custom-model-data`值。 `custom-model-data`决定项目显示的模型，对于下面`model`部分至关重要。

<pre class="language-yaml"><code class="lang-yaml">items:
  default:topaz_rod:
    material: fishing_rod
<strong>    custom-model-data: 1000
</strong>    data:
      display-name: "<!i><#FF8C00>Topaz Rod"
    model:
      template: models:fishing_rod_2d
      arguments:
        rod_model: minecraft:item/custom/topaz_rod
        rod_texture: minecraft:item/custom/topaz_rod
        rod_cast_model: minecraft:item/custom/topaz_rod_cast
        rod_cast_texture: minecraft:item/custom/topaz_rod_cast
</code></pre>

- **item-model** (1.21.2+) (可选)

定义此项目的项目模型资源位置。 例如，`default:custom_book`

1.2.4+ `assets/[namespace]/items/`\
1.2.2+ `assets/[namespace]/models/item/`

<pre class="language-yaml"><code class="lang-yaml">items:
  default:topaz_rod:
    material: fishing_rod
<strong>    item-model: minecraft:topaz_rod
</strong>    data:
      display-name: "<!i><#FF8C00>Topaz Rod"
    model:
      template: models:fishing_rod_2d
      arguments:
        rod_model: minecraft:item/custom/topaz_rod
        rod_texture: minecraft:item/custom/topaz_rod
        rod_cast_model: minecraft:item/custom/topaz_rod_cast
        rod_cast_texture: minecraft:item/custom/topaz_rod_cast
</code></pre>

{% hint style="success" %}
使用自定义模型数据具有更好的版本兼容性，因为它自1.14以来已经发布，而`item_model` 至少需要1.2.2

You can use `custom-model-data` and `item-model` at the same time
{% endhint %}

{% hint style="danger" %}
在配置模型部分时，您必须指定 `custom-model-data` 或 `item-model` 。 如果您的资源包支持版本1.2.2或更高版本，插件将自动使用项目 ID 作为`item-model`的值。 然而，如果您的项目 ID 包含了违反Minecraft规则的字符，它可能导致资源包无法正确加载。 在这种情况下，您必须使用 `custom-model-data` 或指定一个有效的 `item-model` 值。
{% endhint %}

- **client-bound-model** (可选) \[默认：config.yml中的全局客户端-边界模型值]
- **超大型内部** (1.21.6+) (可选) \[默认： true]
- **hand-animation-on-swap** (可选) \[默认：true]
- **data / 客户端-边界数据** (可选)

{% content-ref url="items/item-data" %}
[item-data](items/item-data)
{% endcontent-ref %}

- **behavior(s)** (可选)

{% content-ref url="items/item-behaviors" %}
[item-behaviors](items/item-behaviors)
{% endcontent-ref %}

- **settings** (可选)

{% content-ref url="items/item-settings" %}
[item-settings](items/item-settings)
{% endcontent-ref %}

- **模型/遗留模型** (可选)

{% content-ref url="items/item-models" %}
[item-models](items/iteme-model)
{% endcontent-ref %}

- **事件** (可选)

{% content-ref url="events" %}
[events](events
{% endcontent-ref %}

- **category** (可选)

{% content-ref url="categories" %}
[categories](categories
{% endcontent-ref %}

## 完整配置概述

```yaml
items:
  default:palm_log:
    material: paper
    custom-model-data: 1000
    settings:
      fuel-time: 300
      tags:
        - "default:palm_logs"
        - "minecraft:logs"
        - "minecraft:logs_that_burn"
    data:
      display-name: "<!i>Palm Log"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/palm_log"
      generation:
        parent: "minecraft:block/custom/palm_log"
    oversized-in-gui: true
    hand-animation-on-swap: true
    client-bound-model: false
    behavior:
      type: block_item
      block: default:palm_log
```
