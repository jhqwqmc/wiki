---
description: https://minecraft.wiki/w/Items_model_definition#condition
---

# ⚖️ Condition

{% hint style="info" %}
In this configuration, when you use "minecraft:condition," you need to specify the condition type, which is the "property" mentioned below. "on-false" and "on-true" respectively represent displaying different models under different conditions.
{% endhint %}

```yaml
items:
  default:condition_item:
    model:
      type: "minecraft:condition"
      property: "minecraft:using_item"
      on-false:
        type: "minecraft:model"
        path: "minecraft:item/custom/model_false"
      on-true:
        type: "minecraft:model"
        path: "minecraft:item/custom/model_true"
```

## Available Properties

check [https://minecraft.wiki/w/Items\_model\_definition#condition](https://minecraft.wiki/w/Items_model_definition#condition) for the usage of each argument

### minecraft:broken

> Return `true` if the item is damageable and has only one use remaining before breaking.

### minecraft:carried

> Return `true` if item is carried between slots in GUI.

### minecraft:**damaged**

> Return `true` if the item is damageable and has been used at least once.

### minecraft:**extended\_view**

> Return `true` if player has requested extended details by holding shift key down. Only works when item is displayed in UI. Note: not a keybind, can't be rebound.

### minecraft:**fishing\_rod/cast**

> Return `true` if there is a fishing bobber attached to currently used fishing rod.

### minecraft:**selected**

> Return `true` if item is selected on a hotbar.

### minecraft:**using\_item**

> Return `true` if player is currently using this item.

### minecraft:**view\_entity**

> * When not spectating, return `true` if context entity is the local player entity, i.e. the one controlled by client.
> * When spectating, return `true` if context entity is the _spectated_ entity.
> * If context entity is not present, will return `false`.

### minecraft:**bundle/has\_selected\_item**

> Return `true` if bundle is "open", i.e. it has selected item visible in GUI.

### minecraft:**component (1.21.5+)**

> Uses component [item sub predicates](https://minecraft.wiki/w/Item_sub-predicate) to match item components.

### minecraft:has\_**component**

> Return `true` if the given component is present on the item.

```yaml
type: "minecraft:condition"
property: "minecraft:has_component"
component: minecraft:enchantments
ignore-default: false
```

### minecraft:**keybind\_down**

> Return `true` if keybind is currently active.

```yaml
type: "minecraft:condition"
property: "minecraft:keybind_down"
keybind: key.left
```

### minecraft:**custom\_model\_data**

> Return value from `flags` list in `minecraft:custom_model_data` component.

```yaml
type: "minecraft:condition"
property: "minecraft:custom_model_data"
index: 0
```
