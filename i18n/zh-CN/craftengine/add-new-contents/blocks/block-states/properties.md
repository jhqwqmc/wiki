# 🏷️ 属性

{% hint style="warning" %}
请注意，无论属性类型如何，您都必须在一个合理范围内配置每个属性的默认值。
{% endhint %}

## 自定义属性

### boolean

类型为 `boolean` 的属性只能有两个可能的值：`true` 或 `false` 。

```yaml
properties:
  happy:
    type: boolean
    default: false
```

### 整数

类型`int`的属性可以在指定范围内采集任何整数。

```yaml
属性:
  模式:
    类型: int
    默认值: 1
    范围: 1~3
```

### 字符串

类型为 `string` 的属性只能从预定义的选项集中获取值。

```yaml
属性:
  颜色:
    类型: 字符串
    默认值: 红色
    值:
      - read
      - 绿色
      - 蓝色
```

## 硬编码属性

{% hint style="danger" %}
请注意属性名称必须与要生效的
{% endhint %}

### 正面

面对的价值观是“东面、南部、西部、北部、下面”。 当一个方块具有这个硬编码属性时，其位置方向将自动调整。

```yaml
属性：
  正面：
    # 水平方向 = 4 个面
    # 方向 = 6 个面
    类型： 方向
    默认：
```

### 正在呈现\_顺时针

与以上不同，放置时将旋转90度

```yaml
属性:
  facing_clockwise:
    类型: 水平方向
    默认值:
```

### 蓄水量

waterlogged determines whether this block can contain water.&#x20;

{% hint style="warning" %}
请注意：当使用此状态时 您必须确保相应的视觉模块也包含水，否则客户端不能提供水。
{% endhint %}

```yaml
properties:
  waterlogged:
    type: boolean
    default: false
```

### 轴

轴决定方块是否放置在轴上，如界面和日志。 轴只能是 `x, y, z`

```yaml
属性:
  轴:
    类型: 轴
    默认值: y
```

### sinle\_block\_hal/double\_block\_halt

```yaml
属性:
  一半:
    # sinle_block_half (用于板块, 陷阱) [顶部, 底部]
    # 加倍block_half (门, 双身身高植物（顶，低]
    类型：sinle_block_half
    默认值：底部
```

### hinge

hinge 只能是 `left, right`

```yaml
属性:
  hinge:
    类型: hinge
```

### 板块\_类型

Slab\_type 只能是 `top, bow, double `

```yaml
属性:
  类型:
    类型: slab_type
```
