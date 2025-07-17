# ✏️ 文本格式

## 最小消息

当配置插件名称、描述、GUI等时，请使用 MiniMessage 格式。 [https://docs.advntr.dev/minimessage/format.html](https://docs.advntr.dev/minimessage/form.html)

> 任何有意义的象征都可以在他们有影响力的地方逃脱。 在纯文本中，标签打开字符(<`) 可以用前导反斜杠(`\\`)逃脱。 在引用的字符串中，开头引用字符可以逃避(\`\`\`\`\`)或\`\`\`)。 在其中任何一个地方，逃脱的性能都可以在否则会有相关意义的地方逃脱。 未引用的标签参数无法逃避，因为很简单。 在不支持逃跑的地方，字面逃跑的性质将会经过。 在逃跑得到支持但需要字面逃脱字符的地方，逃脱字符本身可以逃脱以生成 "\"。

## Extra Tags

这些是插件提供的附加标签。

{% hint style="success" %}
[_argument_]意味着可选的
{% endhint %}

{% hint style="info" %}
你可以用\`'和 \`\`\`<papi:'exp_multiplier':'1'> 环绕你的参数

您也可以使用 **嵌套** 标签用于实例 `<expr:'0.##':'<papi:exp_multiplier:1> * 10'>`
{% endhint %}

{% hint style="info" %}
您会注意到一些标签以“**viewer\_**”开头。 这是因为在某些情况下，案文可能由多个上下文实体拟定。 例如，考虑以下配置：

```yaml
消息：-| 
  Hi, <viewer_arg:player.name>。 
  您是否注意到 <arg:player.name> 交互了一个自定义块？
```

如果**Player A** 与自定义方块互动并触发消息广播，那么**Player B** 接收此消息会看到：\
"Hi, B. 您是否注意到一个自定义块交互了？"
{% endhint %}

### \<shift:\\_pixels\\_>

`shift`允许你直接使用插件的偏移字符。

```yaml
项目名称：“<!i><shift:-100><#FF8C00>Topaz Rod”
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/3z6SBihmPpB19j9eenC2/image.png" alt=""><figcaption></figcaption></figure>

### \<papi:\\_placeholder\\_:\\[\\_default\\_value\\_]>

### \<viewer\_papi:\_placeholder\_:\[\_default\_value\_]>

### \<rel\_papi:\_placeholder\_:\[\_default\_value\_]>

`papi` 允许使用 `PlaceholderAPI`提供的占位符。&#x20;

```yaml
项目名称: "<!i><#FF8C00><papi:player_name>'s Topaz Rod"
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ygowY8l2F8zPS4Z2Ncl3/image.png" alt=""><figcaption></figcaption></figure>

您还可以指定一个默认值，以便在更多地方**不会导致错误**例如：

```yaml
函数:
  - 类型: drop_exp
    计数:
      类型: 均匀
      最小: "<papi:exp_multiplier:1> * 3"
      最大: "<papi:exp_multiplier:1> * 5"
```

{% hint style="warning" %}
**rel\_papi**  refers to relational placeholders
{% endhint %}

### \<image:\\_namespace\\_:\\_id\\_:\\[\\_row\\_]:\\[\\_column\\_]>

`image` 允许使用插件中注册的图像

```yaml
项目名称: "<!i><white><image:default:icons><#FF8C00> Topaz Rod"
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/lhx8oEvcEEBsnCw4qMPB/image.png" alt=""><figcaption></figcaption></figure>

```yaml
项目名称: "<!i><white><image:default:icons:0:1><#FF8C00> Topaz Rod"
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/V2djYKHTMnBxFpZwuTWX/image.png" alt=""><figcaption></figcaption></figure>

### \<i18n:\\_id\\_>

搜索适用于当前语言的翻译。

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

### \<expr:\\_format\\_:\\_expression\\_>

执行一些数学操作

```yaml
项目名称：“<!i><#FF8C00><expr:0.##:'70 / 8'>”
```

```yaml
项目名称：“<!i><#FF8C00><expr:0.##:'<papi:player_x> / 8'>”
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FJVYm8tyyUtjNLBMVx02V%2Fimage.png?alt=media&#x26;token=a824c047-0f28-4a0c-a30d-0f9787c2b7fe" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**有用链接**

[https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html)

[https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)
{% endhint %}

### \<arg:\\_index\\_>

仅用于`translations`下的文件，代表索引参数。

### \<arg:\\_id\\_>

### \<viewer\_arg:\_id\_>

是一个命名的参数。 其价值可以来自两个可能的来源：

1. **特定的参数** - 这些参数在当前环境下被明确传递。

```yaml
internal.cooking_info.0: "Time: <arg:cooking_time>ticks"
internal.cooking_info.1: "Experience: <arg:cooking_experience>"
```

2. **通用参数**

```yaml
<arg:random>  # 生成0和 1
<arg:last_random>  获取最后一个随机数字
```

3. **上下文主题** - 如果上下文主题(例如玩家)提供参数。 查看此页面的更多信息：

{% content-ref url="text-format/chain-arguments" %}
[chain-arguments](文本格式/链式)
{% endcontent-ref %}

{% hint style="success" %}
在某些情况下，多个**上下文主题** 可能共存。 通过访问来自不同上下文主题的参数，您可以准确地控制函数的范围和行为。

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

### \<global:\\_id\\_:\\[args...]>

由用户定义的全局变量

```yaml
项目名称：“<global:rare_tag> 稀有率先”
```

[global-variables](add-new-contents/global-variables "提及")
