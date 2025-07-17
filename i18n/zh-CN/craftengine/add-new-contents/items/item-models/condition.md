---
description: https://minecraft.wiki/w/Items_model_definition#condition。
---

# :balanc_scale : 条件

{% hint style="info" %}
在这个配置中，当您使用"minecraft:condition"时，您需要指定条件类型，它是下面提到的“属性”。 “false”和“true”分别表示在不同条件下显示不同的模型。
{% endhint %}

```yaml
items:
  default:condition_item:
    model:
      type: "minecraft:condition"
      property: "minecraft:using_item"
      on-false:
        type: "minecraft:model"
        path: "minecraft:item/custom/model_false"
      on-true:
        type: "minecraft:model"
        path: "minecraft:item/custom/model_true"
```

## 可用属性

检查[https://minecraft.wiki/w/Items\_model\_definition#condition](https://minecraft.wiki/w/Items_model_definition#condition)对每个参数的使用

### 矿工:损坏

> 返回`true`，如果该物品是可损坏的并且在中断前只剩下一个用途。

### 矿工:carried

> 返回`true`，如果项目在图形界面的位置之间传输。

### minecraft：**损坏**

> 返回`true`，如果项目是可损坏的并且至少已经被使用过一次。

### minecraft:**extended\_view**

> 如果玩家按住 shift 键要求扩展详情，返回 `true`。 只有当项目在界面中显示时才能正常工作。 注意：不是按键绑定，不能退回。

### minecraft:**fishing\_rod/cast**

> 如果目前使用过的钓鱼棒附着，则返回 `true`。

### Minecraft：**选择**

> 如果项目在热键上被选中，返回 `true` 。

### Minecraft：**使用\_item**

> 如果玩家正在使用此项目，返回 `true` 。

### minecraft：**view\_entity**

> - 当不投机时，如果上下文实体是本地玩家实体，即客户端控制的实体则返回 `true`。
> - 当投机时，如果上下文实体是 _specated_ 实体则返回 `true`。
> - 如果上下文实体不存在，将返回 \`false'。

### minecraft:**bundle/has\_selected\_item**

> 返回 `true` ，如果bundle 是"open"，也就是它选择了可见于GUI中的项目。

### minecraft:**组件 (1.21.5+)**

> 使用组件[预测子项目](https://minecraft.wiki/w/Item_sub-predicate) 匹配项目组件。

### minecraft:has\_**组件**

> 如果给定的组件存在于项目上，返回 `true` 。

```yaml
输入: "minecraft:condition"
属性: "minecraft:has_component"
组件: minecraft:enchantes
忽略默认值: false
```

### minecraft：**keybind\_down**

> 如果密钥绑定当前激活，返回 `true` 。

```yaml
类型：“minecraft:condition”
属性 "minecraft:keybind_down"
keybind: key.let
```

### minecraft:**custom\_model\_data**

> 从 `minecraft:custom_model_data` 组件中的 `flags` 列表返回值。

```yaml
类型：“minecraft:condition”
属性：“minecraft:custom_model_data”
索引: 0
```
