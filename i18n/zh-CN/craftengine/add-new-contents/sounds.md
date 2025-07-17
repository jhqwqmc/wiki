---
description: 此页主要解释了如何添加新声音到您的服务器。
---

# :speaker_hig_volume: 声音

## 声音

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

当您使用 `/playsound` 命令播放声音时，它实际上应该被称为声音事件， 而实际声音位于声音列表下。 你可以检查 [Minecraft Wiki](https://minecraft.wiki/w/Sounds.json) 来了解每个参数对应的效果。 这个插件没有在这里提供详尽的描述，因为Minecraft Wiki 已经非常清楚地解释了每个部分， 和 CraftEngine 使用与wiki中描述的相同的配置选项名称。

## 唱片机歌曲(1.21+)

{% hint style="danger" %}
由于Minecraft的注册在注册后变得不可变， 您需要重新启动服务器才能应用任何新的修改。 然而，您可以通过修改配置ID实时注册新歌曲。
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
