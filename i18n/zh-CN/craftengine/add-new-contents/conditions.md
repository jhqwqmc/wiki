# :balanc_scale : 条件

{% hint style="success" %}
在条件类型反转之前添加`!`。 例如：

```yaml
输入: "!permission"
权限: "craftengine.admin"
```

{% endhint %}

### 任意\_共

满足任何一个条件。

```yaml
类型：任何
条款：
  - 类型：xxx
  - 类型：xxx
```

### 全部\_共

必须满足所有条件。

```yaml
类型: all_of
条款:
  - 类型: xxx
  - 类型: xxx
```

### 反转

负数当前条件的结果值。

```yaml
类型：反转
术语：
  类型：xxx
```

### 掉落\_块

检查拖放是否由方块跌落造成。

```yaml
类型：跌落块
```

### 存活\_爆炸物

检测爆炸是否能够幸存。

```yaml
类型：幸存者_爆炸数
```

### 匹配\_项目

匹配手头的项目。

```yaml
输入：匹配项
id：“minecraft:iron_pickaxe”
regex：false # 是否使用正则表达式匹配
```

```yaml
输入: 匹配项目
id: 
  - "minecraft:iron_pickaxe"
  - "minecraft:stone_pickaxe"
regex: false # 是否使用正则表达式匹配
```

### 匹配\_block\_property

匹配方块状态属性

```yaml
类型: match_block_property
属性:
  年龄: 3
```

### 附魔效果

检测手头物品上的附魔。

```yaml
类型：附魔
预测：minecraft:silk_touch>=1 # >= < =
```

### 表格\_红包

在不同附属级别提供不同的成功概率。

```yaml
type: table_bont
附魔：minecraft:tornee
机会：
  - 0.1
  - 0.5
  - 0.8
  - 1
```

### 随机的

```yaml
类型：随机
值：0.1 # 10%
```

### 权限

检查玩家是否有权限

```yaml
类型: 权限
权限: "craftengine.admin"
```

### 表达式

检查是否表达式返回 `true`

```yaml
输入：表达式
# https://ezylang.github.io/EvalEx/references/references.html
expression: "<papi:farming_level> > = 10"
```

### string\_等于

确定两个值是否等于

```yaml
type: string_等于
value1: "<arg:player.name>
value2: "Player_A"
```

### 字符串\_contained

决定值1是否包含值2

```yaml
类型：string_contain
值1："<arg:player.name>"
值2："A"
```

### string\_regex

确定值是否匹配图案

```yaml
类型: string_regex
值: "<arg:player.name>"
regex: "[a-Z]"
```

### 为\_null

检查参数是否为空

```yaml
类型: is_null
参数: "player.main_hand_item"
```

### 手

检查互动手部

```yaml
type: hand
hand: main_hand # off_hand
```

### 开启\_冷却时间

检查玩家是否处于冷却状态(使用 set_coldown" 函数为玩家设置冷却时间)

```yaml
类型：on_coldown
id：my_coldown_id
```

{% hint style="info" %}
示例使用

```yaml
事件:
  - 在右键点击
    函数:
      - 类型: set_coldown
        id: test
        time : 30 s
      - 类型: 命令
        命令: 给出 <arg:player.name> minecraft:appe
    条件:
      - 类型: "! n_冷却"
        id: 测试
```

{% endhint %}

{% hint style="warning" %}
更多条件正在出现...
{% endhint %}
