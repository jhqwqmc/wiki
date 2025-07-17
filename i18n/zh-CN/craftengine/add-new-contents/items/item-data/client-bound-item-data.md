# 🔢 Client Bound Item Data

The "client-bound data" exists solely on the client side, and there are no related components on the server side. With the client-side item component, you can easily update item descriptions in real-time - even stuff like `item_model` and `custom_model_data`. Plus, CraftEngine items won't get permanently modified in creative mode like other plugins do!

{% hint style="success" %}
**Every option available in** [](<> "mention") **is applicable in** [client-bound-item-data](client-bound-item-data "mention")**.**
{% endhint %}

```yaml
items:
  default:topaz_rod:
    client-bound-data:
      item-name: "<!i><#FF8C00>I'm not Topaz Rod"
    data:
      item-name: "<!i><#FF8C00>Topaz Rod"
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FosV8ncsaaP8TTpxBwTP8%2Fimage.png?alt=media&#x26;token=e06087ae-9871-4577-96d2-67f4a6e25fa7" alt=""><figcaption></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FXZ8JiAryf19y0MtzHlor%2Fimage.png?alt=media&#x26;token=4e44fefa-ba07-44f0-b939-564c9d7e8722" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
`client-bound-data` is quite useful for players in adventure mode, allowing them to break certain real custom blocks on serverside.

```yaml
items:
  default:topaz_pickaxe:
    material: golden_pickaxe
    custom-model-data: 1000
    settings:
      tags:
        - "default:topaz_tools"
    client-bound-data:
      components:
        # client side block state
        can_break:
          blocks: minecraft:note_block
          state:
            "instrument": "hat"
            "note": "0"
            "powered": "false"
    data:
      item-name: "<!i><#FF8C00><i18n:item.topaz_pickaxe>"
      tooltip-style: minecraft:topaz
      components:
        minecraft:max_damage: 64
        # server side block state
        can_break:
          blocks: "craftengine:note_block_1"
    model:
      template: default:model/simplified_handheld
      arguments:
        path: "minecraft:item/custom/topaz_pickaxe"
```

{% endhint %}
