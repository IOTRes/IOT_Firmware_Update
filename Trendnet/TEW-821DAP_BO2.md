# Buffer Overflow Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware udpate process, there is buffer overflow vulnerability in the function sub_41EC14 of program ssi. The variable `nslookup_target`, which is propagated from the user input, is directly written into buffer value with the size of 2 bytes. However, there is no data size limitation. Once the hackers control and construction a user input which is greater than 392 bytes, a buffer overflow vulnerability occurs.

The vulnerability trigger path is as the following:

```
HTTP POST
HTTP POST /goform/tools_nslookup
  → ssi CGI dispatch table → sub_41EC14 @ 0x41EC14
  → v4 = getenv("cameo.cameo.nslookup_target") 
  → strcpy(value, v4) @ 0x41ED98
```
Stack Layout:

| Variable         | Offset             | Size        | Size of buffer overflow      |
| -------------- | ------------------ | ----------- | ------------------------------ |
| `value`        | `[sp+0x1C]`        | **2 bytes** | 0                     |
| `s`            | `[sp+0x1E]`        | 254 bytes   | 2 bytes                  |
| `command`      | `[sp+0x11C]`       | 2 bytes     | 256 bytes                |
| `v9`           | `[sp+0x11E]`       | 126 bytes   | 258 bytes                |
| `var_8`        | `[sp+0x19C]`       | 4 bytes     | 384 bytes               |
| save `$s0`     | `[sp+0x1A4]`       | 4 bytes     | **392 bytes → overwrite return address** |
| save `$s1~$s4` | `[sp+0x1A8~0x1B4]` | 16 bytes    | return address                     |


