# 🟨 Falling Block

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/f68xQ1ll4vIsWoN6KTOc/image.png" alt=""><figcaption></figcaption></figure>

[falling-block](falling-block "mention") (such as sand and anvils) possess the property of transforming into temporary falling entities when triggered. The following example demonstrates how to configure a falling block:

```yaml
blocks:
  default:falling_block_example:
    behavior:
      type: falling_block
      # Optional
      hurt-amount: -1
      # Optional
      max-hurt: -1
```

{% hint style="info" %}
The configurations `hurt-amount` and `max-hurt` are optional, but they must be configured together. Their effect is to determine the damage inflicted on entities when struck by a falling block.
{% endhint %}
