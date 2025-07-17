# ⚙️ Block Settings

## hardness

Determines how long it takes the player to destroy this block (Default: 2.0)

```yaml
hardness: 0.5
```

## resistance

Determines the probability of the block surviving the explosion (Default: 2.0)

```yaml
resistance: 0.5
```

## is-randomly-ticking

Determines whether the block state accepts random ticks, which is relevant for some block behaviors, such as leaves. (Default: false)

```yaml
is-randomly-ticking: true
```

## push-reaction&#x20;

Determines how the block reacts to piston pushes. Please note that some reactions may not work well with certain block types due to client visual sync issues. This problem will be fixed in future versions. (Default: NORMAL)

- NORMAL   Pistons can push and pull this block normally.
- DESTROY   Blocks pushed by pistons are destroyed instantly.
- BLOCK   Pistons cannot move this block.
- IGNORE  Seems to behave like PUSH\_ONLY but can stick to sticky blocks
- PUSH\_ONLY   Blocks can be pushed by pistons, but cannot be retracted. Do not stick to sticky blocks.

```yaml
push-reaction: NORMAL
```

## map-color

Determines what color the block is displayed on the map. Available colors can be found on [https://minecraft.wiki/w/Map\_item\_format](https://minecraft.wiki/w/Map_item_format) (Default: 0)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/8WeafQSqNMDWGWeLd1NI/image.png" alt=""><figcaption></figcaption></figure>

```yaml
map-color: 36
```

## burnable

Determines whether this block can be ignited by the environment (Default: false)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/yfgOaG8u4n8BGK600ymB/image.png" alt=""><figcaption></figcaption></figure>

```yaml
burnable: true
```

## fire-spread-chance

Determines how long the block can burn. A longer burn time means a greater chance of spreading fire to surrounding blocks. (Default: 0)

```yaml
fire-spread-chance: 100  # 0-100
```

## burn-chance

Determines the probability of being ignited (Default: 0)

```yaml
burn-chance: 30  # 0-100
```

## item

Determines the item that this block corresponds to. This is usually used to get blocks in creative mode with middle click. (Default: null)

```yaml
item: default:xxx_block_item
```

## replaceable

Determines whether to replace the block at its original location when the player uses a block to interact with this block (Default: false)

```yaml
replaceable: false
```

## is-redstone-conductor

Determines whether this block is a redstone signal conductor (Default: UNDEFINED)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/eneBtRUIfZA3e7IkDj43/image.png" alt=""><figcaption></figcaption></figure>

```yaml
is-redstone-conductor: true
```

## is-suffocating

Determines whether the player will take suffocation damage (Default: UNDEFINED)

```yaml
is-suffocating: true
```

## is-view-blocking

Whether to block the line of sight. However, this option is useless for players, but it will affect some entity mechanisms on the server. (Default: UNDEFINED)

```yaml
is-view-blocking: true
```

## sounds

Determines the sound of the block in various situations (Default: null)

- fall    When the player falls on this block
- hit    When the player digs this block
- break    When the player breaks this block
- step    When the player walks on this block
- place    When the player places this block
- land   When the block falls on ground (For falling blocks)
- destroy   When the block falls on ground and break (For falling blocks)

```yaml
sounds:
  break: minecraft:block.deepslate.break
  step: minecraft:block.deepslate.step
  place: minecraft:block.deepslate.place
  hit: minecraft:block.deepslate.hit
  fall: minecraft:block.deepslate.fall
  land: minecraft:block.anvil.land
  destroy: minecraft:block.anvil.destroy
```

{% hint style="info" %}
You can configure like this to precisely control the volume and pitch

```yaml
sounds:
  break:
    id: minecraft:block.deepslate.break
    pitch: 0.5
    volume: 0.25
  step: minecraft:block.deepslate.step
```

{% endhint %}

## require-correct-tools

Determines if correct tool is required for the drops (Default: false)

```yaml
require-correct-tools: false
```

## respect-tool-component

Decides if `minecraft:tool` component's `correct_for_drops` option should work as `correct-tools` below (Default: false)

```yaml
respect-tool-component: false
```

## correct-tools

Determines the correct tool required to mine this block, otherwise no item will be dropped (Default: null)

```yaml
correct-tools:
  - minecraft:wooden_pickaxe
  - minecraft:stone_pickaxe
  - minecraft:iron_pickaxe
  - minecraft:golden_pickaxe
  - minecraft:diamond_pickaxe
  - minecraft:netherite_pickaxe
```

{% hint style="success" %}
If `correct-tools` is set, `require-correct-tools` would be true
{% endhint %}

## incorrect-tool-dig-speed

Slows down the dig speed if the tool is incorrect (Default: 0.3)

```yaml
incorrect-tool-dig-speed: 0.3 # 0~1
```

## tags

Tags determine the properties of many blocks. For example, using minecraft:mineable/axe will make your blocks mine faster with an axe. [useful-tags](block-settings/useful-tags "mention") (Default: null)

```yaml
tags:
  - minecraft:mineable/axe
  - minecraft:logs_that_burn
  - minecraft:logs
  - minecraft:completes_find_tree_tutorial
```

## client-bound-tags

This would only work for vanilla blocks

```yaml
client-bound-tags:
  - minecraft:beacon_base_blocks
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fwnpy7kYwGeRAiJbBTdQ3%2Fimage.png?alt=media&#x26;token=79a6c177-14af-4798-8f49-19c4ca688131" alt=""><figcaption></figcaption></figure>

## instrument

Determines what instrument the note block will play when it is above this block. (Default: harp)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/NhpOFlvMUaWf3xPe3Byo/image.png" alt=""><figcaption></figcaption></figure>

```yaml
instrument: BASEDRUM
```

## fluid-state&#x20;

Decides the fluid state of this block state (Default: empty)

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FNKagcQZqIIVMxX7odHKU%2Fimage.png?alt=media&#x26;token=0f500b1f-bde4-4e28-84de-9ea9a70a7ba4" alt=""><figcaption></figcaption></figure>

```yaml
fluid-state: water
```

## support-shape

Determines the support shape provided by the block. By default, custom blocks will use the **support-shape** of their corresponding visual state. However, you can manually specify the **support-shape** of a vanilla block here instead.

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fd4ZOrffIv47Tzkw2r2fc%2Fimage.png?alt=media&#x26;token=223541ed-7b5f-451a-b909-038fae926f7e" alt=""><figcaption></figcaption></figure>

```yaml
support-shape: minecraft:stone
```

{% hint style="warning" %}
The remaining block settings are all related to the light system. CraftEngine has implemented partial light effects as much as possible without affecting server performance. Visual issues with the light system on the client side are normal and in most cases I can't fix them.

The block's occlusion of **skylight** is entirely determined by the **client-side** and **cannot be fixed** by sending packets from the server. Therefore, the **block-light** and **can-occlude** settings **only affect block-emitted light**, not skylight.
{% endhint %}

## luminance

Determines the light intensity of the block (Default: 0)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/UCgtZHRVaWqDMLV52UAB/image.png" alt=""><figcaption></figcaption></figure>

```yaml
luminance: 15
```

## can-occlude

Determines whether this block can block light. This also determines whether the block can turn below block into another type. (For instance grass\_block -> dirt) (Default: undefined)

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/msw2GomMjl3nfMAjxIGd/image.png" alt=""><figcaption><p>occlude: true</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/C116bz0ylSfikY93jQYN/image.png" alt=""><figcaption><p>occlude: false</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2Fx3zMrfKsVSu4lEhU9Iru%2Fimage.png?alt=media&#x26;token=0c9e7da8-8bf0-42e9-883b-79aad4232a4c" alt=""><figcaption><p>occlude: false</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FIQ62BLMGHWhQYfQbbbyZ%2Fimage.png?alt=media&#x26;token=8a5ff1d2-6d91-44b8-9bb6-ef701d1296e5" alt=""><figcaption><p>occlude: true</p></figcaption></figure>

```yaml
can-occlude: false
```

## block-light

Determines how much light level is reduced after passing through this block (Default: undefined)

```yaml
block-light: 0
```

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FIARHS7xk9UHdF4ZQ12pC%2Fimage.png?alt=media&#x26;token=199f84cd-ede7-40f3-8cd5-1713f2896886" alt=""><figcaption><p>block-light: 15</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FFJBuj7nclW05zBTaWw6n%2Fimage.png?alt=media&#x26;token=c2dd379c-0fa7-4c51-8778-667357cf6f03" alt=""><figcaption><p>block-light: 7</p></figcaption></figure>

<figure><img src="https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2F5uiR2P5WZBE6aVvLkiUi%2Fimage.png?alt=media&#x26;token=c35aa388-96de-4354-abf2-a6dd21cc47ef" alt=""><figcaption><p>block-light: 0</p></figcaption></figure>

## propagate-skylight

{% hint style="danger" %}
**This option has almost no effect, as the client will predict sky light updates.**
{% endhint %}

Determines whether natural light can pass through this block.

```yaml
propagate-skylight: true
```
