# :input_number: 客户端绑定项目数据

“客户端数据”仅存在于客户端，服务器端没有相关的组件。 通过客户端项目组件，您可以轻松地更新项目的实时描述，甚至像`item_model`和`custom_model_data`。 Plus, CraftEngine 项目不会像其他插件那样在创造性模式中永久修改！

{% hint style="success" %}
**每个选项在** [](<> "提及") **适用于** [client-bound-item-data](client-bound-item-data "提及")**。**
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
`client-bound-data` 对于冒险模式中的玩家非常有用，允许他们破坏服务器上某些真正的自定义块。

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
