# 📔 Worldgen Datapack 教程

## 要了解的重要情况

{% hint style="danger" %}
因为Minecraft不允许对方块注册表进行动态修改，插件事先注册所有必要的真实状态。 您可以通过使用 [#get-block-internal-id] (../commands#get-block-internal-id “提及”来查询与方块对应的实际方块状态。

Minecraft只能识别遵循类似于“craftengine:note_block_x”模式的方块名称。 即使您正在使用其他插件，如MythicMobs的块布置技能，这也是如此。 原因是CraftEngine采用了一种动态的绑定方案。 这意味着插件中的块 ID 与服务器上的实际方块 ID 不一致。
{% endhint %}

## 此教程的目标听众。

此教程被设计为崩溃课程 特别是为那些希望在学习Minecraft数据包时不投入时间的人设计的设计。 所提供的例子只是可行的解决办法，并不代表插件的全部潜力。 你完全能够使用 CraftEngine 生成模组式的地形和生物群落。

{% hint style="success" %}
制作您的数据包时，您可能会整合网站&#x20;

[https://misode.github.io/worldgen/feature/](https://misode.github.io/worldgen/feature/)

[https://misode.github.io/worldgen/placed-feature/](https://misode.github.io/worldgen/placed-feature/)

在您的工作流中, 因为它是一个宝贵的工具, 可以在您的配置中最大限度地减少语法错误。
{% endhint %}

{% hint style="danger" %}
此教程是在版本1.21.4期间编写的。 请注意不同版本之间可能存在差异，因此最好作出相应的判断。

这不是一个专业的数据包教程；它只包含简单的例子。 如果你对数据包感兴趣，你应该寻找专业教程并花时间来全面学习。
{% endhint %}
