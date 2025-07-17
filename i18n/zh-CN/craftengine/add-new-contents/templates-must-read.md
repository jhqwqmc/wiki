---
description: 此页主要解释了如何向您的服务器添加新模板。
---

# 📄 模板\[MUST READ]

{% hint style="danger" %}
以下内容适用于CraftEngine 0.0.57 及以上。 如果您更新到 0.0.57 或更高版本，您需要使用命令`/ce debug migrate-templates` 来迁移旧模板。
{% endhint %}

## 一. 导言

插件预示着异常高的自定义程度，但如果不提供任何设置，就无法配置它。 即使是非常简短的选项，在您的 YAML 文件中需要一行。 由于这种选项众多，配置文件可能过长。 因此，插件引入了一个模板系统， 允许您定义基本模板和使用参数并覆盖或覆盖某些参数， 大大简化程序，缩短重复配置的时间。

## 它是如何运作的？

要配置模板，您需要使用 `templates` 作为您的 YAML 文件中的根键。 `templates`下的第一件事是你的模板名称。 在下面的示例中，模板叫做\*\*`namespace:my_first_template`\*\*。 该名称下的一切都是实际模板内容。

```yaml
模板：
  namespace:my_first_template:
    option_1: true
    option_2: false
    option_3: 
      - hello
    option_4: 20.25
    option_5:
      hello: world
```

查看此快速动画以查看插件如何应用模板：

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F0JyPNp4niJkzAGHID1Kv%2Ftemplate.gif?alt=media&#x26;token=cfecd8c1-d494-407f-a5db-ba2cce189f13" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
`namespace:template_id` 是您的模板的唯一标识符。 此名称必须在任何时候被用于引用或在其他地方引用此模板。
{% endhint %}

{% hint style="success" %}
`namespace:template_id`下的配置区域完全可以自定义，但只要它遵守YAML 语法。 您有完全的自由根据您的需要定义它。
{% endhint %}

## 多个模板

您可以通过设置 `template` 作为列表来合并多个模板。

```yaml
items:
  craftengine:custom_item:
     template:
       - namespace:my_first_template
       - namespace:my_second_template
```

{% hint style="warning" %}
**浮动：** 如果两个模板有相同的设置，下面的一个将覆盖上面的一个。 但如果设置是一个列表, 它们将会合并成一个合并列表。
{% endhint %}

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FWiQor59iwPiY7n185412%2Fmultiple.gif?alt=media&#x26;token=ac0c9ff6-d883-4666-81aa-2b279a56e6a2" alt=""><figcaption></figcaption></figure>

## 参数

You can define parameters in template using `${xxx}`, like `${nutrition}` or `${saturation}`.  然后调用模板时，使用 **\`"参数"** 部分来设置参数值。 下面是一个快速示例：

```yaml
templates:
  craftengine:apple_template:
    material: apple
    data:
      food:
        nutrition: "${nutrition}"
        saturation: "${saturation}"
items:
  craftengine:custom_apple:
    template: craftengine:apple_template
    arguments:
      nutrition: 1
      saturation: 2.5
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FEBlTqSuHobBp0HHdAlwK%2Farguments.gif?alt=media&#x26;token=358280cf-c114-41f9-a715-93b6a0edc395" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
如果您需要使用大括号`{}`作为正则文本(不作为参数)， 只需用反斜杠逃脱他们，如`\{` 或 `\}` 。&#x20;

`\${Hello world}`
{% endhint %}

{% hint style="success" %}
要设置参数的默认值，请在参数名称之后添加 ":-" - 例如：

- `${nutrition:-1}`
- `${saturation:-2.5d}`
- `${map:-{aa:bb,cc:ddd}}`
- `${string:-"1234"}`

默认值沿用Minecraft的 SNBT 格式(在命令中指定 NBT 数据时使用相同的格式)。
{% endhint %}

## 覆盖

覆盖完全替换指定的配置路径中的任何东西——包括列表和地图。 没有合并，只是完全交换。

```yaml
items:
  craftengine:custom_bread:
    template: craftengine:apple_template
    arguments:
      nutrition: 1
      saturation: 2.5
    overrides:
      material: bread
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FVSIK99qhdnIUTu7ibtfg%2Foverrides.gif?alt=media&#x26;token=bcdbc323-c3dc-4eb8-aa3e-233131894689" alt=""><figcaption></figcaption></figure>

## 合并

合并时深入合并了两个配置部分，包括所有列表 - 没有留下任何内容。 基本上，合并函数几乎完全像多个模板。

```yaml
items:
  craftengine:custom_bread:
    template: craftengine:apple_template
    arguments:
      nutrition: 1
      saturation: 2.5
    merges:
      data:
        food:
          can-always-eat: true
```
