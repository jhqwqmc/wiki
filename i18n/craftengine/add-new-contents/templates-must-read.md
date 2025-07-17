---
description: This page mainly explains how to add new templates to your server.
---

# 📄 Templates \[MUST READ]

{% hint style="danger" %}
The following content applies to CraftEngine 0.0.57 and above. If you update to version 0.0.57 or newer, you need to use the command `/ce debug migrate-templates` to migrate the old templates.
{% endhint %}

## Introduction

The plugin boasts an exceptionally high degree of customization, but it's impossible to configure it without providing any settings. Even a very brief option requires a line in your YAML file. With numerous such options, a configuration file can become excessively long. Therefore, the plugin has introduced a template system, allowing you to define a base template and use parameters and overrides to fill in or overwrite certain parameters, significantly simplifying the process and reducing the time spent on repetitive configurations.

## How it works?

To configure a template, you need to use `templates` as the root key in your YAML file. The first thing under `templates` is your template's name. In the example below, the template is called **`namespace:my_first_template`**. Everything under that name is the actual template content.

```yaml
templates:
  namespace:my_first_template:
    option_1: true
    option_2: false
    option_3: 
      - hello
    option_4: 20.25
    option_5:
      hello: world
```

Check out this quick animation to see how the plugin applies the template:

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F0JyPNp4niJkzAGHID1Kv%2Ftemplate.gif?alt=media&#x26;token=cfecd8c1-d494-407f-a5db-ba2cce189f13" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
`namespace:template_id` serves as the unique identifier for your template. This name must be used whenever referencing or invoking this template elsewhere.
{% endhint %}

{% hint style="success" %}
The configuration area under `namespace:template_id` is entirely customizable, as long as it adheres to YAML syntax. You have complete freedom to define it according to your needs.
{% endhint %}

## Multiple Templates

You can combine multiple templates by setting up the `template` as a list.

```yaml
items:
  craftengine:custom_item:
     template:
       - namespace:my_first_template
       - namespace:my_second_template
```

{% hint style="warning" %}
**Heads up:** If two templates have the same setting, the one below will overwrite the one above. But if the setting is a list, they’ll merge into one combined list instead.
{% endhint %}

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FWiQor59iwPiY7n185412%2Fmultiple.gif?alt=media&#x26;token=ac0c9ff6-d883-4666-81aa-2b279a56e6a2" alt=""><figcaption></figcaption></figure>

## Arguments

You can define parameters in template using `${xxx}`, like `${nutrition}` or `${saturation}`.  Then, when calling the template, use the **`"arguments"`** section to set the parameter values. Here's a quick example:

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
If you need to use curly braces `{}` as normal text (not as parameters), just escape them with a backslash like `\{` or `\}`.&#x20;

`\${Hello world}`
{% endhint %}

{% hint style="success" %}
To set default values for parameters, add `:-` after the parameter name - for example:

* `${nutrition:-1}`
* `${saturation:-2.5d}`
* `${map:-{aa:bb,cc:ddd}}`
* `${string:-"1234"}`

The default values follow Minecraft's SNBT format (the same format used when specifying NBT data in commands).
{% endhint %}

## Overrides

Overrides completely replace whatever's in the specified config path—including lists and maps. No merging, just a full swap.

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

## Merges

Merges deeply combines two config sections, including all lists - nothing gets left behind. Basically, merges function almost exactly like multiple templates.

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
