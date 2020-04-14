# Protocol

## Message structure

| Offset | Type   | Description                 |
|-------:|--------|-----------------------------|
| 0      | uint16 | The length of the whole packet, if the length is too short it will result in future messages not being read right |
| 2      | uint8  | The message type            |
| 3      |        | Message payload (see below) |

# Messages

## Connection request (1)

This is the first message send by the client asking the server if it's allowed to connect, the server will check if the client's version is not too old and if the client is not banned.

| Offset | Type   | Description                                         |
|-------:|--------|-----------------------------------------------------|
| 0      | string | The version string of the client e.g. 'Terraria194' |

## Boot client (2)

Send by the server if something goes wrong

| Offset | Type   | Description   |
|-------:|--------|---------------|
| 0      | string | Error message |

## Connection approved (3)

The server sends this message if the client is allowed to connect together with the player slot assigned to the client, this will be used in feature messages by the client.

| Offset | Type  | Description                 |
|-------:|-------|-----------------------------|
| 0      | uint8 | Server assigned player slot |

## Player appearance (4)

Send by the client while joining the server, can also be send while playing when updating player appearance.

| Offset | Type   | Description         |
|-------:|--------|---------------------|
| 0      | uint8  | Player slot         |
| 1      | uint8  | Cloth style         |
| 2      | uint8  | Hair texture        |
| 3      | string | Player name         |
| *      | uint8  | Hair dye            |
| 1      | uint8  | Hide visuals bits   |
| 2      | uint8  | Hide visuals bits+8 |
| 3      | uint8  | Unknown             |
| 4      | color  | Hair color          |
| 7      | color  | Skin color          |
| 10     | color  | Eye color           |
| 13     | color  | Shirt color         |
| 16     | color  | Undershirt color    |
| 19     | color  | Pants color         |
| 22     | color  | Shoes color         |
| 25     | uint8  | Bits flag (see below)   |

| Offset | Description         |
|-------:|---------------------|
| 0      | Difficulty 1        |
| 1      | difficulty 2        |
| 2      | Extra accessory     |

## Add inventory item (5)

TODO

## Change state (6)

Set the client's state on the server to 3

| Offset | Type | Description |
|-------:|------|-------------|

## Request spawn tile data (8)

Requests spawn tile data and triggers couple of messages

| Offset | Type  | Description |
|-------:|-------|-------------|
| 1      | int32 | Spawn X     |
| 3      | int32 | Spawn Y     |

## Spawn player (12)

Set the player spawn position and spawns the player, the server will also greet the player

| Offset | Type  | Description |
|-------:|-------|-------------|
| 0      | uint8 | Player slot |
| 1      | int16 | Spawn X     |
| 3      | int16 | Spawn Y     |

## Set life stats (16)

| Offset | Type  | Description       |
|-------:|-------|-------------------|
| 0      | uint8 | Player slot       |
| 1      | int16 | Player health     |
| 3      | int16 | Max Player health |

## Set Mana stats (42)

| Offset | Type  | Description       |
|-------:|-------|-------------------|
| 0      | uint8 | Player slot       |
| 1      | int16 | Mana              |
| 3      | int16 | Max Mana          |
