---
description: >-
  Set vanilla NBT/Components for items to utilize certain native Minecraft
  functionalities.
---

# 🔢 Item Data

## What is Item Data?

Item Data refers to the NBT (Named Binary Tag) of an item in older versions, or the item Components in version 1.20.5 and above. Through this data, we can customize various aspects of an item such as its name, description, attributes, and other functionalities.

## External Data

If you want a CraftEngine item to retain the data of an external plugin's item, follow this configuration:

```yaml
items:
  default:example_item:
    data:
      external:
        plugin: neigeitems
        id: example_item
```

{% content-ref url="../../compatibility/external-item-sources" %}
[external-item-sources](../../compatibility/external-item-sources)
{% endcontent-ref %}

## Hard-coded Data

Hardcoded data, in this context, means that the configuration formats are provided and maintained by plugin, which ensures compatibility across different versions. These formats are defined by the plugin, so they may differ from the standard NBT (Named Binary Tag) or Components formats used by the game itself. The advantage of this approach is that the plugin handles all the maintenance, including version compatibility, so users do not need to worry about changes or updates between game versions.

```yaml
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>Topaz Rod"
```

### item-name

Determines the default name of this item, unlike the `custom-name`, this name can't be erased using an anvil, won't be italicized, and does not show in some labels, such as banner markers and item frames.

```yaml
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>Topaz Rod" # we use <!i> here because 1.20.4 and below
                                          # don't have item_name component
```

### custom-name

Used to specify the item's custom name, like you can in an anvil.

```yaml
items:
  default:topaz_rod:
    data:
      custom-name: "<!i><#FF8C00>Topaz Rod"
```

### lore

Determines the displayed description of the item.

```yaml
items:
  default:topaz_rod:
    data:
      lore: 
        - "What a shiny rod!"
```

### unbreakable

Determines whether the item is unbreakable

```yaml
items:
  default:topaz_rod:
    data:
      unbreakable: true
```

### enchantment

Determines the enchantments of the item

```yaml
items:
  default:topaz_rod:
    data:
      enchantment:
        minecraft:sharpness: 1
        custom:enchant: 3
```

### dyed-color

Determines the color of the item

```yaml
items:
  default:sofa:
    data:
      dyed-color: 255,255,255
```

### custom-model-data

```yaml
items:
  default:sofa:
    data:
      custom-model-data: 100
```

### hide-tooltip

Hides any tooltips provided by the specified **components** on this item. This works for all versions as plugin handles the cross version compatibility. Formerly known as `HideFlags`

```yaml
items:
  default:sofa:
    data:
      hide-tooltip:
        - dyed_color
        - enchantments
        - attribute_modifiers
```

### attribute-modifiers

