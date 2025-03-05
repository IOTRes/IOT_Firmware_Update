# Firmware Integrity verification vulnerability during firmware update process

## Affected Product
LBT-T300-T400 v3.2 routers(firmware version: v3.2)

## Overview
The firmware integrity verification is achieved by hard-coding verification massage, which is checking whether the first four bytes of the firmware are "R3G2". An attacker can construct a malicious firmware image starting with R3G2, which can bypass the firmware integrity verification in the firmware update process and install the malicious firmware image, thereby causing arbitrary command execution or denial-of-service(DOS).



![821E4CC222B3E724E1F481F0987F9BE8](https://github.com/user-attachments/assets/05e02db8-01c3-4a05-91a4-1100df666e69)

![195B74FA6E620CD7AA56DE953940ACDB](https://github.com/user-attachments/assets/5ababf98-f2cb-4527-b15e-d903013dd110)




