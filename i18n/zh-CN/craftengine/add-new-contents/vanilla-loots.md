---
description: 这个页面主要解释如何为原版
---

# 🗃️ Vanilla Loots

## 一. 导言

Minecraft的原生战利品系统已经相当健全， 但它有一个明显的缺陷：它不能包含某些特定插件元素，如占位符检查、权限和其他高级功能。 此外，配置原版数据包是一个繁琐的过程，使默认的掠夺表的覆盖面更加困难。 要解决这个问题，插件为原版掠夺系统提供了覆盖功能。 您可以引用下面的示例来快速开始。 在下面的文本中，"..."表示抢劫配置。 最好是首先阅读 [loot-table](loot-table "提及") 以了解如何有效地配置掠夺。

## 屏蔽护腿

```yaml
香草外观:
  minecraft:grass_lot:
    type: block
    target: "minecraft:grass"
    # 是否覆盖原版图.
    覆盖: false
    look:
...
```

```yaml
可anilla-looks:
  minecraft:grass_lot:
    type: block
    type:
      - minecraft:wheat[age=0] # 使用一个详细的状态
      - minecraft:wheat[age=1]
    覆盖: false
    look:
...
```

## 实体贷款机制

```yaml
香草外观:
  minecraft:sheep_look:
    type: entity
    target: "minecraft:sheep"
    # 是否覆盖原版图
    覆盖: false
    look:
...
```
