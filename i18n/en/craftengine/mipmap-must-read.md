# 🗺️ Mipmap \[MUST READ]

## Introduction

Mipmap determines the anti-aliasing level in Minecraft. Below is a comparison of the differences between Mipmap level 4 and level 0.

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FodziDESugHu27t1CRnHd%2Fimage.png?alt=media&#x26;token=0c20f995-a097-4fc6-8c4a-1b25e77d7a43" alt=""><figcaption><p>mipmap: 4</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FVj5ddbIqysE7Hchz5HMW%2Fimage.png?alt=media&#x26;token=7684ae4c-137c-4f95-9efd-c6d443209781" alt=""><figcaption><p>mipmap: 0</p></figcaption></figure>

Under what circumstances will Mipmap be reduced due to a resource pack?&#x20;

Generally, the Mipmap level will decrease when the width and height of a model texture do not meet the requirement of being a power of 2. Dimensions such as 16x16, 32x16, and 128x32 are valid, while sizes like 15x15, 1x7, and 29x37 are considered invalid (Note: font images are exempt from this restriction).

{% hint style="success" %}
If you don't want to fix those badly made textures, you can enable the plugin's **obfuscation** option, which will automatically fix the mipmap for you. It's incredibly simple! At the same time, the plugin will automatically separate font images that should not be placed within the atlas path to prevent them from polluting the Mipmap.

**However, please note that the plugin will not fix textures that come with .mcmeta files.**

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

{% hint style="warning" %}
When you notice Mipmap issues in your client, please open your client logs! They will tell you what caused the Mipmap level to decrease. `Texture xxx:xxx with size xxx limits mip level from 4 to 0`
{% endhint %}
