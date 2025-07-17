---
description: https://minecraft.wiki/w/Items_model_definition#range_paid
---

# :satellite_atirna: 射程分配

> 基于数字属性渲染项目模型。 将选择临界值小于或等于属性值的最后条目。

{% hint style="info" %}
当使用 "minecraft:range\_调度"时，您需要指定数字`property`类型。 `scale` 代表着将属性值与`输入`表示不同数值下的模型的因素。 和 `fallback` 表示项目模型对象，如果没有找到有效的条目。 它是可选的，但如果未指定，它将会呈现一个“丢失”错误模型。
{% endhint %}

```yaml
items:
  default:range_dispatch_item:
    model:
      type: "minecraft:range_dispatch"
      property: "minecraft:crossbow/pull"
      entries:
        - model:
            type: minecraft:model
            path: "minecraft:item/custom/model_1"
          threshold: 0.58
        - model:
            type: minecraft:model
            path: "minecraft:item/custom/model_2"
          threshold: 1.0
      fallback:
        type: minecraft:model
        path: "minecraft:item/custom/model_3"
```

## 可用属性

检查[https://minecraft.wiki/w/Items\_model\_definition#range\_调度](https://minecraft.wiki/w/Items_model_definition#range_dispatch)对每个参数的使用

### Minecraft：**crossbow/pull**

> 返回跨弓特定使用时间。

### minecraft:**bundle/fulness**

> 如果不存在，返回 `minecraft:bundle_contents` 组件或 `0` 的重量。

### Minecraft：**冷却**

> 返回物品的剩余冷却状态，缩放在 `0.0` 到 `1.0` 之间。

### minecraft：**compass**

> 以x-z平面返回持有者位置和目标之间的 `0.0` 缩放到`1.0` 的角度。 如果目标无效(不存在，其他尺寸或太接近持有者位置)，将会返回随机值。

```yaml
类型：“minecraft:range_paych”
属性：“minecraft:compass”
目标：生成
wob: true
```

### Minecraft：**计数**

> 返回堆栈大小。

```yaml
类型：“minecraft:range_paych”
属性：“minecraft:count”
normalize: true
```

### minecraft：**damage**

> 如果不存在，返回 `minecraft:damage` 组件或 `0` 的值。

```yaml
类型：“minecraft:range_paych”
属性：“minecraft:damage”
normalize: true
```

### Minecraft：**时间**

> 返回游戏中时间的值, 缩放的 Betewen `0.0` 到 \`1.0'。

```yaml
类型：“minecraft:range_appailch”
属性：“minecraft:time”
来源：daytime
wob: true
```

### minecraft:**使用\_cycle**

> 返回剩余的使用条目模块“周期”。

```yaml
类型：“minecraft:range_appoch”
属性 "minecraft:use_cycle"
周期： 1.0
```

### minecraft:**使用\_duration**

> 返回条目使用条目。

```yaml
类型：“minecraft:range_appoch”
属性：“minecraft:use_duration”
剩余：false
```

### minecraft:**custom\_model\_data**

> 从 `minecraft:custom_model_data` 组件中的 `floats` 列表返回值，如果不存在，则返回 `0` 。

```yaml
类型：“minecraft:range_appoch”
属性：“minecraft:custom_model_data”
索引: 0
```
