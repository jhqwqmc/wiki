---
description: This page is not finished
---

# ⌨️ Skript

{% hint style="success" %}
For advanced skript users, please use reflection to achieve more advanced functions. If you encounter problems when using skript, please give us feedback in time. If you'd like to request a new Skript feature and you know Java, consider contributing your code via a pull request!
{% endhint %}

{% hint style="danger" %}
Please note that if you get an error when loading the server, it is probably because the skript script is loaded before the craftengine. This cannot be fixed at this time and can only be solved by reloading.
{% endhint %}

## Events

{% hint style="success" %}
CraftEngine has been integrated with skript native statements. You can use the following format to listen to the corresponding custom block/furniture events
{% endhint %}

```sh
on right click on default:chinese_lantern:
    say_message("You clicked the custom block!")
```

```sh
on break of default:palm_log[axis=y]:
    say_message("You broke the custom block!")
```

## Expressions

**\[the] custom block id of %blocks%**\
**%blocks%'\[s] custom block id**

_Gets the custom block id of the block_

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

_Gets the custom block state of the block_

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

_Gets the furniture id of the entity_

```sh
# no example for the moment
```

**\[the] custom item id of %itemstacks%**\
**%itemstacks%'\[s] custom item id**

_Gets the custom item of the itemstack_

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

## Conditions

**%blocks% (is|are) custom block(s)**\
**%blocks% (is|are)(n't| not) custom block(s)**

_Checks if a block is custom_

**%entities% (is|are) furniture**\
**%entities% (is|are)(n't| not) furniture**

_Checks if an entity is furniture_

**%itemstacks% (is|are) custom item(s)**\
**%itemstacks% (is|are)(n't| not) custom item(s)**

_Checks if an item is custom_

## Effects

**place custom block %customblockstates% \[%directions% %locations%]**

_Places the custom block state_

```sh
# example
place custom block default:palm_log[axis=x] at location of the player
```

**place furniture %strings% \[%directions% %locations%]**

_Places the furniture_

```sh
# example
place furniture "default:bench" at location of the player
```

**remove furniture %entities%**

_Removes the furniture_

```sh
# example
remove furniture target entity
```
