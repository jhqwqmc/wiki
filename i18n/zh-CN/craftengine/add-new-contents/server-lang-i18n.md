# :glube_showing_Europe-Africa: Server Lang (i18n)

i18n 用于服务器端本地化。 如果您正在寻求客户端本地化，请咨询 [client-lang-lang](client-lang-lang "提及")。 一般来说，典型的用户不要求使用i18n， 它主要是为提供多种语言支持的公共模型和资产包的提供者设计的。

若要使用 i18n，请参阅以下链接：[#少于-i18n-id-greater](../../text-format#less-than-i18n-id-greater-than “提及”)。

{% hint style="info" %}
语言的国家或区域规范是可选的(例如"en\_us"可以简化为“en")。 插件将首先尝试找到适合特定国家或区域的语言。 如果没有这种语文，则将寻找一般语文。 如果没有找到语言，插件将默认使用英语(en)作为后备语言。
{% endhint %}

```yaml
i18n:
  en:
    item.chinese_lantern: "Chinese Lantern"
    item.fairy_flower: "Fairy Flower"
    item.bench: "Bench"
    item.table_lamp: "Table Lamp"
    item.wooden_chair: "Wooden Chair"
    item.topaz_rod: "Topaz Rod"
    item.topaz_bow: "Topaz Bow"
    item.topaz_crossbow: "Topaz Crossbow"
    item.topaz_pickaxe: "Topaz Pickaxe"
    item.topaz_axe: "Topaz Axe"
    item.topaz_hoe: "Topaz Hoe"
    item.topaz_shovel: "Topaz Shovel"
    item.topaz_sword: "Topaz Sword"
    item.topaz_ore: "Topaz Ore"
    item.deepslate_topaz_ore: "Deepslate Topaz Ore"
    item.topaz: "Topaz"
    item.palm_log: "Palm Log"
    item.stripped_palm_log: "Stripped Palm Log"
    item.palm_wood: "Palm Wood"
    item.stripped_palm_wood: "Stripped Palm Wood"
    item.palm_planks: "Palm Planks"
    item.palm_sapling: "Palm Sapling"
    item.palm_leaves: "Palm Leaves"
  zh_cn:
    item.chinese_lantern: "灯笼"
    item.fairy_flower: "仙灵花"
    item.bench: "长椅"
    item.table_lamp: "台灯"
    item.wooden_chair: "木椅"
    item.topaz_rod: "黄玉钓竿"
    item.topaz_bow: "黄玉弓"
    item.topaz_crossbow: "黄玉弩"
    item.topaz_pickaxe: "黄玉镐"
    item.topaz_axe: "黄玉斧"
    item.topaz_hoe: "黄玉锄"
    item.topaz_shovel: "黄玉锹"
    item.topaz_sword: "黄玉剑"
    item.topaz_ore: "黄玉矿石"
    item.deepslate_topaz_ore: "深层黄玉矿石"
    item.topaz: "黄玉"
    item.palm_log: "棕榈原木"
    item.stripped_palm_log: "去皮棕榈原木"
    item.palm_wood: "棕榈木"
    item.stripped_palm_wood: "去皮棕榈木"
    item.palm_planks: "棕榈木板"
    item.palm_sapling: "棕榈树苗"
    item.palm_leaves: "棕榈树叶"
```

{% hint style="success" %}
您可以在 i18n 内排料其他标签。

```yaml
i18n:
  en:
    internal.cooking_info.0: "Time: <arg:cooking_time>ticks"
    internal.cooking_info.1: "Experience: <arg:cooking_experience>"
```

{% endhint %}
