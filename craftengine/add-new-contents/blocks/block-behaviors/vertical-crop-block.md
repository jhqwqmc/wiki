# 🎍 Vertical Crop Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FQThsCr8DWL9MnDStY5c4%2Fimage.png?alt=media&#x26;token=0540cc32-fcf8-4a26-9e67-a5d9d81f27d7" alt=""><figcaption></figcaption></figure>

[vertical-crop-block](vertical-crop-block "mention") is a type of block that grows upward/downward over time.&#x20;

{% hint style="danger" %}
You **must** configure the `age` property for this block, as it determines its growth speed. If you are unsure how to set up properties, please refer to [block-states](../block-states "mention"). The more `age` values a sugarcane has, the longer its required growth time.
{% endhint %}

```yaml
blocks:
  default:flame_cane:
    behaviors:
      - type: vertical_crop_block
        max-height: 4
        grow-speed: 0.333
        direction: down  # up/down
      - type: hanging_block
        stackable: true
        delay: 1
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F3vRZWSB3S8jeOEsAx8py%2Fimage.png?alt=media&#x26;token=bb58619f-606e-41fd-ab69-0763d2fa669d" alt=""><figcaption></figcaption></figure>
