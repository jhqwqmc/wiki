# 📓 Config Format Changelog

## 0.0.18

Moved `tags`to `settings`

#### before

```yaml
default:palm_planks:
  material: paper
  custom-model-data: 1004
  tags:
    - "minecraft:planks"
    - "minecraft:wooden_tool_materials"
```

#### after

```yaml
default:palm_planks:
  material: paper
  custom-model-data: 1004
  settings:
    tags:
      - "minecraft:planks"
      - "minecraft:wooden_tool_materials"
```

## 0.0.35

Renamed stonecutting recipe type

#### before

```yaml
type: stone_cutting
```

#### after

```yaml
type: stonecutting
```

## 0.0.48

Moved `offset-characters` to `image.offset-characters` in config.yml

## 0.0.49

Changed how invalid furniture works in config.yml

```yaml
furniture:
  remove-invalid-furniture-on-chunk-load:
    enable: false
    list:
    - "xxx:invalid_furniture"
```

->

```yaml
furniture:
  handle-invalid-furniture-on-chunk-load:
    enable: true
    remove:
      - "default:table_lamp"
    convert:
      "default:wooden_chair": "default:bench"
```

Refactored how host works in config.yml. Read this page for the new format:

{% content-ref url="../resource-pack/host" %}
[host](../resource-pack/host)
{% endcontent-ref %}

## 0.0.57

Changed the template argument format from `{parameter}` to `${parameter:-DEFAULT_VALUE}`
