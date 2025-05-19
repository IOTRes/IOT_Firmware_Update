# Firmware Authentication Verification Vulnerability in Firmware Update Process of DLink DIR619L


## Affected Product
DLink DIR619L (firmware version: 6.02CN02)

## Overview

The function FirmwareUpgrade() that verify the new firmware for firmware update is called by function formFirmwareUpgrad() of program boa which performs firmware update. However, several hard-coded verification information (e.g. F69B) is used to perform authentication verification on new firmware to check whether the new firmware contains certain flags (e.g. F69B). Hackers could craft a tampered firmware with the same hard-coded verification information as the new firmware to bypass the authentication verification, then upload the tampered firmware to the IoT device and cause arbitrary code execution or denial of service. Therefore, there is a firmware authentication verification vulnerability in the firmware update process.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/dba525f1-151d-43b4-8ec4-ae7761f3cbca" />
<img width="465" alt="image" src="https://github.com/user-attachments/assets/e90a00d7-534d-4832-a283-7de85cff695c" />
<img width="468" alt="image" src="https://github.com/user-attachments/assets/2d88f32a-fc9c-4e97-88a5-c2dc15e27f99" />
<img width="337" alt="image" src="https://github.com/user-attachments/assets/a7c9da36-2e9c-45b4-8ffe-90feaa3dfb63" />



