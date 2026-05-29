# Buffer Overflow Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware udpate process, there is buffer overflow vulnerability in the function sub_41EC14 of program ssi. In the construction of nslookup command, the command string is written into a buffer with size of 2 bytes。 However, the size of the command string `"nslookup ${host} > /tmp/nslookup"` is 33 bytes. Therefore, a buffer overflow vulnerability occurs without any external input.


<img width="924" height="188" alt="image-5" src="https://github.com/user-attachments/assets/114c4770-ad0f-41e9-a9c5-5ccdd2242da4" />

The vulnerability trigger path is as the following:

```

HTTP POST /goform/tools_nslookup（任意有效请求）
  → ssi CGI dispatch table → sub_41EC14 @ 0x41EC14
  → setenv("host", value, 1)
  → sprintf(command, "nslookup ${host} > %s", "/tmp/nslookup") @ 0x41ED30

```
