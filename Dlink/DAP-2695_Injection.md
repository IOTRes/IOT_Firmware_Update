# Command Injection Vulnerability in Firmware Update Process of DLink DAP-2695

## Affected Product
DLink DAP-2695 (firmware version: v2.00RC131)

## Overview

During the firmware update process, there is a command injection vulnerability in function sub_4174B0 of program httpd. The network data dword_444084 could be propagated to system command execution function and become part of the function parameters. During the propagation process, there is no verification on  network data dword_444084. If the hackers control the network data dword_444084, they could inject and execute malicious code. This issue in the firmware update process of Dlink DAP-2695(firmware version:v2.00RC131) allows attackers to execute arbitrary code or cause denial of service via constructing a malicious command and injecting it into network data.

The exploit chain of command injection vulnerability is upload_captival_tar -> sub_417298(dword_444084->dest) -> sub_4174B0(dest->src) -> sprintf(command, 0xFFu, "rm -f /var/captival_tar/%s\n", src) -> system(command)

<img width="468" height="291" alt="image" src="https://github.com/user-attachments/assets/913d0c41-d8da-4249-b727-d5f666e4d988" />\


<img width="399" height="383" alt="image" src="https://github.com/user-attachments/assets/563ac8df-a831-49ec-9b56-52fad0656c66" />\

<img width="468" height="71" alt="image" src="https://github.com/user-attachments/assets/67390b8f-6245-43de-90f0-0cd6705db183" />\

<img width="468" height="277" alt="image" src="https://github.com/user-attachments/assets/61c822b6-1f74-4fca-a9e2-de35955c7ad9" />\


