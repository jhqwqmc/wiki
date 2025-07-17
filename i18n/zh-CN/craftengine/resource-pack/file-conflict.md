---
description: 如何解决文件冲突
---

# ⚔️ 文件冲突

## 👋 简介

当合并多个资源包时，我们常常遇到冲突的文件，例如pack.png、sounds.json等等。 将它们配置为单一文件可能是非常棘手的。 因此，插件提供了一个解决冲突的方法，允许你定制解决冲突的方法。 当插件检测到有冲突的文件时，它将搜索符合条件的第一个解决方案。 如果找不到合适的解决方案，它将向控制台中的用户发出警告。

{% hint style="info" %}
冲突解决配置位于`config.yml`部分`resourcack.repated-files-handler` 。&#x20;
{% endhint %}

{% hint style="danger" %}
插件不支持Shaders合并，因为它被认为不稳定。
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
您可以简单地理解为：**条款** 决定匹配的规则，**解析** 决定如何处理冲突文件。 以下是一些可用的匹配方法和分辨率选项：
{% endhint %}

## :input_number: 匹配规则

### 全部\_共

必须满足所有条件。

```yaml
type: all_of
条款:
  - 类型: xxx1
    aaa: bbb
  - 类型: xxx2
    ccc: ddd
```

### 任意\_共

满足任何一个条件。

```yaml
type: any _of
条款:
  - 类型: xxx1
    aaa: bbb
  - 类型: xxx2
    ccc: dd
```

### 反转

负数当前条件的结果值。

```yaml
类型：反转
术语：
  类型：xxx
```

### 文件名

匹配文件名

```yaml
类型：文件名
名称：“sounds.json”
```

### 准确的

匹配准确路径

```yaml
类型：精确
路径：“assets/minecraft/lang/en_us.json”

类型：精确
路径：“pack.mcmeta”
```

### 父级\_path\_prefix / parent\_path\_suffix

检测路径是否有特定的前缀或后缀

```yaml
类型: parent_path_prefix 
路径: "assets/minecraft"

类型: parent_path_subix
路径: "minecraft/models/item"
```

### 包含

检查路径是否包含字符

```yaml
类型：包含
路径：“自定义/家具”
```

### 图案

使用正则表达式来匹配路径

```yaml
类型：图案
模式：“正则表达式”
```

## 🧑‍💻 Resolution

### 合并\_json

将两个json 文件合并为一个

```yaml
类型: 合并json
深度: true
```

### 保留\_匹配

当两个文件冲突时，保留符合指定条件的文件。

```yaml
类型: 保留
条款:
  类型: 包含
  路径: "resources/default/resourcepack"
```

### 条件

运行条件分辨率

```yaml
类型：条件
术语：
  类型：xxx
分辨率：
  类型：xxx
```

### 合并\_pack\_mcmeta

为 `pack.mcmeta` 定制的特殊分辨率

```yaml
类型: "merge_pack_mcmeta"
描述: "<gray>CraftEngine ResourcePack" # 包描述
```

### 合并\_地图集

专为`atlases/xx.json`设计的特殊决议

```yaml
类型：“合并地图集”
```
