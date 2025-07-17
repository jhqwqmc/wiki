# 🪻 Bush Block

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/RFE0okQV9AmYrWNZNon9/image.png" alt=""><figcaption></figcaption></figure>

[bush-block](bush-block "mention") is a type of block behavior that must grow on specific supporting blocks. If the block beneath it is destroyed, or if it is found to be in an invalid position, it will either break or drop as an item.

```yaml
blocks:
  default:fairy_flower:
    behavior:
      type: bush_block
      stackable: false
      blacklist: false # use blacklist mode
      delay: 0
      bottom-blocks:
        - custom:xxx
        - minecraft:stone
      bottom-block-tags:
        - minecraft:dirt
        - minecraft:farmland
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FjeEOdk98aCeu339mvteN%2Fimage.png?alt=media&#x26;token=8ce624ed-d10f-409a-851f-c734d662278b" alt=""><figcaption></figcaption></figure>



