# 🪟 陷阱门块

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FeMkYg3eaWHjUB4ZVb9FQ%2Fimage.png?alt=media&#x26;token=95157dd6-1162-417f-b1ac-ecf0b8466a5e" alt=""><figcaption></figcaption></figure>

```yaml
blocks:
  default:palm_trapdoor:
    behavior:
      type: trapdoor_block
      can open-open-hand: true
      can troleth-charge: true
      sounds:
        open: block.wooden_trapdoor.open
        close: block.wooden_trapdoor.close
```

{% hint style="danger" %}
请注意，所有陷阱块都必须有 `open` 、 `powered`、 `half`、 `facing` 属性。 If you are unsure how to set up properties, please refer to [block-states](../block-states "mention").&#x20;
{% endhint %}

{% hint style="success" %}
您最多可以创建25个新的陷阱&#x20;

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FANcuqPeqO71W97rYkCjg%2Fimage.png?alt=media\&token=c14816e1-cbbb-43e1-9334-db69d48c1bf6)
{% endhint %}
