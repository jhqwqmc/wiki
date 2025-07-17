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

配置文件存储于以下目录中，支持json和yml两种格式。 您可以在配置目录下自由创建任意数量的子目录。 此外，您可以在配置下创建尽可能多的子目录。

{% hint style="success" %}
在 YAML 配置中，不允许以下格式：

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

因此，您需要在配置部分名称后添加 `# + 任何标识符` 。 允许您在单个的 YAML 文件中配置同类型的多个部分。

```yaml
items#0:
  default:topaz_helmet:
    template: default:topaz_armor
    参数:
      part : helmet
      slot: head
items#1:
  default:topaz_boots:
    template: default:topaz_armor
    参数:
      part : boots
      slot: feet
```

{% endhint %}

## ResoucePack

```
plugins
  craftEngine
     de resources
         capk
            cetcepack
               sedresources
               collay_floor
               tanticpack.mcta
               pack.png
```

请确保您资源包的目录结构如以下图所示，否则可能导致一些合并问题。 叠加层\_folder, pack.mcmeta, 和 pack.png 文件不是强制性的。

## 基于版本的配置

CraftEngine 允许您为不同的服务器版本添加基于版本的配置。 Just use keys formatted like `$$version` in your YAML file.

#### **示例1：值选择**

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

#### **示例2：块合并**

```yaml
# 其他配置 ml  
server_properties:  
  motd: "一个通用服务器"  
  online_mode: true  
  # 这是一个正常的地图 但包含一个版本块  
  # 它不是一个值选择器，因为它有常规键(模组， online_mode  
  $1。 1.4:  
    # 此块被合并到 server_properties  
    motd: "A 1.21。 服务器！" # 覆盖通用模组  
    new_feature_enabled：true # 添加一个新密钥  
```

## Debug

添加一个 `debug` 选项以启用此配置的调试模式

```yaml
items#0:
  default:topaz_helmet:
    debug: true
    模板: default:topaz_armor
    参数:
      part : helmet
      slot: head
```
