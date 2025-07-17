# 💦 混凝土粉红色块

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FTZqK3Gho57vlt2oJEPJy%2Fimage.png?alt=media&#x26;token=89aadbd0-381d-4b68-b315-48133832ad61" alt=""><figcaption></figcaption></figure>

[concrete-powder-block](concrete-powder-block "提及") 是一种在接触水时强化的方块类型。 配置示例如下：

```yaml
块:
  默认:followder_block:
    behavior:
      type: concrete_powder_block
      solid-block: default:solid_followder_block
```

{% hint style="danger" %}
目前，自定义方块在降落实体状态下无法在接触水时转换为方块。 这是因为这个代码在Minecraft中被硬编码，我们不能更改它的行为逻辑。
{% endhint %}
