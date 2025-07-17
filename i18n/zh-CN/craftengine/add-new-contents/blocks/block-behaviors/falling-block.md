# :yellow_square：衰减块

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/f68xQ1ll4vIsWoN6KTOc/image.png" alt=""><figcaption></figcaption></figure>

[falling-block](falling-block “提及”) (例如沙子和魔鬼) 拥有在触发时转化为临时落下实体的财产。 下面的示例演示如何配置一个下落块：

```yaml
blocks:
  default:falling_block_示例:
    行为:
      类型: falling_block
      # 可选的
      伤害数量: -1
      # 可选的
      最大伤害: -1
```

{% hint style="info" %}
配置文件“伤害数量”和“最大伤害”是可选的，但它们必须一起配置。 它们的作用是确定在遭到落地块撞击时对实体造成的损害。
{% endhint %}
