# 🗺️ Mipmap \[MUST READ]

## 一. 导言

Mipmap 决定Minecraft中的抗锯齿水平。 下面是Mipmap 4级和0级之间差异的比较。

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FodziDESugHu27t1CRnHd%2Fimage.png?alt=media&#x26;token=0c20f995-a097-4fc6-8c4a-1b25e77d7a43" alt=""><figcaption><p>mipmap: 4</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FVj5ddbIqysE7Hchz5HMW%2Fimage.png?alt=media&#x26;token=7684ae4c-137c-4f95-9efd-c6d443209781" alt=""><figcaption><p>mipmap: 0</p></figcaption></figure>

Under what circumstances will Mipmap be reduced due to a resource pack?&#x20;

一般情况。 当模型纹理的宽度和高度不符合2功率要求时，Mipmap 水平将会下降。 16x16、32x16和128x32等尺寸是有效的，而大小为 15x15，1x7 和 29 x37 被视为无效(注：字体图像不受此限制)。

{% hint style="success" %}
如果您不想修复那些制造不良的纹理， 您可以启用插件的 **obfuscation** 选项，这将自动为您修复mipmap 。 这是非常简单的！ 同时， 插件将自动分离不应放在地图集路径内的字体图像以防止它们污染Mipmap。

**不过请注意，插件将不会修复带有.mcmeta 文件的纹理。**

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

{% hint style="warning" %}
当您注意到您客户端中的Mipmap 问题时，请打开您的客户端日志！ 他们会告诉你什么导致Mipmap 水平下降。 `纹理 xxx:xxx 大小为 xxx 限制 mip 级别从 4 到 0`
{% endhint %}
