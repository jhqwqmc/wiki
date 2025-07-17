# 🪑 Furniture Item

A furniture item is an item that is bound to a piece of furniture. You can configure its corresponding furniture ID here, or even the entire furniture configuration (but please note that doing so will result in the time taken to load the furniture being recorded under the item loading process). When you bind this behavior to an item, you can place it by right-clicking.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SYOQXH6ZY0VcGYGZLdgN/image.png" alt=""><figcaption></figcaption></figure>

```yaml
items:
  default:bench:
    behavior:
      type: furniture_item
      furniture: default:bench
```

This is the simplest way to configure a furniture-item, but it assumes that you have already configured a piece of furniture. If you are unsure how to configure a piece of furniture, please refer to [furniture](../../entities/furniture "mention").

{% hint style="success" %}
If you find it too cumbersome to configure them separately, you can choose to configure them together. Below is an example. The format under `furniture` follows the standard furniture configuration format.

```yaml
items:
  default:bench:
    material: paper
    custom-model-data: 2000
    data:
      display-name: "<!i>Bench"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/bench"
    behavior:
      type: furniture_item
      furniture:
        settings:
          item: default:bench
          sounds:
            break: minecraft:block.bamboo_wood.break
            place: minecraft:block.bamboo_wood.place
        placement:
          ground:
            rules:
              rotation: EIGHT
              alignment: CENTER
            elements:
              - item: default:bench
                display-transform: NONE
                billboard: FIXED
                position: 0.5,0,0
                translation: 0,0.5,0
            hitboxes:
              - position: 0,0,0
                width: 1
                height: 1
                interactive: true
                seats:
                  - 0,0,-0.1 0
              - position: 1,0,0
                width: 1
                height: 1
                interactive: true
                seats:
                  - 1,0,-0.1 0
        loot:
          template: loot_table:normal
          arguments:
            item: default:bench
```
{% endhint %}
