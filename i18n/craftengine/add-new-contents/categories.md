---
description: This page mainly explains how to add new categories to your server.
---

# 📂 Categories

The `category` is used to manage the arrangement order and classification rules of items when using the item browser.

A basic configuration is as follows. Once you complete the setup, it will appear in your /ce menu.

```yaml
categories:
  default:palm_tree:
    name: "<!i><green><i18n:category.palm_tree></green>"
    lore: []
    hidden: false
    priority: 1
    icon: default:palm_log
    list:
      - default:palm_sapling
      - default:palm_leaves
      - default:palm_log
      - default:stripped_palm_log
      - default:palm_wood
      - default:stripped_palm_wood
      - default:palm_planks
```

### Option Explanation

* The `name` and `lore` determine the title and description of the category icon.
* The `icon` represents the visual appearance of the item for this category, and you are required to configure the settings for this item within the plugin.
* The `priority` determines the display order; the smaller the 'priority' value, the higher the precedence it has for presentation in the GUI.
* The `hidden` attribute determines whether this category is displayed in the main menu. There may be instances where you wish to nest a category within another; in such cases, you would set this attribute to `true`. Relevant examples will be provided later.
* In the `list`, you need to fill in items or categories (categories must be prefixed with a '#', for example, `#default:palm_tree` ).

### Sub Categories

At times, you may require a category configuration with the following structure, or even with deeper nesting. In such cases, you will need to flexibly utilize `hidden` and the `#` prefix.

```
category_main
  ├ category_1
  ├ category_2
  └ category_3
     ├ item_1
     ├ item_2
     └ item_3
```

```yaml
categories:
  default:default:
    priority: 1
    name: "<!i><white><i18n:category.default.name></white>"
    lore:
      - "<!i><gray><i18n:category.default.lore>"
    icon: default:topaz
    list:
      - "#default:palm_tree"
      - "#default:topaz"
      - "#default:furniture"
      - "#default:misc"
  default:palm_tree:
    name: "<!i><green><i18n:category.palm_tree></green>"
    hidden: true
    icon: default:palm_log
    list:
      - default:palm_sapling
      - default:palm_leaves
      - default:palm_log
      - default:stripped_palm_log
      - default:palm_wood
      - default:stripped_palm_wood
      - default:palm_planks
  default:topaz:
    name: "<!i><#FF8C00><i18n:category.topaz></#FF8C00>"
    hidden: true
    icon: default:topaz
    list:
      - default:topaz
      - default:topaz_ore
      - default:deepslate_topaz_ore
      - default:topaz_axe
      - default:topaz_pickaxe
      - default:topaz_hoe
      - default:topaz_shovel
      - default:topaz_sword
      - default:topaz_bow
      - default:topaz_crossbow
      - default:topaz_rod
  default:furniture:
    name: "<!i><#FFD700><i18n:category.furniture></#FFD700>"
    hidden: true
    icon: default:table_lamp
    list:
      - default:bench
      - default:table_lamp
      - default:wooden_chair
  default:misc:
    name: "<!i><gray><i18n:category.misc></gray>"
    hidden: true
    icon: default:chinese_lantern
    list:
      - default:chinese_lantern
      - default:fairy_flower
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/rcDhHCdZZA6vSyoL1mnX/image.png" alt=""><figcaption><p>main menu</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/6je6hSGuuxseDsIEwsTS/image.png" alt=""><figcaption><p>sub menu</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/hZqKvQdnJcinwlIa9tae/image.png" alt=""><figcaption><p>furniture category</p></figcaption></figure>

### Tip

{% hint style="danger" %}
You can also directly configure the category to which an item belongs within the item itself. However, please note that in such cases, we cannot guarantee the order in which it will be displayed within the category.
{% endhint %}

```yaml
items:
  default:topaz_sword:
    # category: default:topaz 
    category:
      - default:topaz # use a list of categories
    material: golden_sword
    custom-model-data: 1000
    data:
      display-name: "<!i><#FF8C00><i18n:item.topaz_sword>"
      tooltip-style: minecraft:topaz
      components:
        minecraft:max_damage: 64
    model:
      type: minecraft:model
      path: minecraft:item/custom/topaz_sword
      generation:
        parent: "minecraft:item/handheld"
        textures:
          "layer0": "minecraft:item/custom/topaz_sword"
```
