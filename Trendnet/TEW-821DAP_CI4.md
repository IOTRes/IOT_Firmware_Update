# Command injection Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.11B03)

## Overview

During the firmware update process, there is command injection vulnerability in function sub_42026C of program ssi. In the concatenation of DDNS configuration strings, variables `hostname`, `username`, and `password` are directly concatenated into the configuration strings. Then, the configuration strings is written into config file and the DDNS restart command is executed.  However, these variables are propagated from the user input without any verification. Once the hackers control the user input, malicious command could be injected into the configuration strings.


<img width="409" height="129" alt="image" src="https://github.com/user-attachments/assets/b8a68acc-0bd5-4e86-8114-e0196feed352" />


The vulnerability trigger path is as the following:



```
HTTP POST /goform/tools_ddns
  → ssi CGI dispatch table → DDNS handler @ 0x4137D0
  → sprintf(config, "ddns_hostname=%s&ddns_username=%s&ddns_password=%s", ...) @ 0x4137F0
  → config file writing → system("/etc/init.d/ddns restart")
```
