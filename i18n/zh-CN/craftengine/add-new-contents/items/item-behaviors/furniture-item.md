# 🪑 家具项目

家具是一件附有家具的物品。 您可以在这里配置相应的家具ID。 或甚至整个家具配置(请注意这样做会造成在项目装载过程中记录的家具花费时间)。 当您将此行为绑定到某个项目时，您可以通过右键放置它。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/SYOQXH6ZY0VcGYGZLdgN/image.png" alt=""><figcaption></figcaption></figure>

```yaml
项目:
  默认: 基准:
    行为:
      类型: gabourure_item
      家具: 默认:bench
```

这是配置家具的最简单方法，但它假定您已经配置了一件家具。 如果您不确定如何配置一件家具，请参阅 [furniture](../../entities/furniture "提及")。

{% hint style="success" %}
如果您发现单独配置它们太麻烦，您可以选择一起配置。 下面是一个例子。 “家具”下的格式遵循标准家具配置格式。

```yaml
项目：
  默认：基准：
    材料：
    定制模型数据：2000
    数据：
      显示名称：“<！ >基准”
    型号:
      型号: "minecraft:model"
      路径: "minecraft:item/custom/bey"
    行为:
      型号: gabourure_item
      abourment:
        settings:
          item: default:bench
          sounds:
            bre: minecraft:block. ambo_wood.bret
            位置：minecraft:block.bambo_wood。 lace
        place :
          Framework :
            rules :
              rotation: EIGHTT
              alignment: CENTER
            element:
              - item: default:bench
                display-transform: NOE
                bullet: FIXED
                position: 0. 0,0
                翻译：0,0 ,0
            点击箱：
              - 位置：0,，
                宽度：1
                高度：1
                交互式：真正
                座位：
                  - 0 ,-0。 0
              - 位置： 1,0,
                宽度：1
                高度：1
                交互式：真正
                座位：
                  - 1 ,-0。 0
        观看:
          模板: lot_table:normal
          参数:
            item: default:bench
```

{% endhint %}
