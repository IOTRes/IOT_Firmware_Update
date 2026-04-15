# Firmware Integrity Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware update process, there is firmware integrity verification vulnerability in function platform_do_upgrade_cameo_dev() of program cameo_dev.sh. Function platform_do_upgrade_cameo_dev() performs the firmware integrity verification through CRC32 which could be easily be bypassed. Once the hackers obtain the CRC32 value they could could craft a compromised firmware with the same CRC value as the new firmware to bypass the integrity verification. Then, the compromised firmware which could cause arbitrary code execution or denial of service can be written into the IoT device through the firmware update.


<img width="416" height="468" alt="image" src="https://github.com/user-attachments/assets/f841dba7-ba87-4e56-b375-1d15aeec7f47" />



