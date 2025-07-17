# 🥰 兼容

使用 CraftEngine的配方，您可以使用来自其他插件的项目 - 但您需要正确配置它们。 首先，在`config.yml`中将支持的插件添加到本节：

```yaml
# config.yml
recipe:
  组件源:
    - MythicMobs
```

{% hint style="warning" %}
支持的项目源可以在 [external-item-sources](../../compatibility/external-item-sources "提及")上找到。 您也可以通过API注册您自己的项目源。&#x20;
{% endhint %}

好吧，让我带你穿过一个水泥示例来展示你如何引用外部物品。

## 配方结果

```yaml
items: 
  mythicmobs:kingscrown:
    material: golden_helmet
    data:
      external:
        plugin: MythicMobs
        id: KingsCrown
```

```yaml
recipes:
  mythicmobs:kingscrown:
    type: shaped
    pattern:
      - AAA
      - A A
    ingredients:
      A: default:topaz
    result:
      id: mythicmobs:kingscrown
      count: 1
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FBLgPvnOQAxXCLfY8932P%2Fimage.png?alt=media&#x26;token=2d7f6454-97ec-4a12-965c-4f2e35e5ca6e" alt=""><figcaption></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F0sKcYBkBQmQs5cOC47Rw%2Fimage.png?alt=media&#x26;token=61619cea-643a-426a-be80-043c127add2b" alt=""><figcaption></figcaption></figure>

## 配方元素

```yaml
items:
  mythicmobs:kingscrown:
    material: golden_helmet
    data:
      external:
        plugin: MythicMobs
        id: KingsCrown
```

```yaml
配方：
  默认：基准：
    类型：形状
    模式：
      - A
      - A
    成分：
      A：mythicmobs:kingscrown
    结果：
      id：default:bench
      计数：1
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FTLYvvey387o2OZLK0p5M%2Fimage.png?alt=media&#x26;token=34508394-b98c-4775-8a61-2d5a94654083" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
用于任何用作成分的项目 您必须确保他们在 CraftEngine 中的命名空间是 **lowercase** 中的插件名称，ID也应该在 **lowercase** 中。 让我给你们举几个例子，以便你们可以看看这如何运作：

- 在MythicMobs -> `mythicmobs:mysword` 中命名为“MySword”的项目
- 在 CustomFishing -> `customfishing:star_fish` 中名为 'star\_fish' 的项目
- 在MMOitems -> `mmoitems:gem_magic_gem` 中名为 'MAGIC\_GEM 类型的项目
- 在 RANDOM 插件 -> `random_plugin:namespace_id`
  {% endhint %} 中有命名空间ID的项目
