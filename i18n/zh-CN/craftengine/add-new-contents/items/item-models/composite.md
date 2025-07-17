---
description: https://minecraft.wiki/w/Items_model_definition#composite
---

# 🧩 Composite

> Render multiple sub-models in the same space.

```yaml
default:composite_item:
  model:
    type: "minecraft:composite"
    models:
      - type: minecraft:model
        path: "minecraft:item/custom/model_1"
      - type: minecraft:model
        path: "minecraft:item/custom/model_2"
      - type: minecraft:model
        path: "minecraft:item/custom/model_3"
```
