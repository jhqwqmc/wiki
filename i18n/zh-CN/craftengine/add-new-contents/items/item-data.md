---
description: >-
  设置原版 NBT/组件来使用某些本地Minecraft功能。
---

# :input_number: 项目数据

## 什么是项目数据？

项目数据是指旧版本中项目的NBT (命名二进制标签)，或1.20.5及以上版本中的项目组件。 通过这种数据，我们可以自定义一个项目的各个方面，例如名称、描述、属性和其他功能。

## 外部数据

如果你想要一个 CraftEngine 项目保留外部插件项目的数据，请按照此配置：

```yaml
项目:
  默认值:example_item:
    data:
      外部:
        plugin: neigeitems
        id: example_item
```

{% content-ref url="../../compatibility/external-item-sources" %}
[external-item-sources](../../compatibility/external-item-sources)
{% endcontent-ref %}

## 硬编码数据

在这种情况下，硬代码数据意味着配置格式由插件提供和维护，从而确保不同版本之间的兼容性。 这些格式由插件定义， 这样他们可能不同于标准的 NBT (命名二进制标签) 或游戏本身使用的组件格式。 此方法的优点是插件处理所有维护，包括版本兼容性。 所以用户不需要担心游戏版本之间的更改或更新。

```yaml
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>Topaz Rod"
```

### 项目名称

确定此项目的默认名称，不像“自定义名称”，这个名称不能被删除， 不会被斜体化，并且不会在某些标签，例如横幅标记和项目帧中显示。

```yaml
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>Topaz Rod" # we use <!i> here because 1.20.4 and below
                                          # don't have item_name component
```

### 自定义名称

用于指定物品的自定义名称，就像你可以在一个魔鬼里。

```yaml
items:
  default:topaz_rod:
    data:
      custom-name: "<!i><#FF8C00>Topaz Rod"
```

### 青色

确定项目显示的描述。

```yaml
items:
  default:topaz_rod:
    data:
      lore: 
        - "What a shiny rod!"
```

### 不可破坏的

确定项目是不可破坏的

```yaml
items:
  default:topaz_rod:
    data:
      unbreakable: true
```

### 附魔效果

确定项目的附魔项

```yaml
items:
  default:topaz_rod:
    data:
      enchantment:
        minecraft:sharpness: 1
        custom:enchant: 3
```

### 染色颜色

确定项目的颜色

```yaml
items:
  default:sofa:
    data:
      dyed-color: 255,255,255
```

### 自定义模型数据

```yaml
items:
  default:sofa:
    data:
      custom-model-data: 100
```

### 隐藏工具提示

隐藏此项目上指定的 **组件** 提供的任何工具提示。 这适用于所有版本，因为插件处理交叉版本兼容性。 前称`HideFlags`

```yaml
items:
  default:sofa:
    data:
      hide-tooltip:
        - dyed_color
        - enchantments
        - attribute_modifiers
```

### 属性修改器

