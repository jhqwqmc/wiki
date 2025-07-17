# 🔗 Chain Arguments

## Introduction

**Chain Arguments** represent a dot-notation syntax (connected by `.`) used to access object-related parameters in a hierarchical manner.

For example, in an interaction event where we can access the player instance, we can retrieve additional parameters through this object.

By chaining property accessors like:

* `player.world` → Gets the player's current world
* `world.name` → Gets the name of that world

We can combine them into a parameter tag format like `<arg:player.world.name>`. This tag will dynamically return the name of the world the player is currently in.

## Objects

### player

| parameter        | type                             | description                      |
| ---------------- | -------------------------------- | -------------------------------- |
| x                | double                           | the x coordinate of the player   |
| y                | double                           | the y coordinate of the player   |
| z                | double                           | the z coordinate of the player   |
| block\_x         | int                              | the x coordinate of the player   |
| block\_y         | int                              | the y coordinate of the player   |
| block\_z         | int                              | the z coordinate of the player   |
| name             | string                           | the name of the player           |
| uuid             | uuid                             | the uuid of the player           |
| is\_flying       | boolean                          | check the fly state              |
| is\_sneaking     | boolean                          | check the sneak state            |
| gamemode         | string                           | the gamemode of the player       |
| main\_hand\_item | [#item](#item "mention")         | the item in main hand            |
| off\_hand\_item  | [#item](#item "mention")         | the item in off hand             |
| world            | [#world](#world "mention")       | the world where the player is in |
| position         | [#position](#position "mention") | the position of the player       |

### block

| parameter    | type                                    | description                     |
| ------------ | --------------------------------------- | ------------------------------- |
| x            | double                                  | the x coordinate of the block   |
| y            | double                                  | the y coordinate of the block   |
| z            | double                                  | the z coordinate of the block   |
| block\_x     | int                                     | the x coordinate of the block   |
| block\_y     | int                                     | the y coordinate of the block   |
| block\_z     | int                                     | the z coordinate of the block   |
| world        | [#world](#world "mention")              | the world where the block is in |
| block\_state | [#block\_state](#block_state "mention") | the blockstate of the block     |
| position     | [#position](#position "mention")        | the position of the block       |

### world

| parameter | type   | description           |
| --------- | ------ | --------------------- |
| name      | string | the name of the world |
| uuid      | uuid   | the uuid of the world |
| time      | long   | the time of the world |

### block\_state

| parameter | type | description |
| --------- | ---- | ----------- |
|           |      |             |
|           |      |             |
|           |      |             |

### position

| parameter | type                       | description      |
| --------- | -------------------------- | ---------------- |
| x         | double                     | the x coordinate |
| y         | double                     | the y coordinate |
| z         | double                     | the z coordinate |
| block\_x  | int                        | the x coordinate |
| block\_y  | int                        | the y coordinate |
| block\_z  | int                        | the z coordinate |
| world     | [#world](#world "mention") | the world        |

### item

| paramter            | type    | description                       |
| ------------------- | ------- | --------------------------------- |
| id                  | string  | the id of the item                |
| custom\_model\_data | int     | the custom model data of the item |
| is\_custom          | boolean | checks if the item is custom      |

### furniture

| parameter    | type                             | description                       |
| ------------ | -------------------------------- | --------------------------------- |
| id           | string                           | the id of the furniture           |
| uuid         | uuid                             | the uuid of the furniture         |
| anchor\_type | string                           | the anchor type of the furniture  |
| x            | double                           | the x coordinate of the furniture |
| y            | double                           | the y coordinate of the furniture |
| z            | double                           | the z coordinate of the furniture |
| position     | [#position](#position "mention") | the position of the furniture     |

