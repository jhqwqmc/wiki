---
description: https://minecraft.wiki/w/Items_model_definition#model
---

# 📐 Model

The model consists of two parts: path and tints. Tints are optional. You can view all available tint types in the link below.

{% content-ref url="model/tint" %}
[tint](model/tint)
{% endcontent-ref %}

{% hint style="success" %}
In this configuration, we create a model for custom leaves. However, the default leaves in the vanilla game do not have color, so we need to configure a tint to color them.
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/rlM7FKXsEbSji4SFQsn2/image.png" alt=""><figcaption></figcaption></figure>

```yaml
default:palm_leaves:
  model:
    type: "minecraft:model"
    path: "minecraft:item/custom/palm_leaves"
    generation:
      parent: "minecraft:block/custom/palm_leaves"
    tints:
      - type: "minecraft:constant"
        value: -12012264
```
