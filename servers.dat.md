# servers.dat

servers.dat file contains all recently joined servers including ip, worldname and port.

## Format

| Offset | Type       | Description  |
|-------:|------------|--------------|
| 0      | int32      | Game version |
| 4      | Server[10] | Servers      |

### Server

| Offset | Type   | Description |
|-------:|--------|-------------|
| 0      | string | World name  |
| *      | string | IP Address  |
| *      | string | Port        |