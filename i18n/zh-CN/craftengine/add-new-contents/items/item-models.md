---
description: 此页主要解释了如何配置项目模型。
---

# :very_equals_sign: 项目模型

{% hint style="warning" %}
自1.21.4版本以来，Minecraft已经开始支持更复杂的项目模型。 这允许您为项目创建更多动态变体。 本教程专门针对1.21.4及以上版本。 对于旧版本，插件会降低相应模型文件的等级(注意：这与旧版本不兼容100%) 旧版本中不存在许多条件和型号)。
{% endhint %}

{% hint style="danger" %}
如果您发现CraftEngine 在最新版本中缺少一些功能， 您可以在 GitHub 上提交一个问题来提请开发者注意。
{% endhint %}

## 一. 导言

让我们把最简单的`minecraft:model` [model](item-models/model "提及") 类型作为一个例子。

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
如果您没有指定一个 `type`，它将默认使用 \`minecraft:model'。 因此，上述配置与以下配置相同。

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

从上述配置中，我们可以在模型部分看到这一点。 您必须填写模型的类型及其相应参数。 下面是所有可用模型类型的列表。 一些模型(例如范围调度、选择、合成和条件)支持嵌套模型使用。 您可以点击下面的链接来跳转到相应的模型类型。 一旦你们阅读了所有这些，我们将着手讨论更复杂的例子。

{% content-ref url="item-models/model" %}
[model](item-models/modell)
{% endcontent-ref %}

{% content-ref url="item-models/composite" %}
[composite](item-models/compose)
{% endcontent-ref %}

{% content-ref url="item-models/condition" %}
[condition](item-models/condition)
{% endcontent-ref %}

{% content-ref url="item-models/range-dispatch" %}
[range-dispatch](item-models/range-appailch)
{% endcontent-ref %}

{% content-ref url="item-models/select" %}
[select](item-models/select)
{% endcontent-ref %}

{% content-ref url="item-models/special" %}
[special](item-models/special)
{% endcontent-ref %}

## 示例：

{% hint style="info" %}
在下面的例子中，通过结合`condition`、`model`和`range_dispatch`来创建一个自动生成2D十字弓的模板。
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

## 传统模型

**“传统模型”**具体指在版本**1.21.3及之前**中使用的项目模型格式。 您可以使用 **legacy-model** 部分指定旧项目模型格式。 然而，在大多数情况下，你不需要这样做，因为插件将在可能的情况下自动将 **1.21.4 项模型** 转换成遗留格式。 只有在遗留模型格式出现问题时，您才应该使用此配置部分。

```yaml
items#topaz_gears:
  default:topaz_rod:
    material: fishing_rod
    item: default:topaz_rod
    custom-model数据: 1000
    settings:
      tags:
        - "default:topaz_tools"
    data:
      item-name: "<! ><#FF8C00><i18n:item.topaz_rod>"
      tooltip-style: minecraft:topaz
    model:
      template: default:model/similed_fishing_rod_2d
      参数:
        路径: minecraft:item/custom/topaz_rod
        cast_path: minecraft:items/custom/topaz_rod_cast
    # 如果你在legacy-model中指定一个模型。 
    # 插件将使用您手动定义的模型而不是 
    # 依靠自动转换旧格式。
    legacy-model:
      路径: minecraft:item/custom/topaz_rod
      覆盖:
        - 路径: minecraft:item/custom/topaz_rod_caste
          prediction: 
            cast: 1
```
