# 📍 Atlas \[MUST READ]

{% hint style="success" %}
If you don't want to write the atlas file yourself, you can enable the plugin's **obfuscation** option, which will automatically handle the atlas for you. It's incredibly simple!

```yaml
#config.yml
resource-pack:
  protection:
    obfuscation:
      enable: true
      resource-location:
        enable: true
```

{% endhint %}

## Introduction

Since Minecraft 1.19, resource packs have introduced the concept of "atlas," which determines the paths from which texture images are read. By default, Minecraft can only load textures from the `/textures/block` and `/textures/item` directories because the default `atlas` file only supports these two folders.

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

If you move the texture paths from `/textures/block/custom` to `/textures/custom`, Minecraft will be unable to load these textures because they fall outside the scope defined by the atlas. Textures located outside the atlas will appear as purple-and-black checkered squares, as shown in the image below.

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FRQZMAM1TnobkCpWCAuPD%2Fimage.png?alt=media&#x26;token=2a25a84d-c323-440f-9c67-decd171774df" alt=""><figcaption></figcaption></figure>

## Create Atlas

To create an atlas path, you simply need to add a file to your resource pack at the following path: `resourcepack/assets/minecraft/atlases/blocks.json`. Below is a simple example that adds the `custom` path to the atlas:

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

{% file src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FjafUqhjPxfRdlPJ6v9Xk%2Fblocks.json?alt=media&token=9f43d1ce-4d9c-4818-ac8e-0d16ad1dc56f" %}

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FQIyqzq01rJZeLlvMTg10%2Fimage.png?alt=media&#x26;token=2899af97-58ed-4f16-8d95-056b2223c74a" alt=""><figcaption></figcaption></figure>

After adding such a JSON file, reload the resource pack, and you will see the changes take effect.

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fw6QIh0iqDdLtADU6IqqZ%2Fimage.png?alt=media&#x26;token=7235dd04-76a9-41b7-b17c-559f950bf2ce" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
When you have multiple files containing atlas configurations, you can check [file-conflict](resource-pack/file-conflict "mention") to merge the atlases. By default, the plugin has already configured this option for you.
{% endhint %}

{% hint style="danger" %}
**Texture Atlas Requirements**\
All textures within the atlas directory must conform to power-of-two dimensions (e.g., 16×16, 32×16, 64×128) to maintain full Mipmap functionality. Non-compliant textures will trigger automatic Mipmap level reduction. For detailed Mipmap guidelines, consult [mipmap-must-read](mipmap-must-read "mention")

**Critical Separation Notice**\
Font assets (e.g., 21×7 rank icons) must be stored separately from model textures. Key reasons:

1. **Mipmap Incompatibility**: Font textures don't require Mipmap
2. **Quality Protection**: Co-location forces unnecessary Mipmap downgrades on adjacent textures
3. **Compliance**: Violates Minecraft's texture management best practices

Maintain strict isolation between atlas-managed textures and GUI/font elements to preserve rendering quality.
{% endhint %}
