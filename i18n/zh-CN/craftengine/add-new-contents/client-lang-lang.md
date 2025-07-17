# 🌎️ Client Lang (lang)

```yaml
lang:
  en_us:
    item.custom.palm_leaves: Palm Leaves
    item.custom.palm_log: Palm 日志
```

在没有语言文件的情况下，Minecraft将默认使用 en\_us Therefore, it is highly recommended to configure en\_us if you are creating a **new** translation key.&#x20;

{% hint style="success" %}
要渲染客户端翻译，请插入 [https://docs.advntr.dev/minimessage/format.html#translatable](https://docs.advntr.dev/minimessage/格式.html#translatable)
{% endhint %}

{% hint style="info" %}
Read Minecraft Wiki for how client side translation works\
[https://minecraft.wiki/w/Resource\_pack#Language](https://minecraft.wiki/w/Resource_pack#Language)
{% endhint %}

如果您想要覆盖所有语言，请使用“全部”。

```yaml
lang:
  all:
    container.inventory: ""
```
