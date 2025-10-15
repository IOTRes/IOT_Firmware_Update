# Firmware Integrity Verification Vulnerability in Firmware Update Process of DLink DAP-2695

## Affected Product
DLink DAP-2695 (firmware version: v2.00RC131)

## Overview

During the firmware update process, there is a firmware integrity verification vulnerability in function sub_40C6B8() of program rgbin. In the firmware integrity verification,  the first step is magic check. To be specific, function sub_40C6B8() reads the magic number from a1+32, then compares it with hard-coded verification information sub_40BEC0(537396001). Hackers could bypass the integrity verification by obtaining the magic number and hard-coded verification information. The second step is integrity verification. Function sub_40C51C() applies weak integrity verification algorithm MD5 to verify the firmware image for update. Hackers could forgery MD5 to bypass the integrity verification.

<img width="267" height="293" alt="image" src="https://github.com/user-attachments/assets/b0601288-69f9-4b55-97b1-c68ee44a2e20" />

<img width="261" height="272" alt="image" src="https://github.com/user-attachments/assets/0f17da86-07e1-4e91-8744-23075a438be5" />

<img width="250" height="303" alt="image" src="https://github.com/user-attachments/assets/8f1f9714-89cc-481f-a686-038ac61a096d" />


