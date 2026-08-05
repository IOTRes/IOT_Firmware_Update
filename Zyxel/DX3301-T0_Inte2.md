# Firmware Integrity Vulnerability in Firmware Update Process of Zyxel DX3301-T0

## Affected Product
DX3301-T0 (firmware version:5.50(ABVY.1)C0)

## Overview

During the firmware update process, there is a firmware integrity verification vulnerability in function zcmdReqFirmwareUpgradeForFWUR() of program zcmd. zcmdReqFirmwareUpgradeForFWUR() perform integrity verification through CRC32 which could be easily bypassed. Once the hackers obtain the CRC32 checksum stored in the firmware, they could bypass the integrity verification and upload tampered firmware to the IoT devices, which could caused denial of service or arbitrary code execution.



<img width="1218" height="553" alt="image-5" src="https://github.com/user-attachments/assets/f41669ec-32bb-4624-ba67-3c1bf27c132d" />

<img width="880" height="528" alt="image-6" src="https://github.com/user-attachments/assets/0e022392-5c05-422b-9659-4d0e609e163e" />

<img width="1284" height="961" alt="image-7" src="https://github.com/user-attachments/assets/2d904fd4-6c7b-4171-94dd-67790348cca6" />
