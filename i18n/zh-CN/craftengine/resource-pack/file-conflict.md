---
description: How to resolve file conflict
---

# ⚔️ File Conflict

## 👋 Introduction

When merging multiple resource packs, we often encounter conflicting files, such as pack.png, sounds.json, and so on. Configuring them into a single file can be quite tedious. Therefore, the plugin provides a conflict resolver that allows you to customize the solution for resolving conflicts. When the plugin detects conflicting files, it will search for the first solution that meets the conditions. If no suitable solution is found, it will issue a warning to the user in the console.

{% hint style="info" %}
The configuration for conflict resolution is located in the `config.yml` file under the section `resource-pack.duplicated-files-handler`.&#x20;
{% endhint %}

{% hint style="danger" %}
The plugin does not support the merging of shaders, as it is considered unstable.
{% endhint %}

```yaml
duplicated-files-handler:
  # handle item models
  - term:
      type: any_of
      terms:
        - type: parent_path_suffix
          suffix: "minecraft/items" # 1.21.4+
        - type: parent_path_suffix
          suffix: "minecraft/models/item" # 1.20-1.21.3
    resolution:
      type: merge_json
      deeply: true
  # handle pack.mcmeta
  - term:
      type: exact
      path: "pack.mcmeta"
    resolution:
      type: merge_pack_mcmeta
      description: "<gray>CraftEngine ResourcePack"
  # handle pack.png
  - term:
      type: exact
      path: "pack.png"
    resolution:
      type: retain_matching
      term:
        type: contains
        path: "resources/default/resourcepack"
  # handle sounds
  - term:
      type: filename
      name: "sounds.json"
    resolution:
      type: merge_json
      deeply: false
```

{% hint style="success" %}
You can simply understand it as: **term** determines the matching rules, and **resolution** decides how to handle the conflicting files. Below are some available matching methods and resolution options:
{% endhint %}

## 🔢 Matching Rule

### all\_of

All conditions must be satisfied.

```yaml
type: all_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

### any\_of

Satisfy any one of the conditions.

```yaml
type: any_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

### inverted

Negate the result value of the current condition.

```yaml
type: inverted
term:
  type: xxx
```

### filename

Match the filename

```yaml
type: filename
name: "sounds.json"
```

### exact

Match the exact path

```yaml
type: exact
path: "assets/minecraft/lang/en_us.json"

type: exact
path: "pack.mcmeta"
```

### parent\_path\_prefix / parent\_path\_suffix

Detect whether a path has a specific prefix or suffix

```yaml
type: parent_path_prefix 
path: "assets/minecraft"

type: parent_path_suffix
path: "minecraft/models/item"
```

### contains

Check if the path contains the characters

```yaml
type: contains
path: "custom/furniture"
```

### pattern

Use regex to match path

```yaml
type: pattern
pattern: "Regex Here"
```

## 🧑‍💻 Resolution

### merge\_json

Combine two json files into one

```yaml
type: merge_json
deeply: true
```

### retain\_matching

When two files conflict, keep the one that meets the specified condition.

```yaml
type: retain_matching
term:
  type: contains
  path: "resources/default/resourcepack"
```

### conditional

Run a conditional resolution

```yaml
type: conditional
term:
  type: xxx
resolution:
  type: xxx
```

### merge\_pack\_mcmeta

A special resolution customized for `pack.mcmeta`

```yaml
type: "merge_pack_mcmeta"
description: "<gray>CraftEngine ResourcePack" # pack description
```

### merge\_atlas

A special resolution customized for `atlases/xx.json`

```yaml
type: "merge_atlas"
```
