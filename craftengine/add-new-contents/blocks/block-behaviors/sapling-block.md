# 🌴 Sapling Block

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/2qxcorsLzCM5Vs1MyzC8/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/THfxu33nMbDazLNxRNnE/image.png" alt=""><figcaption></figcaption></figure>

Once a `configured feature` is specified, the  [sapling-block](sapling-block "mention")  can grow into the designated tree configuration during a random tick event.

```yaml
blocks:
  default:palm_sapling:
    behavior:
      type: sapling_block
      # This requires you to register a custom tree configuration with data pack
      # To prevent errors, we use tree feature from vanilla here
      feature: minecraft:fancy_oak
      bone-meal-success-chance: 0.45
      grow-speed: 0.7  # (0-1)
```

{% hint style="warning" %}
Please note that all sapling blocks must have a property named `stage` of type `int`. If you are unsure how to set up properties, please refer to [block-states](../block-states "mention"). The more `stage` values a sapling has, the longer its required growth time. In the vanilla game, saplings only have two stages: 0 and 1.
{% endhint %}
