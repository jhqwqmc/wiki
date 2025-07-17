# 🚪 Door Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FkhYqDmF2zkkWE0L7OLnT%2Fimage.png?alt=media&#x26;token=390a5cf9-4449-4c01-931d-caea5df7672f" alt=""><figcaption></figcaption></figure>

```yaml
blocks:
  default:palm_door:
    behavior:
      type: door_block
      can-open-with-hand: true
      can-open-by-wind-charge: true
      sounds:
        open: block.wooden_door.open
        close: block.wooden_door.close
```

{% hint style="danger" %}
Please note that all door blocks must have `open`, `powered`, `half`, `facing`, `hinge` properties. If you are unsure how to set up properties, please refer to [block-states](../block-states "mention").&#x20;
{% endhint %}

{% hint style="success" %}
You can create at most 25 new doors&#x20;

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fnw9ld2yOdjO4jI2cg3Ha%2Fimage%20\\(1\\).png?alt=media\\&token=cd0a9263-483e-4249-92bb-3e54390c75e7)
{% endhint %}
