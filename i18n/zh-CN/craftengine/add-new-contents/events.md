# 🪇 事件

## 一. 导言

"事件" 部分决定哪些项目/家具/块将在特定事件中执行预定义的行为。 在 `events` 部分下，您需要指定一个事件触发器，如"right_click"以便右击动作。 在事件触发器下，您必须传递一个包含相应类型的动作列表。 例如，`command` 执行一个特定的命令。

```yaml
# 格式 1
事件:
  right_click:
    - 类型: 命令
      命令: 说 1
      条件:
        - 类型: 权限
          权限: "craftengine. dmin"
    - 类型: 命令
      命令: 说 2
      条件: []
# 格式 2
事件:
  - 在: right_click
    函数:
      - 类型: 命令
        命令: 说 1
        条件:
          - 类型: 权限
            permission: "craftengine. dmin"
      - 类型：命令
        命令：说 2
        条件：[……]
```

{% content-ref url="conditions" %}
[conditions](conditions
{% endcontent-ref %}

## :firecacker: 事件触发

### 项目

- 断开
- 右键\_点击
- 左\_点击
- 消耗量

### 封禁

- 断开
- 地点
- 右键\_点击
- 左\_点击
- 步骤

### 家具：

- 断开
- 地点
- 右键\_点击

{% hint style="danger" %}
请注意相应事件应放置在适当的配置区域。 例如，如果您想要在与一件家具互动时执行一个命令， 正确的方法是将“事件”放在“家具”栏下，而不是放在你的项目栏下。

```yaml
项目：
  默认：基准：
    事件：# :cross_mark：
      right_click：
       - 类型：命令
    行为：
      类型：gabure_item
      家具：
        事件：# :check_mark_buton：
          right_click：
           - 类型：命令
```

{% endhint %}

## 🔧 函数

### 取消\_事件

取消原始事件。

```yaml
类型：取消事件
```

### 运行

按顺序运行函数列表。 它对具有相同条件的函数有用。

```yaml
type: 运行
延迟: 0 # 可选; 数字; [default: 0]
函数: # 所需; maplist
  - 类型: 命令
  - 类型: 消息
```

### 命令

作为玩家或控制台运行命令。

```yaml
type: 命令
: "sayhello <arg:player.name>" # 所需; stringlist/string
target: "self" # 可选; 枚举[所有，自己]/玩家选择器；[默认：自己]
作为玩家：false # 可选；[默认：false]
```

### 留言

发送消息/系统操作栏消息

```yaml
类型: 消息
消息: "Hello <papi:player_name>" # 所需; 字符串列表/字符串
target: "self" # 可选; 枚举[所有，自己]/播放器选择器
叠加层：false # 可选；[默认：false]；false = 聊天框 / true = 动作栏
```

### 操作栏

发送操作栏

```yaml
输入: 操作栏
操作栏: "这是一个操作条" # 所需; 字符串
目标："self" # 可选; 枚举[all,self]/播放器选择器; [默认: self]
```

### 标题

发送标题

```yaml
输入：标题
title: "<red>Title</red>" # 所需; 字符串
字幕: "<Yellow>字幕</yellow>" # 所需; 字符串
淡出: 20 # 可选; 数字; [default: 10]
保持: 10 # 可选; 数字; [default: 20]
淡出: 10 # 可选; 数字; [default: 5]
```

### 打开\_窗口

打开界面窗口

```yaml
类型: open_window #
gui-type: anvil, enchanting, grindstone, loom, smites, crafting and captography];
title: "Super Anvil" # optional; string
target: "self" # optional; 枚举[all,self]/播放器选择器; [default: self]
```

### 位置\_块

放置一个块

```yaml
类型: place_block
block-state: "default:e_lantern"
x: <arg:block.block_x>
y: <arg:block.block_y>
z: <arg:block.block_z>
```

### 掉落\_战利品

丢弃根据给定的掠夺表进行的掠夺。

```yaml
类型: drop_loot
x: <arg:block.block_x> + 0.5
y: <arg:block.block_y> + 0.5
z: <arg:block.block_z> + 0.5
外观:
  池: ...
```

### 更新\_interaction\_tick

上次交互结束时更新tick

```yaml
类型：update_interaction_tick
```

### 设置\_计数

在此事件中设置当前项目的数量

```yaml
类型: set_count
add: true # Default: false
count : -1
target: "self" # optional; number [all,self]/player selftor
```

### 设置\_food

设置玩家的食物水平 (0\~20)

```yaml
type: set_food
add: true
food: 4
target: "self" # optional; 枚举[all,self]/播放器选择器
```

### 设置\_饱和度

设置玩家的饱和度(0\~10)

```yaml
类型: set_satarity
add: true
saturation: 2.5
target: "self" # optional; 枚举[all,self]/播放器选择器
```

### 游泳\_hand

将这个事件所涉及的手或配置中指定的手转换。

```yaml
类型：swing_hand
hand：main_hand # 可选参数
```

### 粒子

生成粒子

```yaml
type: partile
parcle: minecraft:end_rod
x: "<arg:position.x>"
y: "<arg:position.y>"
z: "<arg:position.z>"
count : 5
offset-x: 0.
偏移：0.3
偏移：0。
速度: 0

# 以下参数只是有效的
# 当粒子是某一类型的时候。

# 项目
item: default:e_lantern

# block/falling_dust/dust_pillar/block_crumble/block_marker
block-state: default:plam_log[axis=y]

# charge
charge: 1。

# shriek
shriek: 1

# 粉尘
颜色：255,255,255
缩放： 1。

# dust_color_transition
from : 255 255
to 0,0
scale : 4.

# 振动
目标x: 0
target-y: 1
target-z: 0
arrival-time: 10

# Tracil
target-x: 0
target-y: 1
target-z: 0
dur: 10
```

### 药水\_效果

添加药水效果

```yaml
输入：药水效果
药水效果：minecraft:盲目
持续时间： 20 # 默认值： 20
扩音器： 0 # 默认值： 0
环境： false # 来自信标
粒子： true
```

### 移除\_药水\_效果

移除药水效果

```yaml
类型: remove_potion_effect
pottion-effect: minecraft:lindness # 可选，如果'all' 是真的
所有: false # 默认值: false
```

### leveler\_exp

添加技能/工作经验

{% content-ref url="../compatibility/supported-levelers" %}
[supported-levelers](../compatibility/supported-levels)
{% endcontent-ref %}

```yaml
类型: level_exp
插件: AuraSkill# 级别插件
级别: 钓鱼# 工作/技能id
计数: 10 # 要给予的exp 数量
```

### 设置\_冷却时间

设置玩家的冷却时间

```yaml
类型: set_coldown
时间: 1m30s
id: my_courdown_id
add: false # 默认值: false (Whether 以累积冷却时间)
```

### 移除\_冷却时间

移除玩家的冷却时间

```yaml
类型: remove_coldown
id: my_coldown_id # 可选，如果'all' 是真的
所有: false # 默认值: false
```

### 播放\_声音

播放声音

```yaml
type: play_sound
sound: minecraft:xxxx.xxx
x: <arg:position.x>
y: <arg:position.y>
z: <arg:position.z>
pitch: 1
volume: 1
source: master
```

{% hint style="warning" %}
更多功能即将到来...
{% endhint %}
