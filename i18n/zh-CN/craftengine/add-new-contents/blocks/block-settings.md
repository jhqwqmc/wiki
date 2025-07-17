# ⚙️ Block 设置

## 硬度

确定破坏此方块需要多长时间(默认：2.0)

```yaml
难度：0.5
```

## 抗性

确定方块在爆炸中生存的概率(默认：2.0)

```yaml
抗性： 0.5
```

## 随机刻录

确定方块状态是否接受随机的条目，这与某些方块行为相关，例如叶子。 (默认：false)

```yaml
随机打勾：true
```

## push-reaction&#x20;

确定方块如何对手推送作出反应。 请注意，由于客户端视觉同步问题，某些反应可能与某些块类型不很有效。 这个问题将在今后的版本中解决。 (默认：NORMAL)

- NORMAL 手枪可以正常推送和拉此块。
- 由手枪推送的破坏力模块立即被摧毁。
- BloCK 手枪不能移动此块。
- IGNORE 看起来像PUSH\_only，但可以粘贴到粘贴块
- PUSH\_仅限屏幕方块可以被手枪推送，但不能被撤销。 不要粘贴到粘性块。

```yaml
推力反应：NORMAL
```

## 地图颜色

确定方块在地图上显示的颜色。 可用颜色可以在 [https://minecraft.wiki/w/Map\_item\_格式](https://minecraft.wiki/w/Map_item_format) 上找到(默认: 0)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/8WeafQSqNMDWGWeLd1NI/image.png" alt=""><figcaption></figcaption></figure>

```yaml
地图颜色： 36
```

## 可燃烧的

确定此方块是否可以被环境触发(默认：false)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/yfgOaG8u4n8BGK600ymB/image.png" alt=""><figcaption></figcaption></figure>

```yaml
可烧毁：正确
```

## 火焰扩散几率：

确定方块燃烧的时间。 更长的燃烧时间意味着更容易向周围的方块开火。 (默认：0)

```yaml
火焰扩张机会：100 # 0-100
```

## 燃烧几率：

确定被点燃的概率(默认：0)

```yaml
烧焦几率： 30 # 0-100
```

## 项目

确定此方块对应的项目。 这通常用于在创造性模式中点击获取方块。 (默认：空)

```yaml
项目：默认：xxx_block_item
```

## 可替换

当玩家使用一个方块来与该方块交互时，确定是否要在其原始位置替换方块(默认：false)

```yaml
可替换：false
```

## is-redston-conductor

确定此方块是否是红石信号导体 (默认：开发)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/eneBtRUIfZA3e7IkDj43/image.png" alt=""><figcaption></figcaption></figure>

```yaml
is-redstone-conduct: true
```

## 正在窒息中

确定玩家是否会承受窒息伤害(默认：开发)

```yaml
正在窒息：true
```

## is-阻止视图

是否屏蔽视线。 然而，这个选项对玩家毫无用处，但会影响服务器上的一些实体机制。 (默认：开发)

```yaml
is-view-block: true
```

## 声音

在各种情况下确定方块的声音(默认：空)

- 当玩家跌落在这个方块上时减少
- 当玩家挖这个方块时点击
- 当玩家打破此方块时中断
- 当玩家在这个方块上行走时步进
- 当玩家放置此方块时
- 当区块落在地面时（用于落下区块）
- 当方块落在地上并被破坏时销毁(以落下方块)

```yaml
声音:
  断点: minecraft:block.deepslate.brek
  步骤: minecraft:block.deepslate.step
  位置: minecraft:block.deepslate.place
  hit: minecraft:block.deepslate.hit
  fall: minecraft:block.deepslate.fall
  land: minecraft:block.anvil.land
  销毁: minecraft:block.anvil.destruction
```

{% hint style="info" %}
您可以配置这个配置来精确控制音量和音调

```yaml
声音:
  断点:
    id: minecraft:block.deepslate.brek
    pitch: 0.5
    volume: 0.25
  步: minecraft:block.deepslate.step
```

{% endhint %}

## 需要正确工具

确定滴是否需要正确的工具 (默认：false)

```yaml
需要正确的工具：false
```

## 尊重工具组件

决定 `minecraft:tool` 组件的 `correct_for_drops` 选项是否应作为下面的 `correct-tools` (默认：false)

```yaml
尊重工具组件：false
```

## 正确工具

确定输入此方块所需的正确工具，否则将不会丢弃任何项目 (默认：空)

```yaml
正确的工具：
  - minecraft:wooden_picaxe
  - minecraft:stone_picaxe
  - minecraft:iron_picaxe
  - minecraft:golden_picaxe
  - minecraft:diamond_picaxe
  - minecraft:netherite_picaxe
```

{% hint style="success" %}
如果设置了 `correct-tools`，`require-correct-tools`将是真的
{% endhint %}

## incorrect-tool-dig-speed

如果工具不正确，请降低挖掘速度 (默认：0.3)

```yaml
不正确的工具数字速度：0.3 # 0~1
```

## 标签

标签决定了许多方块的属性。 例如，使用 minecraft:mineable/axe 会使你的方块更快地用斧头开采。 [useful-tags](block-settings/useful-tags "提及") (默认: 空)

```yaml
标签：
  - minecraft:mineable/axe
  - minecraft:logs_that_burn
  - minecraft:log
  - minecraft:completes_find_tree_tuturing
```

## 客户端边界标签

这只适用于原版块

```yaml
客户端边界标签：
  - minecraft:beacon_base_blocks
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fwnpy7kYwGeRAiJbBTdQ3%2Fimage.png?alt=media&#x26;token=79a6c177-14af-4798-8f49-19c4ca688131" alt=""><figcaption></figcaption></figure>

## 乐器

确定注释块在该块上方会播放什么工具。 (默认：harp)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/NhpOFlvMUaWf3xPe3Byo/image.png" alt=""><figcaption></figcaption></figure>

```yaml
仪器：BASEDRUM
```

## 流体状态&#x20;

决定此块状态的流体状态(默认：空)

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FNKagcQZqIIVMxX7odHKU%2Fimage.png?alt=media&#x26;token=0f500b1f-bde4-4e28-84de-9ea9a70a7ba4" alt=""><figcaption></figcaption></figure>

```yaml
液态：水
```

## 支持形状

确定方块提供的支持形状。 默认情况下，自定义块将使用相应的视觉状态的 **support-shape** 。 然而，您可以手动在此指定原版块的 **支持-形状** 。

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fd4ZOrffIv47Tzkw2r2fc%2Fimage.png?alt=media&#x26;token=223541ed-7b5f-451a-b909-038fae926f7e" alt=""><figcaption></figcaption></figure>

```yaml
支持形状: minecraft:stone
```

{% hint style="warning" %}
剩余的方块设置都与灯光系统相关。 CraftEngine已尽可能实现部分光效应，但不影响服务器性能。 客户端灯具的视觉问题是正常的，在大多数情况下，我无法修复。

区块的 **skylight** 完全由 **客户端** 决定，**无法通过从服务器发送数据包来修复** 。 因此，**block-light** 和 **can-occluse** 设置**只影响block-emitted light**, 而不是闪光。
{% endhint %}

## 亮度

确定方块的光强度(默认：0)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/UCgtZHRVaWqDMLV52UAB/image.png" alt=""><figcaption></figcaption></figure>

```yaml
亮度：15
```

## 可闭合

确定此方块是否可以屏蔽光线。 这也决定了方块是否可以将下方方块变成另一种类型。 (例如草\_block -> dirt) (默认：未定义)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/msw2GomMjl3nfMAjxIGd/image.png" alt=""><figcaption><p>八角: true</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/C116bz0ylSfikY93jQYN/image.png" alt=""><figcaption><p>屏蔽：错误</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fx3zMrfKsVSu4lEhU9Iru%2Fimage.png?alt=media&#x26;token=0c9e7da8-8bf0-42e9-883b-79aad4232a4c" alt=""><figcaption><p>屏蔽：错误</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FIQ62BLMGHWhQYfQbbbyZ%2Fimage.png?alt=media&#x26;token=8a5ff1d2-6d91-44b8-9bb6-ef701d1296e5" alt=""><figcaption><p>八角: true</p></figcaption></figure>

```yaml
截图：false
```

## 屏蔽光

确定通过此方块后灯级别减小多少(默认：未定义)

```yaml
Block-light: 0
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FIARHS7xk9UHdF4ZQ12pC%2Fimage.png?alt=media&#x26;token=199f84cd-ede7-40f3-8cd5-1713f2896886" alt=""><figcaption><p>block-light: 15</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FFJBuj7nclW05zBTaWw6n%2Fimage.png?alt=media&#x26;token=c2dd379c-0fa7-4c51-8778-667357cf6f03" alt=""><figcaption><p>block-light: 7</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F5uiR2P5WZBE6aVvLkiUi%2Fimage.png?alt=media&#x26;token=c35aa388-96de-4354-abf2-a6dd21cc47ef" alt=""><figcaption><p>block-light: 0</p></figcaption></figure>

## 传播天线

{% hint style="danger" %}
**此选项几乎没有效果，因为客户端将预测天空灯的更新。**
{% endhint %}

确定自然光是否可以通过此方块。

```yaml
宣传天空光: true
```
