
There is firmware integrity verification vulnerability in function check_upload_file() called by function upgrade() of program httpd during the process of firmware update. 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/0a10d05f-9ebc-4bfd-ac49-951d2a542cbf" />

 
Cyclic redundancy check(CRC) is used in check_upload_file() which could be easily bypassed as long as the hackers craft a compromised firmware with the same crc value as the new firmware. Therefore, the firmware integrity verification vulnerability arises which makes the compromised firmware could be written into the IoT device and cause arbitrary code execution or denial of service.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/51c71358-34ea-49b0-92a5-7092fb2aac6f" />

