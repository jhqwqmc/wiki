---
description: https://minecraft.wiki/w/Items_model_definition#special
---

# 👻 Special

> 渲染一个特殊模型。

{% hint style="info" %}
当使用 "minecraft:special," 时，您需要指定 "speical mode" 类型。 `path`参数是基础模型渲染所必需的。
{% endhint %}

```yaml
默认:gui_head_size_1:
  模型:
    类型: minecraft:special
    路径: minecraft:item/custom/gui_head_size_1
    模型:
      类型: minecraft:head
      kind: player
```

## 可用的特殊模型类型

检查[https://minecraft.wiki/w/Items\_model\_definition#special](https://minecraft.wiki/w/Items_model_definition#special) 每个参数的用法

### Minecraft:trident

> 渲染试用。

### 矿工:管道

> 渲染管道。

### 矿工:盾

> 渲染盾牌。 使用 `minecraft:banner_patterns` 组件中的模式和 `minecraft:base_color` 组件中的颜色。

### minecraft:decorated\_pot

> 渲染一个装饰药水 使用 `minecraft:pot_decorations` 组件中的值。

### Minecraft:hanging\_sign

> 渲染悬挂签名。

```yaml
model:
  类型: "minecraft:hanging_sign"
  woodtype: "oak"
  text: ...
```

### minecraft:standing\_sign

> 呈现了一个长期的标志。

```yaml
model:
  类型: "minecraft:standing_sign"
  woodtype: "oak"
  text: ...
```

### 矿工:头

> 渲染头部。 \[在适用情况下使用 `minecraft:profile`组件的配置文件。 (1.21.4-1.21.5)]

```yaml
model:
  类型: "minecraft:head"
  类型: 玩家
  纹理: ...
  动画: 0.0
```

### minecraft:player\_head (1.21.6+)

> 渲染头部。 在适用情况下使用 `minecraft:profile`组件的配置文件。

```yaml
模型：
  类型：“minecraft:player_head”
```

### 矿工:箱子

> 渲染单个箱子。

```yaml
型号:
  类型: "minecraft:chest"
  openness: 0.0
  纹理：
```

### minecraft:**shulker\_box**

> 渲染潜影箱。

```yaml
型号:
  类型: "minecraft:shulker_box"
  openness: 0.0
  方向: up
  纹理: ...
```

### minecraft：**bed**

> 渲染整张床。

```yaml
模型:
  类型: "minecraft:bed"
  纹理: ...
```

### minecraft：**banner**

> 从 `minecraft:banner_patterns` 组件渲染图案横幅。

```yaml
模型:
  类型: "minecraft:bed"
  颜色: 白色
```

