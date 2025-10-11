# Firmware Authentication Verification Vulnerability in Firmware Update Process of Tenda RP3 Pro


## Affected Product
Tenda RP3 Pro(firmware version:  V22.5.7.93)

## Overview

During the firmware update process, there is firmware authentication verification vulnerability in force_upgrade.sh. To be specific, the firmware verification vulnerability includes the use of hard-coded authentication verification information and improper authentication verification. The firmware image name xs7302 is stored as hard-coded information in variable current_soc_name. The firmware password Td2N3ww1.0_tenda_force_upgrade is stored as hard-coded information in variable current_force_upgrade_pwd. In addition, force_upgrade.sh obtains the force_upgrade_pwd from force_upgrade_info through offsetting 20 bytes. After that, performs authentication verification through comparing force_upgrade_pwd and current_force_upgrade_pwd. If the hackers obtain force_upgrade_pwd and current_force_upgrade_pwd, they could bypass the authentication verification. This issue in the firmware update process of Tenda RP3 Pro(firmware version:V22.5.7.93) allows attackers to execute arbitrary code or cause denial of service via uploading a compromised firmware with the same hard-coded verification information as the new firmware for update.

<img width="468" height="303" alt="image" src="https://github.com/user-attachments/assets/f75b719d-2165-4558-b46d-46caf2a25bb4" />\

<img width="468" height="196" alt="image" src="https://github.com/user-attachments/assets/8d190b98-8949-42ba-9b4a-a1cfe4e92262" />

