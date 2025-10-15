# Firmware Integrity Verification Vulnerability in Firmware Update Process of DLink DAP-2695

## Affected Product
Belkin AX1800 WiFi 6 Router (firmware version: V1.1.00.016)

## Overview

During the firmware update process, there is a firmware integrity verification vulnerability in function sub_40C6B8() of program rgbin. In the firmware integrity verification,  the first step is magic check. To be specific, function sub_40C6B8() reads the magic number from a1+32, then compares it with hard-coded verification information sub_40BEC0(537396001). Hackers could bypass the integrity verification by obtaining the magic number and hard-coded verification information. The second step is integrity verification. Function sub_40C51C() applies weak integrity verification algorithm MD5 to verify the firmware image for update. Hackers could forgery MD5 to bypass the integrity verification.

