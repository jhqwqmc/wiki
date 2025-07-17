# :round_puppin: 家具配置

## 一. 导言

家具支撑着三种安置模式：地面、天花板和墙。 您可以使用不同的外观和碰撞框方案来处理不同的布置模式。 例如，一家注明的工厂家具物品放在地面时可能会直立，当从天花板上吊出时会出现带有绳子的危险。 安装在墙上时被木板支持——就像原版钟块。

{% hint style="success" %}
您可以同时为一件家具配置多个布置模式。
{% endhint %}

下面我将使用地面模式作为示例，解释如何配置基本位置。

```yaml
furniture:
  default:bench:
    placement:
      ground:
        # create offsets for the drops so they won't spawn in blocks
        loot-spawn-offset: 0,0,0
        # Supports External Models Here
        # model-engine: blueprint_id
        # better-model: blueprint_id
        rules:
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
        elements:
          - item: default:bench
            display-transform: NONE
            billboard: FIXED
            position: 0.5,0,0
            translation: 0,0.5,0
            apply-dyed-color: true # default: true
        hitboxes:
          - type: interaction # non-collision hitbox
            can-use-item-on: false # default: false
            can-be-hit-by-projectile: false # default: false
            blocks-building: false # default: true
            position: 0,0,0
            width: 1
            height: 2
            # 'width'/'height' can be simplified to 'scale'
            # scale: 1,2 
            interactive: true # whether the interaction entity is interactive
            seats:
              - 0,0,-0.1 0
```

有三个部分: `rules`, `elements`, and `hitboxes`.&#x20;

“规则”部分决定家具放置后的位置和轮换限制。 “元素”部分定义了哪些项目组成家具(您可以为单件家具配置多个项目，每件显示模式不同)。 \
The `hitboxes` section specifies the collision volume of the furniture.

## 规则

### 旋转

插件的家具支持各种轮换方案。 它们之间的差别在于对轮调角度数目的限制或对轮调方向的直接规格。

{% hint style="danger" %}
旋转对Wall-挂载的布置方法没有影响。
{% endhint %}

### 对齐

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/36xb0WeQSH45cr7iSVz6/image.png" alt="" width="375"><figcaption><p>中心</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/F7HhjgTtxdk3wIucZwqy/image.png" alt="" width="375"><figcaption><p>half</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/k4jaenbMWri8AKqaiCPb/image.png" alt="" width="375"><figcaption><p><p></p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/q0lwi6Z0jqkueQMDoiHD/image.png" alt="" width="375"><figcaption><p>角</p></figcaption></figure>

{% hint style="success" %}
对齐也适用于已挂载的位置。
{% endhint %}

## 要件

“元素”是指构成家具外观的每一项物品。 大多数家具只需一件就够了。 然而，如果你想要创建一件更复杂的家具，你可以从多个物品中组装它。 例如，全息投影可分为两个项目：基数和投影本身。 基地可以有固定的方向，而投影可以设置为随时面对玩家。

```yaml
元素:
  - 项目：默认:bench
    显示器变换: NOE # NOE / THIRD_PERSON_LEFT_HAND / THIRD_PERSON_RIGHT_HAND
                            # FIRST_PERSON_HAND / FIRST_PERSON_PERSON_RIGHT_HAND
                            # HEAD / GROUND / FIXed
    显示板: FIXed # FIXed / VERTICAL / HORIZONTAL / CENTER
    位置: 0。 0,0
    翻译：0,0 ,0
    缩放: 1 # 缩放: 1,2,
    应用dyed颜色：真
    # 旋转支持3 格式
    旋转：45 # Y 轴
    旋转：45。 5,0 # Euler 角度
    旋转：0,0,0。 071,0.7071 # Quaternions https://quaternions.online/
```

{% hint style="warning" %}
请注意`position` 和 `translation` 之间的区别。 `position`更改相应显示实体的坐标位置，而`translation`则是显示实体本身的迁移属性。
{% endhint %}

{% hint style="danger" %}
对于放在墙上的家具，您需要使用 "仓位" 进行轻微偏移；否则家具可能会在某些方向变黑。 这关系到Minecraft如何渲染实体。
{% endhint %}

## 希特克斯文

"hitbox" 是发送给玩家的交互实体，您可以使用 F3 + B 调试屏幕来视觉其效果。

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/ZAkiDfKUD0JhyjS161gT/image.png" alt=""><figcaption></figcaption></figure>

### 互动

```yaml
点击框：
- 类型：交互# 无碰撞hitbox
  可以使用下列项目：fals# 默认值：falsal
  可以点击逐个项目：false # 默认值：false
  blocks-building：false # 默认值：true
  位置：0,00,
  宽度: 1
  高度: 2
  # 'width'/'height' 可以简化为“scale”
  # 尺寸: 1, 
  交互式：真的 # 互动实体是否是交互式
  座位：
    - 0, -0.1 0
```

### 潜影人

```yaml
点击框：
- 类型：潜水器# 硬碰撞hitbox
  可以使用项目：true # 默认值：true
  can -be-hit-brojectle：true # 默认值：true
  blocks-building：true # 默认值：true
  位置：1, ,0
  缩放: 1 # 1。 0.5+
  peek: 0 # 0~100
  # 相对方向。 North = face 播放器
  方向：UP # UP/DOWN/NORTH/WEST/EAST/SOUTH
  交互实体：true # 是否召唤另一个交互实体
  交互式实体
 交互式：真# 是否交互实体
  座位：
    - 1, -0.1 0
```

### 快乐的恶心

```yaml
点击框：
- 类型：happy_ghast # hard/soft-碰撞hitbox
  can -use-item-on：true # default : true
  can -be-hit-backtile: true # default: true
  blocks-building: true # default : true
  硬碰撞: true # 默认值: true # 默认值: true
  position: 1, ,0
  缩放：0。 5 # 默认值: 1
  座位:
    - 1 0,-0.1 0
```

### 自定义

```yaml
点击框：
- 类型：自定义# 主要用于软碰撞hitbox
  位置：1 0,0
  比例尺：5 # 1.20。 +
  # 你可以在这里使用任何实体
  实体类型: slime # 默认值: slime
  座位:
    - 1, -0.1 0
```

{% hint style="success" %}
一个单独的 'hitbox' 可以配置多个座位。 如果多个“hitboxes”座位位于同一地点，相当于只有一个座位。
{% endhint %}

{% hint style="info" %}
"座位"的位置是由一个位置和一个旋转决定的，由配置中的一个空间隔开。

```
0,0,0 0
```

您也可以选择不配置旋转角度，允许玩家在座位上自由旋转到任何角度。

```
0,0,0
```

{% endhint %}

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/y0rBULzgm88rptOyeP5e/2.gif" alt=""><figcaption><p>0,0,0</p></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/OgvQ1fEJPROp7131PPlK/blobs/7QS8DIznzoLlEmVELu1I/1.gif" alt=""><figcaption><p>0,0,0</p></figcaption></figure>

## 外部模型

您也可以使用来自ModelEngine/BetterModel的外部模型

```yaml
家具：
  默认：基准：
    位置：
      色彩：
        model-engine：blueprint_id
        较好的模型：bluprint_id
        规则：
          # ANY / FOUR / EIGHT/ SIXTEN / NORTH / EAST / WEST / SOUTH
          旋转：EIGHTT
          # ANY / CENTER / HALF / QUARTER / CORNER
          对齐：CENTER
```
