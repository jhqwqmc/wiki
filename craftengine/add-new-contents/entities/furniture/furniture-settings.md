# ⚙️ Furniture Settings

## item

Determines the item that this furniture corresponds to. This is usually used to get furniture item in creative mode with middle click(1.21.4+).

```yaml
item: default:test_furniture
```

## sounds

Determines the sound of the furniture in various situations

* break    When the player breaks this furniture
* place    When the player places this furniture

```yaml
sounds:
  break: minecraft:block.bamboo_wood.break
  place: minecraft:block.bamboo_wood.place
```

{% hint style="info" %}
You can configure like this to precisely control the volume and pitch

```yaml
sounds:
  break:
    id: minecraft:block.deepslate.break
    pitch: 0.5
    volume: 0.25
  place: minecraft:block.deepslate.step
```
{% endhint %}

## minimized

Determines whether this furniture should minimize the network packet sent to players without admin permissions.

```yaml
minimized: true
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FqmuOtslb0m4pzkyKjf20%2Fimage.png?alt=media&#x26;token=7651bfce-5d2e-494a-8893-5017aa63a332" alt=""><figcaption></figcaption></figure>
