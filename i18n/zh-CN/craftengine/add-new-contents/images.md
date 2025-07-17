---
description: 此页主要解释了如何向您的服务器添加新图像。
---

# 🖼️ Images

{% hint style="warning" %}
Please read Minecraft Wiki firstly if you don't know how bitmap images work\
[https://minecraft.wiki/w/Font#Bitmap\_provider](https://minecraft.wiki/w/Font#Bitmap_provider)
{% endhint %}

## 一. 导言

在其核心上，Minecraft的“图像展示”基本上是一种聪明的字符替代机制。 游戏通过映射特定的 Unicode 字符到通过其字体系统映射文件来渲染纹理。&#x20;

**字体生态系统Essentials**

1. **多个字体集**\
  Minecraft本质上支持可以扩展或修改的各种字体(如：`minecraft:default`、`minecraft:unique`)。
2. **自定义字体创建**
  用户可以通过定义来创建个性化字体：

```
assets/[namespace]/font/[font_name].json
```

- `namespace`：您独特的标识符(例如，`my_namespace`)
- `font_name`: 自定义字体名称(如：`magic_symbols`)

{% hint style="info" %}
MiniMessage 格式：\`<font:namespace:font_name>文本</font>&#x20;

MineDown format `[Text](font=namespace:font_name)`
{% endhint %}

**它如何工作**

- 使用 `\uXXXX` Unicode 逃避序列时：
  1. 游戏检查文本组件中使用的字体
  2. 映射字符到对应的纹理
  3. 在指定字符位置呈现纹理

{% hint style="success" %}
**问题:**

我的国家中的角色会受到影响吗？\
我的玩家能否通过聊天室、魔鬼或其他方式非法使用这些图像吗？

**Answer:** \
Certainly not, unless you use `minecraft:default` (Minecraft's default font). 请避免使用 `minecraft:default`，因为它是不支持的行为。
{% endhint %}

## 单个字符位图

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
"height" 值必须总是大于或等于 "ascent" 值。 这是Minecraft执行的严格要求，你必须遵守这一规则。
{% endhint %}

## 多个字符位图

```yaml
图像:
  默认:icons:
    高度: 10
    ascent: 9
    字体: minecraft:icons
    文件: minecraft:font/image/icons。 ng
    字符:
     - '\ub000\ub001'
     - '\ub002\ub003
```

{% hint style="info" %}
如果您想学习如何使用占位符API来包含这些图像，请参阅以下页面： [placeholderapi](../compatibility/placeholderapi "提及")。

如果您有兴趣学习如何在 CraftEngine 插件中使用这些图像，请参阅以下网站的详细说明: [text-format](../text-format "提及")。
{% endhint %}

## 预览游戏中的图像

您可以使用非常简单的命令来预览图像的效果。 你需要做的只是用与你的图像相对应的字符替换`\ub000`。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/X9GiJ4F4kOgPxWRoKenJ/image.png" alt=""><figcaption></figcaption></figure>

```
/tellraw @p {"text":"\ub000","font":"minecraft:icons"}
```

## 与其他插件兼容性

在其他插件中有两种方式可以使用图像：

1. 使用一个支持 **MiniMessage/MineDown** 和 **PlaceholderAPI** 的插件。 在此情况下，您只需要使用相应的占位符。 请参阅本条以查看如何使用占位符。 [placeholderapi](../compatibility/placeholderapi "提及")
2. 使用一个标签，格式为`<image:namespace:id>`<image:namespace:id:row:column>`<shift:-20>`，就像我们在 [text-format]中所做的一样。(../text-format "mention")。 CraftEngine 将在**数据包级别**用相应字体的字符替换这些标签。

{% hint style="info" %}
您可以在 config.yml 中找到以下配置，它控制这些标签的有效范围。

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
