# 📔 Worldgen Datapack Tutorial

## Important Things to Know

{% hint style="danger" %}
Since Minecraft do not permit the dynamic modification of the block registry, the plugin pre-registers all necessary real states in advance. You can query the actual block states corresponding to a block by using [#get-block-internal-id](../commands#get-block-internal-id "mention").

Minecraft only recognizes block names that follow the pattern similar to `craftengine:note_block_x`. This applies even when you are using other plugins, such as MythicMobs' block placement skills. The reason for this is that CraftEngine employs a dynamic binding scheme, which means the block IDs within the plugin do not align with the actual block IDs on serverside.
{% endhint %}

## The Target Audience for This Tutorial

This tutorial is designed as a crash course, tailored specifically for those who wish to swiftly implement certain functionalities without investing time in learning Minecraft datapacks. The examples provided are merely feasible solutions and do not represent the full potential of the plugin. You are entirely capable of utilizing CraftEngine to generate mod-like terrains and biomes.

{% hint style="success" %}
When making your datapack, you may integrate the website&#x20;

[https://misode.github.io/worldgen/feature/](https://misode.github.io/worldgen/feature/)

[https://misode.github.io/worldgen/placed-feature/](https://misode.github.io/worldgen/placed-feature/)

into your workflow, as it serves as a valuable tool to minimize syntax errors in your config.
{% endhint %}

{% hint style="danger" %}
This tutorial was authored during the era of version 1.21.4. Please be aware that variations may exist across different versions, and it is advisable to exercise discernment accordingly.

This is not a professional datapack tutorial; it contains only simple examples. If you are interested in datapacks, you should seek out professional tutorials and dedicate time to learning them thoroughly.
{% endhint %}
