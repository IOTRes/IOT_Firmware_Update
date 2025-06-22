# Firmware Authentication Verification Vulnerability in Firmware Update Process of Tenda AC15


## Affected Product
Tenda AC15 (firmware version: V15.13.07.13)

## Overview

During the process of firmware update, function upgrade() of program httpd calls function webCgiGetUploadFile() to obtain the new firmware image which will be uploaded to IoT device for update. 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/7f616563-3b8d-4caa-9bad-75bb87957aa2" />


After that, function tpi_upfile_handle() is called to verify the new firmware image. 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/74d9ef30-1e0d-4fb8-8698-d2bc6db55a73" /> \
<img width="468" alt="image" src="https://github.com/user-attachments/assets/4bf0deae-b263-4055-9dd2-dea6d8558638" />


 
However, there is authentication firmware verification vulnerability in tpi_upload() called by tpi_upfile_handle().
<img width="468" alt="image" src="https://github.com/user-attachments/assets/473b795e-9860-49d8-a4f8-e84216fd39d5" /> \
<img width="427" alt="image" src="https://github.com/user-attachments/assets/17de2436-db56-4cab-8d01-18691f851854" />

 

Hard-coded authentication verification information is applied in function check_fw_type() and split_fireware() called by check_fw() of tpi_upload(). These two functions use hard-coded number to verify the new firmware image, which could be easily bypassed as long as the hackers craft a compromised firmware with the same hard-coded number. Therefore, authentication verification vulnerability arises since hackers could replace the compromised firmware with new firmware to execute arbitrary code or cause denial of service.



check_fw_type():
 
<img width="396" alt="image" src="https://github.com/user-attachments/assets/b7d6108d-2780-434c-95f6-af3e5e25ff52" /> \
<img width="262" alt="image" src="https://github.com/user-attachments/assets/26bcdb50-46df-4cc5-8564-1340814970ae" />



split_fireware()
 
<img width="357" alt="image" src="https://github.com/user-attachments/assets/3739e0e5-b374-4b1a-b04d-ac917ad49dcf" /> \
<img width="468" alt="image" src="https://github.com/user-attachments/assets/2ad50904-6d08-4761-b6bf-2318972bbb89" />




