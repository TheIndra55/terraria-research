# Player file

Players are generally stored 'my games' and contain a `.plr` extension, the actual data is encrypted with Rijndael using the encryption key `h3y_gUyZ`.

## Format

| Offset | Type   | Description                   |
|-------:|--------|-------------------------------|
| 0      | int32  | Unknown, player file version? |
| 4      | uint64 | Re-Logic file format header?  |
| 12     | uint32 | Revision                      |
| 16     | uint64 | Is favorite bit field         |
| 24     | string | Player name                   |
| *      | uint8  | Difficulty                    |
| 1      | int64  | Playtime in ticks             |
| 9      | int32  | Hair texture                  |
| 10     | uint8  | Hair dye                      |
| 11     | uint8  | Hide visuals bits             |
| 12     | uint8  | Hide visuals bits+8           |
| 13     | uint8  | Unknown                       |
| 14     | uint8  | Cloth style                   |
| 19     | int32  | Health                        |
| 23     | int32  | Max health                    |
| 27     | int32  | Mana                          |
| 31     | int32  | Max mana                      |
| 35     | uint8  | Extra accessory boolean       |
| 36     | uint8  | Did won any invasion event    |
| 37     | int32  | Tax money                     |
| 41     | color  | Hair color                    |
| 44     | color  | Skin color                    |
| 47     | color  | Eye color                     |
| 50     | color  | Shirt color                   |
| 53     | color  | Under shirt color             |
| 56     | color  | Pants color                   |
| 59     | color  | Shoes color                   |

TODO