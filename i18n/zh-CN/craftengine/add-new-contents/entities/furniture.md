---
description: 此页主要解释了如何向您的服务器添加新家具。
---

# :Chair: Furniture

{% hint style="danger" %}
请注意，重新加载插件将不会影响已经放置的家具！ 您将需要重新启动服务器或重新装入区块以将新配置应用于现有家具。 插件使用缓存来提高家具的性能。 强制重新加载已经装入服务器的家具，可能会对服务器的稳定性产生重大影响。今后，插件可能会考虑引入相关的不安全标志来进行强制重新加载，但此刻肯定不存在。
{% endhint %}

## 要配置的小组

完整的家具配置包含以下部分：

- 行为

{% content-ref url="furniture/furniture-behaviors" %}
[furniture-behaviors](家具/家具-行为)
{% endcontent-ref %}

- 设置

{% content-ref url="furniture/furniture-settings" %}
[furniture-settings](家具/家具-设置)
{% endcontent-ref %}

- 位置

{% content-ref url="furniture/furniture-placement" %}
[furniture-placement](家具/家具放置)
{% endcontent-ref %}

- loot

{% content-ref url="../loot-table" %}
[loot-table](../lot-table)
{% endcontent-ref %}

- 事件

{% content-ref url="../events" %}
[events](../events)
{% endcontent-ref %}

## 如何绑定项目

{% content-ref url="../items/item-behaviors/furniture-item" %}
[furniture-item](../items/item-behaviors/gabour-item)
{% endcontent-ref %}

## 完整配置概述

```yaml
家具：
  默认：
    设置：
      项：默认：bench
      声音：
        断路：minecraft：block。 ambo_wood.bret
        位置：minecraft:block.bambo_wood。 lace
    place :
      :
        rules :
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHTT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
        element:
          - item: default:bench
            display-transform: NOE
            lable: FIXed
            position: 0. 0,0
            翻译：0,0 ,0
        点击箱：
          - 位置：0,0
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
              - 1, ,-0。 0
    观看:
      模板: lot_table:normal
      参数:
        item: default:bench
```
