# 🍁 Leaves Block

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/cOCjIhMj2mDHrpev05Zl/image.png" alt=""><figcaption></figcaption></figure>

[leaves-block](leaves-block "mention") possess three properties: `distance` (the distance from the tree trunk), `persistent` (whether the block can exist permanently), and `waterlogged` (whether the block contains water \[optional]). The `distance` property enables naturally generated leaves to decay over time, while the `persistent` property ensures that player-placed leaves remain permanently.

```yaml
blocks:
  default:palm_leaves:
    behavior:
      type: leaves_block
```

{% hint style="warning" %}
Please note that all leaf blocks must have the `persistent` (boolean) and `distance` (int) properties, with `distance` being at least 1. If you are unsure how to configure these properties, please refer to [block-states](../block-states "mention").
{% endhint %}

{% hint style="success" %}
You can increase or decrease the `distance` value as needed. For particularly large trees, to prevent leaf decay, you can set the `distance` to 10 or higher. In the vanilla game, the maximum `distance` for leaves is 7.
{% endhint %}
