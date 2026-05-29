# Command injection Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.11B03)

## Overview

During the firmware update process, there is command injection vulnerability in function sub_43F2C4 of program ssi. During the construction of DNS lookup command, variables `nslookup_target` and `dns_server` are concatenated directly to the DNS lookup command. However, these two variables are propagated from user input without any verification. Once the hackers control the user input, malicious command could be injected to the  DNS lookup command.

<img width="1010" height="195" alt="image" src="https://github.com/user-attachments/assets/1c1f8638-2301-439d-8984-a0217978925a" />


The vulnerability trigger path is as the following: 

```
HTTP POST /goform/tools_nslookup
  → ssi CGI dispatch table → handler @ 0x41EC14
    → sprintf(cmd, "nslookup %s %s", nslookup_target, dns_server) @ 0x41EC30
  → system(cmd) @ 0x41EC50
```
