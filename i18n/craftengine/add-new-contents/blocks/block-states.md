# 🔣 Block States

## Introduction

In Minecraft's block system, each block has one or more block states. For example, wood has a facing direction, and leaves have different distances. These states determine how the block behaves and appears in the game.

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/u2u3K5ZjVw9Qf7gLcp3k/image.png" alt=""><figcaption></figcaption></figure>

## Examples

Here are three examples to explain how to create a block with a single state and a block with multiple states in Minecraft:

### **Example 1: Creating a Block with a Single State**

```yaml
blocks:
  default:chinese_lantern:
    state:
      id: 15
      state: note_block:15
      model:
        path: "minecraft:block/custom/chinese_lantern"
        generation:
          parent: "minecraft:block/cube_column"
          textures:
            "end": "minecraft:block/custom/chinese_lantern_top"
            "side": "minecraft:block/custom/chinese_lantern"
```

{% hint style="info" %}
The **internal ID** (id) represents a unique identifier for blocks. The maximum number of internal IDs is determined by the sum of two factors:

1. **Available Block Appearance States**: These are defined in the `mappings.yml` file. For a single block type, the more block states you "release," the higher the number of available appearance states.
2. **Additionally Registered Real States**: These are added via the `additional-real-blocks.yml` file. This configuration allows you to manually register extra real serverside states for specific blocks, further increasing the total pool of internal IDs.
{% endhint %}

{% hint style="warning" %}
**Why Register Additional Real Blocks?**\
Some blocks in the game (e.g., vanilla Minecraft leaves) have more **block states** than actual **appearance variations**. For example:

* **Vanilla leaves** have **28 block states** (technical properties like distance, persistant, etc.), but only **2 distinct visual appearances** (e.g., oak leaves with/without water).
* The unused block states (e.g., 26 out of 28) can be repurposed to create **new custom blocks** (e.g., palm leaves and etc.).

**The Challenge**

Creating a **new leaf type** with unique functionality might require **28 server-side states** even if it only uses **2 visual appearances**. However, only **26 serverside real states** are available from vanilla leaves, creating a **shortage of 2 states**.
{% endhint %}

{% hint style="info" %}
**`state`** refers to the **vanilla block state appearance** used by a custom block state.\
For example, **`noteblock:15`** means the **16th released Note Block state** in `mappings.yml` (counting starts at 0).
{% endhint %}

{% hint style="success" %}
You can configure state like this if you want to precisely control the state in use

```yaml
state: minecraft:note_block[instrument=hat,note=0,powered=false]
```
{% endhint %}

{% hint style="info" %}
#### **Model Option**

The **`model`** option specifies the file path to the custom model used by this block.

#### **Generation Option**

The **`generation`** option is **optional**. If you're unsure what this setting does, refer to the documentation linked below: [model-generation](../model-generation "mention")
{% endhint %}

### **Example 2: Creating a Block with One Custom Property**

{% hint style="danger" %}
**For blocks with multiple states, use `states` instead of `state`.**
{% endhint %}

```yaml
blocks:
  default:palm_log:
    states:
      properties:
        axis:
          type: axis
          default: y
      appearances:
        axisY:
          state: "note_block:0"
          model:
            path: "minecraft:block/custom/stripped_palm_log"
            generation:
              parent: "minecraft:block/cube_column"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisX:
          state: "note_block:1"
          model:
            x: 90
            y: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisZ:
          state: "note_block:2"
          model:
            x: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
      variants:
        axis=x:
          appearance: axisX
          id: 0
        axis=y:
          appearance: axisY
          id: 1
        axis=z:
          appearance: axisZ
          id: 2
```

**This configuration file may seem lengthy and complex, but we can simplify everything using the template system.**\
&#xNAN;_(If you haven’t read the template system tutorial yet, make sure to study it after learning about `states`!)_

Let’s break down `states` into three key sections for clarity:

{% hint style="warning" %}
**1. Define Block Properties**

Defines the **block properties** (e.g., `facing`, `level`, `lit`) that determine how the block behaves or interacts. For detailed info read [properties](block-states/properties "mention")

```yaml
properties:
  axis:             # Property name (e.g., axis, color)
    type: axis      # Data type (e.g., axis, boolean, int, string)
    default: y      # Default state (e.g., y for vertical orientation)
```
{% endhint %}

