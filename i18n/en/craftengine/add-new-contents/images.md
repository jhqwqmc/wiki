---
description: This page mainly explains how to add new images to your server.
---

# 🖼️ Images

{% hint style="warning" %}
Please read Minecraft Wiki firstly if you don't know how bitmap images work\
[https://minecraft.wiki/w/Font#Bitmap\_provider](https://minecraft.wiki/w/Font#Bitmap_provider)
{% endhint %}

## Introduction

At its core, Minecraft's "image display" is essentially a clever character substitution mechanism. The game renders textures by mapping specific Unicode characters to image files through its font system.&#x20;

**Font Ecosystem Essentials**

1. **Multiple Font Sets**\
   Minecraft natively supports various fonts (e.g., `minecraft:default`, `minecraft:uniform`) that can be extended or modified.
2. **Custom Font Creation**\
   Users can create personalized fonts by defining:

```
assets/[namespace]/font/[font_name].json
```

* `namespace`: Your unique identifier (e.g., `my_namespace`)
* `font_name`: Custom font designation (e.g., `magic_symbols`)

{% hint style="info" %}
MiniMessage format: `<font:namespace:font_name>Text</font>`&#x20;

MineDown format `[Text](font=namespace:font_name)`
{% endhint %}

**How It Works**

* When using `\uXXXX` Unicode escape sequences:
  1. The game checks the font used in the text component
  2. Maps characters to corresponding textures
  3. Renders textures at specified character positions

{% hint style="success" %}
**Question:**

Will the characters in my country be affected?\
Can my players illegally use these images through chat, anvils, or other means?

**Answer:** \
Certainly not, unless you use `minecraft:default` (Minecraft's default font). Please avoid using `minecraft:default`, as it is an unsupported behavior.
{% endhint %}

## Single Character Bitmap

```yaml
images:
  internal:item_browser:
    height: 140
    ascent: 18
    font: minecraft:internal
    file: minecraft:font/gui/custom/item_browser.png
    char: '\ub000'
```

{% hint style="danger" %}
The `height` value must always be greater than or equal to the `ascent` value. This is a strict requirement enforced by Minecraft, and you must adhere to this rule.
{% endhint %}

## Multiple Characters Bitmap

```yaml
images:
  default:icons:
    height: 10
    ascent: 9
    font: minecraft:icons
    file: minecraft:font/image/icons.png
    chars:
     - '\ub000\ub001'
     - '\ub002\ub003'
```

{% hint style="info" %}
If you'd like to learn how to use PlaceholderAPI to incorporate these images, please refer to the following page: [placeholderapi](../compatibility/placeholderapi "mention").

If you're interested in learning how to use these images within the CraftEngine plugin, please consult the detailed instructions available at: [text-format](../text-format "mention").
{% endhint %}

## Preview the Image In Game

You can use a very simple command to preview the effect of the image. All you need to do is replace `\ub000` with the character corresponding to your image.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/X9GiJ4F4kOgPxWRoKenJ/image.png" alt=""><figcaption></figcaption></figure>

```
/tellraw @p {"text":"\ub000","font":"minecraft:icons"}
```

## Compatibility with Other Plugins

There are two ways to use images in other plugins:

1. Use a plugin that supports **MiniMessage/MineDown** and **PlaceholderAPI**. In this case, you just need to use the corresponding placeholder. Please refer to this article to see how to use placeholder. [placeholderapi](../compatibility/placeholderapi "mention")
2. Use a tag in the format of `<image:namespace:id>` `<image:namespace:id:row:column>` `<shift:-20>` just like what we do in [text-format](../text-format "mention"). CraftEngine will replace these tags with characters of the corresponding font at the **packet level**.

{% hint style="info" %}
You can find the following configuration in config.yml, which controls the scope in which these tags are effective.

```yaml
image:
  # By intercepting packets, you are allowed to use <image:...> <shift:...> in other plugins
  intercept-packets:
    system-chat: true
    tab-list: true
    actionbar: true
    title: true
    bossbar: true
    container: true
    team: true
    scoreboard: true
    entity-name: false
    text-display: true
```
{% endhint %}
