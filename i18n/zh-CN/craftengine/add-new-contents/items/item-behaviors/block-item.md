# 🧱 屏蔽项目

一个块项是一个绑定到一个块的项目。 您可以在这里配置相应的块 ID 。 或者甚至整个区块配置(请注意这样做会导致加载该区块的时间被记录到项目加载过程中)。 当您将此行为绑定到某个项目时，您可以通过右键放置它。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/0g6l5DAJuu3yiN1h9X0I/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Please note, where a block can be placed is determined by its [block-behaviors](../../blocks/block-behaviors "mention"). 例如， 图像中的锯齿只能放在带有“dirt”或“farmland”标签的块上，因为它的块行为是一个“锯齿块”。
{% endhint %}

```yaml
items:
  default:palm_sapling:
    material: paper
    behavior:
      type: block_item
      block: default:palm_sapling
```

这是配置一个区块项的最简单方法，但它假定你已经配置了一个区块。 如果您不确定如何配置一个方块，请参阅 [blocks](../../blocks "提及")。

{% hint style="success" %}
如果您发现单独配置它们太麻烦，您可以选择一起配置。 下面是一个例子。 `block`下的格式遵循标准块配置格式。

```yaml
items:
  default:palm_sapling:
    material: paper
    custom-model-data: 1005
    settings:
      fuel-time: 100
    data:
      item-name: "<!i><i18n:item.palm_sapling>"
    model:
      template: "default:model/generated"
      arguments:
        model: "minecraft:item/custom/palm_sapling"
        texture: "minecraft:block/custom/palm_sapling"
    behavior:
      type: block_item
      block:
        settings:
          template: "default:settings/sapling"
          overrides:
            item: default:palm_sapling
        behavior:
          type: sapling_block
          feature: craftengine:palm_tree
          bone-meal-success-chance: 0.45
          tags:
            - minecraft:dirt
            - minecraft:farmland
            - minecraft:sand
        loot:
          template: "default:loot_table/basic"
          arguments:
            item: default:palm_sapling
        states:
          properties:
            stage:
              type: int
              default-value: 0
              range: 0~1
          appearances:
            default:
              state: oak_sapling:0
              model:
                path: "minecraft:block/custom/palm_sapling"
                generation:
                  parent: "minecraft:block/cross"
                  textures:
                    "cross": "minecraft:block/custom/palm_sapling"
          variants:
            stage=0:
              appearance: "default"
              id: 0
            stage=1:
              appearance: "default"
              id: 1
```

{% endhint %}
