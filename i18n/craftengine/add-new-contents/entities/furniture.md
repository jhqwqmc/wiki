---
description: This page mainly explains how to add new furniture to your server.
---

# 🪑 Furniture

{% hint style="danger" %}
Please note that reloading the plugin will not affect furniture that already placed! You will need to restart the server or reload the chunks to apply new configurations to existing furniture. The plugin utilizes caching to enhance the performance of the furniture. Forcibly reloading furniture that is already loaded on the server without caution could have a significant impact on the server's stability.\
\
In the future, the plugin may consider introducing related unsafe flags for forced reloading, but certainly not at this moment.
{% endhint %}

## Sections to Configure

A complete furniture configuration contains the following sections:

* behavior

{% content-ref url="furniture/furniture-behaviors" %}
[furniture-behaviors](furniture/furniture-behaviors)
{% endcontent-ref %}

* settings

{% content-ref url="furniture/furniture-settings" %}
[furniture-settings](furniture/furniture-settings)
{% endcontent-ref %}

* placement

{% content-ref url="furniture/furniture-placement" %}
[furniture-placement](furniture/furniture-placement)
{% endcontent-ref %}

* loot

{% content-ref url="../loot-table" %}
[loot-table](../loot-table)
{% endcontent-ref %}

* events

{% content-ref url="../events" %}
[events](../events)
{% endcontent-ref %}

## How to Bind Items

{% content-ref url="../items/item-behaviors/furniture-item" %}
[furniture-item](../items/item-behaviors/furniture-item)
{% endcontent-ref %}

## Full Config Overview

```yaml
furniture:
  default:bench:
    settings:
      item: default:bench
      sounds:
        break: minecraft:block.bamboo_wood.break
        place: minecraft:block.bamboo_wood.place
    placement:
      ground:
        rules:
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
        elements:
          - item: default:bench
            display-transform: NONE
            billboard: FIXED
            position: 0.5,0,0
            translation: 0,0.5,0
        hitboxes:
          - position: 0,0,0
            width: 1
            height: 1
            interactive: true
            seats:
              - 0,0,-0.1 0
          - position: 1,0,0
            width: 1
            height: 1
            interactive: true
            seats:
              - 1,0,-0.1 0
    loot:
      template: loot_table:normal
      arguments:
        item: default:bench
```