Applies [attribute modifiers](https://minecraft.wiki/w/Attribute_modifiers) onto items.

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
You can safely use the latest attribute names on legacy versions as plugin will help you convert them.\
Lastest attribute names can be found on [https://minecraft.wiki/w/Attribute](https://minecraft.wiki/w/Attribute)
{% endhint %}

### food (1.20.5+)

```yaml
items:
  default:magic_apple:
    material: apple
    data:
      food: 
        nutrition: 5
        saturation: 3.5
        can-always-eat: false
```

### jukebox-playable (1.21+)

```yaml
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```

### item-model (1.21.2+)

```yaml
items:
  default:music_stick:
    data:
      item-model: default:music_stick
```

### tooltip-style (1.21.2+)

Determines the tooltip style of the item

```yaml
items:
  default:topaz_rod:
    data:
      tooltip-style: minecraft:topaz #namespace:tooltip_style_id
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FG5cqs5c033VOfKiw2TJu%2Fimage.png?alt=media&#x26;token=4c517089-ab55-4fc8-adfe-c26bb7176e91" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
To create a tooltip style, you must place the texture in the directory as follows.

[https://minecraft.wiki/w/Data\_component\_format/tooltip\_style](https://minecraft.wiki/w/Data_component_format/tooltip_style)
{% endhint %}

### trim

apply a decorative alteration to a [tool](https://minecraft.wiki/w/Tool) or [armor](https://minecraft.wiki/w/Armor)

```yaml
trim:
  pattern: eye # https://minecraft.wiki/w/Smithing#Trimming
  material: iron # https://minecraft.wiki/w/Smithing#Material
```

### equippable (1.21.2+)

If present, this item can be equipped in the specified slot.

```yaml
equippable:
  # The slot to put the item on
  slot: head # HEAD / CHEST / LEGS / FEET / BODY / MAIN_HAND / OFF_HAND / SADDLE
  
  # Optional Arguments
  # The directory this refers to is assets/<namespace>/equipment/<id>.json
  asset-id: minecraft:topaz
  # The resource location of the overlay texture to use when equipped. The directory this refers to is assets/<namespace>/textures/<id>.
  camera-overlay: namespace:id
  # Whether the item can be dispensed by using a dispenser.
  dispensable: true
  # Whether this item is damaged when the wearing entity is damaged.
  damage-on-hurt: true
  # Whether the item can be equipped into the relevant slot by right-clicking.
  swappable: true
  # >= 1.21.5
  # Whether this item can be equipped onto a target mob by pressing use on it (as long as this item can be equipped on the target at all)
  equip-on-interact: true
```

## Customizable Data

Customizable Data is not maintained by plugins, and its format can change with updates to Minecraft, particularly with the frequent recent changes to Components. If you want to avoid extensive configuration overhauls due to version updates, you might consider using templates to establish a standardized configuration file format. When a new version is released, you can simply update the template to accommodate any changes. If you are unfamiliar with how to use templates, please make sure to read the guide provided at [templates-must-read](../templates-must-read "mention"). This approach can help streamline the update process and reduce the effort required to keep your configurations compatible with the latest game versions.

### NBT (1.20-1.20.4)

{% hint style="danger" %}
Since NBT (Named Binary Tag) has become outdated, it will not be discussed in detail here.&#x20;

[https://minecraft.wiki/w/Item\_format/Before\_1.20.5](https://minecraft.wiki/w/Item_format/Before_1.20.5)
{% endhint %}

```yaml
items:
  default:topaz_rod:
    data:
      nbt:
        CustomModelData: 1000
```

### Components (1.20.5+)

The format for custom Components strictly adheres to the [Minecraft Wiki](https://minecraft.wiki/w/Data_component_format) guidelines. Below, I will guide you through a few examples to help you become familiar with how to configure custom Components.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/NrlWy1Cxy4vn2GK1ODdL/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
From the image, we can see that `max_damage` accepts an `I` (which stands for an integer type parameter). Therefore, in our configuration, we simply need to use a numerical value directly.

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:max_damage: 128
```
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/7cqvxKcjpE2LTlsbTj9K/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
From the image, we can see that `food` requires three parameters: `nutrition` of type `int`, `saturation` of type `float`, and `can_always_eat` of type `boolean`.

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:food:
          nutrition: 4
          saturation: 2.0
          can_always_eat: false
```
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/B6jF06WTXXXnonNs0kqo/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Now, let's try working with a compound tag. The `{}` signifies that you need to open a new section in your YAML configuration.

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:enchantments:
          levels:
            minecraft:sharpness: 1
          show_in_tooltip: false
```

However, upon closer inspection of the wiki, you'll notice that this method becomes obsolete in version 1.21.5. When 1.21.5 is released, you will need to update your configuration file as follows:

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:enchantments:
          minecraft:sharpness: 1
```
{% endhint %}

{% hint style="success" %}
You can also configure the components in json/snbt format

```yaml
minecraft:custom_data: "(json) {\"test\":1}"
minecraft:food: "(snbt) {nutrition:5,saturation:2.5}"
```
{% endhint %}

### Remove Components (1.20.5+)

Removes the component from the item

```yaml
items:
  test:item:
    data:
      remove-components:
        - minecraft:equippable
```
