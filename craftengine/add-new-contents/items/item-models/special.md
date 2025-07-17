---
description: https://minecraft.wiki/w/Items_model_definition#special
---

# 👻 Special

> Render a special model.

{% hint style="info" %}
When using "minecraft:special," you need to specify a `speical mode` type. `path` argument is required for the base model rendering.
{% endhint %}

```yaml
default:gui_head_size_1:
  model:
    type: minecraft:special
    path: minecraft:item/custom/gui_head_size_1
    model:
      type: minecraft:head
      kind: player
```

## Available Special Model Types

check [https://minecraft.wiki/w/Items\_model\_definition#special](https://minecraft.wiki/w/Items_model_definition#special) for the usage of each argument

### minecraft:trident

> Render a trident.

### minecraft:conduit

> Render conduit.

### minecraft:shield

> Render a shield. Uses patterns from `minecraft:banner_patterns` component and color from `minecraft:base_color` component.

### minecraft:decorated\_pot

> Render a decorated pot. Uses values from `minecraft:pot_decorations` component.

### minecraft:hanging\_sign

> Renders a hanging sign.

```yaml
model:
  type: "minecraft:hanging_sign"
  wood-type: "oak"
  texture: ...
```

### minecraft:standing\_sign

> Renders a standing sign.

```yaml
model:
  type: "minecraft:standing_sign"
  wood-type: "oak"
  texture: ...
```

### minecraft:head

> Render a head. \[Uses profile from `minecraft:profile` component when applicable. (1.21.4-1.21.5)]

```yaml
model:
  type: "minecraft:head"
  kind: player
  texture: ...
  animation: 0.0
```

### minecraft:player\_head (1.21.6+)

> Render a head. Uses profile from `minecraft:profile` component when applicable.

```yaml
model:
  type: "minecraft:player_head"
```

### minecraft:chest

> Render a single chest.

```yaml
model:
  type: "minecraft:chest"
  openness: 0.0
  texture: ...
```

### minecraft:**shulker\_box**

> Render a shulker box.

```yaml
model:
  type: "minecraft:shulker_box"
  openness: 0.0
  orientation: up
  texture: ...
```

### minecraft:**bed**

> Render a whole bed.

```yaml
model:
  type: "minecraft:bed"
  texture: ...
```

### minecraft:**banner**

> Render a banner with patterns from `minecraft:banner_patterns` component.

```yaml
model:
  type: "minecraft:bed"
  color: white
```

