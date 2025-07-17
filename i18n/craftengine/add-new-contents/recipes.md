---
description: This page mainly explains how to add new recipes to your server.
---

# 📖 Recipes

## Tags

In CraftEngine, the plugin allows you to use tags, and you can also create custom tags. To use a tag, simply follow this format: `#namespace:tag` .

In the following example, I have added two vanilla tags to `palm_planks`, allowing them to participate in all recipes within data packs that contain these two tags.

```yaml
items:
  default:palm_planks:
    material: paper
    custom-model-data: 1004
    settings:
      fuel-time: 300
      tags:
        - "minecraft:planks"
        - "minecraft:wooden_tool_materials"
    data:
      item-name: "<!i>Palm Planks"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/palm_planks"
      generation:
        parent: "minecraft:block/custom/palm_planks"
    behavior:
      type: block_item
      block: default:palm_planks
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/UohuvWjBBMBvvYIt8rG0/image.png" alt=""><figcaption><p>#minecraft:planks</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/f6mY7xsQNvHMDOn3vf1C/image.png" alt=""><figcaption><p>#minecraft:wooden_tool_materials</p></figcaption></figure>

## Group / Category

```yaml
recipes:
  default:palm_planks:
    type: shapeless
    category: building
    group: planks
    ingredients:
      A: "#default:palm_logs"
    result:
      id: default:palm_planks
      count: 4
```

The `group` determines which group this recipe belongs to after it is unlocked on the client side. The `group` can be any name you choose freely. However, please avoid using illegal characters.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SoRMQK6BhH7By5iaVOcF/image.png" alt=""><figcaption></figcaption></figure>

The `category` determines which tab this recipe is located in within the recipe book. The `category` type is limited.&#x20;

* For cooking-type recipes, the options are `food`, `blocks`, and `misc`.
* For crafting-type recipes, the options are `building`, `redstone`, `equipment`, and `misc`.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/MvzwXvGqBXFtC5RXTIXg/image.png" alt=""><figcaption></figcaption></figure>

## Shaped Crafting Recipe

```yaml
recipes:
  default:topaz_shovel:
    type: shaped
    pattern:
      - "A"
      - "B"
      - "B"
    ingredients:
      A: "default:topaz"
      B: "minecraft:stick"
    result:
      id: default:topaz_shovel
      count: 1
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/Gr062ZfKJry53tqR4lLB/image.png" alt=""><figcaption></figcaption></figure>

```yaml
recipes:
  default:chinese_lantern:
    type: shaped
    pattern:
      - "ABA"
      - "BCB"
      - "ABA"
    ingredients:
      A: "#minecraft:planks"
      B: "minecraft:stick"
      C: "minecraft:torch"
    result:
      id: default:chinese_lantern
      count: 1
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/uOlikOvTLLzJZZxki5Cl/image.png" alt=""><figcaption></figcaption></figure>

## Shapeless Crafting Recipe

```yaml
recipes:
  default:palm_planks:
    type: shapeless
    category: building
    group: planks
    ingredients:
      - "#default:palm_logs"
      # list is also supported
      - - test:ingredient1
        - test:ingredient2
    result:
      id: default:palm_planks
      count: 4
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/QajicG9iHchp728pMRmm/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/yfUiEjTjVRjO7AG5dQID/image.png" alt=""><figcaption></figcaption></figure>

## Cooking Recipe

Cooking Recipe includes `smelting`, `blasting`, `smoking`, and `campfire_cooking`. Regardless of the type, the configuration format remains the same.

```yaml
recipes:
  default:topaz_from_smelting_topaz_ore:
    type: smelting
    experience: 1.0
    category: misc
    group: topaz
    time: 200
    ingredient: "default:topaz_ore"
    result:
      id: default:topaz
      count: 1
  default:topaz_from_smelting_deepslate_topaz_ore:
    type: smelting
    experience: 1.0
    category: misc
    group: topaz
    time: 200
    ingredient: "default:deepslate_topaz_ore"
    result:
      id: default:topaz
      count: 1
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SJHB7w9gPm0UDldpjwwM/image.png" alt=""><figcaption></figcaption></figure>

## Stone Cutting Recipe

Stone Cutting Recipe is a somewhat unique recipe type. I do not recommend using custom items as ingredients, as this is highly likely to cause significant client-side visual issues.

```yaml
recipes:
  default:stonecutting_example:
    type: stonecutting
    group: topaz
    ingredient: "minecraft:stone"
    result:
      id: default:topaz
      count: 1
```

## Smithing Transform Recipe

```yaml
default:topaz_bow:
  type: smithing_transform
  # slot 1 (Optional)
  template-type: default:topaz
  # slot 2 (Required)
  base: minecraft:bow
  # slot 3 (Optional)
  addition: default:topaz
  # merge two items' components like what vanilla does
  merge-components: true # default: true
  # see the guide below
  post-processors: []
  result:
    id: default:topaz_bow
    count: 1
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FEvTD2AqtbFndtXO4icWX%2Fimage.png?alt=media&#x26;token=1f4a412f-0ccb-465d-adde-e257c2a7a73e" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
If you don't like the vanilla merging method, you can use a custom post-processor.

```yaml
post-processors:
  # Keep the specified components (1.20.5+)
  - type: keep_components
    components:
      - minecraft:enchantments
  # Keep the specified nbt tags (1.20-1.20.4)
  - type: keep_tags
    tags:
      - display.Name
      - CustomModelData
```
{% endhint %}

## Smithing Trim Recipe

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FuerIJfRiyn5n4k8m56fO%2Fimage.png?alt=media&#x26;token=4278291d-32bf-4217-aec0-33c4b593d052" alt=""><figcaption></figcaption></figure>

```yaml
default:bolt_tool_trims:
  type: smithing_trim
  template-type: "minecraft:bolt_armor_trim_smithing_template"
  base: "#minecraft:trimmable_tool"
  addition: "#minecraft:trim_materials"
  pattern: minecraft:bolt # required on 1.21.5+
```

## Brewing Recipe (1.20.2+)

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FwkjXILcWYQN2TaPnmLfM%2Fimage.png?alt=media&#x26;token=9b46b27f-8c92-4700-be8f-0011cea47102" alt=""><figcaption></figcaption></figure>

```yaml
tea_art:tea:
  type: brewing
  ingredient: tea_art:tea_leaf
  container: tea_art:cup
  result:
    id: tea_art:cup_of_tea
    count: 1
```
