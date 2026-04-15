# Firmware Authentication Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware update process, there is a firmware authentication vulnerability in function find_hwid() and new_gui_update_firmware() of program ssi. The firmware uses hard-coded verification information in the authentication verification. In particular, these two functions extract the hardware ID of the firmware from the firmware image and store the hardware ID into the variable dest. Then, these two functions perform firmware authentication verification by comparing dest with the hard-coded authentication verification information: AP152AR9563-AP-150107-00, AP152AR9563-AP-151201-00, and AP152AR9563-AP-150707-00. Once the hackers obtain the hard-coded authentication verification, the hackers could easily bypass the authentication verification and upload maliciously compromised firmware. This issue in the firmware update process of Trendnet TEW-821DAP (firmware version:v1.12B01) allows attackers to execute arbitrary code or cause denial of service via uploading a compromised firmware with the same hard-coded authentication verification information as the new firmware for update.


<img width="416" height="273" alt="image" src="https://github.com/user-attachments/assets/bc04b116-a013-4d75-a958-4a3e9d3a8fbf" />

