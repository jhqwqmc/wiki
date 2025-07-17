---
description: This page mainly explains how to add new blocks to your server.
---

# 🧱 Blocks

## Sections to Configure

A complete block configuration contains the following sections:

* behavior

{% content-ref url="blocks/block-behaviors" %}
[block-behaviors](blocks/block-behaviors)
{% endcontent-ref %}

* settings

{% content-ref url="blocks/block-settings" %}
[block-settings](blocks/block-settings)
{% endcontent-ref %}

* states

{% content-ref url="blocks/block-states" %}
[block-states](blocks/block-states)
{% endcontent-ref %}

* loot

{% content-ref url="loot-table" %}
[loot-table](loot-table)
{% endcontent-ref %}

* events

{% content-ref url="events" %}
[events](events)
{% endcontent-ref %}

## How to Bind Items

{% content-ref url="items/item-behaviors/block-item" %}
[block-item](items/item-behaviors/block-item)
{% endcontent-ref %}

## Full Config Overview

This is a simplified version using the template system, including the sections that need to be configured.

```yaml
blocks:
  default:palm_log:
    behavior:
      type: strippable_block
      stripped: default:stripped_palm_log
    loot:
      template: loot_table:normal
      arguments:
        item: default:palm_log
    settings:
      template: block_settings:log
      overrides:
        item: default:palm_log
    states:
      template: "default:block_state/pillar"
      arguments:
        base_block: note_block
        texture_top_path: minecraft:block/custom/palm_log_top
        texture_side_path: minecraft:block/custom/palm_log
        model_vertical_path: minecraft:block/custom/palm_log
        model_horizontal_path: minecraft:block/custom/palm_log_horizontal
        vanilla_id:
          type: self_increase_int
          from: 0
          to: 2
        internal_id:
          type: self_increase_int
          from: 0
          to: 2
```

{% hint style="danger" %}
If you haven't learned how to use the template system yet, be sure to learn it now [templates-must-read](templates-must-read "mention")

What happens if you don't use a template? Then the configuration file for this block will look like this:

```yaml
blocks:
  default:palm_log:
    behavior:
      type: strippable_block
      stripped: default:stripped_palm_log
    loot:
      pools:
        - rolls: 1
          conditions:
            - type: survives_explosion
          entries:
            - type: item
              item: "default:palm_log"
    settings:
      hardness: 2.0
      resistance: 2.0
      push-reaction: NORMAL
      replaceable: false
      burnable: true
      burn-chance: 5
      fire-spread-chance: 5
      is-redstone-conductor: true
      is-suffocating: true
      instrument: BASS
      can-occlude: true
      item: default:palm_log
      tags:
        - minecraft:mineable/axe
        - minecraft:logs_that_burn
        - minecraft:logs
        - minecraft:completes_find_tree_tutorial
      sounds:
        break: minecraft:block.wood.break
        step: minecraft:block.wood.step
        place: minecraft:block.wood.place
        hit: minecraft:block.wood.hit
        fall: minecraft:block.wood.fall
    states:
      properties:
        axis:
          type: axis
          default: y
      appearances:
        axisY:
          state: "note_block:0"
          model:
            path: "minecraft:block/custom/stripped_palm_log"
            generation:
              parent: "minecraft:block/cube_column"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisX:
          state: "note_block:1"
          model:
            x: 90
            y: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisZ:
          state: "note_block:2"
          model:
            x: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
      variants:
        axis=x:
          appearance: axisX
          id: 0
        axis=y:
          appearance: axisY
          id: 1
        axis=z:
          appearance: axisZ
          id: 2
```
{% endhint %}
