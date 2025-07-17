# 💦 Concrete Powder Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FTZqK3Gho57vlt2oJEPJy%2Fimage.png?alt=media&#x26;token=89aadbd0-381d-4b68-b315-48133832ad61" alt=""><figcaption></figcaption></figure>

[concrete-powder-block](concrete-powder-block "mention") is a type of block that hardens when it comes into contact with water. A configuration example is shown below:

```yaml
blocks:
  default:gunpowder_block:
    behavior:
      type: concrete_powder_block
      solid-block: default:solid_gunpowder_block
```

{% hint style="danger" %}
Currently, custom blocks cannot turn into blocks upon contacting water while in a falling entity state. This is because this piece of code is hardcoded in Minecraft, and we cannot modify its behavioral logic.
{% endhint %}
