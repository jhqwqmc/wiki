# ⚖️ Conditions

{% hint style="success" %}
Adding `!` before a condition type inverts its logic. For instance:

```yaml
type: "!permission"
permission: "craftengine.admin"
```
{% endhint %}

### any\_of

Satisfy any one of the conditions.

```yaml
type: any_of
terms:
  - type: xxx
  - type: xxx
```

### all\_of

All conditions must be satisfied.

```yaml
type: all_of
terms:
  - type: xxx
  - type: xxx
```

### inverted

Negate the result value of the current condition.

```yaml
type: inverted
term:
  type: xxx
```

### falling\_block

Check whether the drop was caused by the block falling.

```yaml
type: falling_block
```

### survives\_explosion

Detect whether it is possible to survive the explosion.

```yaml
type: survives_explosion
```

### match\_item

Match the item in hand.

```yaml
type: match_item
id: "minecraft:iron_pickaxe"
regex: false # whether to use regex matching
```

```yaml
type: match_item
id: 
  - "minecraft:iron_pickaxe"
  - "minecraft:stone_pickaxe"
regex: false # whether to use regex matching
```

### match\_block\_property

Match the block state property

```yaml
type: match_block_property
properties:
  age: 3
```

### enchantment

Detect the enchantments on the item in hand.

```yaml
type: enchantment
predicate: minecraft:silk_touch>=1 # > >= = < <=
```

### table\_bonus

Provide different success probabilities at various enchantment levels.

```yaml
type: table_bonus
enchantment: minecraft:fortune
chances:
  - 0.1
  - 0.5
  - 0.8
  - 1
```

### random

```yaml
type: random
value: 0.1 # 10%
```

### permission

Checks if the player has the permission

```yaml
type: permission
permission: "craftengine.admin"
```

### expression

Checks if the expression returns `true`

```yaml
type: expression
# https://ezylang.github.io/EvalEx/references/references.html
expression: "<papi:farming_level> >= 10"
```

### string\_equals

Determines if the two values are equal

```yaml
type: string_equals
value1: "<arg:player.name>"
value2: "Player_A"
```

### string\_contains

Determines if value1 contains value2

```yaml
type: string_contains
value1: "<arg:player.name>"
value2: "A"
```

### string\_regex

Determines if value matches the pattern

```yaml
type: string_regex
value: "<arg:player.name>"
regex: "[a-Z]"
```

### is\_null

Checks if the argument is null

```yaml
type: is_null
argument: "player.main_hand_item"
```

### hand

Checks the interaction hand

```yaml
type: hand
hand: main_hand # off_hand
```

### on\_cooldown

Checks if player is on cooldown (use `set_cooldown` function to set cooldown for player)

```yaml
type: on_cooldown
id: my_cooldown_id
```

{% hint style="info" %}
Example usage

```yaml
events:
  - on: right_click
    functions:
      - type: set_cooldown
        id: test
        time: 30s
      - type: command
        command: give <arg:player.name> minecraft:apple
    conditions:
      - type: "!on_cooldown"
        id: test
```
{% endhint %}

{% hint style="warning" %}
More conditions are coming...
{% endhint %}
