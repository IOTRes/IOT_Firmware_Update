# Firmware Download Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware update process, there is a firmware download vulnerability in program ssi(/www/cgi/ssi). In the firmware download, the device applies hard-coded firmware download url and use http protocol instead of https protocol. Therefore, the firmware download is vulnerable to the MITM attack. Once the hackers obtain the url, they could overwrite the url to perform firmware modification attack or redirect it to a malicious url to perform redirection attack.

<img width="416" height="45" alt="image" src="https://github.com/user-attachments/assets/768845d8-69df-4864-8379-4d3c83cd8258" />

