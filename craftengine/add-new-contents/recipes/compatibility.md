# 🥰 Compatibility

With CraftEngine's recipes, you can use items from other plugins - but you'll need to configure them properly. First, add the supported plugins to this section in `config.yml`:

```yaml
# config.yml
recipe:
  ingredient-sources:
    - MythicMobs
```

{% hint style="warning" %}
Supported item sources can be found on [external-item-sources](../../compatibility/external-item-sources "mention"). You can also register your own item source through API.&#x20;
{% endhint %}

Alright, let me walk you through a concrete example to show how you can reference external stuff.

## Recipe Result

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

## Recipe Ingredient

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
  default:bench:
    type: shaped
    pattern:
      - A A
      - A A
    ingredients:
      A: mythicmobs:kingscrown
    result:
      id: default:bench
      count: 1
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FTLYvvey387o2OZLK0p5M%2Fimage.png?alt=media&#x26;token=34508394-b98c-4775-8a61-2d5a94654083" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
For any items used as ingredients, you have to make sure their namespace in CraftEngine is the plugin name in **lowercase**, and the ID should also be in **lowercase**. Let me give you a few examples so you can see how this works:

* Item named 'MySword' in MythicMobs  ->  `mythicmobs:mysword`
* Item named 'star\_fish' in CustomFishing -> `customfishing:star_fish`
* Item named 'MAGIC\_GEM' with 'GEM' type in MMOItems -> `mmoitems:gem_magic_gem`
* Item with namespaced id in a RANDOM plugin -> `random_plugin:namespace_id`
{% endhint %}
