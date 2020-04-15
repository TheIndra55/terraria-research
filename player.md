# Player file

Players are generally stored in documents/'my games' and contain a `.plr` extension, the actual data is encrypted with Rijndael using the encryption key `h3y_gUyZ`.

## Format

| Offset | Type       | Description                   |
|-------:|------------|-------------------------------|
| 0      | int32      | Game version                  |
| 4      | uint64     | Re-Logic file format header?  |
| 12     | uint32     | Revision                      |
| 16     | uint64     | Is favorite bit field         |
| 24     | string     | Player name                   |
| *      | uint8      | Difficulty                    |
| 1      | int64      | Playtime in ticks             |
| 9      | int32      | Hair texture                  |
| 10     | uint8      | Hair dye                      |
| 11     | uint8      | Hide visuals bits             |
| 12     | uint8      | Hide visuals bits+8           |
| 13     | uint8      | Unknown                       |
| 14     | uint8      | Cloth style                   |
| 19     | int32      | Health                        |
| 23     | int32      | Max health                    |
| 27     | int32      | Mana                          |
| 31     | int32      | Max mana                      |
| 35     | uint8      | Extra accessory boolean       |
| 36     | uint8      | Did won any invasion event    |
| 37     | int32      | Tax money                     |
| 41     | color      | Hair color                    |
| 44     | color      | Skin color                    |
| 47     | color      | Eye color                     |
| 50     | color      | Shirt color                   |
| 53     | color      | Under shirt color             |
| 56     | color      | Pants color                   |
| 59     | color      | Shoes color                   |
| 62     | Item[20]   | Armor slots                   |
| 82     | Item[10]   | Dye slots                     |
| 92     | Inventory Item[58] | Inventory slots       |
| 150    | Misc Item[5]  | Unknown, items related to dyes and miscellaneous |
| 155    | Bank Item[40] | Bank 1 items               |
| 195    | Bank Item[40] | Bank 2 items               |
| 235    | Bank Item[40] | Bank 3 items               |
| 275    | Buff[22]   | Buff types                    |
| 297    | Spawn[200] | World spawn locations         |
| 497    | uint8      | Hotbar locked                 |
| 498    | uint8[13]  | Hidden info aces              |
| 511    | int32      | Angler quests finished        |

TODO

## Types

### Color

Color represents a rgb color which consists of 3 bytes.

| Offset | Type  | Description |
|-------:|-------|-------------|
| 0      | uint8 | Red         |
| 1      | uint8 | Green       |
| 2      | uint8 | Blue        |

### Item

Item represents an item in a slot, however Terraria can store different info about items. For example all inventory items also include a 'Stack' and 'Ís favorite' while 'armor' and 'dye' does only write 2 properties.

| Offset | Type  | Description |
|-------:|-------|-------------|
| 0      | int32 | Item net ID |
| 4      | uint8 | Item prefix |

### Inventory item

| Offset | Type  | Description |
|-------:|-------|-------------|
| 0      | int32 | Item net ID |
| 4      | int32 | Stack       |
| 8      | uint8 | Item prefix |
| 9      | uint8 | Is favorite |

### Misc item

| Offset | Type  | Description         |
|-------:|-------|---------------------|
| 0      | int32 | Unknown item net ID |
| 4      | uint8 | Unknown item prefix |
| 5      | int32 | Unknown item net id |
| 9      | uint8 | Unknown item prefix |

### Bank item

| Offset | Type  | Description |
|-------:|-------|-------------|
| 0      | int32 | Item net ID |
| 4      | int32 | Stack       |
| 8      | uint8 | Item prefix |

### Spawn

Spawn represents a spawn in a world, there can be max 200. If while reading 'Spawn X' is `-1` it should break the loop.

| Offset | Type   | Description |
|-------:|--------|-------------|
| 0      | int32  | Spawn X     |
| 4      | int32  | Spawn Y     |
| 8      | int32  | World Id    |
| 12     | string | World name  |

### Buff

| Offset | Type  | Description |
|-------:|-------|-------------|
| 0      | int32 | Buff type   |
| 4      | int32 | Buff time   |
