# 💡 Lamp Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FUIoDMeUnwqBcif3P0eed%2Fimage.png?alt=media&#x26;token=e1c32789-458f-489d-be5c-dbe3b911e69e" alt=""><figcaption></figcaption></figure>

[lamp-block](lamp-block "mention") allows the block to turn into `lit` state on redstone powered.&#x20;

```yaml
blocks:
  default:copper_coil:
    behaviors:
      - type: lamp_block
```

{% hint style="danger" %}
Please note that all lamp blocks must have a property named `lit`of type `boolean`. If you are unsure how to set up properties, please refer to [block-states](../block-states "mention").&#x20;
{% endhint %}
