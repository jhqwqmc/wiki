# 📓 配置格式变更日志

## 0.0.18

移动`tags`到`settings`

#### 前

```yaml
默认:palm_plaks:
  material: paper
  custom-model-date: 1004
  tags:
    - "minecraft:planks"
    - "minecraft:wooden_tool_materials"
```

#### 之后

```yaml
默认：palm_plaks:
  material: paper
  custom-model-data: 1004
  settings:
    tags:
      - "minecraft:planks"
      - "minecraft:wooden_tool_materials"
```

## 0.0.35

重命名石头配方类型

#### 前

```yaml
类型：石头切割。
```

#### 之后

```yaml
类型：石头
```

## 0.0.48

在 config.yml 中将 `offset-characters` 移动到 `image.offset-characters`

## 0.0.49

更改 config.yml 中无效的家具工作方式

```yaml
家具：
  移除无效的家具-待机负载：
    已启用：false
    list：
    - "xxx:invalid_gakure"
```

->

```yaml
家具:
  个手势无效的家具-待机-负载:
    启用: true
    移除:
      - "default:table_lamp"
    转换:
      "default:wooden_chair": "defaultbett:"
```

恢复主机如何在 config.yml 中工作。 读取此页面的新格式：

{% content-ref url="../resource-pack/host" %}
[host](../resources pack/host)
{% endcontent-ref %}

## 0.0.57

Changed the template argument format from `{parameter}` to `${parameter:-DEFAULT_VALUE}`
