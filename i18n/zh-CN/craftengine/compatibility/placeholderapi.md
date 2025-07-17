# :P_按钮：占位符API

## %image\_%

`image`占位符用于返回原始的 Unicode 字符及其相关字体以反映给定的 ID。

{% hint style="warning" %}
“row”和“column”都是可选的，但当您使用其中一个时，它们必须同时使用。
{% endhint %}

### %image\_mm\_namespace:id:\[row]:\[column]%

返回一个 `minimessage` 格式的图像。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SoNyzs9VyYKmXS6gbzQD/image.png" alt=""><figcaption></figcaption></figure>

### %image\_md\_namespace:id:\[row]:\[column]%

返回一个 `minedown` 格式的图像。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SWKg5BjsPNE3WVBfnMB6/image.png" alt=""><figcaption></figcaption></figure>

### %image\_raw\_namespace:id:\[row][column]%

返回原始图像字符。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/9WCfoMnR1xOkbdActj5Q/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**为什么占位符不适合某些插件？**

首先，你必须确保负责解析变量的插件支持`MiniMessage`格式或`MineDown`格式。 否则，字体无法适当应用于文本，导致图像无法显示。

如果插件不支持它，肯定要请其开发人员添加支持，或找到支持自定义字体的其他插件。 `&`的时代已经过去了很长时间；请不要在Minecraft中被卡住。 [images](../add-new-contents/images "提及")

_目前市场上仍然有大量使用 Bukkit API 来创建GUI，这是一种可怕的做法。 即使他们声称支持 MiniMessage 格式，他们仍然使用旧颜色处理颜色。 这确实是一种可耻的行为！_
{% endhint %}

{% hint style="danger" %}
如果没有其他方式要求插件添加字体支持 您可以配置 `image` 以使用 `minecraft:default` 字体(因为这是默认字体) 如果没有指定特定的文本字体，它将被使用)。&#x20;

**使用 minecraft:default 始终是最坏的解决方案。 除非绝对有必要，请不要使用它。 也许你可以在下面的绿色提示中考虑解决方案？**
{% endhint %}

{% hint style="success" %}
**您是否尝试过它？**

CraftEngine 可以修改不支持**包层级字体**的插件发送的文本组件。 Read this page for more: [#compatibility-with-other-plugins](../../add-new-contents/images#compatibility-with-other-plugins "mention")
{% endhint %}

## %shift\_%

`shift`占位符用于获取偏移的字符，通常用于调整菜单标题和类似操作。

### %shift\_mm\_value%

返回"最小化"格式的值班字符。

### %shift\_md\_value%

返回`minedown`格式的转换字符。

### %shift\_raw\_value%

返回原始偏移字符

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/pErqfau4KpSshwI7fAeD/image.png" alt=""><figcaption><p>带转移</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/wYlukrOaIpR8uLpkXi6E/image.png" alt=""><figcaption><p>没有转移</p></figcaption></figure>
