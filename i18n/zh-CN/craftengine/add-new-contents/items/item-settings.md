---
description: >-
  与数据不同，设置中的内容涉及插件处理的特殊机制。
---

# ⚙️ 项目设置

## 燃料时间

确定可以烧毁多少只ticks

```yaml
燃料时间：100
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ETo97tqrp6GsxMMc4zOX/image.png" alt=""><figcaption></figcaption></figure>

## 标签

见 [recipes](../recipes "提及")

```yaml
标签：
  - "default:palm_logs"
  - "minecraft:logs"
  - "minecraft:logs_that_burn"
```

## 设备

将设备应用于该项目。 见 [item-equipment](item-equipment "提及")

```yaml
equipment:
  #
  # Required Argument
  #
  asset-id: default:topaz
  
  # 
  # Optional Argument. Defaults to the global client-bound-model option in config.yml
  #
  client-bound-model: true
  
  #
  # Optional Arguments on 1.21.2 and above
  # Option 'slot' is required for these options to work
  #
  slot: head # head / chest / legs / feet / body (animal armor) / saddle 
  # The resource location of the overlay texture to use when equipped. The directory this refers to is assets/<namespace>/textures/<id>.
  camera-overlay: "namespace:id"
  # Whether the item can be dispensed by using a dispenser.
  dispensable: true
  # Whether this item is damaged when the wearing entity is damaged.
  damage-on-hurt: true
  # Whether the item can be equipped into the relevant slot by right-clicking.
  swappable: true
  # >= 1.21.5
  # Whether this item can be equipped onto a target mob by pressing use on it (as long as this item can be equipped on the target at all)
  equip-on-interact: true
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FDrJjArxUMGqZdTcFNlbB%2Fimage.png?alt=media&#x26;token=b507bcfd-b23f-42d5-a610-51e45544b465" alt=""><figcaption></figcaption></figure>

## 可修复

决定是否可以通过合成表/铁修理物品 (默认：true)

```yaml
修复：正确
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FsFmbIZ3gKhZRd0i2aJ8N%2Fimage.png?alt=media&#x26;token=105464c8-4910-4b0e-9e68-a3f968468e99" alt=""><figcaption></figcaption></figure>

## 相机修理物品

确定某个项目在修复时的耐久程度

```yaml
anvil-修理项目:
  - 目标: "#topaz_tools"
    数量: 20 # 还原固定耐久性
  - 目标:
      - "minecraft:iron_pickaxe"
      - "minecraft:shears"
    %: 0. 5 # 0.25 = 25%，恢复总耐久性 n%
```

## 可重命名的

确定该项是否可以重命名为anvil。 (默认：true)

```yaml
可重命名：false
```

## 抛射物

根据项目创建一个自定义抛射物体。 它支持 `trident`, `arrow`, `snowball` 等更多。

```yaml
projectile:
  item: default:topaz_trident # the item to display
  translation: 0,0,0
  rotation: 1,1,1,1
  display-transform: NONE
  scale: 0.5
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FMXNMpGU2nEZuaIZZdXje%2Fimage.png?alt=media&#x26;token=a8d196fb-e093-4c29-a796-83ad28ca3cac" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
您的模型直接影响配置文件中的 `rotation` 参数。

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F6VmwwP0bhtIijZEsXG2e%2Fimage.png?alt=media\&token=df1e2bd8-d608-4c19-9cf5-dcd2cc534505)![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FL7y7eP6xIqwRXrLKlqcb%2Fimage.png?alt=media\&token=df7f1d90-dffd-4db4-b3e9-c86195564187)\
No matter which modeling method you use, the most important thing is to make the sharp part of the trident in the position shown in the picture above to ensure the best hitting point.
{% endhint %}

## 可染料

Decides if the item([leather armor](https://minecraft.wiki/w/Leather_armor) or [wolf armor](https://minecraft.wiki/w/Wolf_armor)) can be dyed in crafting tables. (默认：true)

```yaml
dyeable: true
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FKPAQnbm7LyeQtQ6UHHyp%2Fimage.png?alt=media&#x26;token=bbe9e687-6486-451f-8762-32849b4c0e34" alt=""><figcaption></figcaption></figure>

## 食物：

```yaml
食物:
  营养: 5 # 0~20, 整数
  饱和度: 3.5 # 0~10, float
```

{% hint style="warning" %}
Better to use `food` components on a 1.20.5+ server
{% endhint %}

## 消费替换

在消费后设置返回项。 例如，在玩家喝水瓶后，将返回空瓶。 (默认：空)

```yaml
消费替换：矿工:苹果
```

## 余下的手工物品

选择在制造配方完成时是否返回其他项目。 此选项仅适用于最大堆栈大小为1的自定义项目

```yaml
余下的手工物品：桶子
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FG5Gx2xMlH4SspQC1P66y%2Fimage.png?alt=media&#x26;token=5a6e6d26-8730-4f07-ae94-dabb0fc3b520" alt=""><figcaption></figcaption></figure>

## 无敌的

```yaml
无敌状态:
  - 岩浆.
  - fire_tick
  - block_sepred # respawn 锚点
  - entity_deprest # creeper, tnt
  - 闪烁
  - 联系 # cactus
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FHYC5C0eMeqoVtNWk2QbI%2Fimage.png?alt=media&#x26;token=15fdae30-932b-4ab3-9a00-a81102e5dccf" alt=""><figcaption></figcaption></figure>

## 附魔法

此选项允许您屏蔽某些项目在附魔表中使用。 提示：将其设为“true”将无法使不可更改的项目成为魔法附魔。 (默认：true)

```yaml
附魔：false
```

## compost概率

这个设置控制它对堆肥成功的可能性(默认：0.5)

```yaml
composability: 0.5
```

## 尊敬的可维修组件

如果在 "修理" 组件中列出的项目能够修复这个项目, 这种控制将被控制。 (默认：false)

```yaml
尊重可修复组件：false
```
