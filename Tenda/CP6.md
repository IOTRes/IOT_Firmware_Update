# Firmware Integrity Verification Vulnerability in Firmware Update Process of Tenda CP6

## Affected Product
Tenda CP6 (firmware version: V11.10.00.243)

## Overview
During firmware update process, additive checksum is applied in function sub_2B7D04() which is invoked in program uhttp to perform integrity verification on new firmware for update. Since the hackers could craft a malicious firmware with the same additive checksum as the new firmware, the integrity verification could be easily bypassed. Therefore, the malicious firmware could be written to IoT device through firmware update and cause arbitrary code execution or denial of service.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/207cbac5-f9e7-4a3f-b5b3-6ea2283ba2d6" />\
<img width="468" alt="image" src="https://github.com/user-attachments/assets/6dda382f-45a6-4ae8-b4f5-da837abea19f" />\
<img width="468" alt="image" src="https://github.com/user-attachments/assets/cfd625af-ca4f-4c64-b8d8-ed39627a431a" />



