# :palm_tree：锯切块

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/2qxcorsLzCM5Vs1MyzC8/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/THfxu33nMbDazLNxRNnE/image.png" alt=""><figcaption></figcaption></figure>

一旦指定了 "配置功能" ，  [sapling-block](sapling-block "提及") 可以在随机的牌照事件中成长为指定的树形配置。

```yaml
块:
  默认:palm_sapling:
    行为:
      类型: sapling_block
      # 这需要您注册一个自定义树配置，数据包为
      # 以防止错误, 我们在这里使用原版树木功能，
      功能：minecraft:fancy_oak
      bone-meal-success-opportunity: 0。 5
      增长速度：0.7# (0-1)
```

{% hint style="warning" %}
请注意，所有采树块都必须有名为 `int` 类型的 `stage` 属性。 如果您不确定如何设置属性，请参阅 [block-states](../block-states "提及")。 `stage`值越大，树苗的增长时间就越长。 在原版游戏中，锯齿仅有两个阶段：0和1。
{% endhint %}
