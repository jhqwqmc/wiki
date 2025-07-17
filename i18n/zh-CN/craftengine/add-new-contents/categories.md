---
description: 此页主要解释了如何将新类别添加到您的服务器。
---

# 📂 类别

在使用项目浏览器时，`category`用于管理项目的安排顺序和分类规则。

基本配置如下。 一旦您完成了设置，它将出现在您的 /ce 菜单中。

```yaml
类别:
  默认🌴
    名称: "<! ><green><i18n:category.palm_tree></green>"
    lore: []
    hidden: false
    priority: 1
    icon: default:palm_log
    list:
      - default:palm_saping
      - default:palm_log
      - default:palm_log
      - default:stripped_palm_log
      - default:palm_wood
      - default:striped_palm_palm_wood
      - default:palm_planks
```

### 选项解释

- `name`和`lore`决定类别图标的标题和描述。
- `icon`表示此类别的项目的视觉外观。 并且您需要在插件中配置此项目的设置。
- “优先级”决定显示顺序；“优先级”值越小，它在图形界面中显示的优先级就越高。
- "隐藏" 属性决定该类别是否显示在主菜单中。 可能有些情况下，您希望在另一个类别中排出一个类别；在这种情况下，您会将此属性设置为“true”。 稍后将提供相关的例子。
- 在 `list` 中，您需要填写项目或类别(类别必须以 '#' 作为前缀，例如`#default:palm_tree` )。

### 子类别

有时，您可能需要一个具有以下结构的类别配置，甚至需要更深的嵌套。 在这种情况下，您需要灵活地使用 "隐藏" 和 "#" 前缀。

```
category_main
  category_1
  category_2
  category_3
     category_1
     category_2
     category_3
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

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/rcDhHCdZZA6vSyoL1mnX/image.png" alt=""><figcaption><p>主菜单</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/6je6hSGuuxseDsIEwsTS/image.png" alt=""><figcaption><p>sub menu</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/hZqKvQdnJcinwlIa9tae/image.png" alt=""><figcaption><p>家具类别</p></figcaption></figure>

### Tip

{% hint style="danger" %}
您也可以直接配置项目本身所属的类别。 然而，请注意，在这种情况下，我们不能保证它在该类别中显示的顺序。
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
