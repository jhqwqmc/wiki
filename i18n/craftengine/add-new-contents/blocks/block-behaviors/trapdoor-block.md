# 🪟 Trapdoor Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FeMkYg3eaWHjUB4ZVb9FQ%2Fimage.png?alt=media&#x26;token=95157dd6-1162-417f-b1ac-ecf0b8466a5e" alt=""><figcaption></figcaption></figure>

```yaml
blocks:
  default:palm_trapdoor:
    behavior:
      type: trapdoor_block
      can-open-with-hand: true
      can-open-by-wind-charge: true
      sounds:
        open: block.wooden_trapdoor.open
        close: block.wooden_trapdoor.close
```

{% hint style="danger" %}
Please note that all trapdoor blocks must have `open`, `powered`, `half`, `facing` properties. If you are unsure how to set up properties, please refer to [block-states](../block-states "mention").&#x20;
{% endhint %}

{% hint style="success" %}
You can create at most 25 new trapdoors&#x20;

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FANcuqPeqO71W97rYkCjg%2Fimage.png?alt=media\&token=c14816e1-cbbb-43e1-9334-db69d48c1bf6)
{% endhint %}
