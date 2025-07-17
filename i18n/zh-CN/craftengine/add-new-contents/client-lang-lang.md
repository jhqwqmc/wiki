# 🌎️ Client Lang (lang)

```yaml
lang:
  en_us:
    item.custom.palm_leaves: Palm Leaves
    item.custom.palm_log: Palm Log
```

In the absence of language files, Minecraft will default to using en\_us. Therefore, it is highly recommended to configure en\_us if you are creating a **new** translation key.&#x20;

{% hint style="success" %}
To render client side translation, please insert [https://docs.advntr.dev/minimessage/format.html#translatable](https://docs.advntr.dev/minimessage/format.html#translatable)
{% endhint %}

{% hint style="info" %}
Read Minecraft Wiki for how client side translation works\
[https://minecraft.wiki/w/Resource\_pack#Language](https://minecraft.wiki/w/Resource_pack#Language)
{% endhint %}

If you wish to overwrite all the languages, please use "all".

```yaml
lang:
  all:
    container.inventory: ""
```
