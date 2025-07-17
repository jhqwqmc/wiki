# 🔠 全局变量

### 示例用法

```yaml
global-variables:
  test: "<!i><#FF8C00><arg:0>'s <arg:1>"

items#topaz_gears:
  default:topaz_rod:
    material: fishing_rod
    custom-model-data: 1000
    settings:
      tags:
        - "default:topaz_tools"
    data:
     components:
        minecraft:max_damage: 10000
    client-bound-data:
      item-name: "<global:test:'<arg:player.name>':'<i18n:item.topaz_rod>'>"
      tooltip-style: minecraft:topaz
    model:
      template: default:model/simplified_fishing_rod_2d
      arguments:
        path: minecraft:item/custom/topaz_rod
        cast_path: minecraft:item/custom/topaz_rod_cast
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F79kxK9uQ5dNFfsKILnT9%2Fimage.png?alt=media&#x26;token=16fda105-0db4-4ef8-8b23-6943a2aec895" alt=""><figcaption></figcaption></figure>