应用于项目 [属性修改者] (https://minecraft.wiki/w/Attribute_modifiers)

```yaml
items:
  default:sofa:
    data:
      attribute-modifiers:
        - type: attack_speed
          amount: 1.0
          operation: add_value # add_value, add_multiplied_base, add_multiplied_total
          id: namespace:custom_attribute # Optional
          slot: any # any, hand, armor, mainhand, offhand, head, chest, legs, feet or body
          display: # 1.21.5
            type: override
            value: <yellow>Attack Speed +1
```

{% hint style="success" %}
您可以安全地在旧版本上使用最新的属性名称，因为插件将帮助您转换它们。
最后属性名称可以在 [https://minecraft.wiki/w/Attribute](https://minecraft.wiki/w/Attribute)
{% endhint %}

### 食物(1.20.5+)

```yaml
项目：
  默认：magic_aple：
    材料：Appe
    数据：
      食物： 
        营养：5
        饱和度：3.5
        通风：false
```

### jukebox 可播放(1.21+)

```yaml
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```

### 项目型号(1.21.2+)

```yaml
items:
  default:music_stick:
    data:
      item-model: default:music_stick
```

### tooltip-style (1.21.2+)

确定项目的工具提示样式

```yaml
items:
  default:topaz_rod:
    data:
      tooltip-style: minecraft:topaz #namespace:tooltip_style_id
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FG5cqs5c033VOfKiw2TJu%2Fimage.png?alt=media&#x26;token=4c517089-ab55-4fc8-adfe-c26bb7176e91" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
要创建工具提示风格，您必须将纹理放置在下面的目录中。

[https://minecraft.wiki/w/Data\_component\_format/tooltip\_style](https://minecraft.wiki/w/Data_component_format/tooltip_style)
{% endhint %}

### 修饰

对 [tool](https://minecraft.wiki/w/Tool) 或 [armor](https://minecraft.wiki/w/Armor) 应用装饰性修改

```yaml
trim:
  pattern: eye # https://minecraft.wiki/w/Smithing#Trimming
  material: iron # https://minecraft.wiki/w/Smithing#Material
```

### 可装备(1.21.2+)

如果存在，这个物品可以在指定的位置上装备起来。

```yaml
设备：
  # 将项目放在
  栏位上的槽位：head # HEAD / CHEST/ LEGS / FEEET / BODY / MAIN_HAND / OFF_HAND / SADDLEE
  
  # 可选参数
  # 指的目录是资产/<namespace>/equipment/<id>son
  asset-id: minecraft:topaz
  # 装备时使用的叠加层纹理的资源位置。 此处指的目录是assets/<namespace>/textures/<id>
  相机叠加层：namespace:id
  # 项目是否可以通过使用配电器来分配。
  可撒布: true
  # 当穿戴者实体损坏时此物品是否受损。
  有害无益：true
  # 该物品是否可以通过右击装备到相关的栏位。
  可交换：true
  # >= 1.21。
  # 这个项目是否可以通过在它上按下使用来装备到目标生物上(只要这个项目能够在目标上装备)
  设备之间：true
```

## 可自定义的数据

可自定义的数据不是由插件维护的，其格式可以随着Minecraft的更新而改变，尤其是在组件最近频繁更改的情况下。 如果您想要避免因为版本更新而进行大规模的配置大修，您可以考虑使用模板来建立标准化的配置文件格式。 发布新版本后，您可以简单地更新模板以适应任何更改。 如果您不熟悉如何使用模板，请务必阅读 [templates-must-read](../templates-must-read "提及")所提供的指南。 这个方法可以帮助简化更新过程，减少您的配置与最新游戏版本兼容所需的努力。

### NBT (1.20-1.20.4)

{% hint style="danger" %}
由于NBT (命名二进制标签)已过时，将不会在此详细讨论。&#x20;

[https://minecraft.wiki/w/Item\_format/Before\_1.20.5](https://minecraft.wiki/w/Item_format/Before_1.20.5)
{% endhint %}

```yaml
项目:
  默认值:topaz_rod:
    数据:
      nbt:
        CustomModelData: 1000
```

### 组件(1.20.5+)

自定义组件的格式严格遵循[Minecraft Wiki](https://minecraft.wiki/w/Data_component_format) 准则。 下面我将引导你们通过几个示例来帮助你们熟悉如何配置自定义组件。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/NrlWy1Cxy4vn2GK1ODdL/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
从图像中我们可以看到`max_damage` 接受一个 `I` (代表整数类型参数)。 因此，在我们的组合中，我们只需直接使用一个数值。

```yaml
项目：
  guide:test:
    data:
      component:
        minecraft:max_damage: 128
```

{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/7cqvxKcjpE2LTlsbTj9K/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
从图像中，我们可以看到`food` 需要三个参数：`int`类型`的营养`， `saturation`类型`float`和`boolean`类型`can_always_eat`

```yaml
项目：
  guide:test:
    data:
      component:
        minecraft:food:
          nutrition: 4
          satur: 2.0
          can_always_eat: falsal
```

{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/B6jF06WTXXXnonNs0kqo/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
现在，让我们尝试使用复合标签。 "{}" 表示您需要在您的 YAML 配置中打开一个新的部分。

```yaml
项目：
  指南:test:
    数据:
      组件:
        minecraft:enchants:
          级别:
            minecraft:sharpness: 1
          show_in_tooltip: false
```

然而，在仔细检查wiki后，您会注意到该方法在1.21.5版本中已过时。 当发布1.21.5时，您需要更新您的配置文件如下：

```yaml
项目：
  指南：测试：
    数据：
      组件：
        minecraft:enchants:
          minecraft:sharpness: 1
```

{% endhint %}

{% hint style="success" %}
您也可以以json/snbt 格式配置组件

```yaml
minecraft:custom_data: "(json) {\"test\":1}"
minecraft:food: "(snbt) {nutrition:5,saturation:2.5}"
```

{% endhint %}

### 删除组件 (1.20.5+)

从项目中删除组件

```yaml
items:
  test:item:
    data:
      remove-components:
        - minecraft:equippable
```
