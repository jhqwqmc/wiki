# 🐚  Commands

## Item Commands



## Debug Commands

### appearance-state-usage

`/ce debug appearance-state-usage [block_type]`

The command is used to retrieve the usage status of excess appearances for a specified block type. The red sections indicate states that are already in use, while the green sections represent available, unused states. When you hover your mouse over these sections, you can view the specific states and identify which custom states are utilizing them.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ZsqvpYSQpt2o4uhDUE3C/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/kMmfb8UeeAhOKASNSMx5/image.png" alt=""><figcaption><p>appearance state in use</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/blSWDyawRrCQDbXhfvGB/image.png" alt=""><figcaption><p>free state</p></figcaption></figure>

### real-state-usage

`/ce debug real-state-usage [block_type]`

This command is similar to the one mentioned above, but the key difference lies in its function to inspect the available real states. When you register additional real states in the `additional-real-blocks.yml` file, the number of real states may exceed the number of available appearances.\


<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/DXynVOE87LdmEvt821of/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/KD4bwQJMH8vYjvQnr8M2/image.png" alt=""><figcaption><p>real state in use</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/tI4QxOAKRLBDLgZgQ4cQ/image.png" alt=""><figcaption><p>free state</p></figcaption></figure>

{% hint style="warning" %}
In the image below, the upper section displays the available appearance states for oak leaves, while the lower section shows the available real states for oak leaves.\
You can use the command to experience the difference between them.

```
/ce debug appearance-state-usage minecraft:oak_leaves
```

```
/ce debug real-state-usage minecraft:oak_leaves
```
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/1In5q6KSkwz62u0nsEvh/image.png" alt=""><figcaption></figcaption></figure>

### item-data

`/ce debug item-data`

This command allows you to inspect the item data (such as NBT or components) of the item you are currently holding.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/aPpHMG3j3evHchOBYGia/image.png" alt=""><figcaption></figcaption></figure>

### get-block-internal-id

`/ce debug get-block-internal-id [custom_block_state]`

This command is used to retrieve the server-side real block name corresponding to a custom block, and is commonly utilized in tools like WorldEdit and data packs.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/XQUPusg2dgKs7uOSvab5/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/W7IlQqRjFAGLxMvYl5Fu/image.png" alt=""><figcaption></figcaption></figure>

### get-block-state-registry-id

`/ce debug get-block-state-registry-id [real_block_state]`

This command is used to obtain the registry ID of the corresponding block state (not commonly used).

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/b52WtGRjXNVDwqVG2yJc/image.png" alt=""><figcaption></figcaption></figure>

### target-block

`/ce debug target-block [--this]`

The 'target-block' is used to inspect the data of the block that the mouse is pointing at (or use the '--this' flag to obtain the current position). It includes the actual block ID and the CraftEngine block state. If the block has custom tags, they will also be displayed.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/9klMqxUp0n5OMxDNgzBF/image.png" alt=""><figcaption></figcaption></figure>
