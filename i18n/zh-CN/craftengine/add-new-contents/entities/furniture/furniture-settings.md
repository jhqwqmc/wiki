# ⚙️ 家具设置

## 项目

确定此家具对应的物品。 这通常用来在创造性模式下获得家具物品，中键点击(1.21.4+)。

```yaml
项目：默认:test_bables
```

## 声音

在各种情况下确定家具的声音

- 当玩家打破这个家具时中断
- 当玩家放置此家具时的位置

```yaml
声音:
  断点: minecraft:block.bambo_wood.brek
  位置: minecraft:block.bambo_wood.place
```

{% hint style="info" %}
您可以配置这个配置来精确控制音量和音调

```yaml
声音:
  断点:
    id: minecraft:block.deepslate.brek
    pitch: 0.5
    volume: 0.25
  place: minecraft:block.deepslate.step
```

{% endhint %}

## 最小化

确定此家具是否应最大限度地减少发送给玩家的网络包，无需管理员权限。

```yaml
最小化：true
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FqmuOtslb0m4pzkyKjf20%2Fimage.png?alt=media&#x26;token=7651bfce-5d2e-494a-8893-5017aa63a332" alt=""><figcaption></figcaption></figure>
