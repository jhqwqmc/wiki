# ✏️ Text Format

## MiniMessage

When configuring item names, descriptions, GUIs, etc., for the plugin, please use the MiniMessage format. [https://docs.advntr.dev/minimessage/format.html](https://docs.advntr.dev/minimessage/format.html)

> Any meaningful token can be escaped in the locations where they have influence. In plain text, tag open characters (`<`) can be escaped with a leading backslash (`\`). Within quoted strings, the opening quote character can be escaped (`'` or `"`). In either place, the escape character can be escaped in places where it would otherwise be relevant. Unquoted tag arguments cannot have escapes, for simplicity. In locations where escaping is not supported, the literal escape character will be passed through. In locations where escaping _is_ supported but a literal escape character is desired, the escape character can itself be escaped to produce a `\`.

## Extra Tags

These are additional tags provided by the plugin.

{% hint style="success" %}
`[_argument_]` means Optional
{% endhint %}

{% hint style="info" %}
You can surround your arguments with `'`  & `"` for instance `<papi:'exp_multiplier':'1'>`

You can also use **nested** tags for instance `<expr:'0.##':'<papi:exp_multiplier:1> * 10'>`
{% endhint %}

{% hint style="info" %}
You'll notice that some tags start with "**viewer\_**". This is because, in certain scenarios, a text might be constructed by multiple contextual entities. For example, consider the following configuration:

```yaml
message: -| 
  Hi, <viewer_arg:player.name>. 
  Did you notice that <arg:player.name> interacted a custom block?
```

If **Player A** interacts with the custom block and triggers a message broadcast, then **Player B** receiving this message would see:\
`"Hi, B. Did you notice that A interacted a custom block?"`
{% endhint %}

### \<shift:\_pixels\_>

`shift` allows you to directly use the plugin's offset characters.

```yaml
item-name: "<!i><shift:-100><#FF8C00>Topaz Rod"
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/3z6SBihmPpB19j9eenC2/image.png" alt=""><figcaption></figcaption></figure>

### \<papi:\_placeholder\_:\[\_default\_value\_]>

### \<viewer\_papi:\_placeholder\_:\[\_default\_value\_]>

### \<rel\_papi:\_placeholder\_:\[\_default\_value\_]>

`papi` allows to use placeholders provided by `PlaceholderAPI`.&#x20;

```yaml
item-name: "<!i><#FF8C00><papi:player_name>'s Topaz Rod"
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ygowY8l2F8zPS4Z2Ncl3/image.png" alt=""><figcaption></figcaption></figure>

You can also specify a default value to make it available in more places **without causing errors** for example:

```yaml
functions:
  - type: drop_exp
    count:
      type: uniform
      min: "<papi:exp_multiplier:1> * 3"
      max: "<papi:exp_multiplier:1> * 5"
```

{% hint style="warning" %}
**rel\_papi**  refers to relational placeholders
{% endhint %}

### \<image:\_namespace\_:\_id\_:\[\_row\_]:\[\_column\_]>

`image` allows to use images registered in the plugin

```yaml
item-name: "<!i><white><image:default:icons><#FF8C00> Topaz Rod"
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/lhx8oEvcEEBsnCw4qMPB/image.png" alt=""><figcaption></figcaption></figure>

```yaml
item-name: "<!i><white><image:default:icons:0:1><#FF8C00> Topaz Rod"
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/V2djYKHTMnBxFpZwuTWX/image.png" alt=""><figcaption></figcaption></figure>

### \<i18n:\_id\_>

Searching for translations applicable to the current language.

```yaml
internal:cooking_info:
  template: "internal:icon/2d"
  arguments:
    model_data: 1006
    texture: cooking_info
    name: "<!i><#FF8C00><i18n:internal.cooking_info>"
    lore:
      - "<!i><gray><i18n:internal.cooking_info.0>"
      - "<!i><gray><i18n:internal.cooking_info.1>"
```

### \<expr:\_format\_:\_expression\_>

Perform some math operations

```yaml
item-name: "<!i><#FF8C00><expr:0.##:'70 / 8'>"
```

```yaml
item-name: "<!i><#FF8C00><expr:0.##:'<papi:player_x> / 8'>"
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FJVYm8tyyUtjNLBMVx02V%2Fimage.png?alt=media&#x26;token=a824c047-0f28-4a0c-a30d-0f9787c2b7fe" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Useful links**

[https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html)

[https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)
{% endhint %}

### \<arg:\_index\_>

Only used for files under `translations`, representing indexed parameters.

### \<arg:\_id\_>

### \<viewer\_arg:\_id\_>

The is a named parameter. Its value can come from two possible sources:

1. **Context-specific arguments** – These are parameters explicitly passed in the current context.

```yaml
internal.cooking_info.0: "Time: <arg:cooking_time>ticks"
internal.cooking_info.1: "Experience: <arg:cooking_experience>"
```

2. **Common arguments**

```yaml
<arg:random>  # generates a random number between 0 and 1
<arg:last_random>  # gets the last random number
```

3. **Context subjects** – If the context subject (e.g., a player) provides parameters. Check this page for more:

{% content-ref url="text-format/chain-arguments" %}
[chain-arguments](text-format/chain-arguments)
{% endcontent-ref %}

{% hint style="success" %}
In certain cases, multiple **context subjects** may coexist. By accessing parameters from different context subjects, you can precisely control the scope and behavior of functions.

```yaml
# spawns the particle at the location of the block
- type: particle
  x: '<arg:block.x> + 0.5'
  y: '<arg:block.y> + 0.5'
  z: '<arg:block.z> + 0.5'
  ...
# spawns the particle at the location of the player
- type: particle
  x: '<arg:player.x>'
  y: '<arg:player.y>'
  z: '<arg:player.z>'
  ...
# broadcast the message
- type: message
  target: 'all'
  message:
    - "Hello <viewer_arg:player.name>! This message is from <arg:player.name>."
    - "<arg:player.name> just interacted a <arg:block.owner> block!"
```
{% endhint %}

### \<global:\_id\_:\[args...]>

global variable defined by users

```yaml
item-name: "<global:rare_tag> Rare spear"
```

[global-variables](add-new-contents/global-variables "mention")
