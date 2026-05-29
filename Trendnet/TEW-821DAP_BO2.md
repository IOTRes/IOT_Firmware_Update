# Buffer Overflow Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware udpate process, there is buffer overflow vulnerability in the function _post2nvram of program ssi. The POST argument, which is propagated from the user input, is directly written into a buffer with the size of 512 bytes. However, there is no data size limitation on the POST argument. Once the hackers control the user input and construct a POST argument which is greater than 512 bytes, a buffer overflow vulnerability occurs.

The vulnerability trigger path is as the following:

```
HTTP POST
  → do_ssc @ 0x4099B0 → __do_ssc @ 0x40A55C
  → __post2nvram @ 0x40CCC0
  → sprintf(local_buf, "%s=%s", param_name, param_value)
```

