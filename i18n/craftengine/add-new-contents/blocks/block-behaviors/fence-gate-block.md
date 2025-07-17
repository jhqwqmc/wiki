# 🪵 Fence Gate Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FNPmKMLMPGQz3qSBO3W26%2Fimage.png?alt=media&#x26;token=c6ec1ee0-a6e2-400a-985b-090dc61321dc" alt=""><figcaption></figcaption></figure>

```yaml
blocks:
  default:palm_fence_gate:
    behavior:
      type: fence_gate_block
      can-open-with-hand: true
      can-open-by-wind-charge: true
      sounds:
        open: block.fence_gate.open
        close: block.fence_gate.close
```

{% hint style="danger" %}
Please note that all fence gate blocks must have `open`, `powered`, `facing`, `in_wall`properties. If you are unsure how to set up properties, please refer to [block-states](../block-states "mention").&#x20;
{% endhint %}

{% hint style="success" %}
You can create at most 12 new fence gates

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FsYt7jqZOLRHRrnUgfhfd%2Fimage.png?alt=media\&token=e94e5a24-9d2b-4093-be42-e0d3434c86de)
{% endhint %}
