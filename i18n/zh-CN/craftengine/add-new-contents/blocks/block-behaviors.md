# 🕹️ 阻止行为

CraftEngine 实现一个全面的物理属性系统，允许您自由结合多个方块行为！ 这里有两个简单的例子：一个显示单个方块行为，另一个显示多个方块行为的组合。

```yaml
# 单个行为
块:
  默认:fairy_flower:
    行为:
      类型: bush_block
      底部块标签:
        - minecraft:dirt
        - minecraft:farmland
```

```yaml
# 组合行为
块:
  default:followder_block:
    行为:
      - 类型: commande_powder_block
        solid-block: default:solid_followder_block
      - 类型: falling_block
```

{% hint style="danger" %}
请注意：合并一些块行为可能会导致意外冲突。 如果你遇到问题，请联系支持者，我们会尝试解决任何冲突。
{% endhint %}
