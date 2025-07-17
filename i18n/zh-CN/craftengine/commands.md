# 🐚 命令

## 项目命令

## 调试命令

### 外观状态使用

`/ce 调试外观状态-使用 [block_type]`

该命令用于检索指定区块类型超量外观的使用状态。 红部分显示已经在使用的状态，而绿部分则表示可用的状态。 当你将鼠标悬停在这些部分时，你可以查看特定的状态并确定哪些自定义状态正在使用它们。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ZsqvpYSQpt2o4uhDUE3C/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/kMmfb8UeeAhOKASNSMx5/image.png" alt=""><figcaption><p>appearance state in use</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/blSWDyawRrCQDbXhfvGB/image.png" alt=""><figcaption><p>free state</p></figcaption></figure>

### 实际使用情况

`/ce 调试真实状态的使用 [block_type]`

这个命令与上述命令相似，但关键的区别在于其检查现有实际状态的职能。 当您在 `additional-retial-blocks.yml` 文件中注册额外的真实状态时，真实状态的数量可能会超过可用外观的数量。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/DXynVOE87LdmEvt821of/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/KD4bwQJMH8vYjvQnr8M2/image.png" alt=""><figcaption><p>real state in use</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/tI4QxOAKRLBDLgZgQ4cQ/image.png" alt=""><figcaption><p>free state</p></figcaption></figure>

{% hint style="warning" %}
在下面的图像中，上面部分显示橡皮叶的可用外观状态， 下面部分显示可用的橡皮叶的真实状态。
您可以使用命令体验它们之间的差异。

```
/ce 调试外观状态-使用minecraft:oak_left
```

```
/ce 调试实际使用的minecraft:oak_let
```

{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/1In5q6KSkwz62u0nsEvh/image.png" alt=""><figcaption></figcaption></figure>

### 项目数据

`/ce debug item-data`

此命令允许您检查您当前持有的物品的数据(例如NBT或组件)。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/aPpHMG3j3evHchOBYGia/image.png" alt=""><figcaption></figcaption></figure>

### 获取block-internal-id

`/ce 调试get-block-internal-id [custom_block_state]`

此命令用于检索与自定义方块相对应的服务器端真实方块名称 并且通常用于Worlded和数据包等工具。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/XQUPusg2dgKs7uOSvab5/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/W7IlQqRjFAGLxMvYl5Fu/image.png" alt=""><figcaption></figcaption></figure>

### get-block-state-registry-id

`/ce 调试get-block-state-id-registry-id [real_block_state]`

此命令用于获取相应区块状态的注册表ID(不常用)。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/b52WtGRjXNVDwqVG2yJc/image.png" alt=""><figcaption></figcaption></figure>

### target-block

`/ce debug target-block [--this]`

"target-block"用于检查鼠标指向的方块的数据(或使用“--this”标志获取当前位置)。 它包含实际方块ID和 CraftEngine 方块状态。 如果方块有自定义标签，它们也会被显示。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/9klMqxUp0n5OMxDNgzBF/image.png" alt=""><figcaption></figcaption></figure>
