# 🌊 Near Liquid Block

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FQThsCr8DWL9MnDStY5c4%2Fimage.png?alt=media&#x26;token=0540cc32-fcf8-4a26-9e67-a5d9d81f27d7" alt=""><figcaption></figcaption></figure>

Unlike [on-liquid-block](on-liquid-block "mention") , [near-liquid-block](near-liquid-block "mention") does not require the liquid to be a source block.

```yaml
blocks:
  default:flame_cane:
    behaviors:
      - type: near_liquid_block
        liquid-type: lava
        stackable: true
        positions:
          - -1,-1,0
          - 1,-1,0
          - 0,-1,-1
          - 0,-1,1
```

