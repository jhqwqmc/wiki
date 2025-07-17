# 🎍 垂直裁剪块

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FQThsCr8DWL9MnDStY5c4%2Fimage.png?alt=media&#x26;token=0540cc32-fcf8-4a26-9e67-a5d9d81f27d7" alt=""><figcaption></figcaption></figure>

[vertical-crop-block](vertical-crop-block "mention") is a type of block that grows upward/downward over time.&#x20;

{% hint style="danger" %}
你**必须** 配置此方块的 `age` 属性，因为它决定了它的生长速度。 如果您不确定如何设置属性，请参阅 [block-states](../block-states "提及")。 “年龄”越是为甘蔗值越多，它所需的成长时间就越长。
{% endhint %}

```yaml
块:
  默认:flame_cane:
    行为:
      - 类型: vertical_crow_block
        最大高度: 4
        增长速度: 0. 33
        方向：向下# 向上/向下
      - 类型：hanging_block
        可堆栈：true
        延迟：1
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F3vRZWSB3S8jeOEsAx8py%2Fimage.png?alt=media&#x26;token=bb58619f-606e-41fd-ab69-0763d2fa669d" alt=""><figcaption></figcaption></figure>
