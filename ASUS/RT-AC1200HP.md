# Firmware Integrity Verification Vulnerability in Firmware Update Process of Asus RT-AC1200HP 

## Affected Product
Asus RT-AC1200HP (firmware version: 3.0.0.4.380.8457)

## Overview
During the process of firmware update, function check_imagefile() is used to check the new firmware image. However, cyclic redundancy check (CRC) is used for checking firmware image header in function check_imageheader(), which could be easily bypass and cannot defend malicious tampering against new firmware image. A tampered firmware with the same CRC value as the new firmware could be crafted to bypass the CRC verification, then, the tampered firmware which could cause arbitrary code execution and denial of service can be written into the IoT device through the firmware update. Therefore, there is a firmware integrity verification vulnerability in the firmware update process.

<img width="418" alt="image" src="https://github.com/user-attachments/assets/1b3b68f6-f30b-43ba-b448-b902dff35d98" />\
<img width="246" alt="image" src="https://github.com/user-attachments/assets/7b752edf-df1e-4e65-8421-c8e69a18406e" />\
<img width="468" alt="image" src="https://github.com/user-attachments/assets/37c91968-1814-4565-b57d-2a11f62d2e21" />\
<img width="468" alt="image" src="https://github.com/user-attachments/assets/09901117-7acc-49f4-9396-cf8e856af796" />  

