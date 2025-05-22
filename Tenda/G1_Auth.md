

There is firmware authentication verification vulnerability in function check_upload_file() called by function upgrade() of program httpd during the process of firmware update. 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/32f59758-3a29-4c6b-9eaf-0fc4a6587b86" />


Hard-coded authentication verification information is applied in function check_fw_valid() called by flash_check_fw() of check_upload_file(). check_fw_valid() use hard-coded number to verify the new firmware image, which could be easily bypassed as long as the hackers craft a compromised firmware with the same hard-coded number. Therefore, authentication verification vulnerability arises since hackers could replace the compromised firmware with new firmware to execute arbitrary code or cause denial of service.
<img width="468" alt="image" src="https://github.com/user-attachments/assets/c3efb6ec-ae28-4538-afdb-e12dbd20a260" />

<img width="467" alt="image" src="https://github.com/user-attachments/assets/b46a23ab-8fd0-4a8e-b68f-694f7ba73ee5" />

<img width="468" alt="image" src="https://github.com/user-attachments/assets/63bcc262-146c-4e1a-9ee3-7556bdc56068" />


