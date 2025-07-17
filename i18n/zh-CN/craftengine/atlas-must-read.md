# :round_plappin: Atlas \[MUST READ]

{% hint style="success" %}
如果您不想自己写入地图集文件 您可以启用插件的 **obfuscation** 选项，这将自动处理您的地图集。 这是非常简单的！

```yaml
#config.yml
资源包：
  保护：
    obfuscation：
      已启用：true
      资源位置：
        已启用：true
```

{% endhint %}

## 一. 导言

自Minecraft 1.19以来，资源包引入了“atlas”概念，这一概念决定了阅读纹理图像的路径。 默认情况下，Minecraft只能从 `/textures/block` 和 `/textures/item` 目录加载纹理，因为默认的 `atlas` 文件只支持这两个文件夹。

```json
{
    "sources": [
        {
            "type": "directory",
            "source": "block",
            "prefix": "block/"
        },
        {
            "type": "directory",
            "source": "item",
            "prefix": "item/"
        },
        ...more
    ]
}

```

如果您将纹理路径从 `/textures/block/custom` 移动到 `/textures/custom` ， Minecraft将无法加载这些纹理，因为它们不在图集定义的范围之内。 地图集之外的纹理将显示为紫色和黑色检查的正方形，如下面的图像所示。

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FRQZMAM1TnobkCpWCAuPD%2Fimage.png?alt=media&#x26;token=2a25a84d-c323-440f-9c67-decd171774df" alt=""><figcaption></figcaption></figure>

## 创建地图集

要创建地图集路径，您只需在以下路径向资源包添加一个文件：“resourcepack/assets/minecraft/atlases/blocks.json”。 下面是一个简单的例子，可以将 `custom` 路径添加到地图集：

```yaml
{
    "sources": [
        {
            "type": "directory",
            "source": "custom",
            "prefix": "custom/"
        }
    ]
}
```

{% file src="https:///1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FjafUqhjjpxfRdlPJ6v9Xk%2Fblocks.json?alt=media&token=9f43d1c-4d9c-4818-ac8e-0d16ad1dc56f" %}

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FQIyqzq01rJZeLlvMTg10%2Fimage.png?alt=media&#x26;token=2899af97-58ed-4f16-8d95-056b2223c74a" alt=""><figcaption></figcaption></figure>

添加这样一个 JSON 文件后，重新加载资源包，您将看到更改生效。

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fw6QIh0iqDdLtADU6IqqZ%2Fimage.png?alt=media&#x26;token=7235dd04-76a9-41b7-b17c-559f950bf2ce" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
当您有多个包含地图集配置的文件时，您可以检查 [file-conflict](resource-pack/file-conflict "提及") 合并地图集。 默认情况下，插件已经为您配置了此选项。
{% endhint %}

{% hint style="danger" %}
**纹理图集要求**
地图集目录内的所有纹理必须符合两个尺寸的电量(e)。 ., 16x16, 32x16, 64x128, 以保持完整的 Mipmap 功能。 不符合要求的纹理会自动降低Mipmap 级别。 详细的 Mipmap 准则，请参阅 [mipmap-must-read](mipmap-must-read "提及")

**暴击分离通知**\
字体资产(例如，21×7级图标)必须与模型纹理分开存储。 主要原因：

1. **Mipmap 不兼容**: 字体纹理不需要 Mipmap
2. **Quality Protection**: Co-location 强制在附近的纹理上不必要地降级Mipmap。
3. **Compliance**：违反Minecraft的纹理管理最佳做法

保持地图集管理的纹理和 GUI/字体元素之间的严格隔离，以保持渲染质量。
{% endhint %}
