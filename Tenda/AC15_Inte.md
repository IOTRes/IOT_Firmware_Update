# Firmware Integrity Verification Vulnerability in Firmware Update Process of Tenda AC15


## Affected Product
Tenda AC15 (firmware version: V15.13.07.13)

## Overview
During the process of firmware update, function upgrade() of program httpd calls function webCgiGetUploadFile() to obtain the new firmware image which will be uploaded to IoT device for update. 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/167c9cf6-4de9-42ca-a52f-f7716ed6e3ee" />


After that, function tpi_upfile_handle() is called to verify the new firmware image. 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/81b5b2da-5f57-4065-8c4a-0e21ad83df74" /> \
<img width="468" alt="image" src="https://github.com/user-attachments/assets/6d5f4f1f-ad95-44f0-ab02-3959be04d252" />


 
However, there is integrity firmware verification vulnerability in tpi_upload() called by tpi_upfile_handle().
<img width="468" alt="image" src="https://github.com/user-attachments/assets/c16fa11b-39ad-4b6a-b1f4-74f37d883252" /> \
<img width="427" alt="image" src="https://github.com/user-attachments/assets/8c916012-eb9e-4ed3-8645-1bb431294153" />


Cyclic redundancy check(CRC) is used in check_fw() which could be easily bypassed as long as the hackers craft a compromised firmware with the same CRC value as the new firmware. Therefore, the firmware integrity verification vulnerability arises which makes the compromised firmware could be written into the IoT device and cause arbitrary code execution or denial of service.
<img width="599" alt="image" src="https://github.com/user-attachments/assets/0f19ca8e-3108-4848-90c4-a2e89d224ab7" />





