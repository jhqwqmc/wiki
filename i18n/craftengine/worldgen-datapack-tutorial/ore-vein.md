# 🪨 Ore Vein

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/zpzxKSGLzNTYyM86Bmqe/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/YdA2B6pzJDhJLeW5ur7i/image.png" alt=""><figcaption></figcaption></figure>

## Configured Feature

```json
{
  "type": "minecraft:ore",
  "config": {
    "discard_chance_on_air_exposure": 0,
    "size": 3,
    "targets": [
      {
        "state": {
          "Name": "craftengine:note_block_13"
        },
        "target": {
          "predicate_type": "minecraft:tag_match",
          "tag": "minecraft:stone_ore_replaceables"
        }
      },
      {
        "state": {
          "Name": "craftengine:note_block_14"
        },
        "target": {
          "predicate_type": "minecraft:tag_match",
          "tag": "minecraft:deepslate_ore_replaceables"
        }
      }
    ]
  }
}
```

## Placed Feature

```json
{
  "feature": "craftengine:ore_topaz",
  "placement": [
    {
      "type": "minecraft:count",
      "count": 10
    },
    {
      "type": "minecraft:in_square"
    },
    {
      "type": "minecraft:height_range",
      "height": {
        "type": "minecraft:uniform",
        "max_inclusive": {
          "absolute": 72
        },
        "min_inclusive": {
          "above_bottom": -40
        }
      }
    },
    {
      "type": "minecraft:biome"
    }
  ]
}
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/MhILJaAfEm7EDavPOI8P/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/wMJjO7A0rsjY8rG0rxEm/image.png" alt=""><figcaption></figcaption></figure>

{% file src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/AUuQxbedEBV6DugvykFm/topaz_ore.zip" %}
