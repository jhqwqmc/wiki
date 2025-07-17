# :water_wave : 液体碰撞方块项目

不同于`block_item`, `liber_collecion_block_item` 检查液体碰撞。 它适合创建可以放在水面或湖面上的方块。 所有其他配置选项与 `block_item` 完全相同。

```yaml
项目:
  默认值:
    材料:
    行为:
      类型: 液体_collecion_block_item
      offset-y: 1 # 将方块放置于
      方块: 默认:reed
```

