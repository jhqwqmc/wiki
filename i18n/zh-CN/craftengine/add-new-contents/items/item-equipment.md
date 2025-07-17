# ⚔️ Item Equipment

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F878bezD7rvi7aNszRcBQ%2Fimage.png?alt=media&#x26;token=0409a115-5d15-4d84-b758-567e94867ff8" alt=""><figcaption></figcaption></figure>

CraftEngine offers two ways to create custom equipment. One method is based on **Trim** (for Minecraft 1.20+), and the other uses the **Equippable component** (introduced in 1.21.2).

## Trim Based (1.20+)

The plugin removes the base texture of a vanilla armor (like chainmail) and replaces it with your custom texture by applying custom `trim_pattern`. You can set this up in `config.yml` - but remember, the `sacrificed-vanilla-armor` feature only activates after you've configured at least one trim-based armor.

<pre class="language-yaml"><code class="lang-yaml"><strong># config.yml
</strong>equipment:
  # The sacrificed-vanilla-armor argument determines which vanilla armor gets completely removed (loses all its trims)
  # when you create new armor using trim types, freeing up a slot for your custom armor.
  sacrificed-vanilla-armor:
    type: chainmail
    # CraftEngine repurposes a vanilla armor's texture slot for custom armor trims.
    # To preserve the original look, it uses trim configurations to reconstruct the default appearance.
    asset-id: minecraft:chainmail
    humanoid: minecraft:trims/entity/humanoid/chainmail
    humanoid-leggings: minecraft:trims/entity/humanoid_leggings/chainmail
</code></pre>

{% hint style="danger" %}
Because we removed vanilla armor textures, we add [client-bound-item-data](item-data/client-bound-item-data "mention") with special trims to make them appear normal. (This is setup in the `legacy_armor` config.)

```yaml
# Since we removed the chainmail armor textures, 
# we need to add a client-side trim pattern for the
# vanilla chainmail armor to make it display properly.
items:
  minecraft:chainmail_helmet:
    client-bound-data:
      trim:
        pattern: chainmail
        material: custom
      hide-tooltip:
        - trim
```

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FRjQWNF4zqX6E30JcfQPi%2Fimage.png?alt=media\&token=1ce14e73-573a-4ab5-a5d1-96de3e896c53)
{% endhint %}

```yaml
equipments:
  # the equipment asset id
  default:topaz:
    type: trim
    humanoid: minecraft:entity/equipment/humanoid/topaz
    humanoid-leggings: minecraft:entity/equipment/humanoid_leggings/topaz
```

{% hint style="warning" %}
**Heads up!** Armor made with the trim method can't use the smithing table's trim upgrades. Plus, the vanilla armor you sacrificed loses its trim ability too. If you're running a 1.21.2+ server, you'll want to use the component method instead.
{% endhint %}

## Component Based (1.21.2+)

[https://minecraft.wiki/w/Equipment](https://minecraft.wiki/w/Equipment)

```yaml
equipments:
  # the equipment asset id
  default:topaz:
    type: component
    # 'namespace:path' resolves to assets/<namespace>/textures/entity/equipment/<layer_type>/<path>.png.
    # 
    # Example: minecraft:topaz
    #               ↓
    # assets/minecraft/textures/entity/equipment/humanoid/topaz.png
    humanoid: "minecraft:topaz"

    # You can also set it up as a block like this for some extra options
    humanoid:
      texture: "minecraft:leather"
      # supports color
      dyeable:
        color-when-undyed: -6265536 # leather color
      # for elytra texture
      use-player-texture: false
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FLR0DDiy5hFX6YM7dGYHc%2Fimage.png?alt=media&#x26;token=eaa277bf-38c0-434c-873f-5f0b426a0485" alt=""><figcaption><p>how texture path works</p></figcaption></figure>

{% hint style="info" %}
❓️**Q:** Why doesn't the plugin let users use random texture paths and relocate them when generating the resource pack?

✔️ **A:** I want users to follow Minecraft's resource pack standards - I'll only allow custom paths if Mojang breaks their own rules. Then the plugin will handle version-specific paths for you.
{% endhint %}

You can also combine multiple textures using lists. Here are two examples:

```yaml
equipments:
  custom:partialy_dyeable_armor:
    type: component
    humanoid:
      - texture: "minecraft:dyeable_part"
        dyeable:
          color-when-undyed: -6265536
      - texture: "minecraft:undyeable_part"
```

```yaml
equipments:
  custom:red_flower_wreath:
    type: component
    humanoid:
      - texture: "minecraft:wreath"
      - texture: "minecraft:red_flower"
  custom:yellow_flower_wreath:
    type: component
    humanoid:
      - texture: "minecraft:wreath"
      - texture: "minecraft:yellow_flower"
  custom:white_flower_wreath:
    type: component
    humanoid:
      - texture: "minecraft:wreath"
      - texture: "minecraft:white_flower"
```

{% hint style="success" %}
S**upported layer types:**

- humanoid
- humanoid-leggings
- wings
- wolf-body
- horse-body
- llama-body
- pig-saddle
- strider-saddle
- camel-saddle
- horse-saddle
- donkey-saddle
- mule-saddle
- skeleton-horse-saddle
- zombie-horse-saddle
- happy-ghast-body
  {% endhint %}

## Apply the Equipment

See [#equipment](../item-settings#equipment "mention")

```yaml
items:
  custom:my_helmet:
    settings:
      equipment:
        # the equipment asset id
        asset-id: default:topaz
```
