# :decruous_tree: Tree

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/dnabesUIDYkJCJAmbjA5/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/RbdTh3SUCgVxaUD53ul8/image.png" alt=""><figcaption></figcaption></figure>

## 配置的功能

```json
{
  "type": "minecraft:tree",
  "config": {
    "ignore_vines": true,
    "force_dirt": false,
    "minimum_size": {
      "type": "minecraft:two_layers_feature_size",
      "min_clipped_height": 10,
      "limit": 1,
      "lower_size": 0,
      "upper_size": 2
    },
    "dirt_provider": {
      "type": "minecraft:simple_state_provider",
      "state": {
        "Name": "minecraft:sand"
      }
    },
    "trunk_provider": {
      "type": "minecraft:simple_state_provider",
      "state": {
        "Name": "craftengine:note_block_1"
      }
    },
    "foliage_provider": {
      "type": "minecraft:simple_state_provider",
      "state": {
        "Name": "craftengine:oak_leaves_6"
      }
    },
    "trunk_placer": {
      "type": "minecraft:straight_trunk_placer",
      "base_height": 6,
      "height_rand_a": 5,
      "height_rand_b": 0
    },
    "foliage_placer": {
      "type": "minecraft:cherry_foliage_placer",
      "radius": 5,
      "offset": 0,
      "height": 4,
      "wide_bottom_layer_hole_chance": 0.8,
      "corner_hole_chance": 1,
      "hanging_leaves_chance": 0.8,
      "hanging_leaves_extension_chance": 0.4
    },
    "decorators": []
  }
}
```

## 已放置的功能

```json
{
  "feature": "craftengine:palm_tree",
  "placement": [
    {
      "type": "minecraft:count",
      "count": 1
    },
    {
      "type": "minecraft:in_square"
    },
    {
      "type": "minecraft:surface_water_depth_filter",
      "max_water_depth": 0
    },
    {
      "type": "minecraft:heightmap",
      "heightmap": "WORLD_SURFACE"
    },
    {
      "type": "minecraft:block_predicate_filter",
      "predicate": {
        "type": "minecraft:matching_blocks",
        "offset": [
          0,
          -1,
          0
        ],
        "blocks": "#minecraft:sand"
      }
    },
    {
      "type": "minecraft:biome"
    }
  ]
}
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/4l5Kl4kRCahKS8C50KBe/image.png" alt=""><figcaption></figcaption></figure>

{% file src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/Doyv1N9EYaDAz6OxKQrJ/palm_tree.zip" %}
