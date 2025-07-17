---
description: This page mainly explains how to use model generation.
---

# 🏭️ Model Generation

## Introduction

[model-generation](model-generation "mention") is acting a role to create a model in YAML format.

When configuring multiple similar models (e.g., 16 wool-colored sofas that only differ in textures), you would normally need to create an equal number of separate models. However, with Model Generation, you can easily manage these model inheritance relationships using YAML format.

{% hint style="danger" %}
The path specified in the `path` option (located in the same configuration section as `generation`) must point to a non-existent model path! Otherwise, it will conflict with your existing models.

Model generation is **always an optional** configuration. If you already have a dedicated JSON model file for that block/item, you **do not need** to use `generation`—simply specify the model path using `path` instead.
{% endhint %}

## Where to Configure

If you observe carefully, you'll notice that the plugin uses the following configuration format in many places.&#x20;

```yaml
path: "xxx:xxx"
generation:
  parent: "minecraft:xxx/xxx"
  textures:
    "xxx": "xxx:xxx"
```

{% hint style="info" %}
In fact, the plugin supports model generation wherever a model path (`path`) can be specified. Whenever you see `path`, it means you can use `generation` within the same configuration section.
{% endhint %}

## Arguments

### parent

> Loads a different model from the given path, in form of a [resource location](https://minecraft.wiki/w/Tutorial:Models#File_path)

The `parent` field can not only reference the default models provided by vanilla Minecraft but can also point to your custom models. You can view all available Minecraft models on this [website](https://misode.github.io/assets/model/)

```yaml
items#test:
  default:big_apple:
    material: apple
    custom-model-data: 1000
    model:
      type: minecraft:model
      path: "minecraft:item/custom/big_apple"
      generation:
        parent: "minecraft:item/apple" # inherits apple's model
        # displays a big apple in gui
        display:
          gui:
            scale: 2,2,2
  default:big_big_apple:
    material: apple
    custom-model-data: 1001
    model:
      type: minecraft:model
      path: "namespace:item/custom/big_big_apple"
      generation:
        # inherits the custom big apple model above
        parent: "minecraft:item/custom/big_apple"
        # now it would be very big both in hand and in gui
        display:
          firstperson_righthand:
            scale: 4,4,4
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fto4U9vBexccrrEoONGwg%2Fimage.png?alt=media&#x26;token=eabaf9a9-a8d6-45a9-bf90-b15ed1b917ad" alt=""><figcaption><p>big apple</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FdFCvFSb48gXkn8JCLPCF%2Fimage.png?alt=media&#x26;token=34b110c6-34e5-40d3-9772-fec90a2d0903" alt=""><figcaption><p>big big apple</p></figcaption></figure>

### textures

> Holds the textures of the model, in form of a [resource location](https://minecraft.wiki/w/Tutorial:Models#File_path) or can be another texture variable.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/7Av9LqhtMmYcb2pFXS9X/image.png" alt=""><figcaption></figcaption></figure>

If we intend to generate a block based on this model, the parameters for `parent` and `textures` should be specified as follows:

```yaml
generation:
  parent: "minecraft:block/cube_all"
  textures:
    "particle": "minecraft:block/custom/block_particle"
    "down": "minecraft:block/custom/block_down"
    "up": "minecraft:block/custom/block_up"
    "north": "minecraft:block/custom/block_north"
    "east": "minecraft:block/custom/block_east"
    "south": "minecraft:block/custom/block_south"
    "west": "minecraft:block/custom/block_west"
```

```yaml
items#test:
  default:big_apple:
    material: apple
    custom-model-data: 1000
    model:
      type: minecraft:model
      path: "minecraft:item/custom/big_apple"
      generation:
        parent: "minecraft:item/apple"
        textures:
          # replace the apple's texture with an axe
          layer0: minecraft:item/custom/topaz_axe 
        display:
          gui:
            scale: 2,2,2
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FUwVKVhbAtn1FNPStu82a%2Fimage.png?alt=media&#x26;token=89a11095-54ab-4f07-82fe-b36c61c30bf0" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
The key-value pairs under the `textures` section are determined by the parent model.

For example:

* `minecraft:item/apple` inherits from `minecraft:item/generated`.
* `layer0` is one of the `textures` parameters defined in `minecraft:item/generated`.
* This is why you can override this texture in the child model (`apple`).

**You can view all available Minecraft models and their textures on this** [**website**](https://misode.github.io/assets/model/)

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FsYTMHVsoTPN2uOsYs9hZ%2Fimage.png?alt=media\&token=e4496f8f-6daa-4da2-a407-89a9444807d0)![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F0s9Mqk0BpqkZj48WC3mQ%2Fimage.png?alt=media\&token=15b290f8-f945-4384-944a-fb27ec0de698)
{% endhint %}

### gui-light

> Can be `"front"` or `"side"`. If set to `"side"`, the model is rendered like a block. If set to `"front"`, model is shaded like a flat item. Defaults to `"side"`.

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FSHZtI9R1FFXQulE7pVmM%2Fimage.png?alt=media&#x26;token=5d351073-450f-48cb-945a-a9e72401bfb3" alt=""><figcaption><p>left: front  right: side</p></figcaption></figure>

### display

> Holds the different places where item models are displayed.
>
> * rotation: Specifies the rotation of the model according to the scheme `[x, y, z]`.
> * translation: Specifies the position of the model according to the scheme `[x, y, z]`. If the value is greater than 80, it is displayed as 80. If the value is less than -80, it is displayed as -80.
> * scale: Specifies the scale of the model according to the scheme `[x, y, z]`. If the value is greater than 4, it is displayed as 4.

Available values: `thirdperson_righthand`, `thirdperson_lefthand`, `firstperson_righthand`, `firstperson_lefthand`, `gui`, `head`, `ground`, or `fixed`.&#x20;

Let's continue with this **big big apple** example. You may notice that when held in the right hand, its rotation behaves incorrectly. This happens because we overrode its parent model's `display.firstperson_righthand` settings. Now, let's fix it!

```yaml
generation:
  parent: "minecraft:item/custom/big_apple"
  display:
    firstperson_righthand:
      scale: 4,4,4
      rotation: 0,-90,25
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FDTJGNCHXveVe5Rb4Z9PQ%2Fimage.png?alt=media&#x26;token=f6d88f18-0cad-429f-ad63-eb5808c06a42" alt=""><figcaption></figcaption></figure>
