# Firmware Integrity Vulnerability in Firmware Update Process of Zyxel DX3301-T0

## Affected Product
DX3301-T0 (firmware version:5.50(ABVY.1)C0)

## Overview

During in the firmware update process, there is a firmware integrity verification vulnerability in function zcmdCheckImage() of program zcmd. zcmdCheckImage() invokes zcmdValidateImage() to perform integrity verification. However, there is only CRC integrity verification which could be easily bypassed. Once the hackers obtain the CRC checksum stored in the firmware header, they could bypass the integrity verification and upload tampered firmware to the IoT devices, which could cause denial of service or arbitrary code execution. 

<img width="1244" height="333" alt="image-1" src="https://github.com/user-attachments/assets/418e6ad7-95e9-40e0-abd0-e090fc250318" />

<img width="791" height="426" alt="image-2" src="https://github.com/user-attachments/assets/66f72bf1-ba3f-416c-a2ca-b26fb472ed20" />

<img width="1005" height="904" alt="image-3" src="https://github.com/user-attachments/assets/8d10bab5-ab05-48fb-82e9-063e1f0ff981" />

<img width="1312" height="933" alt="image-4" src="https://github.com/user-attachments/assets/c69879ab-7ab0-4bd1-ae6d-3f38e98ab3ab" />

<img width="1047" height="486" alt="image-8" src="https://github.com/user-attachments/assets/f45c5e4e-f1a2-41b5-9505-40f1242da2af" />








