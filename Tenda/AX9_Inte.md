# Firmware Integrity Verification Vulnerability in Firmware Update Process of Tenda AX9


## Affected Product
Tenda AX9 (firmware version: V22.03.01.46)

## Overview

During the firmware update process, the there is integrity verification vulnerability in function image_check() of program httpd.

<img width="468" height="234" alt="image" src="https://github.com/user-attachments/assets/1c740be9-297b-4698-ba69-48c18e590671" />


Cyclic redundancy check(CRC) is used in image_check() to verify the firmware header and firmware image. CRC could be easily bypassed as long as the hackers craft a compromised firmware with the same crc value as the new firmware. Therefore, the firmware integrity verification vulnerability arises which makes the compromised firmware could be written into the IoT device during firmware update and cause arbitrary code execution or denial of service.


<img width="468" height="260" alt="image" src="https://github.com/user-attachments/assets/81a1aed7-f686-4008-9ce6-3498483e0ca4" />
