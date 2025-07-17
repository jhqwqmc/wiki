# 🌽 Crop Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FhmVLWF8LYSK3x2zJDRy2%2Fimage.png?alt=media&#x26;token=8dc7854c-a1f7-49d4-a713-6f6ef31a2069" alt=""><figcaption></figcaption></figure>

[crop-block](crop-block "mention") is a type of block that grows over time. When receiving random ticks, it has a chance to advance to the next growth stage. However, if the plant lacks sufficient light, it will either stop growing or drop as an item.&#x20;

{% hint style="danger" %}
You **must** configure the `age` property for this block, as it determines its stages. If you are unsure how to set up properties, please refer to [block-states](../block-states "mention").
{% endhint %}

```yaml
blocks:
  default:ender_pearl_flower:
    behavior:
      type: crop_block
      grow-speed: 0.25  # 0~1, the chance of growing on random tick
      light-requirement: 9  # light requirement for this crop
      is-bone-meal-target: true # default true
      bone-meal-age-bonus:
        type: uniform
        min: 1
        max: 3
```