{% hint style="warning" %}
**2. Configure Appearances**

Appearances define the used visual states.

```yaml
appearances:
  axisY:            # Unique appearance name (e.g., axisY, red)
    state: "note_block:0"  # Vanilla state (e.g., note_block:0)
    model:
      path: "minecraft:block/custom/stripped_palm_log"  # Path to model file
      generation:   # (Optional) Procedural model generation rules
        parent: "minecraft:block/cube_column"  # Base model template
        textures:    # Override textures for the parent model
          "end": "minecraft:block/custom/palm_log_top"
          "side": "minecraft:block/custom/palm_log"
```
{% endhint %}

{% hint style="warning" %}
**3. Map Variants**

Variants link property combinations to specific appearances and internal IDs.

```yaml
variants:
  axis=x:           # Property condition (e.g., axis=x, color=red)
    appearance: axisX  # Appearance to use for this variant
    id: 0           # Unique internal ID (must be unique per variant)
    settings:       # Optional settings override
      ...
```

If you don't know how to configure settings, read [block-settings](block-settings "mention")
{% endhint %}

### **Example 3: Creating a Block with Multiple Properties**

{% hint style="success" %}
Don’t worry if this seems overwhelming at first! In Minecraft, **only a handful of vanilla blocks have a high number of states**, which is why most custom blocks are built using these "state-rich" vanilla blocks as a foundation. Let’s break it down step by step.
{% endhint %}

```yaml
default:palm_leaves:
  states:
    properties:
      waterlogged:
        type: boolean
        default: false
      persistent:
        type: boolean
        default: true
      distance:
        type: int
        default: 7
        range: 1~7
    appearances:
      default:
        state: "oak_leaves[distance=1,persistent=false,waterlogged=false]"
        model:
          path: "minecraft:block/custom/palm_leaves"
          generation:
            parent: "minecraft:block/leaves"
            textures:
              "all": "minecraft:block/custom/palm_leaves"
      waterlogged:
        state: "oak_leaves[distance=1,persistent=false,waterlogged=true]"
        model:
          path: "minecraft:block/custom/palm_leaves"
    variants:
      distance=1,persistent=false,waterlogged=false:
        appearance: "default"
        id: "0"
      distance=2,persistent=false,waterlogged=false:
        appearance: "default"
        id: "1"
      distance=3,persistent=false,waterlogged=false:
        appearance: "default"
        id: "2"
      distance=4,persistent=false,waterlogged=false:
        appearance: "default"
        id: "3"
      distance=5,persistent=false,waterlogged=false:
        appearance: "default"
        id: "4"
      distance=6,persistent=false,waterlogged=false:
        appearance: "default"
        id: "5"
      distance=7,persistent=false,waterlogged=false:
        appearance: "default"
        id: "6"
        settings:
          is-randomly-ticking: true
      distance=1,persistent=true,waterlogged=false:
        appearance: "default"
        id: "7"
      distance=2,persistent=true,waterlogged=false:
        appearance: "default"
        id: "8"
      distance=3,persistent=true,waterlogged=false:
        appearance: "default"
        id: "9"
      distance=4,persistent=true,waterlogged=false:
        appearance: "default"
        id: "10"
      distance=5,persistent=true,waterlogged=false:
        appearance: "default"
        id: "11"
      distance=6,persistent=true,waterlogged=false:
        appearance: "default"
        id: "12"
      distance=7,persistent=true,waterlogged=false:
        appearance: "default"
        id: "13"
      distance=1,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "14"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=2,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "15"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=3,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "16"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=4,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "17"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=5,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "18"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=6,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "19"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=7,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "20"
        settings:
          resistance: 1200.0
          burnable: false
          is-randomly-ticking: true
          fluid-state: water
      distance=1,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "21"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=2,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "22"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=3,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "23"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=4,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "24"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=5,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "25"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=6,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "26"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=7,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "27"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
```

#### **Step 1: Define Properties**

We start by declaring three properties for the block, which determine its possible variants:

```yaml
properties:
  waterlogged:
    type: boolean
    default: false  # Whether the block contains water
  persistent:
    type: boolean
    default: true   # Whether the block persists (e.g., leaves decay if false)
  distance:
    type: int
    default: 7      # Distance from the nearest log (1-7)
    min: 1
    max: 7
```

