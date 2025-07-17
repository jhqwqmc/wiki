# :hyacin：布什块

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/RFE0okQV9AmYrWNZNon9/image.png" alt=""><figcaption></figcaption></figure>

[bush-block](bush-block "提及") 是一种必须在特定支持方块上增长的方块行为。 如果该方块下方被摧毁，或者它被发现处于无效的位置， 它会被打断或丢弃。

```yaml
blocks:
  default:fairy_flower:
    行为:
      类型: bush_block
      stack: false
      blacklist: false # 使用黑名单模式
      延迟: 0
      底部块:
        - custom:xxx
        - minecraft:stone
      底部块标签:
        - minecraft:dirt
        - minecraft:farmland
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FjeEOdk98aCeu339mvteN%2Fimage.png?alt=media&#x26;token=8ce624ed-d10f-409a-851f-c734d662278b" alt=""><figcaption></figcaption></figure>



