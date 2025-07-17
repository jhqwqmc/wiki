---
description: 此页主要解释如何使用模型生成方法。
---

# 🏭 Model Generation

## 一. 导言

[model-generation](model-generation "提及") 正在以YAML 格式创建模型。

当配置多个类似的模型时(例如) 16 羊毛颜色的软体，但在纺织品上只有不同的东西。您通常需要创建同样数量的单独型号。 然而，在Model General中，您可以使用 YAML 格式轻松地管理这些模型继承关系。

{% hint style="danger" %}
"path" 选项中指定的路径(位于同一个配置部分与 `generation`) 必须指向一个不存在的模型路径! 否则，它将与你现有的模式发生冲突。

模型生成**总是一个可选的** 配置。 如果你已经有一个专门的 JSON 模型文件来处理那个块/项目， 你**不需要**使用 `generation` - 只需使用 `path` 指定模型路径。
{% endhint %}

## 配置位置

如果你仔细观察，你会注意到插件在许多地方使用了以下配置格式。&#x20;

```yaml
路径: "xxx:xxx"
generation:
  parent: "minecraft:xxx/xxx"
  textures:
    "xxx": "xxx:xxx"
```

{% hint style="info" %}
事实上，插件支持模型生成，只要可以指定一个模型路径 (`path`)。 当你看到`path`时，它意味着你可以在同一个配置部分使用`generation`。
{% endhint %}

## 参数

### 父级

> 从给定路径中加载不同的模型，形式为[资源位置](https://minecraft.wiki/w/Tutorial:Models#File_path)

"parent" 字段不仅可以引用原版Minecraft提供的默认模型，而且也可以指向您的自定义模型。 您可以在此 [website]上查看所有可用的Minecraft模型(https://misode.github.io/assets/model/)

```yaml
项目 #test:
  default:big_aple:
    material: Appe
    custom-model: 1000
    model:
      类型: minecraft:model
      路径: "minecraft:item/custom/big_apple"
      generation:
        parent: "minecraft:item/apple" # 继承其Apple's model
        # 在gui
        显示一个大应用程序:
          gui:
            scale: 2,2,
  default:big_big_aple:
    material: appe
    custom-model: 1001
    model:
      type: minecraft:model
      path: "namespace:item/custom/big_big_apple"
      generation:
        # 继承
        parent: "minecraft:item/custom/big_apple"
        # 现在手和在Guui
        display:
          firstperson_right:
            scale: 4,4
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fto4U9vBexccrrEoONGwg%2Fimage.png?alt=media&#x26;token=eabaf9a9-a8d6-45a9-bf90-b15ed1b917ad" alt=""><figcaption><p>大苹果</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FdFCvFSb48gXkn8JCLPCF%2Fimage.png?alt=media&#x26;token=34b110c6-34e5-40d3-9772-fec90a2d0903" alt=""><figcaption><p>大苹果</p></figcaption></figure>

### 纹理

> 以[资源位置](https://minecraft.wiki/w/Tutorial:Models#File_path)的形式持有模型的纹理，或可以是另一个纹理变量。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/7Av9LqhtMmYcb2pFXS9X/image.png" alt=""><figcaption></figcaption></figure>

如果我们打算生成基于此模型的方块，则应指定`parent` 和 `textures` 的参数如下：

```yaml
generation:
  parent: "minecraft:block/cube_all"
  textures:
    "particle": "minecraft:block/custom/block_particle"
    "down": "minecraft:block/custom/block_down"
    "up": "minecraft:block/custom/block_up"
    "north": "minecraft:block/custom/block_north"
    "east": "minecraft:block/custom/block_east"
    "south": "minecraft:block/custom/block_south"
    "west": "minecraft:block/custom/block_west"
```

```yaml
items#test:
  default:big_apple:
    material: apple
    custom-model-data: 1000
    model:
      type: minecraft:model
      path: "minecraft:item/custom/big_apple"
      generation:
        parent: "minecraft:item/apple"
        textures:
          # replace the apple's texture with an axe
          layer0: minecraft:item/custom/topaz_axe 
        display:
          gui:
            scale: 2,2,2
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FUwVKVhbAtn1FNPStu82a%2Fimage.png?alt=media&#x26;token=89a11095-54ab-4f07-82fe-b36c61c30bf0" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
`textures`部分下的键值对由父模型决定。

例如：

- `minecraft:item/apple` 继承自 `minecraft:item/generated` 。
- `layer0` 是`minecraft:item/generated`定义的`textures`参数之一。
- 这就是为什么您可以在子模型中覆盖这个纹理 (`Apple`)。

**你可以在这里查看所有可用的Minecraft模型及其纹理** [**website**](https://misode.github.io/assets/model/)

![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FsYTMHVsoTPN2uOsYs9hZ%2Fimage.png?alt=media\&token=e4496f8f-6daa-4da2-a407-89a9444807d0)![](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F0s9Mqk0BpqkZj48WC3mQ%2Fimage.png?alt=media\&token=15b290f8-f945-4384-944a-fb27ec0de698)
{% endhint %}

### gui-light

> 可以是 "front"" 或 "side"。 如果设置为“side”`，模型会变成一个方块。 如果设置为“前端”，模型就像一件平坦物品。 默认为`side\`。

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FSHZtI9R1FFXQulE7pVmM%2Fimage.png?alt=media&#x26;token=5d351073-450f-48cb-945a-a9e72401bfb3" alt=""><figcaption><p>left: front  right: side</p></figcaption></figure>

### 显示

> 保持显示项目模型的不同地点。
>
> - 旋转：指定模型按照方案`x, y, z]`旋转.
> - 翻译：根据方案\`x, y, z]指定模型的位置。 如果值大于80，则显示为80。 如果值小于-80，则显示为 -80。
> - 缩放：根据方案\`x, y, z]指定模型的缩放。 如果值大于4，则显示为4。

可用值： `thirdperson_rightthand`, `thirdperson_lefthand`, `firstperson_rightthand`, `firstperson_lefthand`, `gui`, `head`, `ground`, or `固定`。&#x20;

让我们继续看这个**大小部件** 的例子。 你可能会注意到，当你在右手中时，它的旋转行为是不正确的。 发生这种情况是因为我们覆盖了它的父模型的 `display.firstperson_rightthand` 设置。 现在，让我们修复它！

```yaml
generation:
  父级: "minecraft:item/custom/big_apple"
  显示:
    firstperson_rightthand:
      scale : 4,4,4
      旋转: 0,-90,25
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FDTJGNCHXveVe5Rb4Z9PQ%2Fimage.png?alt=media&#x26;token=f6d88f18-0cad-429f-ad63-eb5808c06a42" alt=""><figcaption></figcaption></figure>
