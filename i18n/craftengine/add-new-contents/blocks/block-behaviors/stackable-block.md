# 🥪 Stackable Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F4A2deddepooDFNBl9YaU%2Fimage.png?alt=media&#x26;token=8584d058-4036-4b06-99e2-32d9e67a158c" alt=""><figcaption></figcaption></figure>

```yaml
blocks:
  default:pebble:
    behavior:
      type: stackable_block
      property: pebble  # the name of the property for amount
      items:
        - default:pebble
      sounds:
        stack: minecraft:block.stone.fall
```
