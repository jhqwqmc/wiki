# 🏷️ Properties

{% hint style="warning" %}
Please note that, regardless of the type of property, you must configure a default value within a reasonable range for each one.
{% endhint %}

## Custom Property

### boolean

A property of type `boolean` can only have two possible values: `true` or `false`.

```yaml
properties:
  happy:
    type: boolean
    default: false
```

### int

A property of type `int` can take any integer value within the specified range.

```yaml
properties:
  mode:
    type: int
    default: 1
    range: 1~3
```

### string

A property of type `string` can only take values from a predefined set of options.

```yaml
properties:
  color:
    type: string
    default: red
    values:
      - read
      - green
      - blue
```

## Hard-coded Property

{% hint style="danger" %}
Please note that the property name must be the same as the examples to take effect
{% endhint %}

### facing

The facing values ​​are `east, south, west, north, up, down`. When a block has this hardcoded property, its placement orientation will automatically adapt.

```yaml
properties:
  facing:
    # horizontal_direction = 4 faces
    # direction = 6 faces
    type: direction
    default: north
```

### facing\_clockwise

Unlike the above, it will be rotated 90 degrees when placed

```yaml
properties:
  facing_clockwise:
    type: horizontal_direction
    default: north
```

### waterlogged

waterlogged determines whether this block can contain water.&#x20;

{% hint style="warning" %}
Please note: When using this state, you must ensure that the corresponding visual block also contains water, otherwise the client cannot render the water.
{% endhint %}

```yaml
properties:
  waterlogged:
    type: boolean
    default: false
```

### axis

Axis determines whether the blocks are placed along the axis, such as pillar and log. The axis can only be `x, y, z`

```yaml
properties:
  axis:
    type: axis
    default: y
```

### single\_block\_half  / double\_block\_half

```yaml
properties:
  half:
    # single_block_half  (for slabs, trapdoors) [top, bottom]
    # double_block_half  (for doors, double height plants) [upper, lower]
    type: single_block_half
    default: bottom
```

### hinge

The hinge can only be `left, right`

```yaml
properties:
  hinge:
    type: hinge
```

### slab\_type

The slab\_type can only be `top, bottom, double`

```yaml
properties:
  type:
    type: slab_type
```
