# 🅿️ PlaceholderAPI

## %image\_%

The `image` placeholder is used to return the original Unicode characters and their associated font for the image corresponding to a given ID.

{% hint style="warning" %}
Both "row" and "column" are optional, but when you use one of them, they must be used in pairs.
{% endhint %}

### %image\_mm\_namespace:id:\[row]:\[column]%

Return an image in `minimessage` format.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SoNyzs9VyYKmXS6gbzQD/image.png" alt=""><figcaption></figcaption></figure>

### %image\_md\_namespace:id:\[row]:\[column]%

Return an image in `minedown` format.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SWKg5BjsPNE3WVBfnMB6/image.png" alt=""><figcaption></figcaption></figure>

### %image\_raw\_namespace:id:\[row]:\[column]%

Return an the raw image character.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/9WCfoMnR1xOkbdActj5Q/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Why placeholder doesn't work for some plugins?**

First, you must ensure that the plugin responsible for parsing variables supports either the `MiniMessage` format or the `MineDown` format. Otherwise, the font cannot be properly applied to the text, resulting in the image not being displayed.

If the plugin does not support it, be sure to ask their developers to add support, or find another plugin that supports custom fonts. The era of `&` is long over; please don't stay stuck in the Minecraft 1.15 days.re. [images](../add-new-contents/images "mention")

_Currently, there are still a large number of plugins on the market that use the Bukkit API to create GUIs, which is a terrible practice. Even when they claim to support the MiniMessage format, they still process colors using the legacy colors. This is truly a shameful behavior!_
{% endhint %}

{% hint style="danger" %}
If there is no other way to ask the plugin to add font support, you can configure the `image` to use the `minecraft:default` font (since this is the default font, it will be used if no specific text font is specified).&#x20;

**Using minecraft:default is always the worst solution. Please do not use it unless it is absolutely necessary. Perhaps you can consider the solution in the green tip below?**
{% endhint %}

{% hint style="success" %}
**Have you tried it?**

CraftEngine can modify text components sent by plugins that do not support fonts at **packet level**. Read this page for more: [#compatibility-with-other-plugins](../../add-new-contents/images#compatibility-with-other-plugins "mention")
{% endhint %}

## %shift\_%

The `shift` placeholder is used to obtain the character for offset, typically employed for aligning menu titles and similar operations.

### %shift\_mm\_value%

Return shift characters in `minimessage` format.

### %shift\_md\_value%

Return shift characters in `minedown` format.

### %shift\_raw\_value%

Return raw shift characters

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/pErqfau4KpSshwI7fAeD/image.png" alt=""><figcaption><p>with shift</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/wYlukrOaIpR8uLpkXi6E/image.png" alt=""><figcaption><p>without shift</p></figcaption></figure>
