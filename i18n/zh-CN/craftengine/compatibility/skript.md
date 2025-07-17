---
description: 此页面尚未完成
---

# ⌨️ Skript

{% hint style="success" %}
高级skript 用户，请使用反思实现更高级的函数。 如果您使用 skript 时遇到问题，请及时给我们反馈。 如果你想请求一个新的 Skript 功能并且你知道Java，请考虑通过拉取请求贡献你的代码！
{% endhint %}

{% hint style="danger" %}
请注意，如果你在加载服务器时遇到错误， 这可能是因为脚本被加载到手势前的脚本。 此时无法修复，只能通过重新加载解决。
{% endhint %}

## 事件

{% hint style="success" %}
CraftEngine 已经并入草原语句。 您可以使用以下格式来监听相应的自定义块/家具事件
{% endhint %}

```sh
右键单击默认值：中文：
    say_message("你点击了自定义块！")
```

```sh
on break of default:palm_log[axis=y]:
    say_message("You broke the custom block!")
```

## 表达式

**\[the] custom block id of %blocks%**\
**%blocks%'\[s] custom block id**

_获取方块的自定义方块ID_

```sh
# example
on block break:
   set {id} to custom block id of target block
   say_message("You break the %{id}% !")
```

```sh
# example
on block break:
   set {id} to target block's custom block id
   say_message("You break the %{id}% !")
```

**\[the] custom block state of %blocks%**\
**%blocks%'\[s] custom block state**

_获取方块的自定义方块状态_

```sh
# example
on block break:
   set {custom_state} to target block's custom block state
   set {id} to custom block id of {custom_state}
   say_message("You break the %{custom_state}% which is a %{id}% block!")
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FY5CQfTc3ASBZASEdJxVz%2Fimage.png?alt=media&#x26;token=7d12dcf4-7b97-4ac7-ba77-9bedc90ecb55" alt=""><figcaption></figcaption></figure>

**\[the] furniture id of %entities%**\
**%entities%'\[s] furniture id**

_获取实体的家具ID_

```sh
# 目前没有示例
```

**\[the] custom item id of %itemstacks%**\
**%itemstacks%'\[s] custom item id**

_获取项目的自定义项目

```sh
# example
set {_item} to a nether_brick
set the custom item id of {_item} to "default:bench"
give player {_item}
set {_id} to the custom item id of {_item}
say_message("You got a %{_id}%!")
```

**\[the] custom item \[with id] %string%**

```sh
# example
set {_item} to the custom item with id "default:bench"
give player {_item}
```

## 条件

**%blocks% (is|are) custom block(s)**\
**%blocks% (is|are)(n't| not) custom block(s)**

检查一个方块是否为自定义_

**%entities% (is|are) furniture**\
**%entities% (is|are)(n't| not) furniture**

检查一个实体是否为家具_

**%itemstacks% (is|are) custom item(s)**\
**%itemstacks% (is|are)(n't| not) custom item(s)**

检查是否一个项目是自定义的_

## 效果

**place custom block %customblockstates% \[%directions% %locations%]**

_放置自定义方块状态_

```sh
# 示例
将自定义块默认值:palm_log[axis=x]放置在玩家的位置
```

**place furniture %strings% \[%directions% %locations%]**

_放置家具_

```sh
# 示例
在玩家所在的位置放置家具"默认:bie"
```

**remove furniture %entities%**

拆除家具_

```sh
# 示例
移除家具目标实体
```
