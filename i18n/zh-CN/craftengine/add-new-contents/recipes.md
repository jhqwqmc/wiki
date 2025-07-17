---
description: 此页主要解释了如何添加新配方到您的服务器。
---

# 📖 配方

## 标签

在 CraftEngine 中，插件允许您使用标签，您也可以创建自定义标签。 要使用标签，只需遵循这种格式：`#namespace:tag` 。

在下面的例子中，我在 `palm_planks` 中添加了两个原始标签， 允许他们参与包含这两个标签的数据包内的所有配方。

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

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/UohuvWjBBMBvvYIt8rG0/image.png" alt=""><figcaption><p>#minecraft:ploks</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/f6mY7xsQNvHMDOn3vf1C/image.png" alt=""><figcaption><p>#minecraft:wooden_tool_materials</p></figcaption></figure>

## 组 / 类别

```yaml
配方：
  default:palm_plaks:
    type: shapeless
    category: building
    group: ploks
    components:
      A: "#default:palm_logs"
    结果：
      id: default:palm_planks
      count: 4
```

"群组" 决定该配方在客户端解锁后属于哪个群组。 "群组"可以是您自由选择的任何名称。 但是，请避免使用非法字符。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SoRMQK6BhH7By5iaVOcF/image.png" alt=""><figcaption></figcaption></figure>

`category`决定该配方位于配方簿中的标签。 `category`类型是有限的。&#x20;

- 对于cooking类型的配方，选项是 `food`、`blocks`和`misc`。
- 就制造型配方而言，备选办法是`building`、`redstone`、`equipment`和`misc`'。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/MvzwXvGqBXFtC5RXTIXg/image.png" alt=""><figcaption></figcaption></figure>

## 绘制配方图

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

## 无缝制作配方

```yaml
配方：
  default:palm_plaks:
    type: shapeless
    category: building
    group: ploks
    components:
      - "#default:palm_logs"
      # 列表也支持
      - test:informent1
        - test:informent2
    结果：
      id: default:palm_plaks
      计数: 4
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/QajicG9iHchp728pMRmm/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/yfUiEjTjVRjO7AG5dQID/image.png" alt=""><figcaption></figcaption></figure>

## 烹饪配方

做饭配方包括“熔炼”、“爆破”、“烟雾”和“campfire_cooking”。 无论类型如何，配置格式都保持不变。

```yaml
配方：
  默认：topaz_from_smelting_topaz_ore：
    类型：熔炼
    experience: 1。
    类别: misc
    组: topaz
    时间: 200
    成分: "default:topaz_ore"
    结果:
      id: default:topaz
      计数: 1
  default:topaz_from_smelting_deepslate_topaz_ore:
    类型: 熔炼
    经验
    类别: misc
    group: topaz
    time: 200
    component: "default:deepslaste_topaz_ore"
    result:
      id: default:topaz
      count: 1
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SJHB7w9gPm0UDldpjwwM/image.png" alt=""><figcaption></figcaption></figure>

## 石制剪切配方

石制切割配方是一个有点独特的配方类型。 我不建议使用自定义项目作为成分，因为这很可能引起客户端视觉问题。

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

## 正在变形配方

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
如果您不喜欢原版合并方法，您可以使用自定义后处理器。

```yaml
post-processors:
  # 保留指定组件(1.20)。 +)
  - 类型：keep_component
    components:
      - minecraft:enchantes
  # 保留指定的忍受标签 (1)。 0-1.20.4)
  - 类型：keep_tags
    标签：
      - 显示。
      - 自定义建制数据
```

{% endhint %}

## 翻模修配方

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FuerIJfRiyn5n4k8m56fO%2Fimage.png?alt=media&#x26;token=4278291d-32bf-4217-aec0-33c4b593d052" alt=""><figcaption></figcaption></figure>

```yaml
默认:bolt_tool_trims:
  类型: smithing_trim
  模板类型: "minecraft:bolt_armor_trim_smithing_template"
  基础: "#minecraft:trimmable_tool"
  添加: "#minecraft:trim_materials"
  模式: 1.21.5+ 需要 minecraft:bolt #
```

## 酿造配方(1.20.2+)

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FwkjXILcWYQN2TaPnmLfM%2Fimage.png?alt=media&#x26;token=9b46b27f-8c92-4700-be8f-0011cea47102" alt=""><figcaption></figcaption></figure>

```yaml
tea_art:tea:
  type: brewing
  component: tea_art:tea_leaf
  container: tea_art:cup
  result:
    ident: tea_art:cup_of_tea
    计数: 1
```
