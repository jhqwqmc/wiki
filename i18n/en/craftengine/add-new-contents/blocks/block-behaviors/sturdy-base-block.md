# 🪨 Sturdy Base Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FSv0hYsWZ2ZznVipMcnYq%2Fimage.png?alt=media&#x26;token=775c0713-2243-448f-b9c2-e35a242b41ce" alt=""><figcaption></figcaption></figure>

```yaml
blocks:
  default:pebble:
    behavior:
      type: sturdy_base_block
      direction: down
      support-types:
        - full
```

[sturdy-base-block](sturdy-base-block "mention") refers to blocks that need a sturdy supporting face. For example, doors won't work on dripstones. Support types include `full`, `rigid`, and `center`.
