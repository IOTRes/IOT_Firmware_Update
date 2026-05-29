# Command injection Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.11B03)

## Overview

During the firmware update process, there is command injection vulnerability in function sub_41FBD0 of program ssi. In the NTP client configuration, the variable `hostname` is directly concatenated into the NTP time synchronization command. However, this variable is propagated from the user input without any verification. Once the hackers control the user input, malicious command could be injected into the NTP time synchronization command.

<img width="487" height="109" alt="image-1" src="https://github.com/user-attachments/assets/964a6851-fe5b-4134-b4ac-5b38c45aeaab" />


The vulnerability trigger path is as the following:


```
HTTP POST /goform/system_ntp
  → NTP handler @ 0x40FC58
  → sprintf(cmd, "ntpclient -i %d -s -l -D -h %s", interval, hostname) @ 0x40FC80
  → system(cmd)
```
