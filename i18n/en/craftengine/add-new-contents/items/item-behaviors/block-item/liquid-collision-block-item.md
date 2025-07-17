# 🌊 Liquid Collision Block Item

Unlike `block_item`, `liquid_collision_block_item` checks for collisions with fluids. It is suitable for creating blocks that can be placed on the surface of water or lava. All other configuration options are identical to those of `block_item`.

```yaml
items:
  default:reed:
    material: paper
    behavior:
      type: liquid_collision_block_item
      offset-y: 1 # the position to place block on
      block: default:reed
```

