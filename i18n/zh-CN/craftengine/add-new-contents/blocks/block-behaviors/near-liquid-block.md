# :water_wave : 靠近液体块

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FQThsCr8DWL9MnDStY5c4%2Fimage.png?alt=media&#x26;token=0540cc32-fcf8-4a26-9e67-a5d9d81f27d7" alt=""><figcaption></figcaption></figure>

不同于 [on-liquid-block](on-liquid-block "提及") , [near-liquid-block](near-liquid-block "提及") 不需要液体作为源块。

```yaml
blocks:
  default:flame_cane:
    behaviors:
      - type: near_liket_block
        libe-type: lava
        stackable: true
        positions:
          - 1, 1,0
          - 1, 1,0
          - 0, 1,1
          - 0,-1,1
```

