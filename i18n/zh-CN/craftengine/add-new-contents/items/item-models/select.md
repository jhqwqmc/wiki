---
description: https://minecraft.wiki/w/Items_model_definition#select
---

# ✅ Select

> Render an item model based on discrete property.

{% hint style="info" %}
When using "minecraft:select," you need to specify a `property` type. `cases` represent a list of scenarios to match against, while `fallback` represents the item model object that will be used if no valid entry is found. It is optional, but if not provided, a "missing" error model will be rendered.
{% endhint %}

```yaml
items:
  default:select_item:
    model:
      type: "minecraft:select"
      property: "minecraft:charge_type"
      cases:
        - when: arrow
          model:
            type: minecraft:model
            path: "minecraft:item/custom/model_1"
        - when: rocket
          model:
            type: minecraft:model
            path: "minecraft:item/custom/model_2"
      fallback:
        type: minecraft:model
        path: "minecraft:item/custom/model_3"
```

## 可用属性

check [https://minecraft.wiki/w/Items\_model\_definition#select](https://minecraft.wiki/w/Items_model_definition#select) for the usage of each argument

### minecraft:**charge\_type**

> Return charge type stored in `minecraft:charged_projectiles` component.

### minecraft:**context\_dimension**

> Return the ID of the dimension in context, if any.

### minecraft:**context\_entity\_type**

> Return the holding entity type, if present.

### minecraft:**display\_context**

> Return context this item is rendered in.

### minecraft:**main\_hand**

> Return main hand of holding player.

### minecraft:**trim\_material**

> Return value of `material` field from `minecraft:trim` component, if present.

### minecraft:**block\_state**

> Return value for some property from `minecraft:block_state` component.

```yaml
type: "minecraft:select"
property: "minecraft:block_state"
block-state-property: "facing"
```

### minecraft:**组件 (1.21.5+)**

> Return value from a [component](https://minecraft.wiki/w/Data_component_format). If the selected value comes from a registry and the current datapacks does not provide it, the entry will be silently ignored.

```yaml
type: "minecraft:select"
property: "minecraft:component"
component: "minecraft:unbreakable"
```

### minecraft:**custom\_model\_data**

> Return value from `strings` list in `minecraft:custom_model_data` component.

```yaml
type: "minecraft:select"
property: "minecraft:custom_model_data"
index: 0
```

### minecraft:**local\_time**

> Returns the current time formatted according to a given pattern. The value is updated every second. For full format documentation for locale, time zone and pattern, see ICU (International Components for Unicode) documentation.

```yaml
type: "minecraft:select"
property: "minecraft:local_time"
locale: "en_US"
time-zone: "GMT+0:45"
pattern: "HH:mm:ss"
```
