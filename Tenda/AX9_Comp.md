# Firmware Compatibility Verification Vulnerability in Firmware Update Process of Tenda AX9


## Affected Product
Tenda AX9 (firmware version: V22.03.01.46)

## Overview

During the firmware update process there is a compatibility verification vulnerability in function image_check() of program httpd.

<img width="468" height="234" alt="image" src="https://github.com/user-attachments/assets/9d05fe06-290d-4ce3-89ed-d4319e46c9a5" />

Hard-coded compatibility verification is applied to verify the product name v10. Once the hackers obtain the hard-coded compatibility verification information 4f70656e577274206667756c6c696d6167, they can bypass or disable the compatibility verification, which could cause denial of service.

<img width="468" height="272" alt="image" src="https://github.com/user-attachments/assets/3da2fba0-dba5-4676-8cad-eddeffb5a96a" />
