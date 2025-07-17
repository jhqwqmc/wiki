---
description: This page mainly explains how to configure loot for vanilla stuff
---

# 🗃️ Vanilla Loots

## Introduction

Minecraft's native loot system is already quite robust, but it has one notable shortfall: it cannot incorporate certain plugin-specific elements such as placeholder checks, permissions, and other advanced functionalities. Additionally, configuring vanilla data packs is a cumbersome process, making the overriding of default loot tables particularly challenging. To address this, the plugin offers an override feature for the vanilla loot system. You can refer to the following example to get started quickly. In the text below, the "..." represents loot configurations. It is advisable to first read [loot-table](loot-table "mention") to understand how to configure loot effectively.

## Block Loots

```yaml
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target: "minecraft:grass"
    # Whether to overwrite the vanilla loots
    override: false
    loot:
      ...
```

```yaml
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target:
      - minecraft:wheat[age=0] # use a detailed state
      - minecraft:wheat[age=1]
    override: false
    loot:
      ...
```

## Entity Loots

```yaml
vanilla-loots:
  minecraft:sheep_loot:
    type: entity
    target: "minecraft:sheep"
    # Whether to overwrite the vanilla loots
    override: false
    loot:
      ...
```
