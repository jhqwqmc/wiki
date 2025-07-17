---
description: https://minecraft.wiki/w/Items_model_definition#model
---

# :三角形规则：模型

该模型由两部分组成：路径和温度。 提示是可选的。 您可以在下面的链接中查看所有可用的色调类型。

{% content-ref url="model/tint" %}
[tint](mel/tint)
{% endcontent-ref %}

{% hint style="success" %}
在这个配置中，我们为自定义的假期创建一个模型。 然而，原版游戏中的默认留言没有颜色，所以我们需要配置一个色调来对它们进行颜色。
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/rlM7FKXsEbSji4SFQsn2/image.png" alt=""><figcaption></figcaption></figure>

```yaml
默认:palm_leaves:
  model:
    type: "minecraft:model"
    path: "minecraft:item/custom/palm_leaves"
    generation:
      parent: "minecraft:block/custom/palm_leaves"
    tints:
      - type: "minecraft:constant"
        value: -12012264
```
