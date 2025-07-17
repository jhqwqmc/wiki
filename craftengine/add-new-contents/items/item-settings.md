---
description: >-
  Unlike data, the contents within settings pertain to special mechanisms
  processed by the plugin.
---

# ⚙️ Item Settings

## fuel-time

Determines how many ticks can be burned

```yaml
fuel-time: 100
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ETo97tqrp6GsxMMc4zOX/image.png" alt=""><figcaption></figcaption></figure>

## tags

See [recipes](../recipes "mention")

```yaml
tags:
  - "default:palm_logs"
  - "minecraft:logs"
  - "minecraft:logs_that_burn"
```

## equipment

Apply the equipment to the item. See [item-equipment](item-equipment "mention")

```yaml
equipment:
  #
  # Required Argument
  #
  asset-id: default:topaz
  
  # 
  # Optional Argument. Defaults to the global client-bound-model option in config.yml
  #
  client-bound-model: true
  
  #
  # Optional Arguments on 1.21.2 and above
  # Option 'slot' is required for these options to work
  #
  slot: head # head / chest / legs / feet / body (animal armor) / saddle 
  # The resource location of the overlay texture to use when equipped. The directory this refers to is assets/<namespace>/textures/<id>.
  camera-overlay: "namespace:id"
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

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FDrJjArxUMGqZdTcFNlbB%2Fimage.png?alt=media&#x26;token=b507bcfd-b23f-42d5-a610-51e45544b465" alt=""><figcaption></figcaption></figure>

## repairable

Decides if the item can be repaired through crafting table/anvil (Default: true)

```yaml
repairable: true
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FsFmbIZ3gKhZRd0i2aJ8N%2Fimage.png?alt=media&#x26;token=105464c8-4910-4b0e-9e68-a3f968468e99" alt=""><figcaption></figcaption></figure>

## anvil-repair-item

Determines how much durability a given item provides when repairing

```yaml
anvil-repair-item:
  - target: "#topaz_tools"
    amount: 20  # restores fixed durability
  - target:
      - "minecraft:iron_pickaxe"
      - "minecraft:shears"
    percent: 0.25  # 0.25 = 25%, restores n% total durability
```

## renameable

Determines if the item can be renamed in anvil. (Default: true)

```yaml
renameable: false
```

## projectile

Creates a custom projectile entity based on the item. It supports `trident`, `arrow`, `snowball` and more.

```yaml
projectile:
  item: default:topaz_trident # the item to display
  translation: 0,0,0
  rotation: 1,1,1,1
  display-transform: NONE
  scale: 0.5
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FMXNMpGU2nEZuaIZZdXje%2Fimage.png?alt=media&#x26;token=a8d196fb-e093-4c29-a796-83ad28ca3cac" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
The way you model directly affects the `rotation` arguments in the configuration file.

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F6VmwwP0bhtIijZEsXG2e%2Fimage.png?alt=media\&token=df1e2bd8-d608-4c19-9cf5-dcd2cc534505)![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FL7y7eP6xIqwRXrLKlqcb%2Fimage.png?alt=media\&token=df7f1d90-dffd-4db4-b3e9-c86195564187)\
No matter which modeling method you use, the most important thing is to make the sharp part of the trident in the position shown in the picture above to ensure the best hitting point.
{% endhint %}

## dyeable

Decides if the item([leather armor](https://minecraft.wiki/w/Leather_armor) or [wolf armor](https://minecraft.wiki/w/Wolf_armor)) can be dyed in crafting tables. (Default: true)

```yaml
dyeable: true
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FKPAQnbm7LyeQtQ6UHHyp%2Fimage.png?alt=media&#x26;token=bbe9e687-6486-451f-8762-32849b4c0e34" alt=""><figcaption></figcaption></figure>

## food

```yaml
food:
  nutrition: 5  # 0~20, integer
  saturation: 3.5  # 0~10, float
```

{% hint style="warning" %}
Better to use `food` components on a 1.20.5+ server
{% endhint %}

## consume-replacement

Set the return item after consuming the item. For example, after the player drinks the water bottle, the empty bottle will be returned. (Default: null)

```yaml
consume-replacement: minecraft:apple
```

## craft-remaining-item

Choose whether items should return other items when the crafting recipe is finished. This option only works for custom items with a max stack size of 1

```yaml
craft-remaining-item: bucket
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FG5Gx2xMlH4SspQC1P66y%2Fimage.png?alt=media&#x26;token=5a6e6d26-8730-4f07-ae94-dabb0fc3b520" alt=""><figcaption></figcaption></figure>

## invulnerable

```yaml
invulnerable:
  - lava
  - fire_tick
  - block_explosion  # respawn anchor
  - entity_explosion  # creeper, tnt
  - lightning
  - contact  # cactus
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FHYC5C0eMeqoVtNWk2QbI%2Fimage.png?alt=media&#x26;token=15fdae30-932b-4ab3-9a00-a81102e5dccf" alt=""><figcaption></figcaption></figure>

## enchantable

This option lets you block certain items from being used on the enchantment table. Tip: setting it to `true` won’t magically make unenchantable items enchantable. (Default: true)

```yaml
enchantable: false
```

## compost-probability

This setting controls how likely it is for composting to succeed (Default: 0.5)

```yaml
compost-probability: 0.5
```

## respect-repairable-component

This controls if the items listed in `repairable` component can fix this item in anvil gui. (Default: false)

```yaml
respect-repairable-component: false
```
