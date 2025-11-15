# Command Injection Vulnerability in Firmware Update Process of DLink DAP-2695

## Affected Product
DLink DAP-2695 (firmware version: v2.00RC131)

## Overview

During the firmware update process, there is a command injection vulnerability in function upload_certificate() of program httpd. The private key file and CA file is uploaded by the users through pcVar1 where param3 is the user input. Then function FUN_00416dd8 executes system command to commit private key, certificate or delete old certificate. However FUN_00416dd8 takes pcVar1 as the parameter of system execution function and there is no verification on pcVar1. Once the hackers control pcVar1, they could inject malicious command in pcVar1. The malicious command would be passed to system execution function through parameters. This issue in the firmware update process of Dlink DAP-2695(firmware version:v2.00RC131) allows attackers to execute arbitrary code or cause denial of service via constructing a malicious command and injecting it into pcVar1.

<img width="445" height="299" alt="image" src="https://github.com/user-attachments/assets/d8caf91a-1eda-4811-9781-5478a9d57482" />
<img width="468" height="274" alt="image" src="https://github.com/user-attachments/assets/03da343d-c237-4307-b06b-8764c2fe7eb1" />
