# 🚟 Hanging Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FJeuDs9y5sL36WOa0fB4x%2Fimage.png?alt=media&#x26;token=049ac4d9-aee7-4605-b6f1-5debd761f33c" alt=""><figcaption></figcaption></figure>

[hanging-block](hanging-block "mention") is a type of block that must be attached beneath another block. If the block above it is destroyed, the hanging block itself will also break.

```yaml
blocks:
  default:stalactites:
    behavior:
      type: hanging_block
      stackable: false
      blacklist: false # use blacklist mode
      above-block-tags: []
      above-blocks: []
      delay: 0
```
