# 🌽 裁剪块

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FhmVLWF8LYSK3x2zJDRy2%2Fimage.png?alt=media&#x26;token=8dc7854c-a1f7-49d4-a713-6f6ef31a2069" alt=""><figcaption></figcaption></figure>

[crop-block](crop-block “提及”是一种随着时间增长的方块类型。 当收到随机的牌子时，它有机会进入下一生长阶段。 然而，如果工厂没有足够的光线，它将停止生长或作为物品掉落。。&#x20;

{% hint style="danger" %}
你**必须** 配置此方块的 `age` 属性，因为它决定了它的阶段。 如果您不确定如何设置属性，请参阅 [block-states](../block-states "提及")。
{% endhint %}

```yaml
blocks:
  默认值:ender_pearl_flow:
    行为:
      类型: crop_block
      增长速度: 0. 5 # 0~1, 在随机勾画上生长的几率
      光量要求：9 # 此裁剪的光量要求
      is-bone-meal-target: true # default true
      bone-meal-age-addus:
        type
        min: 1
        max: 3
```
