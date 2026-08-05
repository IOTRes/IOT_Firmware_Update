# Firmware Integrity Vulnerability in Firmware Update Process of Zyxel DX3301-T0

## Affected Product
DX3301-T0 (firmware version:5.50(ABVY.1)C0)

## Overview

During in the firmware update process, there is a firmware integrity verification vulnerability in function zcmdCheckImage() of program zcmd. zcmdCheckImage() invokes zcmdValidateImage() to perform integrity verification. However, there is only CRC integrity verification which could be easily bypassed. Once the hackers obtain the CRC checksum stored in the firmware header, they could bypass the integrity verification and upload tampered firmware to the IoT devices, which could cause denial of service or arbitrary code execution. 

<img width="1244" height="333" alt="image-1" src="https://github.com/user-attachments/assets/418e6ad7-95e9-40e0-abd0-e090fc250318" />




