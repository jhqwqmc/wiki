# 📍 Furniture Placement

## Introduction

Furniture supports three placement modes: ground, ceiling, and wall. You can employ distinct appearances and collision box schemes for different placement modes. For instance, a potted plant furniture item may stand upright when placed on the ground, dangle with a rope when hung from the ceiling, and be supported by a wooden plank when mounted on the wall—much like vanilla bell block.

{% hint style="success" %}
You can configure multiple placement modes simultaneously for a single piece of furniture.
{% endhint %}

Below, I will use the ground mode as an example to explain how to configure a basic placement.

```yaml
furniture:
  default:bench:
    placement:
      ground:
        # create offsets for the drops so they won't spawn in blocks
        loot-spawn-offset: 0,0,0
        # Supports External Models Here
        # model-engine: blueprint_id
        # better-model: blueprint_id
        rules:
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
        elements:
          - item: default:bench
            display-transform: NONE
            billboard: FIXED
            position: 0.5,0,0
            translation: 0,0.5,0
            apply-dyed-color: true # default: true
        hitboxes:
          - type: interaction # non-collision hitbox
            can-use-item-on: false # default: false
            can-be-hit-by-projectile: false # default: false
            blocks-building: false # default: true
            position: 0,0,0
            width: 1
            height: 2
            # 'width'/'height' can be simplified to 'scale'
            # scale: 1,2 
            interactive: true # whether the interaction entity is interactive
            seats:
              - 0,0,-0.1 0
```

There are three sections: `rules`, `elements`, and `hitboxes`.&#x20;

The `rules` section determines the position and rotation constraints of the furniture after placement. The `elements` section defines which items compose the furniture (you can configure multiple items for a single piece of furniture, each with different display modes). \
The `hitboxes` section specifies the collision volume of the furniture.

## Rules

### rotation

The plugin's furniture supports a variety of rotation schemes, with the differences between them lying in the limitations on the number of rotation angles or the direct specification of rotation directions.

{% hint style="danger" %}
Rotation has no effect on wall-mounted placement methods.
{% endhint %}

### alignment

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/36xb0WeQSH45cr7iSVz6/image.png" alt="" width="375"><figcaption><p>center</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/F7HhjgTtxdk3wIucZwqy/image.png" alt="" width="375"><figcaption><p>half</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/k4jaenbMWri8AKqaiCPb/image.png" alt="" width="375"><figcaption><p>quarter</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/q0lwi6Z0jqkueQMDoiHD/image.png" alt="" width="375"><figcaption><p>corner</p></figcaption></figure>

{% hint style="success" %}
Alignment is also applicable to wall-mounted placements.
{% endhint %}

## Elements

An `element` is each item that constitutes the appearance of the furniture. For most furniture, a single item suffices. However, if you wish to create a more intricate piece of furniture, you can assemble it from multiple items. For example, a holographic projection could be divided into two items: a base and the projection itself. The base could have a fixed orientation, while the projection could be set to always face the player.

```yaml
elements:
  - item: default:bench
    display-transform: NONE # NONE / THIRD_PERSON_LEFT_HAND / THIRD_PERSON_RIGHT_HAND
                            # FIRST_PERSON_LEFT_HAND / FIRST_PERSON_RIGHT_HAND
                            # HEAD / GUI / GROUND / FIXED
    billboard: FIXED  # FIXED / VERTICAL / HORIZONTAL / CENTER
    position: 0.5,0,0
    translation: 0,0.5,0
    scale: 1 # scale: 1,2,1
    apply-dyed-color: true
    # rotation support 3 formats
    rotation: 45  # Y axis
    rotation: 45,45,0  # Euler angle
    rotation: 0,0,0.7071,0.7071  # Quaternions  https://quaternions.online/
```

{% hint style="warning" %}
Please note the distinction between `position` and `translation`. `position` alters the coordinate location of the corresponding display entity, whereas `translation` is a displacement attribute of the display entity itself.
{% endhint %}

{% hint style="danger" %}
For furniture placed on walls, you need to use `position` for slight offsets; otherwise, the furniture may turn black in certain directions. This is related to how Minecraft renders entities.
{% endhint %}

## Hitboxes

The `hitbox` is the interaction entity sent to the player, and you can visualize its effect by using the F3+B debug screen.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ZAkiDfKUD0JhyjS161gT/image.png" alt=""><figcaption></figcaption></figure>

### interaction

```yaml
hitboxes:
- type: interaction # non-collision hitbox
  can-use-item-on: false # default: false
  can-be-hit-by-projectile: false # default: false
  blocks-building: false # default: true
  position: 0,0,0
  width: 1
  height: 2
  # 'width'/'height' can be simplified to 'scale'
  # scale: 1,2 
  interactive: true # whether the interaction entity is interactive
  seats:
    - 0,0,-0.1 0
```

### Shulker

```yaml
hitboxes:
- type: shulker # hard-collision hitbox
  can-use-item-on: true # default: true
  can-be-hit-by-projectile: true # default: true
  blocks-building: true # default: true
  position: 1,0,0
  scale: 1 # 1.20.5+
  peek: 0 # 0~100
  # Relative direction. North = facing the player
  direction: UP # UP/DOWN/NORTH/WEST/EAST/SOUTH
  interaction-entity: true # whether to summon another interaction entity
  interactive: true # whether the interaction entity is interactive
  seats:
    - 1,0,-0.1 0
```

### Happy Ghast

```yaml
hitboxes:
- type: happy_ghast # hard/soft-collision hitbox
  can-use-item-on: true # default: true
  can-be-hit-by-projectile: true # default: true
  blocks-building: true # default: true
  hard-collision: true # default: true
  position: 1,0,0
  scale: 0.25 # default: 1
  seats:
    - 1,0,-0.1 0
```

### Custom

```yaml
hitboxes:
- type: custom # mainly used for soft-collision hitbox
  position: 1,0,0
  scale: 5 # 1.20.5+
  # You can use any entity here
  entity-type: slime # default: slime
  seats:
    - 1,0,-0.1 0
```

{% hint style="success" %}
A single `hitbox` can be configured with multiple seats. If the seats of multiple `hitboxes` are positioned at the same location, it is equivalent to having only one seat.
{% endhint %}

{% hint style="info" %}
The position of a `seat` is determined by a location and a rotation, separated by a space in the configuration.

```
0,0,0 0
```

You may also choose not to configure a rotation angle, allowing players to rotate freely to any angle while seated.

```
0,0,0
```
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/y0rBULzgm88rptOyeP5e/2.gif" alt=""><figcaption><p>0,0,0 0</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/7QS8DIznzoLlEmVELu1I/1.gif" alt=""><figcaption><p>0,0,0</p></figcaption></figure>

## External Models

You can also use external models from ModelEngine/BetterModel

```yaml
furniture:
  default:bench:
    placement:
      ground:
        model-engine: blueprint_id
        better-model: blueprint_id
        rules:
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
```
