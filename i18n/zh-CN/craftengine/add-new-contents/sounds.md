---
description: This page mainly explains how to add new sounds to your server.
---

# 🔊 Sounds

## Sound

```yaml
sounds:
  minecraft:custom_block.place:
    replace: false
    subtitle: subtitles.custom_block.place
    sounds:
      - "block/custom_block_1"
  minecraft:custom_ambient.custom_biome:
    replace: false
    subtitle: subtitles.custom_ambient.custom_biome
    sounds:
      - name: "ambient/custom_biome_1"
        volume: 0.4
        weight: 3
      - name: "ambient/custom_biome_2"
        volume: 0.4
        weight: 7
      - name: "ambient/custom_biome_3"
        volume: 0.4
        weight: 10
        stream: false
        attenuation-distance: 16
        preload: false
        type: "file"
```

When you use the `/playsound` command to play a sound, it should actually be referred to as a sound event, while the actual sounds are located under the `sounds` list. You can check the [Minecraft Wiki](https://minecraft.wiki/w/Sounds.json) to understand the effects corresponding to each parameter. The plugin does not provide extensive descriptions here because the Minecraft Wiki already explains each part very clearly, and CraftEngine uses the same configuration option names as those described in the wiki.

## Jukebox Song (1.21+)

{% hint style="danger" %}
Due to the fact that Minecraft's registry becomes immutable once registered, you will need to restart the server in order to apply any new modifications. However, you can register a new song in real-time by modifying the configuration ID.
{% endhint %}

```yaml
jukebox-songs:
  default:credits_music:
    sound: minecraft:music.credits
    length: 100.0  # music length in seconds
    description: "Credits"  
    comparator-output: 15
    range: 32
```

```yaml
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```
