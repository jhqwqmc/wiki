---
description: This page mainly explains how to manage custom contents
---

# ➕️ Add New Contents

## Resources&#x20;

In the root directory of the plugin (`plugins/CraftEngine/resources/`), all packages are stored, and the names of these packages are arbitrary. Each package consists of two folders and one YAML file. The folders contain configurations and resource packs respectively, while the YAML file holds the metadata for the package.

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

## Pack Meta File

The Meta File is a YAML document that records some fundamental information. Among its entries, the most significant is the `namespace`.

```yaml
author: XiaoMoMi
version: 0.0.1
description: Default Assets for CraftEngine
namespace: default
enable: true # set `false` to disable this pack 
```

{% hint style="info" %}
The effect of a namespace is confined to the second-level nodes under the root node in the YAML hierarchy, exemplified here by "default:palm\_leaves " and "palm\_leaves". Provided that a namespace is specified in `pack.yml`, if a namespace is not explicitly designated, the package namespace will be used by default.

```yaml
blocks:
  default:palm_leaves:
    behavior:
      type: leaves_block
```

is equivalent to

```yaml
blocks:
  palm_leaves:
    behavior:
      type: leaves_block
```

{% endhint %}

## Configuration

```
plugins
  └ CraftEngine
     └ resources
         └ pack
            └ configuration
```

The configuration files are stored in the following folder. The configuration file format supports both json and yml. Moreover, you can create as many subdirectories as you like under the configuration.

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
