# Buffer Overflow Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware udpate process, there is buffer overflow vulnerability in the function auto_update_firmware() of program ssi. The variable str is a external data which stores the file name of the new firmware. It is copied to array s in strcpy without any size constraint such as strlen. The total size of array s is 1552 bytes and the offset of strcpy is 388 bytes. Since there is no size constraint on variable str, once the size of str is larger than 1163 bytes, a buffer overflow vulnerability occurs. The hackers could control the str and perform out-of-bounds writing to cause buffer overflow vulnerability which could further cause the denial of service.

<img width="416" height="446" alt="image" src="https://github.com/user-attachments/assets/7d2c1591-0e11-44b1-bbb7-8b22736f3d2e" />





