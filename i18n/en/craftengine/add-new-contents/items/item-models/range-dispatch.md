---
description: https://minecraft.wiki/w/Items_model_definition#range_dispatch
---

# 📡 Range Dispatch

> Render an item model based on numeric property. Will select last entry with threshold less or equal to property value.

{% hint style="info" %}
When using "minecraft:range\_dispatch," you need to specify the numeric `property` type. `scale` represents the factor to multiply the property value with, `entries` represent the models under different numerical values, and `fallback` represents the item model object if no valid entry was found. It is optional, but if not specified, it will render a "missing" error model.
{% endhint %}

```yaml
items:
  default:range_dispatch_item:
    model:
      type: "minecraft:range_dispatch"
      property: "minecraft:crossbow/pull"
      entries:
        - model:
            type: minecraft:model
            path: "minecraft:item/custom/model_1"
          threshold: 0.58
        - model:
            type: minecraft:model
            path: "minecraft:item/custom/model_2"
          threshold: 1.0
      fallback:
        type: minecraft:model
        path: "minecraft:item/custom/model_3"
```

## Available Properties

check [https://minecraft.wiki/w/Items\_model\_definition#range\_dispatch](https://minecraft.wiki/w/Items_model_definition#range_dispatch) for the usage of each argument

### minecraft:**crossbow/pull**

> Return crossbow-specific use time.

### minecraft:**bundle/fullness**

> Return weight of `minecraft:bundle_contents` component or `0` if not present.

### minecraft:**cooldown**

> Return remaining cooldown for item, scaled between `0.0` to `1.0`.

### minecraft:**compass**

> Return an angle, scaled from `0.0` to `1.0` in x-z plane between holder position and target. If target is not valid (not present, in other dimension or too close to holder position) random value will be returned.

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:compass"
target: spawn
wobble: true
```

### minecraft:**count**

> Return stack size.

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:count"
normalize: true
```

### minecraft:**damage**

> Return value for `minecraft:damage` component or `0` if not present.

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:damage"
normalize: true
```

### minecraft:**time**

> Return value of a in-game time, scaled betewen `0.0` to `1.0`.

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:time"
source: daytime
wobble: true
```

### minecraft:**use\_cycle**

> Return remaining use ticks modulo `period`.

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:use_cycle"
period: 1.0
```

### minecraft:**use\_duration**

> Return item use ticks.

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:use_duration"
remaining: false
```

### minecraft:**custom\_model\_data**

> Return value from `floats` list in `minecraft:custom_model_data` component or `0` if not present.

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:custom_model_data"
index: 0
```
