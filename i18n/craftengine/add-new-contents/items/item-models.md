---
description: This page mainly explains how to configure models for an item.
---

# 🟰 Item Models

{% hint style="warning" %}
Since version 1.21.4, Minecraft has started supporting more complex item models. This allows you to create more dynamic variants for items. This tutorial is specifically for version 1.21.4 and above. For older versions, the plugin will downgrade the corresponding model files (note: this is not 100% compatible with older versions, as many conditions and model types do not exist in older versions).
{% endhint %}

{% hint style="danger" %}
If you discover that CraftEngine lacks some features in latest Minecraft version, you might submit an issue on GitHub to bring this to the attention of the developers.
{% endhint %}

## Introduction

Let's take the simplest `minecraft:model` [model](item-models/model "mention") type as an example.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/wSGX7wtV4qUdSwqNGm6Z/image.png" alt=""><figcaption></figcaption></figure>

```yaml
items:
  default:topaz_pickaxe:
    model:
      type: minecraft:model
      path: minecraft:item/custom/topaz_pickaxe
      generation:
        parent: "minecraft:item/handheld"
        textures:
          "layer0": "minecraft:item/custom/topaz_pickaxe"
```

{% hint style="success" %}
If you do not specify a `type`, it will default to using `minecraft:model`. Therefore, the configuration above is the same as the configuration below.

```yaml
items:
  default:topaz_pickaxe:
    model:
      path: minecraft:item/custom/topaz_pickaxe
      generation:
        parent: "minecraft:item/handheld"
        textures:
          "layer0": "minecraft:item/custom/topaz_pickaxe"
```
{% endhint %}

{% hint style="danger" %}
If you are unsure how to handle model `generation` and model `path` specification, please read [model-generation](../model-generation "mention").
{% endhint %}

From the above configuration, we can see that under the model section, you are required to fill in the type of the model and its corresponding parameters. Below is a list of all available model types. Some models (such as range dispatch, select, composite, and condition) support nested model usage. You can click on the link below to jump to the corresponding model type. Once you have read through all of them, we will proceed to discuss more complex examples.

{% content-ref url="item-models/model" %}
[model](item-models/model)
{% endcontent-ref %}

{% content-ref url="item-models/composite" %}
[composite](item-models/composite)
{% endcontent-ref %}

{% content-ref url="item-models/condition" %}
[condition](item-models/condition)
{% endcontent-ref %}

{% content-ref url="item-models/range-dispatch" %}
[range-dispatch](item-models/range-dispatch)
{% endcontent-ref %}

{% content-ref url="item-models/select" %}
[select](item-models/select)
{% endcontent-ref %}

{% content-ref url="item-models/special" %}
[special](item-models/special)
{% endcontent-ref %}

## Examples

{% hint style="info" %}
In the following example, a template for automatically generating a 2D crossbow is created by combining `condition`, `model`, and `range_dispatch`.
{% endhint %}

```yaml
templates:
  default:model/crossbow_2d:
    type: "minecraft:condition"
    property: "minecraft:using_item"
    on-false:
      type: "minecraft:select"
      property: "minecraft:charge_type"
      cases:
        - when: arrow
          model:
            type: minecraft:model
            path: "${arrow_model}"
            generation:
              parent: "minecraft:item/crossbow_arrow"
              textures:
                "layer0": "${arrow_texture}"
        - when: rocket
          model:
            type: minecraft:model
            path: "${firework_model}"
            generation:
              parent: "minecraft:item/crossbow_firework"
              textures:
                "layer0": "${firework_texture}"
      fallback:
        type: minecraft:model
        path: "${model}"
        generation:
          parent: "minecraft:item/crossbow"
          textures:
            "layer0": "${texture}"
    on-true:
      type: "minecraft:range_dispatch"
      property: "minecraft:crossbow/pull"
      entries:
        - model:
            type: minecraft:model
            path: "${pulling_1_model}"
            generation:
              parent: "minecraft:item/crossbow_pulling_1"
              textures:
                "layer0": "${pulling_1_texture}"
          threshold: 0.58
        - model:
            type: minecraft:model
            path: "${pulling_2_model}"
            generation:
              parent: "minecraft:item/crossbow_pulling_2"
              textures:
                "layer0": "${pulling_2_texture}"
          threshold: 1.0
      fallback:
        type: minecraft:model
        path: "${pulling_0_model}"
        generation:
          parent: "minecraft:item/crossbow_pulling_0"
          textures:
            "layer0": "${pulling_0_texture}"
```

## Legacy Model

**"Legacy model"** specifically refers to the item model format used in versions **1.21.3 and earlier**. You can specify the legacy item model format using the **legacy-model** section. However, in most cases, you don’t need to do this because the plugin will automatically convert **1.21.4 item models** into the legacy format whenever possible. You should only use this configuration section if there are issues with the legacy model format.

```yaml
items#topaz_gears:
  default:topaz_rod:
    material: fishing_rod
    item-model: default:topaz_rod
    custom-model-data: 1000
    settings:
      tags:
        - "default:topaz_tools"
    data:
      item-name: "<!i><#FF8C00><i18n:item.topaz_rod>"
      tooltip-style: minecraft:topaz
    model:
      template: default:model/simplified_fishing_rod_2d
      arguments:
        path: minecraft:item/custom/topaz_rod
        cast_path: minecraft:item/custom/topaz_rod_cast
    # If you specify a model in the legacy-model section, 
    # the plugin will use your manually defined model instead of 
    # relying on the auto-converted legacy format.
    legacy-model:
      path: minecraft:item/custom/topaz_rod
      overrides:
        - path: minecraft:item/custom/topaz_rod_cast
          predicate: 
            cast: 1
```