#### **Total Variants**

The combination of these properties creates **2 × 2 × 7 = 28 variants**:

* **`waterlogged`**: 2 states (`true`/`false`).
* **`persistent`**: 2 states (`true`/`false`).
* **`distance`**: 7 states (values `1` to `7`).

#### **Step 2: Define Visual States**

Even though this block uses **28 server-side states** (combinations of `waterlogged`, `persistent`, and `distance`), we only need **two visual appearances** to represent it. Here’s how we achieve this:

```yaml
appearances:
  default:
    # (non-waterlogged) leaves
    state: "oak_leaves[distance=1,persistent=false,waterlogged=false]"
    model:
      path: "minecraft:block/custom/palm_leaves"
      generation:
        parent: "minecraft:block/leaves"  # Inherit vanilla leaves model
        textures:
          "all": "minecraft:block/custom/palm_leaves"  # Custom texture
  waterlogged:
    # waterlogged leaves
    state: "oak_leaves[distance=1,persistent=false,waterlogged=true]"
    model:
      path: "minecraft:block/custom/palm_leaves"  # Same model as default
```

#### **Step 3: Assign Internal IDs and Override Behaviors**

Map all possible block state combinations to **internal IDs** and appearances. Some variants require overriding vanilla behaviors (e.g., waterlogged blocks being explosion-proof, `distance=7` blocks triggering `randomTick`).

**Example Configuration**

```yaml
variants:
  distance=1,persistent=false,waterlogged=false:
    appearance: "default"  # Uses the "default" visual state
    id: 0                  # Unique internal ID
  distance=2,persistent=false,waterlogged=false:
    appearance: "default"  # Reuse the "default" visual state
    id: 1
```

#### **Advanced Overrides**

To customize block behavior for specific states, add logic like this:

```yaml
variants:
  distance=7,persistent=false,waterlogged=false:
    appearance: "default"
    id: "6"
    settings:
      is-randomly-ticking: true
  distance=7,persistent=true,waterlogged=true:
    appearance: "waterlogged"
    id: "27"
    settings:
      resistance: 1200.0
      burnable: false
```

## Block Models

```yaml
# Part of block state config
state:
  id: 0
  state: tripwire:0
  models:
    - path: "minecraft:block/custom/fairy_flower_1"
      weight: 100
    - path: "minecraft:block/custom/fairy_flower_2"
      weight: 5
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_2"
    - path: "minecraft:block/custom/fairy_flower_3"
      weight: 5
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_3"
    - path: "minecraft:block/custom/fairy_flower_4"
      weight: 5
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_4"
    - path: "minecraft:block/custom/fairy_flower_5"
      weight: 1
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_5"
```

{% hint style="success" %}
The model of the block supports multiple models with random weights. When using it, you simply need to change "model" to "models" and provide a list containing all the models.
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/wZsDZu6S6d2iyfANAoLl/image.png" alt=""><figcaption></figcaption></figure>

```yaml
# Part of block state template
appearances:
  axisY:
    state: "${base_block}:${vanilla_id}"
    model:
      path: "${model_vertical_path}"
      generation:
        parent: "minecraft:block/cube_column"
        textures:
          "end": "${texture_top_path}"
          "side": "${texture_side_path}"
  axisX:
    state: "${base_block}:${vanilla_id}"
    model:
      x: 90
      y: 90
      path: "${model_horizontal_path}"
      generation:
        parent: "minecraft:block/cube_column_horizontal"
        textures:
          "end": "${texture_top_path}"
          "side": "${texture_side_path}"
  axisZ:
    state: "${base_block}:${vanilla_id}"
    model:
      x: 90
      path: "${model_horizontal_path}"
      generation:
        parent: "minecraft:block/cube_column_horizontal"
        textures:
          "end": "${texture_top_path}"
          "side": "${texture_side_path}"
```

{% hint style="success" %}
Additionally, you can use `x` and `y` to rotate the model by a certain degree along the x-axis or y-axis. In this example, the plugin actually uses only two models, with the variants along the x and z axes derived from rotation.
{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/0cprZp0jgclG0YVFJHgf/image.png" alt=""><figcaption></figcaption></figure>
