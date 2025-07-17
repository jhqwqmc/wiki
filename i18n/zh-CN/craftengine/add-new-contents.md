---
description: 本页主要说明如何管理自定义内容
---

# ➕️ 添加新内容

## 资源&#x20;

在插件根目录（`plugins/CraftEngine/resources/`）中存放着所有内容包，这些包的名称可自由定义。 每个内容包由两个文件夹和一个YAML文件构成。 文件夹分别存储配置和资源包，YAML文件则保存该内容包的元数据。

```
plugins
  └ CraftEngine
     └ resources
         ├ pack_1
         ├ pack_2
         └ pack_3
            ├ configuration
            ├ resourcepack
            └ pack.yml
```

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/k0BUh80VNuR2bSJvfjhO/image.png" alt=""><figcaption></figcaption></figure>

## 包元文件

元文件是一个记录基础信息的YAML文档。 其中最重要的条目是 `namespace`。

```yaml
author: XiaoMoMi
version: 0.0.1
description: CraftEngine默认资源
namespace: default
enable: true # 设置为 `false` 可禁用此包 
```

{% hint style="info" %}
命名空间的作用范围仅限于YAML层级结构中根节点下的二级节点，如示例中的"default:palm\_leaves"与"palm\_leaves"。 若在`pack.yml`中指定了命名空间，当未显式声明命名空间时，将默认使用包命名空间。

```yaml
blocks:
  default:palm_leaves:
    behavior:
      type: leaves_block
```

等价于

```yaml
blocks:
  palm_leaves:
    behavior:
      type: leaves_block
```

{% endhint %}

## 配置

```
plugins
  └ CraftEngine
     └ resources
         └ pack
            └ configuration
```

配置文件存储于以下目录中，支持json和yml两种格式。 您可以在配置目录下自由创建任意数量的子目录。 Moreover, you can create as many subdirectories as you like under the configuration.

{% hint style="success" %}
In YAML configuration, the following format is not allowed:

```yaml
items:
  default:topaz_helmet:
    template: default:topaz_armor
    arguments:
      part: helmet
      slot: head
items:
  default:topaz_boots:
    template: default:topaz_armor
    arguments:
      part: boots
      slot: feet
```

Therefore, you need to add `# + any identifier` after the configuration section name, which allows you to configure multiple sections of the same type within a single YAML file.

```yaml
items#0:
  default:topaz_helmet:
    template: default:topaz_armor
    arguments:
      part: helmet
      slot: head
items#1:
  default:topaz_boots:
    template: default:topaz_armor
    arguments:
      part: boots
      slot: feet
```

{% endhint %}

## ResoucePack

```
plugins
  └ CraftEngine
     └ resources
         └ pack
            └ resourcepack
               ├ assets
               ├ overlay_folder
               ├ pack.mcmeta
               └ pack.png
```

Please ensure that the directory structure of your resource pack is as shown in the figure below, otherwise, it may lead to some merging issues. The overlay\_folder, pack.mcmeta, and pack.png files are not mandatory.

## Version-Based Configs

CraftEngine lets you add version-based configs for different server versions. Just use keys formatted like `$$version` in your YAML file.

#### **Example 1: Value Selection**

```yaml
# my_config.yml  
settings:  
  status:  
    $$1.21.4: "enabled"  
    $$1.20.1: "disabled"  
  max_players:  
    $$1.19: 50  
    $$1.20~1.21.3: 80  
    $$>=1.21.4: 100  
  allowed_worlds:  
    $$1.18: ["world", "world_nether"]  
    $$fallback: ["default"]  # Fallback if no version matches  
```

#### **Example 2: Block Merging**

```yaml
# other_config.yml  
server_properties:  
  motd: "A generic server"  
  online_mode: true  
  # This is a normal map, but contains a versioned block  
  # It's not a value selector because it has regular keys (motd, online_mode)  
  $$1.21.4:  
    # This block gets merged into server_properties  
    motd: "A 1.21.4 Server!"  # Overrides the generic motd  
    new_feature_enabled: true  # Adds a new key  
```

## Debug

Enable debug mode for this configuration by adding a `debug` option

```yaml
items#0:
  default:topaz_helmet:
    debug: true
    template: default:topaz_armor
    arguments:
      part: helmet
      slot: head
```
