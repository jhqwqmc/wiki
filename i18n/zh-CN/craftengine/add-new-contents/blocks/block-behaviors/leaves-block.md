# 🍁 叶块

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/cOCjIhMj2mDHrpev05Zl/image.png" alt=""><figcaption></figcaption></figure>

[leaves-block](leaves-block “提到”拥有三个属性：“距离”(距离树干距离)， `persistent` (块是否可以永久存在) 和 `水流量` (块是否包含水\[optional]) “距离”属性使自然生成的假期随着时间的推移而衰减，而“持久”属性确保玩家安置的假期永远保持不变。

```yaml
块:
  默认 palm_leaves:
    行为:
      类型: leaves_block
```

{% hint style="warning" %}
请注意，所有的叶块都必须具有`persistent` (boolean) 和 `distance` (int) 属性，其中`distance` 至少是1。 如果您不确定如何配置这些属性，请参阅 [block-states](../block-states "提及")。
{% endhint %}

{% hint style="success" %}
您可以根据需要增加或减少 "Distance" 值。 对于特别大的树木，为了防止叶衰变，你可以将 "距离" 设置为 10 或更高。 在原版游戏中，叶的最大“距离”为7。
{% endhint %}
